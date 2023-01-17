<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<h3>Creating our Resources</h3>

<p>
1. Create a Resource Group in Microsoft Azure.<br />
2. Create a Windows 10 Virtual Machine (VM)<br />
&nbsp; &nbsp; a. While creating the VM, select the previously created Resource Group<br />
&nbsp; &nbsp; b. While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet<br />
3. Create a Linux (Ubuntu) VM<br />
4. While create the VM, select the previously created Resource Group and Vnet<br />
4. Observe Your Virtual Network within Network Watcher<br />
</p>
<br />

<img src="https://i.imgur.com/1tKnuig.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />

<h3>Observe ICMP Traffic</h3>

<p>
1. Use Remote Desktop to connect to your Windows 10 Virtual Machine<br />
2. Within your Windows 10 Virtual Machine, Install Wireshark (https://www.wireshark.org/download.html)<br />
3. Open Wireshark and filter for ICMP traffic only<br />
4. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
&nbsp; &nbsp; a. Observe ping requests and replies within WireShark<br />
5. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (for example, www.google.com) and observe the traffic in WireShark<br />
6. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM<br />
&nbsp; &nbsp;a. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic<br />
&nbsp; &nbsp;b. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity<br />
&nbsp; &nbsp;c. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using<br />
&nbsp; &nbsp;d. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)<br />
&nbsp; &nbsp;e. Stop the ping activity<br />
</p>
<br />

<img src="https://i.imgur.com/IIUShxp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/GLxSIG3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/5vXO75R.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/Asl80tN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Observe SSH Traffic</h3>

<p>
1. Back in Wireshark, filter for SSH traffic only<br />
2. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)<br />
&nbsp; &nbsp;a. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark<br />
&nbsp; &nbsp;b. Exit the SSH connection by typing ‘exit’ and pressing [Enter]<br />
</p>
<br />

<img src="https://i.imgur.com/zteR41r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Observe DHCP Traffic</h3>

<p>
1. Back in Wireshark, filter for DHCP traffic only<br />
2. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig/renew)<br />
3. Observe the DHCP traffic appearing in WireShark<br />
</p>
<br />

<img src="https://i.imgur.com/vU8fpQf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Observe DNS Traffic</h3>

<p>
1. Back in Wireshark, filter for DNS traffic only<br />
2. From your Windows 10 VM within a command line, use nslookup to see the IP addresses of google.com and disney.com<br />
3. Observe the DNS traffic being shown in WireShark<br />
</p>
<br />

<img src="https://i.imgur.com/VMcwmsO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Observe RDP Traffic</h3>

<p>
1. Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)<br />
2. Observe the immediate non-stop spam of traffic<br />
</p>
<br />

<img src="https://i.imgur.com/VxXGv6X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>Conclusion</h3>

<p>
Thank you for reading my tutorial.  I hope this helps you. When you finish the tutorial, be sure to delete the Resource Groups on Azure and verify that they are deleted to avoid extra fees.
</p>
