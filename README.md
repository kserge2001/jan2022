# Server creation steps: 
```
cd ~
mkdir utrains-project
cd utrains-project
mkdir project1
cd project1
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
  config.vm.box = "utrains/centos7"
  config.vm.box_version = "3.0"
  config.vm.network "private_network", ip: "192.168.56.30"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    #vb.name = "centos-project1"
    vb.cpus = 2
  end
  #change the value of the SSH configuration file, then restart the ssh service
  config.vm.provision "shell", inline: <<-SHELL
   sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
   sudo systemctl restart sshd
  SHELL
end
```

# project_linux_administrator
### project1  


#### 1. Consider you are a linux Engineer.
#### During the release to production, a deployment is failing, with the following error : 
#### /opt/deployment/uat/deploy.cfg: No such file or directory, Deployment failed!! 
#### So the developers code is trying to access the deploy.cfg file with no avail.
#### Check on the server, if the path that the developer has put in his code is correct (provide the correct path to the developers if /opt/deployment/uat/deploy.cfg is not correct). 

#### 2.  There is a file on the system called success.txt, run a command to display its content.

#### 3.  what group does the success.txt file belongs to ?  

#### 4.  what is the permission on success.txt file for others people on the system

#### 5.  we want the file success.txt to be owned by the user u5bt , how can we do that?

#### 6.  the user u5bt's full name is "John Mary" please modify their account to reflect this.

#### 7.  change the permission on the file success.txt to reflect the access below :
##### - owner: full permission
##### - group: read and write
##### - others: no permission what so ever

#### 8.  change the password for the user u5bt to redhat

#### 9. create a user sarah with no access to an interactive shell

#### 10.  create a group called network

#### 11. create a user called henry with network as subgroup

#### 12. Herman is a new contractor in the team and is complaining that he can not login to this server. 
#### please investigate what can be the issue and solve it so he can login to the server

#### 13. go ahead and force Herman to change his password on his next login

#### 14. A deployment to this server is failing and apparently it is due to selinux been set to enforcing mode. 
#### you are tasked to disable it. Below are the steps to do that. go ahead and do it.
######    vi /etc/selinux/config
######    change
######    SELINUX=enforcing
######    to
######    SELINUX=permissive
######    save and quit
######    NB:( you can read more about selinux feature later on this link https://www.redhat.com/en/topics/linux/what-is-selinux ) 
#### 15.  this server will be used as a webserver. Please go ahead and configure apache on it.
#### It should display below message on the browser
## "I feel like I am sitting in the office working for real"

