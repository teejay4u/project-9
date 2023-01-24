# project-9
>># TOOLING WEBSITE DEPLOYMENT AUTOMATION WITH CONTINUOUS INTEGRATION. INTRODUCTION TO JENKINS 

># Project Description
 >> This project focusses on automation of routine tasks using Jenkins (a CI/CD tool). The previous project was enhanaced by adding a Jenkins server which was configured to automatically deploy source code changes from Git to NFS server, as seen in the project diagram below ;
 ![](Diagram%20of%20Project.png) 

>> The Following steps were taken to complete this project successfully:
1. The first thing was to spin up an EC2 machine in AWS running linux ubuntu version 20.04 LTS  along with the created NFS server 
![](/1.%20Jenkins-Server%20installed.png)

2. Installing JDK (Java Development kits)
    - sudo apt install default-jdk-headless
![](2.%20Installing%20JDK%20Application%20.png)

3. Installing Jenkins on Server 
 - wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
 - sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
 -   /etc/apt/sources.list.d/jenkins.list'
 - sudo apt update
 - sudo apt-get install jenkins
 - Ensuring Jenkins is up and running sudo systemctl status jenkins 
 ![](3.%20Installing%20Jenkins.png)
 ![](4.%20Jenkins%20running%20.png)

4. Next port 8080 was opened in the security group of the server on TCP protocol
![](Opening%20Port%2080%20in%20security%20group%20of%20Jenkins-Server.png) 

5. Accessing Jenkins on public IP of server on 8080
 ![](/5.%20Jenkins%20Initial%20setup%20page.png)

6. Retrieving administrator password from the directory ;
  - sudo cat /var/lib/jenkins/secrets/initialAdminPassword

7. Jenkins was the installed and its plugins on the server 

8. Configuring Jenkins to retrieve source codes from Github using webhooks
![](6.%20Creating%20Webhook%20for%20Jenkins.png)
![](7.%20configuring%20Jenkins%20file.png)

9. Configuring Build triggers and post-build actions 
![](/8.%20Configuring%20Build%20triggers.png)
![](/9.%20Configuring%20Post-Build%20actions%20.png)

10. Configuring Jenkins to copy files to NFS server Via SSH by installing Publish over SSH plugin and setting it up.
![](11.%20Installing%20Publish%20over%20ssh%20plugin.png)
![](/Editing%20send%20build%20artifacts%20over%20ssh.png)

11. Successfully automated changes to update on NFS-Server
![](7.%20Successful%20Build.png)

