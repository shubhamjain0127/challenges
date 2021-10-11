# challenges
- Challenge 2: We need to write code that will query the meta data of an instance within AWS and provide a
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
