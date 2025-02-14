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

<p>Use Remote Desktop to connect to your Windows 10 Virtual Machine</p>
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

<p>Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM</p>
<p>- Observe ping requests and replies within WireShark</p>
<br />

![Screenshot 2025-02-14 211744](https://github.com/user-attachments/assets/4c053ac9-4d34-4746-ba34-6fd7469dfc9f)
![Screenshot 2025-02-14 212033](https://github.com/user-attachments/assets/4952a2a4-9590-4ebe-bb21-b5111c64ef26)
![Screenshot 2025-02-14 212208](https://github.com/user-attachments/assets/0c46f327-c83b-4c6c-b55f-773279a39d6e)


<p>Open the Network Security Group your Ubuntu VM is using and disable incoming
 (inbound) ICMP traffic</p>
<br />

![Screenshot 2025-02-14 212330](https://github.com/user-attachments/assets/650ca876-81ce-4555-adae-357a7f800c6a)

<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the
 command line Ping activity</p>
<br />

![Screenshot 2025-02-14 212831](https://github.com/user-attachments/assets/479a85af-55fb-4204-8f9c-6cc27b1217f0)

<p>Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is</p>
<br />

![Screenshot 2025-02-14 213006](https://github.com/user-attachments/assets/12953c73-354b-4b1f-8222-450a3aa45ef3)

<p>Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the
 command line Ping activity </p>
<br />
