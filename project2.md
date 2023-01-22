#Project2   version: 5  

# Server creation steps: 
```
cd ~
cd utrains-project
mkdir project2
cd project2
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
  config.vm.box_version = "5.0"
  config.vm.network "private_network", ip: "192.168.56.132"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    #vb.name = "centos-project2"
    vb.cpus = 2
  end
  #change the value of the SSH configuration file, then restart the ssh service
  config.vm.provision "shell", inline: <<-SHELL
   sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
   sudo systemctl restart sshd
  SHELL
end
```



###  1- At work you are in the middleware team and as such, there is a request from the DevOps team to build a jenkins server. 
### The documentation on the process to follow is in the confluence page. follow that and install a jenkins server for the devops team.
### The deliverable will be the url of jenkins server, the username and password to access jenkins.
### Confluence url: https://dataservicegroup.atlassian.net/l/cp/QLkWo2r2
### username: unixtteam24@gmail.com
### password: school123

### 2- Every month in your company, we need to patch the linux servers. To do that, we need to check some services status on the  server depending on which application is running. This is to make sure that  after patch and reboot, those services are in the same state. And in some cases, you need to shutdown some services running and bring them back after a gracefull reboot. Use below steps to patch your system as an example.

### a- check if jenkins service is runing and stop it.
#### #systemctl status jenkins
#### #systemctl stop jenkins
### b- Update the system 
#### # yum update -y  ( this command might take a long time)

### c- Do a graceful shutdown and reboot of the system.
#### # shutdown -r now
### d Log back into the server 
### e- Start the jenkins service
#### # systemctl start jenkins
### NB: When we run yum update -y at work or any yum install, yum pull the repos from the satellite server ( satellite is a server from redhat used to manage packages at work so yum doesnt go online to get packages)

### 3- There is an application running on this server thru apache, but for some reason, we are not able to start the httpd  daemon ( the apache web server daemon for centos) and this is making the application to be down. you can test that yourself by typing the ip address on the browser which will throw an error. when we run systemctl start httpd, it throws an error and point us to run systemctl status httpd to see a more verbose error message.  upon reading the message it looks like another application is consuming/using port 80. go ahead and help figure out what is that application and kill it, then start apache and check if the application is coming on your browser.

### 4- Type a command to check if port 8080 is open. 
### 5- Type a command to check what app is using port 8080.
### 6- run a command to install git on the server 
### 7- what is a soft link?
### 8- what is sticky bit ?
### 9- what is the default port for these services?  SSH, HTTP, HTTPS, FTP , DNS 
### 10- There is a file on the system that contains a list of employees called emp.csv run a command that will display just the emails of all employees.
### 11-Consider you are sitting on an interview, describe a troubleshooting scenario you encounter.
