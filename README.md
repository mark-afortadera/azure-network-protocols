<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create Virtual Machines using Microsoft Azure Cloud Platform
- Observe ICMP Traffic
- Configuring a Firewall Network Security Group
- Step 4

<h2>Actions and Observations</h2>

![Screenshot 2025-02-14 151022](https://github.com/user-attachments/assets/eaac3a94-123f-4dbc-8bad-38eb4e99e730)

<p>Create a resource group using Microsoft Azure Cloud Platform</p>
<br />

![Screenshot 2025-02-14 151240](https://github.com/user-attachments/assets/b9b93f86-f892-4f0e-9cc8-33025a49327e)
![Screenshot 2025-02-14 163906](https://github.com/user-attachments/assets/30549962-1ecb-4a47-a64b-4b3ef769105d)
![Screenshot 2025-02-14 164024](https://github.com/user-attachments/assets/14ec8bb4-6e14-414a-9c5a-7a35bc74f9da)

<p>Create 2 virtual machines within the resource group (windows and linux vm)</p>
<br />

![Screenshot 2025-02-14 203813](https://github.com/user-attachments/assets/61a1cea0-ab09-4a25-98c5-cc98d1e54d07)

<p>Use Remote Desktop to connect to Windows 10 Virtual Machine</p>
<br />

![Screenshot 2025-02-14 204013](https://github.com/user-attachments/assets/723bb893-3e85-431d-b47b-c20c3bdc19e3)
![Screenshot 2025-02-14 204245](https://github.com/user-attachments/assets/45ff6b89-b807-45a6-ae43-0596c7dea934)

<p>Within your Windows 10 Virtual Machine, Install Wireshark</p>
<br />

![Screenshot 2025-02-14 204353](https://github.com/user-attachments/assets/069e9731-8bbe-4069-a265-86fb6f78fd7d)
![Screenshot 2025-02-14 204555](https://github.com/user-attachments/assets/50ca49c1-0108-404b-9ebf-0c958750737f)
![Screenshot 2025-02-14 204602](https://github.com/user-attachments/assets/c7d07e50-a629-4787-aabc-eb93735c2b48)

<p>Open Wireshark and start packet capture</p>
<br />

![Screenshot 2025-02-14 205003](https://github.com/user-attachments/assets/b5405ba1-80c6-4b03-8d93-c1d6386dc749)
![Screenshot 2025-02-14 205216](https://github.com/user-attachments/assets/6b6b5a7b-5547-4c78-9968-63722427e261)

<p>Within Wireshark, filter for ICMP traffic only</p>
<p>From The Windows 10 VM, open command line or PowerShell and attempt to ping a
 public website (such as www.google.com) and observe the traffic in WireShark</p>
<br />

![Screenshot 2025-02-14 210733](https://github.com/user-attachments/assets/91b09a4e-bb7d-46ab-962c-dd08391341bd)
![Screenshot 2025-02-14 210947](https://github.com/user-attachments/assets/197768f6-556b-469b-b463-8d2e0278d6c3)

<p>Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from
 within the Windows 10 VM</p>

![Screenshot 2025-02-14 211535](https://github.com/user-attachments/assets/b73234d5-e76c-41a2-bd23-d4d2128301b2)

<p>Initiate a perpetual/non-stop ping from your Windows 10 VM to Ubuntu VM</p>
<p>- Observe ping requests and replies within WireShark</p>
<br />

![Screenshot 2025-02-14 211744](https://github.com/user-attachments/assets/4c053ac9-4d34-4746-ba34-6fd7469dfc9f)
![Screenshot 2025-02-14 212033](https://github.com/user-attachments/assets/4952a2a4-9590-4ebe-bb21-b5111c64ef26)
![Screenshot 2025-02-14 212208](https://github.com/user-attachments/assets/0c46f327-c83b-4c6c-b55f-773279a39d6e)


<p>Open the Network Security Group, Ubuntu VM is using and disable incoming
(inbound) ICMP traffic</p>
<br />

![Screenshot 2025-02-14 212330](https://github.com/user-attachments/assets/650ca876-81ce-4555-adae-357a7f800c6a)

<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the
 command line Ping activity</p>
<br />

![Screenshot 2025-02-14 212831](https://github.com/user-attachments/assets/479a85af-55fb-4204-8f9c-6cc27b1217f0)

<p>Re-enable ICMP traffic for the Network Security Group</p>
<br />

![Screenshot 2025-02-14 213006](https://github.com/user-attachments/assets/12953c73-354b-4b1f-8222-450a3aa45ef3)

<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the
 command line Ping activity </p>
<br />

![Screenshot 2025-02-17 161823](https://github.com/user-attachments/assets/ad48ca4a-7b5a-4263-b827-8e036e3b43ba)
![Screenshot 2025-02-17 161920](https://github.com/user-attachments/assets/b7888fd0-87ad-4ad8-a1ec-715895bed067)

<p>Filter for SSH traffic only</p>
<p>From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP
 address)</p>
<p>Open PowerShell, and type: ssh labuser@(Private IP Address)</p>
<br />

![Screenshot 2025-02-17 163811](https://github.com/user-attachments/assets/684f79f6-639c-4a02-8f4d-304db1d6bc19)

<p>Type commands (username, pwd, etc) into the linux SSH connection and
 observe SSH traffic spam in WireShark</p>
<br />

![Screenshot 2025-02-17 162924](https://github.com/user-attachments/assets/b845b5d8-829c-4dc9-a5b0-e7082e896036)

<p>Exit the SSH connection by typing ‘exit’ and pressing [Enter]</p>
<br />

![Screenshot 2025-02-17 165245](https://github.com/user-attachments/assets/04fbea19-66b0-4b8e-b508-0b36bf06717e)
![Screenshot 2025-02-17 165539](https://github.com/user-attachments/assets/68539c2b-39a8-47b6-8a3d-b196df989b7f)

<p>Back in Wireshark, filter for DHCP traffic only</p>
<p>From your Windows 10 VM, attempt to issue your VM a new IP address from the
 command line</p>
<br />

![Screenshot 2025-02-17 165642](https://github.com/user-attachments/assets/692f41e1-2476-448d-af64-3bb102dd2228)

<p>Open PowerShell as admin and run: ipconfig /renew</p>
<br />

![Screenshot 2025-02-17 165734](https://github.com/user-attachments/assets/89e479b7-48fe-46ff-bd6d-39c46d33b5fe)

<p>Observe the DHCP traffic appearing in WireShark</p>
<p>- This sequence shows the normal process of a device releasing an old IP address and acquiring a new one through DHCP</p>
<br />

![Screenshot 2025-02-17 171138](https://github.com/user-attachments/assets/a3f88be0-5823-4b6b-be68-058f0e3179fc)

<p>Back in Wireshark, filter for DNS traffic only</p>
<p>From your Windows 10 VM within a command line, use nslookup to see what
 google.com and disney.com’s IP addresses are</p>
<p>- Observe the DNS traffic being show in WireShark</p>
<br />

![Screenshot 2025-02-17 172046](https://github.com/user-attachments/assets/66dee761-df42-4950-b252-65524e45f1d5)

<p>Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)</p>
<p>- Observe the immediate non-stop spam of traffic</p>
<p>- The RDP protocol continuously transmits data as a live stream between computers, 
 causing non-stop traffic even when no activity is being performed from one computer to another,
 therefore traffic is always being transmitted.</p>
<br />
