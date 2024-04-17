<p align="center">
<img src="https://i.imgur.com/dx77eQI.png" alt="Microsoft Active Directory Logo" height="60%" width="60%"/>
</p>

<h1>Catch-and-Visualize-Cyber-Threats-in-Real-Time-with-Azure-Sentinel</h1> 
This tutorial outlines the implementation of a Honeypot using an Azure virtual machine monitor failed RDP attempts and visualize these attacks in Azure Sentinel .<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Sentinel)
- Remote Desktop
- PowerShell

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

<p>
</p>
<p> In this lab, we're going to set up a Honeypot using an Azure virtual machine monitoring failed RDP attempts and visualize these attacks on a world map using Azure Sentinel. this project is a visually engaging way to understand the global landscape of cyber threats targeting your system.
</p>
<p>
<img src="https://i.imgur.com/NqNxYCn.png"  height="60%" width="60%"/>
</p>
<p>
A Honeypot is a decoy system designed to lure in potential attackers. By monitoring attacks on the Honeypot, we can learn about attack methods and prepare our defenses. We'll start by creating a new virtual machine in Azure to serve as our honey pot. We'll configure the network security group to allow inbound RDP connections to make it attractive to potential attackers
</p>
<p>
<img src="https://i.imgur.com/Kep2a6E.png" alt="img3" height="60%" width="60%"/>
</p>
<p>
Awesome! We've successfully set up our Azure environment and deployed a Honeypot VM laying the groundwork for our project. Let's set up our log analytics workspace. Think of this workspace as your data Reservoir where logs and Telemetry from your Honeypot will be stored and analyzed. You'll need to provide a few details starting with your workspace name. Select the same Resource Group you used for Azure Sentinel and then create.
</p>
<p>
<img src="https://i.imgur.com/2Rz41WK.png" alt="img4" height="60%" width="60%"/>
</p>
