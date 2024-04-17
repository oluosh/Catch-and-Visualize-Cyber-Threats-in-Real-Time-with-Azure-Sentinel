<p align="center">
<img src="https://i.imgur.com/dx77eQI.png" alt="Microsoft Active Directory Logo" height="60%" width="60%"/>
</p>

<h1>Catch-and-Visualize-Cyber-Threats-in-Real-Time-with-Azure-Sentinel</h1> 
This tutorial outlines the implementation of a Honeypot using an Azure virtual machine monitor failed RDP attempts and visualize these attacks in Azure Sentinel .<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Microsoft Sentinel (SIEM)
- Log Analytics
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
<img src="https://i.imgur.com/Kep2a6E.png" alt="img3" height="50%" width="50%"/>
</p>
<p>
Awesome! We've successfully set up our Azure environment and deployed a Honeypot VM laying the groundwork for our project. Let's set up our log analytics workspace. Think of this workspace as your data Reservoir where logs and Telemetry from your Honeypot will be stored and analyzed. You'll need to provide a few details starting with your workspace name. Select the same Resource Group you used for Azure Sentinel and then create.
</p>
<p>
<img src="https://i.imgur.com/2Rz41WK.png" alt="img4" height="60%" width="60%"/>
</p>
<p>
Next we'll set up Defender. click on the environment settings section and click on the arrow on the left to open up our created VM. We'll turn the defender plan on for our Servers, and enable data collection for all events. Now navigate to your VM, then to the diagnostic settings and add the newly created log analytics workspace as the destination for your logs.
</p>
<p>
<img src="https://i.imgur.com/qR4y7bi.png" alt="img50" height="60%" width="60%"/>
</p>
<p>
Excellent work! Next open up Azure Portal then search Sentinel. Click on create to add Azure Sentinel to your workspace. You'll need to select or create a new Resource Group which is essentially a collection of resources that share the same life cycle permissions and policies
</p>
<p>
<img src="https://i.imgur.com/vcIPSPH.png" alt="img51" height="60%" width="60%"/>
</p>
<p>
After setting up Azure Sentinel you're now ready to dive into the world of cyber security monitoring and threat detection. Now in our virtual machine, we are going to disable our firewall.
</p>
<p>
<img src="https://i.imgur.com/Kg6DMXz.png" alt="img52" height="60%" width="60%"/>
</p>
<p>
After we disable the firewall you can see when you go to command prompt, it is able to Ping our VM machine.
</p>
<p>
<img src="https://i.imgur.com/OqXRUw9.png" alt="img6" height="60%" width="60%"/>
</p>
<p>
Great! It's time to breathe life into our project with a bit of automation. We'll use a Powershell script to monitor failed RDP attempts on our Honeypot and enrich this data with attacker IP geolocation information. The script operates in two main parts: first it scans the Windows Event log for failed RDP login attempts. For each failed attempt it extracts the IP address of the potential attacker. Next the script sends these IP addresses to an IP geolocation API (we're using IP geolocation IO). For each IP the API returns its geographical location which we then log for analysis
</p>
<p>
<img src="https://i.imgur.com/WYUEl1Q.png" alt="img7" height="60%" width="60%"/>
</p>
<p>
Now on the log analytics we created, go to the tables tab. Create a custom log and make sure it is the MMA based custom log. Now we have to add the file from the virtual machine to link the custom log to our log analytics workspace. Go back to the VM and copy the destination of the file and paste into Azure. Now we have to wait a little while for the virtual machine and log analytics workspace to sync up which usually takes about 10 to 15 minutes.
</p>
<p>
<img src="https://i.imgur.com/1skTltI.png" alt="img8" height="60%" width="60%"/>
</p>
<p>
Sweet! Now it's time to go to Sentinel.  Azure Sentinel allows us to use KQL (Kusto Query Language) to query our logs. For our purposes we'll write a query to select failed RDP attempts and extract the IP addresses associated with these attempts. Make sure the query labels align with the map settings. 
</p>
<p>
<img src="https://i.imgur.com/TGMUKwy.png" alt="img9" height="60%" width="60%"/>
</p>
<p>
And there it is: a visual representation of attacks on our Honeypot mapped out across the globe. Each point represents a failed attempt to breach our system giving us invaluable insights into the global distribution of these threats. After letting our Honeypot collect data for a while this map is a window into the tactics and locations of potential attackers. You'll notice concentrations of attacks emanating from certain regions. Also, by analyzing the timing of these attacks, we can identify peak periods of activity. This information is crucial for bolstering our defenses when we're most vulnerable.
</p>
