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
 <li>clicke review+create, then create</li>

 ![Image](https://github.com/user-attachments/assets/8b4ca50f-e26a-4ba1-a0a7-c6d0b8c43129)
 <h2>create the virtual network</h2>

 ![Image](https://github.com/user-attachments/assets/29767af1-ef76-4b57-bf2d-e535923b0fc3)
 <li>click create virtual network</li>
 <li>be sure its in the same region as the resource group</li>
 <li>name it, click review+create, click create</li>

 ![Image](https://github.com/user-attachments/assets/91de3ea9-4a13-4846-ab06-8854e4d2255d)
 <h2>create VM (the honeypot)</h2>

 ![Image](https://github.com/user-attachments/assets/041fea75-0b29-4416-9310-af68cff811a1)
 <li>click create, select Azure VM</li>
 <li>select the resource group that was created</li>
 <li>name it (dont include the word 'honeypot' in the name)</li>
 <li>select disk (2 vcpus, 8 Gib memory). be sure to delete when done to prevent accidental billing(Windows10)</li>
 <li>provide admin username and password</li>
 <li>check the licensing box</li>
 <li>next> Disks, select Standard SSD</li>
 <li>next> Networking> select the virtual network that was created> Subnet (default)> check the 'delete public IP and NIC when VM is deleted' box> next</li>
 <li>just accept all the defaults in Management> next</li>
 <li>check 'disable' boot diagnostics in Monitoring> next> next> review+create</li>
 <li>once Deployment is finished, search for resource group again and select the resourc group that was created</li>

![Image](https://github.com/user-attachments/assets/49123113-94ce-4016-9bc8-ac881814a315)
<li>you will see the vm, the public IP, network security group (cloud-based firewall), disk, etc</li>

<h2>edit the network security group to expose it to the internet</h2>
<li>click the security group</li>
<li>delete the default RDP rule</li>

![Image](https://github.com/user-attachments/assets/e4ebee28-26d0-48d2-a7a8-283a8be047dd)
<li>select settings> inbound security rules> add</li>
<li>Source Any, Source port ranges *, Destination Any, Service Custom, Destination port *, Protocol Any, Action Allow, Priority 100, Name except the default or change it, click add</li> 

![Image](https://github.com/user-attachments/assets/5c8d86f6-0826-4a24-bf6a-775b95c2c689)
 <h2>disable the Windows firewall in the VM</h2>
 <li>search for virtual machines</li>
 <li>select the vm and copy the public IP address</li>
 <li>on your own pc, launch remote desktop (for windows machines), or download the Windows App for Mac. enter the public IP address to sign into the VM</li>

 ![Image](https://github.com/user-attachments/assets/603b21f8-247d-4382-bb18-388c2211f095)
 <li>sign in with admin username and password created on the vm</li>
 <li>select Yes on certificate error</li>

 ![Image](https://github.com/user-attachments/assets/1795b943-baf5-49d1-885d-dc900b233285)
 ![Image](https://github.com/user-attachments/assets/cf90c654-f59f-4010-b0c3-6897f00972f7)
 <li>from inside the vm, type wf.msc in the search field</li>

 ![Image](https://github.com/user-attachments/assets/4bd29f53-e56b-4bba-9659-a3c4a5f737c3)
 <li>open the console and select Windows Defender Firewall Properties</li>

 ![Image](https://github.com/user-attachments/assets/c6056084-0d88-4a63-a680-8a9706d54441)
 <li>select Off under each tab> apply> Ok</li>

 ![Image](https://github.com/user-attachments/assets/7335947a-6b4f-4a52-abfb-f2489facb9cd)
 <li>ping vm from your local machine. from the command prompt/powershell for windows or terminal for Mac, ping the vm's public IP </li>

 ![Image](https://github.com/user-attachments/assets/7e4d851a-8a5d-4f04-a554-063b79850585)
 <li>we can now close/log out of the vm</li>
 <h2>Logging</h2>
 <li>intentionally fail to log back into the vm several times which will create log files</li>

 ![Image](https://github.com/user-attachments/assets/e9ab74f6-69c7-46c8-bc9d-24827ed1da02)
 <li>now log in with your correct credentials</li>
 <li>launch event viewer</li>

 ![Image](https://github.com/user-attachments/assets/0e753184-4979-4233-abe7-067a7eb62b41)
 <li>expand windows log> security</li>
 <li>event ID 4625 is the failed logon attempt</li>
 <li>right-click security> Find> and enter the 4625 event ID for a search</li>

 ![Image](https://github.com/user-attachments/assets/720cf840-7a0c-4591-b731-fe8f0153f54f)
 <li>once attackers see the vm on internet and attempt to hack into it, those failed attempts will show here</li>
