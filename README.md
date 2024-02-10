# Honeypot Lab
Implementing a SOC and Honeynet in Azure 

Project Summary:
Setting up Azure Sentinel which is a cloud based SIEM(Security Information and Event Management)

Also create a VM in the cloud which will be our Honeypot

We will make the honeypot vulnerable to the internet by taking down Windows Firewall

Then we will monitor and log attacks from different IP addresses from different countries all over the world and then display it on a map

![image](https://github.com/cenkcafer/honeypotlab/assets/61919465/89c476b6-0389-4b6f-9150-424563a226de)

Instructions:
Create Azure account

Create Resource Group, Give resource group a title(like honeypotlab), in resoruce group create Windows VM

Windows VM Instance details:

Winodows 10 Pro 22H2-Gen2

NIC network security group: Advanced>create new>remove default rule, create inbound rule, destination port *(means any)>priority 100

Create Log Analytics Workspace:

Store in same resource group 

Same region

Microsoft Security>Log Analytics Workspace>turn off sql server

Data Collections>Select all events

Log analytics workspace>VMs>VM(name)>connect

Microsoft sentinel>VM(name)>add to workspace

Log into VM

Turn off Windows Firewall in Windows VM to allow pings from anywhere

Domain Profile: Off, Public Profile: Off, Private Profile: Off, Apply>OK

Next we need to get an API key from https://ipgeolocation.io/

Copy and paste API key into Powershell script and run the script in the vulnerable Windows VM

The script will look throught the event viewer and check for the failed logons code#4625, it will get the IP address from the failed logon attempt and run it through the IP geolocation API and save it to a txt file, the txt files name is failed_rdp

Next The failed_rdp txt file will also be uploaded into the log analytics in Azure 

Go to Azure>VMs>Create a custom log>Sample log>import failed_rdp>Collection paths Type>Windows, Path>C:\ProgramData\failed_rdp.log, Details>FAILED_RDP_WITH_GEO

We need to parse out the txt file for Country, IP address, Time, Longitude, Latitude, User Name, Password

We can use this KQL Query to sort the data imported through the failed_rdp txt file

https://github.com/cenkcafer/honeypotlab/blob/main/KQL_GeoLocate_Query.kql

Next go to Azure Sentinel>honeypotlab>Workbooks>edit>add a query



Might add my own custom triggers or alerts later(last updated Feb 10,2024)
