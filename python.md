#Python Projects   version: NA  

# Script modification tickets ( this sctipt is used by your team to check end points but will throw an error when the url doent have http so we need to add an exception for that to avoid the code breaking when the url is not good.(example: google.com won't work but http://google.com will.)
# the : 
```
#Program to fetch the http status code give the url/api
from urllib.request import urlopen
from urllib.error import URLError, HTTPError
import emoji

#Taking input url from user
requestURL = input("Enter the URL to be invoked: ")

#Gets the response from URL and prints the status code, corresponding emoji and message accordingly
try:
    response = urlopen(requestURL)
    #In case of success, prints success status code and thumbs_up emoji
    print('Status code : ' + str(response.code) + ' ' + emoji.emojize(':thumbs_up:'))
    print('Message : ' + 'Request succeeded. Request returned message - ' + response.reason)
except HTTPError as e:
    #In case of request failure, prints HTTP error status code and thumbs_down emoji
    print('Status : ' + str(e.code) + ' ' + emoji.emojize(':thumbs_down:'))
    print('Message : Request failed. Request returned reason - ' + e.reason)
except URLError as e:
    #In case of bad URL or connection failure, prints Win Error and thumbs_down emoji
    print('Status :',  str(e.reason).split(']')[0].replace('[','') +  ' ' + emoji.emojize(':thumbs_down:'))
    print('Message : '+ str(e.reason).split(']')[1])
```
## Copy the script run it and see how you can correct it:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # load de centos7 box from vagrant cloud
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.56.33"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 2
  end
  #change the value of the SSH configuration file, then restart the ssh service
  config.vm.provision "shell", inline: <<-SHELL
   sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
   sudo systemctl restart sshd
  SHELL
end
```



###  1- At work you are in the middleware team and as such, there is a request from the DevOps team to build a Sonarqube server. 
### The documentation on the process to follow is in the confluence page. follow that and install a Sonarqube server for the devops team.
### The deliverable will be the url of Sonarqube server, the username and password to access Sonarqube.
### Confluence url: https://dataservicegroup.atlassian.net/wiki/spaces/RET/pages/1978105890/Sonarqube+installation+on+Centos
### username: unixteam24@gmail.com
### password: school123

### 2- AT work, there are documents for installation of various applications stored in confluence, and during the meeting , the obersavation was that some of them need to be automated.
### a- Go ahead and automate the installation of Sonarqube, using a bash shell script. ( we should be able to copy the script to the server and execute it.)

### b- For better collaboration at work, we need to keep the scripts in github. Create a repo in github called middleware-scripts and push your scripts there. 

