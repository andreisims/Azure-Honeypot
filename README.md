# Azure-Honeypot
In this lab, we will be setting up a basic SOC (security operations center) in the cloud (Azure). This will be a walkthrough on creating an internet accessible virual machine (honeypot) to view unauthorized access attempts. The logs will be sent to a central repository, where they will be analyzed in real-time. Below are the steps:
<li>create a resourc group in <a href="https://portal.azure.com/">Azure</a></li>
<li>create a virtual network</li>
<li>create the honeypot (virtual machine)</li>
<li>allow access to the vm from the internet</li>
<li>send logs to Azure</li>
<li>create a SIEM (Sentinel)</li>
<li>connect the honeypot to the SIEM</li>
<li>show attackers on visual map</li>
<li>clean up</li>
