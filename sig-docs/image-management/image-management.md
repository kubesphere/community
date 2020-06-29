# Image Management

You can insert images in your files where they can be accessed anywhere, creating a consistent experience for your readers. Here is an example of how you can use PicGo to pull images from QingStor.

## Getting Started

- You can check the [official introduction](https://picgo.github.io/PicGo-Doc/en/) of PicGo or click [here](https://github.com/Molunerfinn/PicGo/releases) to install it.
- You need an account to use object storage services (the example here is QingStor).

## Step

1. Log in the QingCloud [console](https://console.qingcloud.com/login) and click Access Key in the drop-down menu at the top right corner.

![api-key](https://ap3.qingstor.com/kubesphere-website/docs/access-key.png)

2. Click Create to create a new API Key and download it.

![create-api](https://ap3.qingstor.com/kubesphere-website/docs/create-key.png)

3. Launch PicGo and search for **qingstor-uploader** in Plugin Setting.

4. Install the plugin and click the gear icon to configure qingstor-uploader.

![qingstor-plugin](https://ap3.qingstor.com/kubesphere-website/docs/configure-qingstor.png)

5. For the first two fields, enter the API Key ID and Secret you have downloaded. You may see a configuration as below:

![qingstor-config](https://ap3.qingstor.com/kubesphere-website/docs/configure-api.png)

6. After you save the configuration, go back to this interface and select QingStor in the drop-down menu.

![select-qingstor](https://ap3.qingstor.com/kubesphere-website/docs/select-qingstor.png)

7. Drag and drop your image to PicGo.

8. Your image will display here where you can copy the link to use it.

![images](https://ap3.qingstor.com/kubesphere-website/docs/images.png)