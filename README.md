# 🌐 Hybrid Network Architecture (HomeLab)

### 📌 Project Overview
The goal was to establish a secure, permanent connection between two geographically separate locations (Home & Apartment) to share resources and centralize management.

### 🛠 Technical Specifications
- **VPN Protocol:** IPsec IKEv1 (Main Mode)
- **Encryption:** AES-256 / SHA-256
- **NAT Traversal:** Enabled (One location is behind a double NAT, the other has a Public IP)

### 🏗 Topology Details
- **Location A (Central):** Fortigate 60D, Public IP, 5 VLANs (Management, DMZ, Internal, IoT, Guest).
- **Location B (Remote):** Fortigate 60D, behind ISP NAT.
- **VLAN Segmentation:** Strict firewall policies to isolate DMZ services from the internal management network.
- **Gateway Security:** Cloudflare Tunnels (Zero Trust) for exposing internal services (Nginx Proxy Manager) without opening ports.

### 🖥 Compute Stack
- **Cluster:** 3x Proxmox VE Nodes.
- **Automation:** Ansible for system updates and container deployments.
- **Monitoring:** Uptime Kuma, Graylog (centralized logs from Fortigate & Nginx).
