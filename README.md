# Red Hat OpenShift for Web Development
This tutorial aims to introduce some of the features in OpenShift that are useful for building web applications using S2I and Docker Images.<br>
In this tutorial you will learn:<br>
- Building web applications and deploying on OpenShift from scratch
- autotmating deployment using GitHub Webhooks
- Scaling Applications
- Update and Rollback
## Prerequisites
- Create your IBM Cloud account for free <a href="#">here</a>.
- Access to free OpenShift Cluster:
  - URL:
  - Key:
- OC CLI. You can install it on your machine or use the CLI on IBM Cloud <a href="#">here</a>.
## Steps
### Fork this Repository
You will need to fork this repository because you will be making changes in your code.
### Create Project
On the web console, go to <b>Projects</b> and click 'Create Project'. Name it 'my-flask-project'.
### Create Application from GitHub
Switch to the Developer Perspective, and from the topology create application from Git.<br>
![topology](https://user-images.githubusercontent.com/36239840/99640028-d47ba780-2a61-11eb-9345-eef6da18b245.JPG)
Copy the URL of the GitHub repository that you forked and paste it under 'Git Repo URL', and choose Python 3.6 for your builder image, then click 'Create'.<br>
![git app](https://user-images.githubusercontent.com/36239840/99640275-1b699d00-2a62-11eb-9d8d-aab23c988e93.JPG)
Once created, you will be redirected to the topology view where you can view your pods. Once the application is built successfully, the pod will turn from light blue to dark blue. You can access the URL of the application from the top corner of the pod as shown in the image.<br>
![app](https://user-images.githubusercontent.com/36239840/99641007-2244df80-2a63-11eb-85b4-20b575721aa3.JPG)
You will be redirected to a simple Hello World page.<br>
![hello world](https://user-images.githubusercontent.com/36239840/99641191-5cae7c80-2a63-11eb-8f98-71ca6aef8bc2.JPG)
If you add ```/version``` at the end of the URL, you will be redirected to a different route with the following details.<br>
![version](https://user-images.githubusercontent.com/36239840/99641407-a7c88f80-2a63-11eb-8603-e2189a76d3c9.JPG)
### Scale application
To scale your application, you can simply do it on the web console by clicking on top arrow.<br>
![scale](https://user-images.githubusercontent.com/36239840/99646668-32ac8880-2a6a-11eb-9a2f-a7dfb898a1bb.JPG)
If you go to Deployments -> Deployment Details -> Pods, you will find the newly created replicas.<br>
![replicas](https://user-images.githubusercontent.com/36239840/99646767-55d73800-2a6a-11eb-9122-1b26aa0546e8.JPG)

### Connect Application to GitHub Webhook
Go to <b>Builds</b> where you can show Build Configs. Click on 'my-flask-app' where you will be redirected to an overview page of the build configs of the application.<br>
![builds](https://user-images.githubusercontent.com/36239840/99652342-25df6300-2a71-11eb-9cc6-5cc0618ac935.JPG)
Scroll all the way down to Webhooks and copy the URL with secret (usually go for the GitHub URL, but if it fails for some applications the Generic URL would still work and you can go for it as well).<br>
![webhooks](https://user-images.githubusercontent.com/36239840/99652613-7656c080-2a71-11eb-993d-8a18d6059c04.JPG)
Now go to Settings in your GitHub repository, then go to Webhooks tab where you can find an 'add webhook' button, when you click it, you will be prompted to enter your password, then you will be redirected to a new page. Paste the copied URL under 'Payload URL' as shown below. You can go with the default settings and then 'add webhook'.<br>
![git webhooks](https://user-images.githubusercontent.com/36239840/99653384-5e337100-2a72-11eb-9a5c-eb1b4008d057.JPG)


### Make Changes to application
Now that you have connected your application to GitHub Webhook, make a change in app.py file by adding the following lines right above line 16.
```
@app.route('/test')
def get_test():
    return 'You are accessing /test endpoint'
```
### See Changes on Web Console
