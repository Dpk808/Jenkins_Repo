# This Project is about CI / CD using Jenkins & Git WebHook Automation

## (CI/ CD using Jenkins and ngrok) 




1. Start Jenkins: 




![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.1%20Start%20Jenkins.png) 




2.Log in to Jenkins: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.2%20Logging%20In%20Jenkins.png) 




## Configure Jenkins: 


1. Go to Credentials: 

   

![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.3%20Manage%20Jenkins%2C%20Credentials.png) 




2. Then go to _**Stores scoped to Jenkins**_ 

   

![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.4%20Global%20Credentials.png) 









Then Global credentials (unrestricted):
![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.5%20Add%20Credentials.png)





Then type in your Github username in the username field and a token (can be created by going to Settings in Github> Developer Settings> Personal Access token> Tokens (classic) ) in the password field: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.5%20Credentials%20added.png) 




And Create the Credentials. 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/1.5%20The%20credentials%20page%20will%20show%20something%20like%20this.png) 




It will look something like this. 



## Creating a Pipeline 


Create a new Item > Select Pipeline: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/2.1%20Create%20a%20new%20Item.png) 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/2.2%20Create%20new%20Pipeline.png) 







## Configure Pipeline: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/3.1%20Pipeline.png) 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/3.2%20Pipeline%20Script.png) 



Select Pipeline script from SCM:



a. Then in SCM choose Git
b. Paste your github link
c. And then choose the previously created Credentials: 




![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/3.2%20Configure%20the%20Pipeline%20like%20this.png) 








Then Specify the Branch of your repo: (master/main) 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/3.3%20Selecting%20Branch.png) 



And proceed to _**Pipeline Syntax**_ 


## Pipeline Syntax 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/4.1%20Pipeline%20Syntax.png) 


Choose git:Git from the Sample step dropdown menu

Fill in: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/4.2%20Fill%20in%20Pipeline%20Syntax.png) 



Then Click on Generate Pipeline Script:


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/4.3%20Pipeline%20Script.png)



 
Copy this Script and keep it somewhere




Then go back to the Pipeline Configure page and : 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/4.4%20Pipeline%20Config%20Done.png) 




Choose Apply and then Save.




Then go to your github repo:

And open Jenkins file and edit it: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/5.1%20Edit%20Jenkinsfile.png) 




Then add the Pipeline Script to the Jenkins file: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/5.2%20Add%20Pipeline%20Script%20to%20Jenkinsfile.png) 





Then go back to the Jenkins Dashboard:

Select Plugin > Available Plugins 


And install Docker and Docker Pipeline Plugin (if its not already installed) 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/6.1%20Install%20Docker%20pipeline%20plugin.png) 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/6.2%20Docker%20Plugin%20Installed.png) 




Then proceed to Build the pipeline:
(Docker must be running on the host machine) 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/7.1%20Building%20the%20Pipeline.png) 



This is the output: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/7.2%20Pipeline%20Built.png) 



If any error persists, check the ‘Console Output’ that will display below the ‘Changes’ when error occurs. 






# Now Proceeding to ngrok: 



## Install ngrok on your machine 




type this command on terminal:


ngrok http http:// <your_private_ip>:<ngrok_port>


example:

ngrok http http://:192.168.x.x:8080 



This will appear: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.1%20ngrok.png) 






Copy this url to somewhere safe: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.2%20link.png) 




Enter this url on browser: 




![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.3%20accessing%20ngrok%20url.png) 




And then view site: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.4%20Error%20with%20the%20ngrok%20app.png) 





You might incur error like this.

To fix, try this:

enter: 

ngrok http 8080 

on terminal 


And then go to the url provided there: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.5%20Alternate%20link.png) 



The Jenkins Page will show now: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.6%20Ngrok%20Jenkins.png) 





## Sign in using your jenkins credentials: 


Ngrok will redirect to the Jenkins Portal: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/8.7%20NgrokRedirected%20to%20Jenkins.png) 





Now go to your github project (jenkins-test-12, in my case):

Go to settings > Webhooks 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/9.1%20Webhook.png) 




## Then Add Webhook 


and paste the link obtained from terminal after the command: ngrok http 8080:

https://<link_obtained_from_terminal>/github-webhook/


example:

https://6256-203-9-x-x.ngrok-free.app/github-webhook/ 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/9.2%20Webhook%20Added.png) 




This will show: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/9.3%20Webhook%20updated.png) 




## Back to the Jenkins Page 


This is the Jenkins Page right now: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/9.4%20Jenkins%20Page%20RN.png) 



And this is the original html file: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/9.5%20Current%20Html%20file.png) 




Then Go back to the Jenkins Page > Configure and enable hook trigger: 




![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/10.1%20Enable%20hook%20trigger%20in%20jenkins%20config.png)










Once I make changes here and push it to github: 



![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/10.2%20Editing%20Html.png) 








## The Jenkins page autoamtically runs the build process: 


![image alt](https://github.com/Dpk808/Jenkins_Repo/blob/main/Jenkins_Screenshots/10.3%20The%20changes%20in%20the%20git%20auto%20triggers%20the%20Jenkins%20Build%20Process.png) 





And that is this project for CI/ CD using Jenkins and Ngrok. 

