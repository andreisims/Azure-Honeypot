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

<h2>log into or create an account in Azure and create a resource group</h2>
 <li>search for resource group</li>
 <li>click create</li>
 <li>choose your subscription</li>
 <li>name the resource group</li>
 <li>select your region</li>
 <li>clicke review+create, then create </li>

 ![Image](https://github.com/user-attachments/assets/8b4ca50f-e26a-4ba1-a0a7-c6d0b8c43129)
 <h2>create the virtual network</h2>

 ![Image](https://github.com/user-attachments/assets/29767af1-ef76-4b57-bf2d-e535923b0fc3)
 <li>click create virtual network</li>
 <li>be sure its in the same region as the resource group</li>
 <li>name it, click review+create, click create </li>

 ![Image](https://github.com/user-attachments/assets/91de3ea9-4a13-4846-ab06-8854e4d2255d)
 
