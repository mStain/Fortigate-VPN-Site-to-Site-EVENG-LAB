🌐 Secure Site-to-Site VPN with OSPF Routing (EVE-NG Lab)

Project Name: Site-to-Site IPsec VPN using FortiGate & OSPF

Overview

This project demonstrates the configuration and verification of a secure site-to-site Virtual Private Network (VPN) tunnel utilizing IPsec between two simulated next-generation firewall (NGFW) appliances (e.g., FortiGate, Cisco ASA, or Palo Alto).

The lab incorporates OSPF (Open Shortest Path First) as the dynamic routing protocol running over the VPN tunnel interface to automatically exchange routing information between the two sites, proving the tunnel's functionality and providing a scalable solution for network connectivity.

🎯 Key Learning Objectives

Differentiate between tunnel-mode and transport-mode IPsec usage.

Bind the IPsec VPN tunnel to a virtual tunnel interface (e.g., st0.0 or equivalent).

Configure OSPF peering across the secure tunnel interface.

Verify end-to-end connectivity, encryption, and routing table updates.

🧪Lab Topology
<img width="995" height="627" alt="image" src="https://github.com/user-attachments/assets/483fade0-6f44-44df-89f5-178a6411fbf3" />


🛠️ Prerequisites (For Replicating the Lab)

EVE-NG Installation: A functional EVE-NG Pro or Community edition server.

Device Images: Appropriate QEMU images for the networking devices used (e.g., FortiGate VM images, Cisco IOSv, etc.).

Lab File: The exported topology file (ipsec_ospf_lab.unl) included in this repository.

📝 Configuration Steps Summary

Step 1: IPsec Tunnel Configuration

IKE Phase 1 (Proposal): Configured for (e.g., AES-256, SHA-256, DH Group 14).

IKE Phase 2 (Selectors): Configured for (e.g., AES-256, SHA-256, Lifetime 3600 seconds).

Interface: A virtual tunnel interface was created and bound to the IPsec VPN.

Step 2: OSPF Configuration

Tunnel Interface: The virtual tunnel interface (10.10.10.0/30 network) was included in OSPF Area 0 (Backbone).

Internal Networks: The local LAN subnet (e.g., 192.168.10.0/24 at Site A) was advertised into OSPF.

Step 3: Security Policy / Firewall Rules

Policy: A firewall policy was created on both devices to permit traffic between the internal zones and the newly created VPN tunnel zones.

✅ Verification and Testing

To verify the successful deployment, the following commands/checks were performed:

VPN Status Check: Confirmed the IPsec tunnel status was Up (Phase 1 and Phase 2 established).

Routing Table: Verified that the remote subnet was successfully learned via OSPF (e.g., Site A's routing table contained 192.168.20.0/24 via 10.10.10.2).

End-to-End Ping: Successfully pinged the remote LAN PC (e.g., ping 192.168.20.10 from 192.168.10.10).


Files in this Repository

VPN-S2S.unl

README.md: This documentation.

.gitignore: Standard git exclusion file.


Author: mStain

