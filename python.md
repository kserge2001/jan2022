# Python Projects   version: NA  

### 1- Script modification tickets ( this sctipt is used by your team to check end points but will throw an error when the url doesn't have http so we need to add an exception for that to avoid the code breaking when the url is not good.(example: google.com won't work but http://google.com will.)
## the script is below: 
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
### 2-  The dev team is using a script to inventory instance infos from aws using the boto3 module. (the script is querying all instances with tag {environment: dev } this value is hard coded in the script. please modify the script so the qa team and eventually the subsequent team can use it to do the same.

```
#!/usr/bin/python
'''
This script starts all instances with a specific tag.
'''

import boto3

def instances_find(name, value):
    '''
    Finds instance id's based on tags.
    Returns a list of instances found.
    '''
    list_instances = []
    # filter based on tags
    filters =[
        {
        'Name': name,
        'Values': [
            value,
            ]
        },
    ]
    instances = ec2_resource.instances.filter(Filters=filters)
    
    
    for instance in instances:
        
        # for each instance, append to list
        list_instances.append(instance)
        #list_instances.append(instance.describe_instances())

    return list_instances

def show_instances(instances):
    header = "instance.id\t\t instance_type\t\t instance_image.id"
    print(header)
    for instance in instances:
        instance_details = f"{instance.id}\t {instance.instance_type} \t\t{instance.image_id}"
        print(instance_details)


def instances_start(list):
    '''
    Starts instances defined in the list.
    '''
    ec2_client.start_instances(InstanceIds=list)

# enter tag name and value
tag_name = 'tag:environment'
tag_value = 'dev'

ec2_resource = boto3.resource('ec2')
ec2_client = boto3.client('ec2')

# find instances
ec2_list = instances_find(tag_name, tag_value)
# start instances
# ec2_stop = instances_start(ec2_list)
#print('started instances: ' + str(ec2_list))
show_instances(ec2_list)

```



### 3- we have a script that we use to generate QR codes. it needs two input the message/url and the file name for the qr code.
Please lookto how to use the argparser module to set it in the way that we can run it with arguments and provide those inputs.
-h or --help should show how to use the script, -u or --url should be used to provide a url and -i or --im shoulb be used to provide the fileimage name. see the script bellow:

```
import pyqrcode
import png
from pyqrcode import QRCode
# Text which is to be converted to QR code
print("Enter text to convert")
s=input(": ")
# Name of QR code png file
print("Enter image name to save")
n=input(": ")
# Adding extension as .pnf
d=n+".png"
# Creating QR code
url=pyqrcode.create(s)
# Saving QR code as  a png file
url.show()
url.png(d, scale =6)
```
### 4- At work, we have an internal application running on postgressql, and we need a python script that will take backup of the database and upload it in s3 bucket everyday at a certain time. 

### 5- AT work , there is a need for a python script that can convert .xml files to json format. ( give it a try)


