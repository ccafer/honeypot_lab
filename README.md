# Honeypot Lab
Implementing a SOC and Honeynet in Azure 

Project Summary:
Setting up Azure Sentinel which is a cloud based SIEM(Security Information and Event Management)
Also create a VM in the cloud which will be our Honeypot

We will make the honeypot vulnerable to the internet by taking down Windows Firewall and then we will monitor and log a lot of attacks from different IP addresses from different countries all over the world and then display it on a map

![image](https://github.com/cenkcafer/honeypotlab/assets/61919465/89c476b6-0389-4b6f-9150-424563a226de)

Instructions:
Create Azure account
Create VM in Azure
Turn off Windows Firewall in Windows VM to allow pings from anywhere
Public
Private 
create log analytics workspace in azure to store data into log analytics workspace from vulnerable VM
then set up azure sentinel and map data from log analytics workspace
