# 使用 Terraform 一键自动安装 Kubernetes 和 KubeSphere

* 使用 Terraform 作用是不需要用户在 iaas 平台上单独创建机器，配置好参数之后由Terraform自动创建，实现一键自动化部署。
* 单节点的安装主要分为三部分，var.tf、kubesphere.tf 和 install.sh，以下文件内容只需要修改API密钥值就可以部署 KubeSphere 集群。

### 执行步骤说明
* 安装 terraform 工具
* 创建一个目录，把 var.tf、kubesphere.tf 和 install.sh 三个文件放到该目录下。
* 修改 iaas 的 API 密码
* 进入目录下执行 `terraform init` 指令，显示成功。
* init 成功之后，然后执行 `terraform apply` 即可就开始创建机器，安装 KubeSphere。
* 删除机器指令操作为 `terraform destroy`

### 1、terraform 安装（单独一台机器）
* 以 centos 操作系统为例来安装，需要执行以下指令即可。
* 其余操作系统，参考[terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started)

```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install terraform
```
* 是否安装成功及版本输出

`terraform version`

### 2、var.tf文件说明
* access_key 和 secret_key 为必填项。点击 iaas 用户--》 API 密钥--》创建即可，然后把两个参数填入到下面的配置文件中。zone 可以根据自己需求来修改，默认 pek3a。

```
terraform {
  required_providers {
    qingcloud = {
      source = "shaowenchen/qingcloud"
      version = "1.2.6"
    }
  }
}

variable "access_key" {
  default = "***"
}

variable "secret_key" {
  default = "***"
}

variable "zone" {
  default = "pek3a"
}

provider "qingcloud" {
  access_key = "${var.access_key}"
  secret_key = "${var.secret_key}"
  zone = "${var.zone}"
}
```

### 3、kubesphere.tf文件说明
* resource qingcloud_eip 为创建外网ip，也可以用已存在外网 IP，如果用已存在外网 ip，就不需要 qingcloud_eip resource 模块。
* qingcloud_security_group 为创建防火墙，也可以使用已存在防火墙，同理。
* qingcloud_security_group_rule 为创建防火墙开放的端口。
* qingcloud_keypair 为密钥创建，此处注释掉，用密码形式。
* qingcloud_instance 创建机器，包含名字，操作系统，内存，cpu，磁盘，密码，绑定外网 IP，防火墙，子网和类型等。
* null_resource 和 install_kubesphere 包含文件拷贝及执行命令。

```
resource "qingcloud_eip" "init"{
  name = "tf_eip"
  description = ""
  billing_mode = "traffic"
  bandwidth = 20
  need_icp = 0
}

resource "qingcloud_security_group" "basic"{
  name = "防火墙"
  description = "这是第一个防火墙"
}

resource "qingcloud_security_group_rule" "openport" {
  security_group_id = "${qingcloud_security_group.basic.id}"
  protocol = "tcp"
  priority = 0
  action = "accept"
  direction = 0
  from_port = 22
  to_port = 40000
}

# qingcloud_keypair upload an SSH public key
# In this example, upload ~/.ssh/id_rsa.pub content.
# You may not have this file in your system, you will need to create your own SSH key.
#resource "qingcloud_keypair" "arthur"{
#  name = "arthur"
#  public_key = "${file("~/.ssh/id_rsa.pub")}"
#}

resource "qingcloud_instance" "init"{
  count = 1
  name = "master-${count.index}"
  image_id = "centos76x64a"
  cpu = "16"
  memory = "32768"
  instance_class = "0"
  managed_vxnet_id="vxnet-0"
#  keypair_ids = ["${qingcloud_keypair.arthur.id}"]
  login_passwd = "Qcloud@123"
  security_group_id ="${qingcloud_security_group.basic.id}"
  eip_id = "${qingcloud_eip.init.id}"
}

resource "null_resource" "install_kubesphere" {
  provisioner "file" {
    destination = "./install.sh"
    source      = "./install.sh"

    connection {
      type        = "ssh"
      user        = "root"
      host        = "${qingcloud_eip.init.addr}"
      password    = "Qcloud@123"
#      private_key = "${file("~/.ssh/id_rsa")}"
      port        = "22"
    }
  }

  provisioner "remote-exec" {
    inline = [
      "sh install.sh"
    ]

    connection {
      type        = "ssh"
      user        = "root"
      host        = "${qingcloud_eip.init.addr}"
      password    = "Qcloud@123"
 #     private_key = "${file("~/.ssh/id_rsa")}"
      port        = "22"
    }
  }
}
```

### 4、install.sh 文件说明
* 具体执行命令

```
export KKZONE=cn
curl -sfL https://get-kk.kubesphere.io | VERSION=v1.0.1 sh -
chmod +x kk
yum install -y vim openssl socat conntrack ipset
./kk create cluster --with-kubesphere -y
```

### 5、执行及删除
* 进入目录，执行init，出现successfully字样。
* terraform apply, 输入yes开始安装。
* terraform destroy

```
[root@node4 ~]# cd terraform
[root@node4 terraform]# ls
install.sh  kubesphere.tf  var.tf
[root@node4 terraform]# terraform init

Initializing the backend...

Initializing provider plugins...
Terraform has been successfully initialized!

[root@node4 terraform]# terraform apply

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create
Enter a value: yes
```

### 6、参考
https://github.com/yunify/terraform-provider-qingcloud