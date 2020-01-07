# Create your own Jenkins Locally and CI



## What is Jenkins?? What is it used for??
Jenkins is an open source automation server written in java with plugins built for continuous integration purpose. It is used to build and test your software projects making it easier for developers to integrate changes.



## Building your own Jenkins Locally



1. Create a new repo for Jenkins



2. add your readme and gitignores



3. use the command **vagrant init** to create a vagrant file



4. set the vagrant file as shown in the file in this repo



5. create a bash provisioning file which contains the installation commands of Java and Jenkins, this is located in **jenkins.sh**



## Fire it up



1. use vagrant up to fire up the vm, in the script run make sure you see the default is installing the commands listed in the provisioning script.



2. Then **vagrant ssh**



3. go to your browser and type **localhost:8080**



4. It should prompt you for your password, which we will find in the next step.




## configure Jenkins



1. vagrant ssh then cd into this **/var/log/jenkins**



2. **sudo nano jenkins.log**



3. scroll to the bottom till it gives you a password, copy and past that in to the localhost:8080



4. Continue



5. Select your preferences & wait for completion



6. Create a Admin User fill in the credentials and save and Continue



7. You will get given a jenkins URL



8. you will be automatically redirected to the welcome page



YOU HAVE JENKINS RUNNING!!!



- to turn it off **vagrant halt**



## How to create a CI pipeline



1. Go on to your local Jenkins



2. Create a new job and name the item accordingly and build a freestyle software project.



3. Fill in the description



- click github project and past the project url



4. Go to **Source Code Management** and select **git** and enter the https link to the git repo
  - under the credentials click the add key and jenkins in the drop down
  - change kind to ssh username with private key
  - create a user name which is recognisable to your task
  - under private key click the enter directly button
  - https://medium.com/@mosheezderman/how-to-set-up-ci-cd-pipeline-for-a-node-js-app-with-jenkins-c51581cc783c
  - add public key to github, allow write access
  - add private key to jenkins

To install nodeJS do localhost:8080/configureTools
Manage jenkins > available > nodeJS





  5. Paste that into the repo url.



6. Go to **build triggers** and select **github hook trigger for GITScm polling** this will start the jenkins job on every git push on the master branch
  - this can be changed when your on your coruse code management, you can change your branches to build to another branch
  - to create another branch you can use the command **git checkout -b <branch name>**



7. Go to **build** and add a build step



8. Execute shell



9. In the commands section you want to enter the commands to run the tests



````
npm install
npm test



````



10. Adding a Git webhook
  - go to the Github repo
  - click settings > webhooks > add webhooks
  - go to ur jenkins and you want to get the url up to the port
    eg . http://localhost:8080/
  - paste it into payload url on github
  - add **github-webhook** as the end of the URl
  - then add the webhook button

  # Create new public and private key
  1. go to user/.ssh and enter the command ssh-keygen -t rsa
  2. Follow the steps and use cat to get the keys
