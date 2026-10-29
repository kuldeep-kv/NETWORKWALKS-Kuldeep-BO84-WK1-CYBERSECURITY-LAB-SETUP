Here is a professionally structured, complete **`README.md`** file tailored for your GitHub repository. It fixes all typos, formats the tables and architecture diagrams cleanly, cleans up the command placeholders, and formats the output into a polished, industry-standard project report.


# NETWORKWALKS Cybersecurity Training Program
## Week 01: Cybersecurity Lab Setup (`NETWORKWALKS-Kuldeep-BO84-WK1-CYBERSECURITY-LAB-SETUP`)

![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-blue?logo=kali-linux)
![VirtualBox](https://img.shields.io/badge/Virtualization-Oracle%20VirtualBox-orange?logo=virtualbox)
![Focus](https://img.shields.io/badge/Focus-Network%20%26%20Lab%20Setup-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)



## 📌 Project Overview

This repository documents the step-by-step setup and verification of a dedicated virtual cybersecurity lab environment as part of the **NetworkWalks Cybersecurity Training Program**. 

The main objective was to establish a secure, controlled, and isolated environment using **Oracle VirtualBox** and **Kali Linux**. The project covers virtual networking topology configuration, local IP/routing inspection, systematic DNS resolution and connectivity testing, snapshot management, and complete verification.



## 🎯 Objectives

* **Virtualization:** Install and configure Oracle VirtualBox to manage local guest VMs.
* **VM Deployment:** Import, configure, and optimize a Kali Linux virtual machine.
* **Network Isolation:** Design and attach a private VirtualBox NAT Network subnet.
* **Network Audit:** Inspect network interfaces, local IP configurations, and routing tables inside Kali Linux.
* **Connectivity Verification:** Perform multi-stage testing for local gateway reachability, external internet access, and DNS name resolution.
* **Baseline Preservation:** Create a pristine VM state snapshot for future lab recovery.
* **Documentation:** Maintain evidence-based technical documentation for version control.

---

## 🛠️ Tools & Technologies

| Tool / Technology | Category | Purpose |
| :--- | :--- | :--- |
| **Oracle VirtualBox** | Hypervisor | Virtualization software and virtual machine management |
| **Kali Linux** | Operating System | Primary guest OS equipped for ethical hacking & pentesting |
| **VirtualBox NAT Network** | Virtual Networking | Provides isolated network routing and outbound internet connectivity |
| **Linux Networking Utilities** | Network Admin | System tools (`ip`, `ping`, `getent`) for configuration & verification |
| **VirtualBox Snapshot Manager** | Security / Recovery | Preserves clean baseline state before executing lab activities |
| **GitHub** | Version Control | Technical documentation, markdown reporting, and tracking |

---

## 🏗️ Lab Architecture

The host machine executes Oracle VirtualBox as the Type-2 hypervisor hosting the Kali Linux guest operating system. The guest VM communicates outbound through VirtualBox's internal NAT Engine and Network adapter.


```

+-------------------------------------------------------------+
|                        Host Computer                        |
|                                                             |
|   +-----------------------------------------------------+   |
|   |                  Oracle VirtualBox                  |   |
|   |                                                     |   |
|   |   +---------------------------------------------+   |   |
|   |   |                Kali Linux VM                |   |   |
|   |   |              (10.0.0.X Subnet)              |   |   |
|   |   +----------------------|----------------------+   |   |
|   |                          | (eth0)               |   |
|   |   +----------------------v----------------------+   |   |
|   |   |            Virtual NAT Network              |   |   |
|   |   |                (NATNETWORK)                 |   |   |
|   |   +----------------------|----------------------+   |   |
|   +--------------------------|--------------------------+   |
+------------------------------|------------------------------+
| (Host Network Adapter)
v
[ External Internet ]

```

> **Note:** External connectivity depends on the host network status, gateway configuration, DNS settings, and applicable firewall rules.

---

## 📋 Lab Configuration

| Parameter | Assigned Value |
| :--- | :--- |
| **Host Operating System** | Windows |
| **Virtualization Platform** | Oracle VirtualBox |
| **Guest Operating System** | Kali Linux |
| **Virtual Network Mode** | NAT Network |
| **NAT Network Name** | `NATNETWORK` |
| **IPv4 Subnet Prefix** | `10.0.0.0/24` |
| **Primary Recovery Snapshot** | `KaliLinux` |

---

## ⚙️ Implementation & Verification

### Step 1: VirtualBox Environment Setup
* **Objective:** Establish the virtualization hypervisor layer.
* **Procedure:** Downloaded and installed Oracle VirtualBox on the host machine. Launched the VirtualBox Manager and configured global default preferences.
* **Verification:** VirtualBox Manager initialized cleanly and was verified ready for VM operations.

---

### Step 2: Kali Linux VM Deployment
* **Objective:** Deploy Kali Linux as the primary laboratory operating system.
* **Procedure:** Imported the pre-built Kali Linux virtual appliance into VirtualBox. Customized RAM allocation, CPU cores, and storage parameters.
* **Verification:** The system booted successfully into the Kali desktop environment.

---

### Step 3: Private NAT Network Creation
* **Objective:** Build an isolated private virtual network for controlled connectivity.
* **Procedure:** 
  1. Navigated to VirtualBox **Tools** -> **Network Manager** -> **NAT Networks**.
  2. Created a new network named `NATNETWORK` with the IP prefix `10.0.0.0/24` and enabled DHCP.
  3. Attached the Kali Linux virtual machine's primary Network Adapter (Adapter 1) to `NATNETWORK`.
* **Verification:** VM network adapter attached cleanly in system settings.

---

### Step 4: Guest Interface & Routing Verification
* **Objective:** Verify assigned network interfaces and routing tables inside Kali Linux.
* **Procedure:** Executed interface and routing diagnostic commands inside the Kali Linux terminal:
  ```bash
  # Check network interface addresses in compact format
  ip -br addr

  # Display kernel routing table and default gateway
  ip route

```

* **Verification:**
* `eth0` interface present and assigned an active IPv4 address within the `10.0.0.0/24` range.
* Default route correctly configured pointing toward the NAT gateway (`10.0.0.1`).



---

### Step 5: Network Connectivity & DNS Testing

* **Objective:** Confirm reachability, packet routing, and hostname lookup resolution.
* **Procedure & Commands:**
**A. Verify Gateway Reachability:**
```bash
ping -c 4 10.0.0.1

```


**B. Verify External IP Reachability (Cloudflare Public DNS):**
```bash
ping -c 4 1.1.1.1

```


**C. Verify Domain Name Resolution (DNS):**
```bash
getent hosts example.com

```


* **Test Matrix Results:**

| Test Focus | Target / Command | Purpose | Result | Status |
| --- | --- | --- | --- | --- |
| **Gateway Reachability** | `10.0.0.1` | Local virtual network routing verification | 0% Packet Loss | **PASS** |
| **External IP Reachability** | `1.1.1.1` | Outbound internet ICMP transit check | 0% Packet Loss | **PASS** |
| **DNS Name Resolution** | `example.com` | Name resolution lookup check | IP Resolved Correctly | **PASS** |

---

### Step 6: VM Baseline Snapshot Creation

* **Objective:** Create a clean operational state recovery point.
* **Procedure:** Shut down/paused non-essential processes, opened VirtualBox Snapshot Manager, and created a snapshot named `KaliLinux`.
* **Verification:** Snapshot saved successfully and visible under the snapshot tree structure.

---

## 🧪 Summary Matrix of Completed Tasks

| Task Description | Verification Artifact | Status |
| --- | --- | --- |
| VirtualBox Installation & Setup | VirtualBox Manager active | ✅ **Completed** |
| Kali Linux Import & Optimization | Operational guest VM terminal | ✅ **Completed** |
| Private NAT Network Configuration | `NATNETWORK` created in VirtualBox | ✅ **Completed** |
| Network & Routing Verification | Valid `ip -br addr` & `ip route` output | ✅ **Completed** |
| End-to-End Connectivity & DNS | Successful `ping` and `getent` output | ✅ **Completed** |
| Pristine Snapshot Creation | `KaliLinux` snapshot point visible | ✅ **Completed** |

---

## 🐛 Troubleshooting & System Diagnostics

If network connectivity issues occur during future lab exercises, use the following systematic checklist to diagnose the issue:

```
[ Step 1: Check Local Interface ]  ---> Command: ip -br addr
                                         Ensure interface is UP and holds a valid IP.
                                                  |
[ Step 2: Check System Gateway ]   ---> Command: ip route
                                         Confirm default route points to gateway (10.0.0.1).
                                                  |
[ Step 3: Test IP Connectivity ]   ---> Command: ping -c 4 1.1.1.1
                                         Rules out DNS issues if IP responds.
                                                  |
[ Step 4: Test Name Resolution ]   ---> Command: getent hosts example.com
                                         Verifies /etc/resolv.conf & DNS servers.
                                                  |
[ Step 5: Check Hypervisor Settings]---> Confirm VirtualBox network mode is attached to 'NAT Network'.

```

---

## 📚 Key Learnings & Practical Takeaways

* **Systematic Setup:** Lab management requires verifying each network layer step-by-step rather than assuming connectivity.
* **Linux Networking:** Hands-on mastery of Linux network tools (`ip`, `ping`, `getent`) for rapid interface auditing.
* **Snapshot Management:** Recognizing snapshots as essential safeguards to restore working states after complex testing.
* **Layered Verification:** Distinguishing between IP-level routing issues and higher-level DNS resolution failures.

---

## 🔒 Security Considerations & Lab Hygiene

* **Authorized Use Only:** The environment is built strictly for educational, research, and authorized security assessments.
* **Network Isolation:** Ensure vulnerable target machines (e.g., Metasploitable) remain isolated within private virtual networks.
* **Data Protection:** Never commit sensitive credentials, API keys, private ssh keys, or sensitive host details to version control.
* **Media Hygiene:** Review screenshot captures to redact any sensitive host system paths or personal identifying details prior to publishing.

---

## 📁 Recommended Repository Structure

```text
cybersecurity-lab-setup/
├── README.md
└── screenshots/
    ├── 01-virtualbox-manager.png
    ├── 02-kali-linux-running.png
    ├── 03-nat-network-configuration.png
    ├── 04-network-configuration.png
    └── 05-vm-snapshot.png

```

---

## 👤 Author & Acknowledgments

* **Submitted By:** Kuldeep Verma
* **Project ID:** `NETWORKWALKS-Kuldeep-BO84-WK1-CYBERSECURITY-LAB-SETUP`
* **Program:** NetworkWalks Cybersecurity Training Program
* **Instructor:** Waqas Karim (CCIE)

```

<FollowUp>
Would you like me to help you draft the Git command-line steps to initialize this repository, commit the files, and push it to GitHub?
</FollowUp>

```
