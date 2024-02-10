# Honeypot Lab
Implementing a SOC and Honeynet in Azure 
Could potentially add triggers or alerts 
Project Summary:
Setting up Azure Sentinel which is a cloud based SIEM(Security Information and Event Management)
Also create a VM in the cloud which will be our Honeypot

We will make the honeypot vulnerable to the internet by taking down Windows Firewall and then we will monitor and log a lot of attacks from different IP addresses from different countries all over the world and then display it on a map

![image](https://github.com/cenkcafer/honeypotlab/assets/61919465/89c476b6-0389-4b6f-9150-424563a226de)

Instructions:
Create Azure account
Create Resource Group, Give resource group a title(like honeypotlab), in resoruce group create Windows VM
Windows VM Instance details:
Winodows 10 Pro 22H2-Gen2
NIC network security group: Advanced>create new>remove default rule, create inbound rule, destination port *(means any)>priority 100

Create Log Analytics Workspace:
store in same resource group 
same region

Microsoft security>log analytics workspace>turn off sql server
Data collections>click all events
Log analytics workspace>VMs>VM(name)>connect

Microsoft sentinel>VM(name)>add to workspace

Log into VM
Turn off Windows Firewall in Windows VM to allow pings from anywhere
Domain Profile: Off, Public Profile: Off, Private Profile: Off, Apply>OK
Pings should work now since Echo requests are allowed now

