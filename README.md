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
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Creating Virtual Machines" width="80%">
</p>

<h2>Part 2: Observing ICMP Traffic</h2>

1. Since I use a Mac, I installed Microsoft Remote Desktop to connect to my Windows 10 VM.
2. Once connected to the Windows 10 VM, I installed WireShark for network analysis.
3. I started a packet capture in WireShark and filtered specifically for ICMP traffic.
4. From the Windows 10 VM, I pinged my Ubuntu VM using its private IP address.
5. In WireShark, I observed the ICMP traffic flowing between the VMs.
6. I also pinged a public website (e.g., google.com) and inspected the ICMP traffic for the public request.

<p align="center">
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Observing ICMP Traffic" width="80%">
</p>

<h2>Part 3: Configuring Network Security Groups (NSGs)</h2>

1. To test the effects of security rules, I started a continuous ping from my Windows 10 VM to the Ubuntu VM.
2. I then went to Azure and disabled inbound ICMP traffic in the NSG associated with the Ubuntu VM.
3. Back in WireShark, I observed the blocked ICMP traffic and noticed the ping activity had stopped.
4. Afterward, I re-enabled ICMP traffic in the NSG and observed the traffic being restored and the ping activity resuming.
5. Once done, I stopped the ping command.

<p align="center">
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Configuring NSGs" width="80%">
</p>

<h2>Part 4: Observing Protocol Traffic</h2>

I explored different protocols and observed their behavior using WireShark:

- **SSH Traffic:** 
  - I captured SSH traffic in WireShark by initiating an SSH session from the Windows 10 VM to the Ubuntu VM using its private IP address.
  - I monitored the encrypted traffic as I interacted with the Ubuntu VM via SSH.
  
- **DHCP Traffic:** 
  - I filtered for DHCP traffic in WireShark.
  - On the Windows 10 VM, I ran `ipconfig /renew` and observed the DHCP handshake taking place in the packet capture.

- **DNS Traffic:** 
  - Filtering for DNS traffic in WireShark, I used `nslookup` to query DNS records for google.com and disney.com, observing the queries and responses.

- **RDP Traffic:** 
  - Lastly, I filtered for RDP traffic and observed the continuous flow of packets due to my active Remote Desktop session on the Windows 10 VM.

<p align="center">
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Observing Protocol Traffic" width="80%">
</p>

<h2>Conclusion</h2>

<p>By completing this lab, I gained experience in deploying VMs, analyzing network traffic, and configuring Network Security Groups in Azure. I also deepened my understanding of network protocols such as ICMP, SSH, DHCP, DNS, and RDP while using WireShark to inspect and analyze these protocols.</p>

<p align="center">
  <!-- Add Conclusion Image -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Conclusion Image" width="80%">
</p>
