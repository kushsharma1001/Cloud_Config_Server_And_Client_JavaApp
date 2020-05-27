# Cloud_Config_Server_And_Client_JavaApp
This example explains how to read a git configuration associated with a client using a config server app.

Read this for details:https://howtodoinjava.com/spring-cloud/spring-cloud-config-server-git/

# Steps to use:
1) Create your git files from where all configurations should be fetched. Commit them. (We can also use some remote git url instead of local git files) using git init, git add. , git commit -m "added new files".

2) Specify the url in config server so that it knows where to fetch details/configurations from. Start the config server app.

3) Start the client server app. Make sure to keep the git file name same as client app name.

Now, both apps are running. Hence, lets go to below urls to make sure that config server is able to read from th git files properly:
http://localhost:8888/client-config/development or http://localhost:8888/client-config/production

Now, lets go to http://localhost:8080/msg
This will give us the configs from git.

Now incase we wish to change the configurations in the git files. Change them and again commit them. 
Now again,

Now, both apps are still running. Hence, lets go to below urls to make sure that config server is able to read from th git files properly:
http://localhost:8888/client-config/development or http://localhost:8888/client-config/production

Note that updated git details are fetched in config server now.

Now, lets go to http://localhost:8080/msg
This will give us the old configs from git not new updated details.

This is becasue that a refresh scope is mentioned in client. Hence, we trigger a refresh using POSTMAN:
http://localhost:8080/actuator/refresh POST method.

Now trigger:  http://localhost:8080/msg
we see the latest configurations mentioned in the git files now. :)
