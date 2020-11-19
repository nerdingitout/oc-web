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
### Scale application
### Connect Application to GitHub Webhook
### Make Changes to application
Now that you have connected your application to GitHub Webhook, make a change in app.py file by adding the following lines right above line 16.
```
@app.route('/test')
def get_test():
    return 'You are accessing /test endpoint'
```
### See Changes on Web Console
