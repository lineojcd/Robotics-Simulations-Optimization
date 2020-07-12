# Jenkins Tutorial
A detailed installation tutorial ```Jenkins Installation Guide.pdf``` can be found in the current folder.
  
## Pre-installation check
**Java8** and **python 3.6+** is need for installing Jenkins. 

To check if you have Java8 or not, type the command in your terminal:
```
java -version
```
To check if you have python3 or not, type the command in your terminal:
```
python3
```

## Install Jenkins on ubuntu
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```
Now, we are done with Jenkins Installation!

## Jenkins Service
You can start the Jenkins service with the command:
```
sudo systemctl start jenkins
```
You can check the status of the Jenkins service using the command:
```
sudo systemctl status jenkins
```
You can stop the Jenkins service with the command:
```
service jenkins stop
```
## Connect to Jenkins Dashboard 
```
http://localhost:8080/
```
#### Authentification for first time connection: 
If you are the first time to connect to Jenkins dashboard, it will ask your password. 
Just follow what it instructed by typing the command at the terminal and copy the password back to unlock Jenkins : 
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

## Configuration on Jenkins
Once the above steps succeed, you will be able to see as follows. Click on **Install suggested plugins** and the plugins are about to be installed.

![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/customize_jenkins.jpg)
![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/install_plugins.png)

click on **Install suggested plugins** and the plugins are about to be installed: 

## Create Jenkins account
Create Jenkins account by typing  ```Username, PWD, Full name, E-mail address```.
Once you have finished all the above steps, you will be able to see the welcome messages from  the Jenkins Dashboard.

## Install Blue Ocean
**Blue Ocean produce better UI for Jenkins**, 
you can see more descriptions about Blue Ocean here
: https://www.jenkins.io/blog/2016/05/26/introducing-blue-ocean/ 
A detailed installation tutorial ```Install Blue Ocean.pdf``` can be found in the current folder.

Step 1: Go to Jenkins Dashboard, click **Manage Jenkins**

![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/manage_jenkins.png)

Step 2: Click **Manage Plugins**

![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/manage_jenkins_1.png)

Step 3: At **Available** tab, type “Blue Ocean” into the search box

![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/manage_jenkins_2.png)

Step 4: Find the **Blue Ocean** plug-in and click “Download now and install after restart”.
 Now the related plugins are about to download and install.
 
![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/manage_jenkins_3.png) 
![customize jenkins](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/manage_jenkins_4.png)

Follow the instructions on the above picture and restart your Jenkins.

## Accessing Blue Ocean
Once a Jenkins environment has Blue Ocean installed, after logging in to the Jenkins classic UI, you can access the Blue Ocean UI by clicking Open Blue Ocean on the left. ![open_blue_ocean](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/open_blue_ocean.png)


