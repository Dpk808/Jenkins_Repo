# This Project is about CI / CD using Jenkins & Git WebHook Automation

## (CI/ CD using Jenkins and ngrok)


1. Start Jenkins:






2.Log in to Jenkins:





3.Configure Jenkins:





Go to Credentials:





Then go to system in Stores scoped to Jenkins








Then Global credentials (unrestricted):





Then type in your Github username in the username field and a token (can be created by going to Settings in Github> Developer Settings> Personal Access token> Tokens (classic) ) in the password field:






And Create the Credentials.



It will look something like this.










##Creating a Pipeline

Create a new Item > Select Pipeline:












##Configure Pipeline:






Select Pipeline script from SCM:



a. Then in SCM choose Git
b. Paste your github link
c. And then choose the previously created Credentials:











Then Specify the Branch of your repo: (master/main)



And proceed to Pipeline Syntax
Pipeline Syntax



Choose git:Git from the Sample step dropdown menu

Fill in:





Then Click on Generate Pipeline Script:




Copy this Script and keep it somewhere


Then go back to the Pipeline Configure page and :



Choose Apply and then Save.




Then go to your github repo:

And open Jenkins file and edit it:






Then add the Pipeline Script to the Jenkins file:




Then go back to the Jenkins Dashboard:

Select Plugin > Available Plugins

And install Docker and Docker Pipeline Plugin (if its not already installed)






Then proceed to Build the pipeline:
(Docker must be running on the host machine)





This is the output:



If any error persists, check the ‘Console Output’ that will display below the ‘Changes’ when error occurs.





#Now Proceeding to ngrok:


##Install ngrok on your machine



type this command on terminal:


ngrok http http:// <your_private_ip>:<ngrok_port>


example:

ngrok http http://:192.168.x.x:8080


This will appear:





Copy this url to somewhere safe:



Enter this url on browser:



And then view site:




You might incur error like this.

To fix, try this:

enter: 

ngrok http 8080 

on terminal

And then go to the url provided there:



The Jenkins Page will show now:




##Sign in using your jenkins credentials:

Ngrok will redirect to the Jenkins Portal:



Now go to your github project (jenkins-test-12, in my case):

Go to settings > Webhooks



##Then Add Webhook

and paste the link obtained from terminal after the command: ngrok http 8080:

https://<link_obtained_from_terminal>/github-webhook/


example:

https://6256-203-9-x-x.ngrok-free.app/github-webhook/




This will show:





This is the Jenkins Page right now:




And this is the original html file:




Then Go back to the Jenkins Page and enable hook trigger:












Once I make changes here and push it to github:








##The Jenkins page autoamtically runs the build process:






And that is this project for CI/ CD using Jenkins and Ngrok.
