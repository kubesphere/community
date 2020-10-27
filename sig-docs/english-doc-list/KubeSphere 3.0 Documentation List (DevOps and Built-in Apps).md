# KubeSphere 3.0 Documentation List (DevOps and Built-in Apps)

Below are lists of guides that need to be written as part of KubeSphere documentation 3.0. Please add your name under **Writer** to claim the task. When you submit your pr, put the PR link under **PR Link**.

## DevOps User Guide & Administration

### Overview

| Guide                                                        | Writer | PR Link | Language (En/Zh) |
| ------------------------------------------------------------ | ------ | ------- | ------ | 
| Introduction                                                 |        |         |        |     
| Create a Pipeline - using Graphical Editing Panel            |        |         |        | 
| Create a Pipeline - using Jenkinsfile                        |        |         |        | 
| Pipeline Management (including webhook, Timing trigger, etc.） |        |         |        | 
| Credential Management                                        |        |         |        | 
| Role and Member Management                                   |        |         |        | 
| Artifactory Management                                       |        |         |        | 
| Add new types of pod for pipeline                            |        |         |        | 

### How to Integrate

| Guide                                    | Writer | PR Link | Language (En/Zh) |
| ---------------------------------------- | ------ | ------- | ------ | 
| Integrating SonarQube in Pipeline        |        |         |        |   
| Integrating Harbor in Pipeline           |        |         |        |   
| Integrating Nexus in Pipeline            |        |         |        |   
| Integrating Jrog Artifactory in Pipeline |        |         |        |   

### Pipeline Example

| Guide                                                  | Writer | PR Link | Language (En/Zh) |
| ------------------------------------------------------ | ------ | ------- | ------ | 
| How to compile and deploy a Maven project              |        |         |        |   
| How to compile and deploy a Spring Cloud project       |        |         |        |   
| How to compile and deploy a nodejs project             |        |         |        |   
| How to compile and deploy a Go project                 |        |         |        |   
| How to compile and deploy a Python project             |        |         |        |   
| How to run automated testing                           |        |         |        |   
| How to deploy applications cross multiple clusters     |        |         |        |   
| How to deploy a microservice application based on K8s |        |         |        |   

## App Store

As for the apps documentation, in addition to basic deployment on KubeSphere, Some apps need to be provided with simple demos and instruct the users on how to expose the app's service to other services or expose its dashboard. 

### Built-in App Deployment

| Guide                                       | Writer | PR Link | Language (En/Zh) |
| ------------------------------------------- | ------ | ------- | ------ | 
| Deploy Tomcat in KubeSphere                 | wenxin       |         |       |  
| Deploy Redis in KubeSphere                  | yaping liu       |         |       |  
| Deploy MySQL in KubeSphere                  | wenxin       |         |       |  
| Deploy Redis Exporter in KubeSphere         |        |         |       |  
| Deploy MySQL Exporter in KubeSphere         |  Guangzhe Huang      |    https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/get-started/monitor-mysql/     |
| Deploy RabbitMQ in KubeSphere               | wenxin       |         |       |  
| Deploy Memcached in KubeSphere              |        |         |       |  
| Deploy PostgreSQL in KubeSphere             |        |         |       |  
| Deploy NGINX in KubeSphere                  | yaping liu       |         |       |  
| Deploy MongoDB in KubeSphere                | yaping liu       |         |       |  
| Deploy Harbor in KubeSphere                 |        |         |       |  
| Deploy MinIO in KubeSphere                  |        |         |       |  
| Deploy Porter in KubeSphere                 |        |         |       |  
| Deploy etcd in KubeSphere                   |        |         |       |  
| Deploy Elasticsearch Exporter in KubeSphere |        |         |       |  

### From helm-charts Repo (excluding those shown above)

| Guide               | Writer | PR Link | Language (En/Zh) |
| ------------------- | ------ | ------- |  ------ | 
| APISIX              |        |         |        |  
| aws-ebs-csi-driver  |        |         |       |  
| aws-efs-csi-driver  |        |         |       |  
| aws-fsx-csi-driver  |        |         |       |  
| Snapshot Controller |        |         |       |  
| RBD Provisioner     |        |         |       |  
| Skywalking          |        |         |       |  
| Biz-engine          |        |         |       |  
| Csi-neonsan         |        |         |       |  
| Csi-qingcloud       |        |         |       |  
| GitLab              | [Hongliang Wang](https://github.com/hlwanghl) |         | En   |  
| ks-installer        |        |         |       |  
