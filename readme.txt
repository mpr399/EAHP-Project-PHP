How to run the Emergency Ambulance Hiring Portal Project using PHP and MySQL

1. Download the project zip file

2. Extract the file and copy eahp folder

3.Paste inside root directory(for xampp xampp/htdocs, for wamp wamp/www, for lamp var/www/Html)

4.Open PHPMyAdmin (http://localhost/phpmyadmin)

5. Create a database with the name  eahpdb

6. Import eahpdb.sql file(given inside the zip package in SQL file folder)

7. Run the script http://localhost/eahp

Admin Credential
Username: admin
Password: Test@123


#SonarQube:
-----------

#docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

#ip:9000

username admin; password admin

Sonarqube Scanner(Install Jenkins plugin)

Grab the Public IP Address of your EC2 Instance, Sonarqube works on Port 9000, so <Public IP>:9000.

Goto your Sonarqube Server. 

Click on Administration → Security → Users → Click on Tokens and Update Token → Give it a name → and click on Generate Token , 

Create a token with a name and generate

copy Token 

Goto Jenkins Dashboard → Manage Jenkins → Credentials → Add Secret Text


Now, go to Dashboard → Manage Jenkins → System

SonarQube Insatallations

Global Tool Configuration is used to configure different tools that we install using Plugins We will install a sonar scanner in the tools.

SonarScanner Insatallations

In the Sonarqube Dashboard add a quality gate also Administration → Configuration →Webhooks

Click on Create

#webhook:
---------

In Jenkins server:

#ssh-keygen

#cd .ssh

#ls

#cat id_rsa.pub

(copy and paste this in New SSH Key in github)

The Jenkins pipeline will be triggered automatically by GitHub webhook integration when changes are made to the code repository

>Go to your GitHub account settings.

>Go to SSH and GPG keys, Add public key that we created using ssh-keygen and select key-type Authentication key

>Go to your GitHub repository and click on Settings

>Click on Webhooks and then click on Add webhook.

>In the ‘Payload URL’ field, paste your Jenkins environment URL. At the end of this URL add /github-webhook/. In the ‘Content type’ select: ‘application/json’.(e.g:http://ip:8080/github-

webhook/)

>Manage Jenkins >Manage plugins > Available plugins > install 'github integration' plugin

>In build Triggers, select ‘Github hook trigger for GITScm polling

>Now run Job
