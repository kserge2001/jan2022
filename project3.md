#Project3   version: NA  

# Server creation steps: 
```
cd ~
cd utrains-project
mkdir project3
cd project3
code Vagrantfile
paste below code into the Vagrantfile and then save.
vagrant up
vagrant ssh
```
## Vagrantfile instructions:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # load de centos7 box from vagrant cloud
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.56.133"
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
### Confluence url:  https://dataservicegroup.atlassian.net/wiki/spaces/RET/pages/1991246045/Sonarqube+installation+on+Centos-7
### username: unixtteam24@gmail.com
### password: school123

### 2- AT work, there are documents for installation of various applications stored in confluence, and during the meeting , the obersavation was that some of them need to be automated.
### a- Go ahead and automate the installation of Sonarqube, using a bash shell script. ( we should be able to copy the script to the server and execute it.)

### b- For better collaboration at work, we need to keep the scripts in github. Create a repo in github called middleware-scripts and push your scripts there. 

