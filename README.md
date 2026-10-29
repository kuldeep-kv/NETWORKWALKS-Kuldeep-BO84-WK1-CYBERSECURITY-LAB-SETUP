# NETWORKWALKS-Kuldeep-BO84-WK1-CYBERSECURITY-LAB-SETUP
A hands-on cybersecurity lab setup using VirtualBox, Kali Linux, NAT networking, connectivity testing, and VM snapshots
 🔐 Cybersecurity Lab Setup | VirtualBox & Kali Linux

<p align="center">
  <img src="https://img.shields.io/badge/Domain-Cybersecurity-0A66C2?style=for-the-badge" alt="Domain: Cybersecurity">
  <img src="https://img.shields.io/badge/Platform-VirtualBox-183A61?style=for-the-badge" alt="Platform: VirtualBox">
  <img src="https://img.shields.io/badge/OS-Kali%20Linux-557C94?style=for-the-badge" alt="Operating System: Kali Linux">
  <img src="https://img.shields.io/badge/Focus-Networking-2E8B57?style=for-the-badge" alt="Focus: Networking">
</p>

📌 Project Overview
This project documents the setup of a virtual cybersecurity lab using Oracle VirtualBox and Kali Linux. The objective was to establish a controlled environment for cybersecurity learning, configure virtual networking, verify connectivity and DNS resolution, and create a recovery point for future practical exercises.

The project emphasizes hands-on implementation, systematic verification, troubleshooting, and technical documentation.

🎯 Objectives
Install and configure Oracle VirtualBox.
Import and configure a Kali Linux virtual machine.
Create a dedicated private NAT Network.
Verify IP addressing, network interfaces, and routing.
Test network connectivity and DNS resolution.
Create a clean virtual machine snapshot.
Document the configuration process with screenshots and verification results.
🛠️ Tools & Technologies
Tool / Technology	Purpose
Oracle VirtualBox	Virtualization and virtual machine management
Kali Linux	Linux environment for cybersecurity practice
VirtualBox NAT Network	Virtual networking and outbound connectivity
Linux networking utilities	Interface inspection, routing, and connectivity testing
VirtualBox Snapshot Manager	Recovery to a saved virtual machine state
GitHub	Project documentation and version control
🏗️ Lab Architecture
The lab uses a host machine to run Oracle VirtualBox, which hosts Kali Linux as a guest operating system. The guest VM connects to a dedicated NAT Network configured in VirtualBox.

                 Host Computer
                       |
                Oracle VirtualBox
                       |
                 Kali Linux VM
                       |
                Virtual Network
                       |
                  NAT Network
                       |
              External Connectivity
Note: External connectivity depends on the actual network configuration, gateway, DNS settings, and applicable firewall rules. The diagram represents the intended setup, not a guarantee that every connection succeeds.

Lab Configuration
Record the actual values from your environment.

Configuration	Value
Host operating system	Windows
Virtualization platform	Oracle VirtualBox
Guest operating system	Kali Linux
Virtual network mode	NAT Network
NAT Network name	NATNETWORK
IPv4 network/prefix	10.0.0.1
Recovery snapshot	KaliLinux
⚙️ Implementation & Verification
1. Install and Configure VirtualBox
Objective: Establish the virtualization environment.

Procedure:

Install Oracle VirtualBox on the host machine.
Launch VirtualBox and review the VM management interface.
Verify that the application opens correctly and is ready to manage virtual machines.
Verification: VirtualBox Manager opens successfully.

Evidence:

VirtualBox installation and manager screenshot placeholder

2. Import and Configure Kali Linux
Objective: Deploy Kali Linux as a guest virtual machine.

Procedure:

Import the Kali Linux virtual machine or appliance.
Review the VM configuration, including memory, processors, storage, and network adapter.
Start the virtual machine and confirm that Kali Linux boots successfully.
Verification: The guest operating system starts and its desktop or terminal is accessible.

Evidence:

Kali Linux virtual machine screenshot placeholder

3. Create a Private NAT Network
Objective: Establish a dedicated virtual network for the lab.

Procedure:

Open VirtualBox's network management settings.
Create a NAT Network with a suitable name and IPv4 subnet.
Review the DHCP setting and other network parameters.
Attach the Kali Linux VM's network adapter to the newly created NAT Network.
Save the configuration.
Verification: The NAT Network exists in VirtualBox, and the VM is attached to the intended network.

Evidence:

NAT Network configuration screenshot placeholder

4. Configure and Verify Kali Linux Network Settings
Objective: Inspect the guest's IP addressing and routing configuration.

Run the following commands inside Kali Linux:

ip -br addr
ip route
Command purpose:

ip -br addr displays network interfaces and their assigned addresses in a compact format.
ip route displays the routing table, including the default route when configured.
Verification checklist:

 The expected network interface is present.
 The interface is active.
 The IP address matches the intended network configuration.
 The routing table contains the expected route.
Record any discrepancies and the corrective actions taken.

Evidence:

Kali Linux IP and routing output screenshot placeholder

5. Test Network Connectivity and DNS Resolution
Objective: Verify network reachability and hostname resolution.

Run these tests separately:

A. Check gateway reachability

ping -c 4 <gateway-ip>
Replace <gateway-ip> with the actual gateway address identified from the lab configuration.

B. Check external IP connectivity

ping -c 4 1.1.1.1
This tests reachability to an external IP address, provided the destination and network permit ICMP traffic.

C. Check DNS resolution

getent hosts example.com
This checks whether the system can resolve the hostname using its configured name-resolution mechanisms.

Interpretation:

Test	What it helps verify
Gateway ping	Reachability to the configured gateway
External IP test	External network reachability
Hostname lookup	DNS/name-resolution functionality
A failed ping does not always mean that a destination is unreachable; ICMP traffic may be filtered. Interpret results alongside routing information and other relevant tests.

Verification results:

Test	Actual result	Status
Gateway reachability	Pass	
External IP connectivity	Pass	
DNS resolution	Pass	
6. Create a Clean VM Snapshot
Objective: Preserve a known working state before conducting future lab activities.

Procedure:

Complete the initial VM and network configuration.
Verify the current system state.
Open the VM's snapshot management interface.
Create a snapshot with a descriptive name.
Confirm that the snapshot appears in the VM's snapshot list.
Verification: The saved snapshot is visible in VirtualBox Snapshot Manager.

Snapshot name: KaliLinux

Evidence:

VirtualBox snapshot screenshot placeholder

Why this matters: A snapshot provides a convenient recovery point if later configuration changes or experiments affect the VM. It is not a substitute for independent backups.

🧪 Overall Results
Task	Completion evidence	Status
VirtualBox installation and configuration	VirtualBox Manager	Completed
Kali Linux import and configuration	Running guest VM	Completed
Private NAT Network creation	Network settings	Completed
Kali network settings verification	Interface and route output	Completed
Connectivity and DNS testing	Actual test outputs	Update with results
Clean snapshot creation	Snapshot Manager	Completed
🐛 Troubleshooting & Problem-Solving
Virtual machine networking depends on several components working together, including the network adapter, IP configuration, routing, NAT Network settings, and DNS configuration.

If connectivity or DNS resolution fails, investigate systematically:

1. Inspect the interface

ip -br addr
Check the interface state and assigned IP address.

2. Inspect routing

ip route
Verify the expected gateway and default route.

3. Separate IP connectivity from DNS

Test the configured gateway, then an external IP address, and finally a hostname lookup. This helps narrow down the affected layer.

4. Review VirtualBox configuration

Confirm that the VM is connected to the intended NAT Network and that the network settings match the guest's configuration.

5. Re-test after making a change

📚 Key Learnings
This project strengthened my practical understanding of:

Virtualization and guest operating system deployment.
Linux network interfaces and IP addressing.
Routing and NAT Network configuration.
Network connectivity and DNS troubleshooting.
Virtual machine snapshots and recovery planning.
Technical documentation and evidence-based verification.
🔒 Security Considerations
Use the environment only for authorized cybersecurity learning and testing.
Keep intentionally vulnerable systems isolated as appropriate.
Take snapshots before significant configuration changes.
Avoid exposing sensitive services or credentials.
Do not commit passwords, private keys, tokens, or sensitive host information.
Review screenshots before uploading them to a public repository.
Do not upload complete VM disk images or large appliance exports unless explicitly required and safe.
📁 Repository Structure
cybersecurity-lab-setup/
├── README.md
├── screenshots/
   ├── 01-virtualbox-manager.png
   ├── 02-kali-linux-running.png
   ├── 03-nat-network-configuration.png
   ├── 04-network-configuration.png
   └── 05-vm-snapshot.png

The screenshot filenames above are suggested names. Ensure that the files you upload match the paths referenced in this README.

✅ Conclusion
The project established a foundation for future cybersecurity lab exercises by combining virtualization, Linux networking, connectivity verification, and recovery planning.

The main takeaway is that a reliable lab requires more than deploying a virtual machine: its configuration must be inspected, its connectivity tested, and its baseline documented before more advanced activities begin.

Project: NETWORKWALKS-Kuldeep-BO84-WK1-CYBERSECURITY-LAB-SETUP Tools: Oracle VirtualBox and Kali Linux
Focus: Virtualization, Networking, Verification, and Recovery
Repository: cybersecurity-lab-setup Submitted By: KULDEEP VERMA 
