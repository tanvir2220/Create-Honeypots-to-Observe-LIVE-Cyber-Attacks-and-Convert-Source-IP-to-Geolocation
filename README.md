<h1>Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation</h1>


<h2>Overview</h2>
Basically, this project involves three main parts:

1.	I will set up Microsoft Sentinel, a cloud based SIEM and create Honeypot in the cloud via a super vulnerable VM
2.	I will then monitor and log LIVE Cyber-attacks from different IP addresses around the world
3.	Finally, I will take all the source IP data and display those to a map via a PowerShell script
<br />

<h2>Environments Used </h2>

- <b>Microsoft Azure</b>
<h2>Languages Used</h2>

- <b>PowerShell:</b> Extract RDP failed logon logs from Windows Event Viewer 

<h2>Utilities Used</h2>

- <b>ipgeolocation.io:</b> IP Address to Geolocation API

<h2>To-Do</h2>

To successfully complete the project, we need to perform following tasks:

1.	Create Azure Subscription
2.	Create Virtual Machine
3.	Allow all in NIC Network Security Group in Azure
4.	Create Log Analytics Workspace
5.	Enable gathering VM logs in Microsoft Defender for Cloud
6.	Connect Log Analytics to VM
7.	Setup Microsoft Sentinel
8.	Log into VM with Remote Desktop
9.	Observe Event Viewer Logs in VM
10.	Turn of Windows Firewall on VM
11.	Download PowerShell Script
12.	Get Geolocation.io API Key
13.	Run Script To get Geo Data from attackers
14.	Create custom log in LAW to bring in our custom log
15.	Create custom fields/extract fields from raw custom log data
16.	Testing Extracts
17.	Setup map in sentinel with Latitude and Longitude (or country)


<h2>Program Walk-Through</h2>

1.	Create Azure Subscription: First of all, create free Azure Subscription. Make sure you delete the resource group that has all of our resources in it otherwise it will eat up our subscription cost. Here's the link: https://azure.microsoft.com/en-us/free/
   
2.	Create Virtual Machine: I will create a Virtual Machine with the following settings in Microsoft Azure.

3.	Allow all in NIC Network Security Group in Azure: In this step, I will allow all incoming connection in NIC Network Security Group in Microsofot Azure. The purpose of this is to make is completely vulnerable, acting like a honeypot.

<p align="center">
<img src="https://i.ibb.co/TBD7zNt/1.jpg" height="80%" width="80%" alt="Vulnerability Scanning on Windows Hosts Using Nessus"/>
<br />
<br />

4.	Create Log Analytics Workspace: Now I will create a Log Analytics Workspace. The purpose of this is to ingest logs from the virtual machine to Log Analytics Workspace. I will then create custom log that contains geographic information.

<p align="center">
<img src="https://i.ibb.co/zmdqtbL/2.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

5.	Enable gathering VM logs in Microsoft Defender for Cloud: Next i will go to "Defender Plans" and "Data Collection" in Microsoft Defender for Cloud and do the following:

<p align="center">
<img src="https://i.ibb.co/wK7hbPg/3.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

<p align="center">
<img src="https://i.ibb.co/XY9Ktrv/4.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

6.	Connect Log Analytics to VM: Then connect Log Analytics to Virtual Machine which I created earlier.

<p align="center">
<img src="https://i.ibb.co/SyMr0pW/6.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

7.	Setup Microsoft Sentinel

<p align="center">
<img src="https://i.ibb.co/9T6XyDT/5.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

8.	Log into VM with Remote Desktop

<p align="center">
<img src="https://i.ibb.co/rfzqnyJ/7.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

9.	Observe Event Viewer Logs in VM

<p align="center">
<img src="https://i.ibb.co/K2JrGYw/9.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

10.	Turn off Windows Firewall on VM: Then I turned off Windows Firewall in the Virtual Machine.

11.	Download PowerShell Script: Now download the PowerShell script from the link https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1. Run the script from VM's Windows PowerShell ISE.

<p align="center">
<img src="https://i.ibb.co/7SWwC4y/11.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

12.	Get Geolocation.io API Key: However, before running the script in the previous step, we must get our own API key from https://ipgeolocation.io/

13.	Run Script To get Geo Data from attackers: As soon as someone tries to login to honeypot, the log will be saved in C:\ProgramData directory. Itried to login with incorrect password and here's the saved log:

<p align="center">
<img src="https://i.ibb.co/JrNpC4m/12.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

14.	Create custom log in LAW to bring in our custom log

<p align="center">
<img src="https://i.ibb.co/fxd1GyD/15.jpg" height="80%" width="80%" alt="Create Honeypots to Observe LIVE Cyber Attacks and Convert Source IP to Geolocation"/>
<br />
<br />

