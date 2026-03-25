# 🔐 Zero Trust Home Lab Architecture

## 📌 Overview
This project presents the design and implementation of a Zero Trust-inspired network architecture in a small-scale home lab environment.

The goal was to reduce the attack surface, eliminate implicit trust, and replace traditional VPN-based remote access with a more secure, identity-based approach.

The setup is built and tested in a live environment.

---

## 🧠 Key Concepts
- Zero Trust Architecture
- Network Segmentation (VLAN)
- Least Privilege Access
- Intrusion Detection & Prevention (IDS/IPS)
- Attack Surface Reduction

---

## 🏗️ Architecture

The lab environment consists of:

- Ubiquiti Express 7 (Gateway with IDS/IPS)
- VLAN-segmented network
- Proxmox virtualization host
- TrueNAS (ZFS storage with snapshots)
- Identity-based remote access (Twingate)

### 🔒 Design Principles
- No port forwarding
- Segmentation between all network zones
- Access control based on necessity
- Continuous monitoring via IDS/IPS

---

## 🌐 Network Segmentation

The network is divided into multiple VLANs to prevent lateral movement and isolate systems.

![VLAN Overview](images/vlan-overview.png)

### VLAN Structure

- **Management (10.0.10.0/27)**  
  Network infrastructure and administrative access

- **Servers (10.0.20.0/29)**  
  Proxmox, TrueNAS and core services

- **Family LAN (10.0.30.0/28)**  
  Trusted client devices

- **Guest (10.0.40.0/28)**  
  Isolated network with internet-only access

- **IoT (10.0.50.0/28)**  
  Restricted devices with limited access

- **NAS Backup (10.0.60.0/29)**  
  Backup network with strict access control

### 🔐 Security Benefit
Segmentation ensures that compromised devices cannot move laterally across the network.

---

## 🔥 Firewall & Traffic Control

Firewall rules are used to enforce segmentation and restrict communication between networks.

![Firewall Rules](images/firewall-rules.png)

### Key Controls
- Blocking communication between VLANs
- Restricting IoT access to internal systems
- Isolating guest network traffic
- Allowing only required communication paths

### 🔐 Security Benefit
Implements Zero Trust principles by only allowing explicitly permitted traffic.

---

## 🛡️ Intrusion Detection & Prevention (IDS/IPS)

The gateway is configured with active IDS/IPS functionality.

![IDS/IPS Settings](images/ids-ips-settings.png)

### Configuration
- Intrusion Prevention enabled
- Detection mode: Notify and Block
- All detection signatures active
- Regular signature updates

### 🔐 Security Impact
- Real-time threat detection
- Automatic blocking of malicious traffic
- Increased visibility into network activity

IDS/IPS was tested in a live environment to observe detection and blocking behavior.

---

## 🖥️ Implementation

### Virtualization (Proxmox)
- Services are hosted in isolated environments
- Separation between critical and non-critical systems

### Storage (TrueNAS)
- ZFS-based storage
- Snapshot capability for backup and recovery

### Remote Access (Zero Trust)
- Identity-based access using Twingate
- No exposure of internal services
- No traditional VPN usage

---

## 📊 Security Improvements

This setup achieved:

- Reduced attack surface (no exposed ports)
- Limited lateral movement through VLAN segmentation
- Improved access control using identity-based access
- Active threat detection with IDS/IPS

---

## 🌊 Real-World Relevance

Experience from ROV operations and industrial systems influenced the design, particularly:

- Network stability and reliability
- Latency considerations
- Secure remote access without exposing services

---

## 🎯 Key Takeaways

- Designed and implemented a segmented network using VLANs
- Applied Zero Trust principles to reduce attack surface
- Implemented IDS/IPS for active threat detection
- Built and tested in a real home lab environment

This project demonstrates practical skills in networking and cybersecurity.

---

## 👨‍💻 Author

Technical background:
- Electrical trade certificate
- Telecommunications trade certificate
- Automation (in progress)
- Network & IT Security student

Focus areas:
- Networking
- Cybersecurity
- Industrial / OT systems
