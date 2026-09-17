# 🔐 Cybersecurity Lab Setup – Kali Linux & VirtualBox

> A controlled virtual cybersecurity lab environment built using Oracle VirtualBox and Kali Linux for cybersecurity learning, penetration-testing practice, network security testing, and future security labs.

---

## 📌 Project Overview

This project documents the setup of a virtual cybersecurity laboratory using:

- Oracle VirtualBox
- Kali Linux
- NAT Network
- Linux networking tools

The purpose of this lab is to create an isolated and controlled environment where cybersecurity tools and security-testing techniques can be practiced safely.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

The lab will also serve as the foundation for future cybersecurity projects involving:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Web application security testing
- Packet analysis
- Security tool practice
- Penetration-testing labs

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure Oracle VirtualBox
- Set up Kali Linux as a virtual machine
- Create a dedicated NAT Network
- Configure Kali Linux network connectivity
- Verify IP addressing and network communication
- Test DNS resolution and Internet connectivity
- Create a clean VM snapshot for recovery
- Build a reusable environment for future cybersecurity labs

---

## ⚙️ Lab Configuration

|   Component       |    Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 10         |
| 🧠 Host RAM        | 8 GB               |
| ⚡ Processor       | Intel Core i7      |
| 🧰 Hypervisor      | VirtualBox 7.2  |
| 🐉 Security OS     | Kali Linux 2026.2  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

---

## 🪜 Lab Setup Procedure

## Step 1 - Download and Install 7-Zip

Download & install 7-zip: https://7-zip.org/download.html

7-Zip is to extract the required zip files resulting in executable normal files.

---

## Step 2 – Download and Import Kali Linux

Download & install Virtualbox on your laptop/PC: https://virtualbox.org/wiki/Downloads

Oracle VirtualBox was installed and configured as the virtualization platform for the cybersecurity laboratory.

---

## Step 3 - Create the NAT Network

A dedicated NAT Network was created in VirtualBox

Example configuration:

Network Type: NAT Network
DHCP: Enabled
IPv4: Enabled
IPv6: Disabled



The NAT Network allows multiple virtual machines to communicate with each other while providing controlled outbound network connectivity.

---

## Step 4 – Download and Import Kali Linux

Download & import Kali Linux Virtual Machine in your Virtualbox: https://kali.org/get-kali

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
```

---

## Step 5 – Configure Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

---

## Step 6 - Create a Clean VM Snapshot

After completing the initial configuration, a clean VirtualBox snapshot was captured.

The snapshot provides a recovery point for the laboratory, if future experiments modify the VM configuration or cause unwanted changes.

---

## 🔎 Lab Verification

The following tests were performed to verify the laboratory setup.

| Test             | Command               | Purpose                           |
| ---------------- | --------------------- | --------------------------------- |
| Check IP Address | `ip a`                | Verify network configuration      |
| Test Gateway     | `ping <gateway-ip>`   | Verify local connectivity         |
| Test Internet    | `ping 8.8.8.8`        | Verify outbound connectivity      |
| Test DNS         | `nslookup google.com` | Verify DNS resolution             |
| Check Nmap       | `nmap --version`      | Verify security tool availability |
| Snapshot Test    | Restore snapshot      | Verify recovery capability        |

---

## Expected results

IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8

---

# 🐞 Problems Encountered & Solutions

Problem 1. Internet Connectivity After Static IP Configuration

After manually configuring the static IPV4 address the network connectivity worked as expected, but network connection failed but rebooted the virtual box.

ran the below command and rebooted the VM again to restore the network connection.

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

# 💡 What I Learned

This project provided hands-on experience in building a controlled cybersecurity laboratory from the ground up.

### 1. NAT vs NAT Network

Network Address Translation (NAT) is a general networking method used to let multiple devices share a single public IP address, whereas a NAT Network is a specific virtualized network setting (like in VirtualBox) that allows multiple virtual machines to talk to each other while sharing a single internet connection.

Core Differences:

NAT: A general protocol and router function that translates private IP addresses into a public IP address for internet access.

NAT Network: A virtual switch environment provided by hypervisors that groups multiple virtual machines under one shared internal subnet and NAT gateway.Device 

Communication:

NAT: Virtual machines or local devices are isolated from each other and cannot communicate directly.

NAT Network: Virtual machines on the same network can communicate directly with one another while remaining hidden from the outside physical LAN.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

I learned how to capture a clean VM which can be used as a recovery point for the laboratory, if future experiments modify the VM configuration or cause unwanted changes.
