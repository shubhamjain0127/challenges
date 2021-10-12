# challenges
- **Challenge1**: Create a 3-tier architecture.

Architecture Diagram:

![image](https://user-images.githubusercontent.com/35572868/136897514-47bb599e-129e-4c35-9f31-164c52705b26.png)


Here I am using Ansible playbook which will run on Ansible Tower host to create resources mentioned in Architecture diagram on Azure.

Prerquisite:
1. Ansible Tower
2. Ansible Template and project to run playbook Create-3-tier-arch.yaml
3. Valid Subsciption and SPN with Contibutor permissions in the subscription.


- **Challenge 2:** We need to write code that will query the meta data of an instance within AWS and provide a
json formatted output. The choice of language and implementation is up to you.
Bonus Points
The code allows for a particular data key to be retrieved individually

Here I am using az cli commands to get the meta data of Virtual Machine in Azure Cloud. As a pre-requisite az cli should be installed on machine where these command will run.

```
# Method of authentication can differ. It can be either using SPN or interactive user login. We can hide the sensitive data like client secret depeneding upon the tool we are using. Ex: in Ansible we can store the SPN data as credential and we can use shell module to execute below commands.
az login --service-principal -u "<SPN-CLIENT-ID>" -p "<SPN-CLIENT-SECRET>" --tenant "<YOUR-TENANT-ID>" ;
az account set --subscription "<YOUR-SUBSCRIPTION-ID>"

# Below command prints all the data of VM in json format
az vm show --name "<VM-NAME>" --resource-group "<RG-NAME>"

# Below commands are used to get specific properties of VM in azure

az vm show --name "<VM-NAME>" --resource-group "<RG-NAME>" --query type
az vm show --name "<VM-NAME>" --resource-group "<RG-NAME>" --query tags
```

- **Challenge 3**: Create a function which accepts object and key and prints the value.

Here I am using python to create the function which will take the object and key as input . It will first create the json object to python dictionary and key to an array by splitting delimiter "\".


```
import json

def giveValue(a,b):
    x = b.split("/")
    y= json.loads(a)
    value = y[x[0]][x[1]][x[2]]
    return value
    
value = giveValue('{"x" : {"y" : {"z": "a"}}}',"x/y/z")

print(value)
```
