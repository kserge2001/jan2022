
#Project 4:  Scripting 

# Server creation steps: 
```
cd ~
cd utrains-project
mkdir project4
cd project4
code Vagrantfile
paste below code into the Vagrantfile and then save.
vagrant up
vagrant ssh
```
## Vagrantfile instructions:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

box instructions here
```


#Project 4:  Scripting  


## Project Description:

#### You have just been recruited as a __DevOps__ in a large financial institution. In your mission, you have to manipulate highly sensitive data about users, concerning their financial transactions. 
#### In the company, a bash program performs the transactions and the data is logged in a directory. The program that logs the data is launched as a job every minute. Every minute we have a number of transactions that are made. 

### 1- the log files for the transactions are in a directory named: utrains_logs. Give us the complete path where this directory is located.

### 2- Give us the number of lines in a file taken at random in this directory, then the structure of the name of the files in this directory?

### 3- Do you know why the program generates logs? and why these logs are in the /var/log directory?

### 4- The name of the program that generates the logs is called utrains_log_script.sh, give us the name of the directory where this file is located, then comment on its content;

### 5- To find out how this script is executed every minute to retrieve 10 financial transactions enter this command below, then comment on its contents: 

```
$ crontab -e
```

### 6- Now, we want to use the same process to archive every 5 minutes, our transaction files. Check and install the zip tool to archive these logs in the system.

### 7- one of your colleagues tried to write the script to archive these Logs, but forgot some little mistake. the name of the script he wrote is called utrains_archive_script.sh. and its content is like this:

```
#!/bin/bash

# --------- @Author : Utrains 
# ------- Date : Jan 2022 ----------
#
# description : in this script, we are going to group together a set of log files,
# created after a certain time (5 minutes) in a folder.
# we will then archive the folder, then delete it and only keep the archive


DIR="/tmp/utrains_logs"
if [ -d "$DIR" ]; then
  # Control will enter here if $DIR exist.
  cd /tmp/utrains_logs

  MYDATE=$(date "+%b_%d_%Y_%H.%M.%S")
  mkdir utrains_arch_cron-$MYDATE
  mv utrains_cron_logs_* utrains_arch_cron-$MYDATE

  zip -r utrains_cron_zip_$MYDATE.zip utrains_arch_cron-$MYDATE 
  
  rm -r utrains_arch_cron-$MYDATE

fi
```

### a- what is the purpose of archiving data?
### b- tell us the directory where this script is located
### c- correct this script so that it can archive our log files
### d- use the contab to schedule the execution of this script for archiving every 5 minutes
### e- test, then tell us in which form are archived the script

### 8- In reality, the file transfer_data is a file extracted from the database which records the financial transactions of the company. each line of this file is in the form : id,first_name,last_name,email,gender,bank_account,transaction_date,phone_number,salary. write a command which allows to display only the first_name, the transaction_date and the salary of the company's customers.