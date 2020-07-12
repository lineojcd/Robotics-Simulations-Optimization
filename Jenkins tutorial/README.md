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
Once a Jenkins environment has Blue Ocean installed, after logging in to the Jenkins classic UI, you can access the Blue Ocean UI by clicking the icon ![open_blue_ocean](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/open_blue_ocean.png) on the left. 

You will see the pipeline that has been run, click on the record.

![pipeline_blue_ocean](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_blue_ocean.png)

You will see the advanced pipeline visualisations.

![pipeline_visualisations_blue_ocean](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_visualisations_blue_ocean.png)

## Switching to the classic UI
Click the Go to classic icon 
![Switching to the classic UI](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/switching_to_the_classic_UI.png)
 at the top of common section of Blue Ocean’s navigation bar to get back to the classic UI.
 
## Create Jobs and Pipeline in Jenkins
Here are some tutorials that introduce how to create jobs and pipeline: https://www.youtube.com/watch?v=m0a2CzgLNsc and https://opensource.com/article/19/9/intro-building-cicd-pipelines-jenkins. Our detailed tutorial ```Jenkins Create Jobs and Pipeline.pdf``` can also be found in the current folder.

### Case 1: Create through a direct script
**Step 1: Create a new Jenkins job**: Click **Create New Jobs**. You can also click **New Item** on the left.

![create_new_job](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/create_new_job.png)

**Step 2: Create a pipeline job**

In this step, you can select and define what type of Jenkins job you want to create. Select **Pipeline** and give it a name (e.g., TestPipeline). Click **OK** to create a pipeline job.

![select_pipeline](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/select_pipeline.png)

**Step 3: Configure and execute a pipeline job through a direct script** 

To execute the pipeline with a direct script, choose **Pipeline script** and copy the below script.  Notice that there are three Stages: Build, Test, and Deploy, which are arbitrary and can be anything. Inside each Stage, there are Steps.  In this example, they just print some random messages.
```
pipeline {
   agent any

   stages {
      stage('Build') {
        steps {
          echo 'Building...'
          echo "Running ${env.BUILD_ID} ${env.BUILD_DISPLAY_NAME} on ${env.NODE_NAME} and JOB ${env.JOB_NAME}"
        }
   }
   stage('Test') {
     steps {
        echo 'Testing...'
     }
   }
   stage('Deploy') {
     steps {
       echo 'Deploying...'
     }
   }
  }
}
```
![pipeline_build](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_build.png)

To start the process to build the pipeline, click **Build Now**. If everything works, you will see your first pipeline (like the one below).

![pipeline_script](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_script.png)

To see the output from the pipeline script build, click any of the Stages and click **Log**. You will see a message like this.
![pipeline_log](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_log.png)

You can also see this pipeline in Blue Ocean with a better UI.

### Case 2: Create through a SCM
**Step 4 Configure and execute a pipeline job with SCM** 

Now, switch gears: In this step, you will deploy the same Jenkins job by copying the **Jenkinsfile** from a source-controlled GitHub(https://github.com/bryantson/CICDPractice.git).

![pipeline_scm](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_scm.png)

Click **Configure** to modify the existing job. Scroll to the **Advanced Project Options** setting, but this time, select the **Pipeline script from SCM** option in the **Destination** dropdown. Paste the GitHub repo's URL in the **Repository URL**, and type **Jenkinsfile** in the **Script Path**. Save by clicking the **Save** button.

![pipeline_scm_conf](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/pipeline_scm_conf.png)

To build the pipeline, click Build Now to execute the job again. The result will be the same as before, except you have one additional stage called **Declaration: Checkout SCM**.

![scm_conf_build](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/scm_conf_build.png)

To see the pipeline's output from the SCM build, click the Stage and view the **Log** to check how the source control cloning process went.

![scm_conf_log](https://github.com/lineojcd/Robotics-Simulations-Optimization/blob/master/Jenkins%20tutorial/src/scm_conf_log.png)

### Case 3 Create a pipeline with parallel stages

