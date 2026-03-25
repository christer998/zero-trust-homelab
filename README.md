# 🔐 Zero Trust Home Lab Architecture

## 📌 Overview
This project presents the design and implementation of a Zero Trust-inspired network architecture in a small-scale home lab environment.

The goal was to reduce the attack surface, eliminate implicit trust, and replace traditional VPN-based remote access with identity-based access control.

The solution is designed, implemented, and tested in a live environment.

---

## 🧠 Key Concepts
- Zero Trust Architecture
- Network Segmentation (VLAN)
- Least Privilege Access
- Intrusion Detection & Prevention (IDS/IPS)
- Attack Surface Reduction

---

## 🧰 Technologies Used
- Ubiquiti Express 7 (Gateway with IDS/IPS)
- Proxmox (Virtualization)
- TrueNAS (ZFS storage and snapshots)
- Twingate (Zero Trust remote access)
- Fedora Linux
- VLAN-based network segmentation

---

## 🏗️ Architecture

The lab environment consists of:

- Segmented network using VLANs
- Virtualized services hosted on Proxmox
- Centralized storage with TrueNAS
- Secure remote access via Twingate

### 🔒 Design Principles
- No port forwarding
- No direct exposure of internal services
- Segmentation between all network zones
- Access based on identity and necessity
- Continuous monitoring via IDS/IPS

---

## 🌐 Network Segmentation

The network is divided into multiple VLANs to prevent lateral movement and isolate systems.

![VLAN Overview](images/vlan-overview.png)

### VLAN Structure

- **Management (10.0.10.0/27)**  
  Infrastructure and administrative access

- **Servers (10.0.20.0/29)**  
  Proxmox, TrueNAS and core services

- **Family LAN (10.0.30.0/28)**  
  Trusted client devices

- **Guest (10.0.40.0/28)**  
  Internet-only access

- **IoT (10.0.50.0/28)**  
  Restricted devices with limited access

- **NAS Backup (10.0.60.0/29)**  
  Backup network with strict access rules

### 🔐 Security Benefit
Segmentation ensures compromised devices cannot move laterally across the network.

---

## 🔥 Firewall & Traffic Control

Firewall rules enforce segmentation and restrict communication between VLANs.

![Firewall Rules](images/firewall-rules.png)

### Key Controls
- Blocking inter-VLAN communication by default
- Restricting IoT network access
- Isolating guest network traffic
- Allowing only explicitly required communication

### 🔐 Security Benefit
Implements Zero Trust principles by enforcing least privilege at the network level.

---

## 🛡️ Intrusion Detection & Prevention (IDS/IPS)

The gateway is configured with active IDS/IPS functionality.

![IDS/IPS Settings](images/ids-ips-settings.png)

### Configuration
- Intrusion Prevention enabled
- Detection mode: Notify and Block
- All available signatures enabled
- Regular signature updates

### 🔐 Security Impact
- Real-time detection of suspicious traffic
- Automatic blocking of threats
- Increased visibility into network behavior

---

## 🧪 Testing & Validation

The environment was tested in a live setup to validate security controls and network behavior.

### Tests performed:
- Verified VLAN isolation by attempting cross-network communication
- Confirmed restricted access between IoT, Guest and internal networks
- Observed IDS/IPS detection and blocking behavior
- Tested remote access using Twingate without exposing services
- Validated that no internal systems were reachable from the internet

### Result:
The implementation successfully reduced attack surface, prevented lateral movement and enforced controlled access across the environment.

---

## 🖥️ Implementation

### Virtualization (Proxmox)
- Services deployed in isolated environments
- Separation between critical and non-critical workloads

### Storage (TrueNAS)
- ZFS-based storage with snapshot capability
- Reliable backup and recovery strategy

### Remote Access (Zero Trust)
- Identity-based access using Twingate
- No VPN required
- No exposed services or open ports

---

## 📊 Security Improvements

- Eliminated external attack surface (no open ports)
- Reduced lateral movement through segmentation
- Improved access control with identity-based access
- Enabled real-time threat detection (IDS/IPS)

---

## 🌊 Real-World Relevance

Experience from ROV operations and industrial systems influenced the design:

- Focus on network reliability and stability
- Consideration of latency and data flow
- Secure remote access without exposing infrastructure

---

## 🎯 Key Takeaways

- Designed and implemented segmented network using VLANs
- Applied Zero Trust principles in a real environment
- Implemented IDS/IPS for active threat detection
- Built and validated in a live home lab

This project demonstrates practical skills in networking and cybersecurity.

---

## 👨‍💻 Author

Technical background in electrical systems, telecommunications and industrial operations.

Currently focused on networking, cybersecurity and IT/OT integration.
