# This Project is about CI / CD using Jenkins & Git WebHook Automation

## (CI/ CD using Jenkins and ngrok)



1. Start Jenkins:


![image alt](---image address---)



2.Log in to Jenkins:

![image alt](---image address---)



## Configure Jenkins:

1. Go to Credentials:

![image alt](---image address---)



2. Then go to _**Stores scoped to Jenkins**_

![image alt](---image address---)








Then Global credentials (unrestricted):

![image alt](---image address---)



Then type in your Github username in the username field and a token (can be created by going to Settings in Github> Developer Settings> Personal Access token> Tokens (classic) ) in the password field:


![image alt](---image address---)



And Create the Credentials.

![image alt](---image address---)



It will look something like this.


![image alt](---image address---)







## Creating a Pipeline

Create a new Item > Select Pipeline:


![image alt](---image address---)


![image alt](---image address---)






## Configure Pipeline:

![image alt](---image address---)

![image alt](---image address---)


Select Pipeline script from SCM:



a. Then in SCM choose Git
b. Paste your github link
c. And then choose the previously created Credentials:



![image alt](---image address---)







Then Specify the Branch of your repo: (master/main)

![image alt](---image address---)


And proceed to_ **Pipeline Syntax**_

## Pipeline Syntax

![image alt](---image address---)

Choose git:Git from the Sample step dropdown menu

Fill in:


![image alt](---image address---)


Then Click on Generate Pipeline Script:

![image alt](---image address---)


Copy this Script and keep it somewhere




Then go back to the Pipeline Configure page and :

![image alt](---image address---)



Choose Apply and then Save.




Then go to your github repo:

And open Jenkins file and edit it:


![image alt](---image address---)



Then add the Pipeline Script to the Jenkins file:

![image alt](---image address---)




Then go back to the Jenkins Dashboard:

Select Plugin > Available Plugins

And install Docker and Docker Pipeline Plugin (if its not already installed)


![image alt](---image address---)

![image alt](---image address---)



Then proceed to Build the pipeline:
(Docker must be running on the host machine)


![image alt](---image address---)


This is the output:


![image alt](---image address---)


If any error persists, check the ‘Console Output’ that will display below the ‘Changes’ when error occurs.





# Now Proceeding to ngrok:


## Install ngrok on your machine



type this command on terminal:


ngrok http http:// <your_private_ip>:<ngrok_port>


example:

ngrok http http://:192.168.x.x:8080


This will appear:

![image alt](---image address---)





Copy this url to somewhere safe:

![image alt](---image address---)



Enter this url on browser:

![image alt](---image address---)



And then view site:

![image alt](---image address---)




You might incur error like this.

To fix, try this:

enter: 

ngrok http 8080 

on terminal

And then go to the url provided there:


![image alt](---image address---)


The Jenkins Page will show now:

![image alt](---image address---)




## Sign in using your jenkins credentials:

Ngrok will redirect to the Jenkins Portal:

![image alt](---image address---)




Now go to your github project (jenkins-test-12, in my case):

Go to settings > Webhooks

![image alt](---image address---)



## Then Add Webhook

and paste the link obtained from terminal after the command: ngrok http 8080:

https://<link_obtained_from_terminal>/github-webhook/


example:

https://6256-203-9-x-x.ngrok-free.app/github-webhook/


![image alt](---image address---)



This will show:


![image alt](---image address---)



## Back to the Jenkins Page

This is the Jenkins Page right now:

![image alt](---image address---)


And this is the original html file:


![image alt](---image address---)



Then Go back to the Jenkins Page > Configure and enable hook trigger:


![image alt](---image address---)












Once I make changes here and push it to github:


![image alt](---image address---)







## The Jenkins page autoamtically runs the build process:

![image alt](---image address---)




And that is this project for CI/ CD using Jenkins and Ngrok.
