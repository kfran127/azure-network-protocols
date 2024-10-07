<p align="center">
  <img src="https://github.com/user-attachments/assets/a9e62984-6877-41d3-b24c-25d0460b9005" alt="Microsoft Azure Banner">
</p>

<h1>Network Security Groups (NSGs) and Inspecting Network Protocols</h1>

<p>In this lab, I demonstrated how to create virtual machines in Microsoft Azure, inspect network traffic using WireShark, and configure Network Security Groups (NSGs) to control traffic flow. This hands-on lab helped me understand network protocols and security group rules in a cloud environment.</p>

<h2>Part 1: Creating Virtual Machines</h2>

1. I logged into the <a href="https://portal.azure.com/">Azure Portal</a>.
2. First, I created a Resource Group to organize the resources for the lab.
3. I created a Windows 10 VM:
    - I selected the Resource Group I had created earlier.
    - Let Azure create a new Virtual Network (VNet) and Subnet automatically.
4. Next, I created a Linux (Ubuntu) VM:
    - I used the same Resource Group and VNet as the Windows 10 VM.
    - For authentication, I chose a Username/Password combination.
5. I made sure both VMs were in the same VNet and Subnet.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7c82d5a2-d632-4ea9-9527-5dc3e37983fd" alt="Creating Virtual Machines" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/30064df8-a984-48a4-8856-111f0ace3a4e" alt="Creating Virtual Machines" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/c7c78ef7-4ba3-4063-b343-8b5076cd1b7d" alt="Creating Virtual Machines" width="80%">
</p>



<h2>Part 2: Observing ICMP Traffic</h2>

1. Since I use a Mac, I installed Microsoft Remote Desktop to connect to my Windows 10 VM.
2. Once connected to the Windows 10 VM, I installed WireShark for network analysis.
3. I started a packet capture in WireShark and filtered specifically for ICMP traffic.
4. From the Windows 10 VM, I pinged my Ubuntu VM using its private IP address.
5. In WireShark, I observed the ICMP traffic flowing between the VMs.


<p align="center">
  
  <img src="https://github.com/user-attachments/assets/5587f9e5-7b54-4181-9a07-1f7f50b5deac" alt="Observing ICMP Traffic" width="80%">
</p>


<p align="center">
  
  <img src="https://github.com/user-attachments/assets/72fe7d44-65c8-45b5-848b-8ae13d813acf" alt="Observing ICMP Traffic" width="80%">
</p>

<p align="center">
  
  <img src="https://github.com/user-attachments/assets/effd7cb5-6e33-436c-8665-39129fe5ff03" alt="Observing ICMP Traffic" width="80%">
</p>


<p align="center">

  <img src="https://github.com/user-attachments/assets/02bc9a1f-6287-41e0-a6c5-3185e61a5681" alt="Observing ICMP Traffic" width="80%">
</p>


<p align="center">
  
  <img src="https://github.com/user-attachments/assets/df329d07-c0e2-49e5-b8b0-5451428c68a6" alt="Observing ICMP Traffic" width="80%">
</p>



<h2>Part 3: Configuring Network Security Groups (NSGs)</h2>

1. To test the effects of security rules, I started a continuous ping from my Windows 10 VM to the Ubuntu VM.
2. I then went to Azure and disabled inbound ICMP traffic in the NSG associated with the Ubuntu VM.
3. Back in WireShark, I observed the blocked ICMP traffic and noticed the ping activity had stopped.
4. Afterward, I re-enabled ICMP traffic in the NSG and observed the traffic being restored and the ping activity resuming.


<p align="center">
  <img src="https://github.com/user-attachments/assets/0fa62b13-5f87-4e54-99bd-f7e97c417568" alt="Configuring NSGs" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d543f20f-e4b8-4304-854e-6af9983c4bb4" alt="Configuring NSGs" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/38c61870-4574-4d79-81e9-77eeb3743455" alt="Configuring NSGs" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6dea725f-feed-4147-8ba1-2a5119dd7f9b" alt="Configuring NSGs" width="80%">
</p>









<h2>Part 4: Observing Protocol Traffic</h2>

I explored different protocols and observed their behavior using WireShark:

- **SSH Traffic:** 
  <p>I captured SSH traffic in WireShark by initiating an SSH session from the Windows 10 VM to the Ubuntu VM using its private IP address (10.0.0.5).</p>
<ul>
  <li>The session was encrypted using the SSHv2 protocol, which includes key exchanges and encrypted packets as part of the secure communication between the two machines.</li>
  <li>In WireShark, I monitored the encrypted traffic as I executed commands within the Ubuntu VM via SSH. The capture confirmed that SSH provides a secure and encrypted channel for communication.</li>
</ul>
<p align="center">
 <img src="https://github.com/user-attachments/assets/1305de79-365c-4724-beff-9df431dacfe7" alt="Observing Protocol Traffic" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/bcd375b3-87a2-4fe9-8810-372686a27aa8" alt="Observing Protocol Traffic" width="80%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b6ab294c-e004-4eb1-bf5b-83bf7ed9c5eb" alt="Observing Protocol Traffic" width="80%">
</p>





- **DHCP Traffic:**
  - I filtered for DHCP traffic in WireShark.
  - On the Windows 10 VM, I created a batch file named `dhcp.bat` containing the commands `ipconfig /release` and `ipconfig /renew`.
  - I executed the batch file in PowerShell, then observed the DHCP handshake taking place in WireShark.


<p align="center">
  <img src="https://github.com/user-attachments/assets/6c694ae7-31c6-4289-a414-75853c918214" alt="Observing Protocol Traffic" width="80%">
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/887454d0-fa4e-432c-afa4-ad33fd5f08df" alt="Observing Protocol Traffic" width="80%">
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/a33433be-f0ac-4e6a-951b-46bfb5a00c71" alt="Observing Protocol Traffic" width="80%">
</p>




- **DNS Traffic:** 
  - Filtering for DNS traffic in WireShark, I used `nslookup` to query DNS records for google.com and disney.com, observing the queries and responses.
 
  <p align="center">
  <img src="" alt="Observing Protocol Traffic" width="80%">
</p>

<p align="center">
  <img src="" alt="Observing Protocol Traffic" width="80%">
</p>

- **RDP Traffic:** 
  - Lastly, I filtered for RDP traffic and observed the continuous flow of packets due to my active Remote Desktop session on the Windows 10 VM.


<p align="center">
  <img src="" alt="Observing Protocol Traffic" width="80%">
</p>

<p align="center">
  <img src="" alt="Observing Protocol Traffic" width="80%">
</p>







<h2>Conclusion</h2>

<p>By completing this lab, I gained experience in deploying VMs, analyzing network traffic, and configuring Network Security Groups in Azure. I also deepened my understanding of network protocols such as ICMP, SSH, DHCP, DNS, and RDP while using WireShark to inspect and analyze these protocols.</p>

<p align="center">
  <!-- Add Conclusion Image -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Conclusion Image" width="80%">
</p>
