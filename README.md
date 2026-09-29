# Active-Directory-Homelab
Deployment and documentation of a virtualized Active Directory environment on Windows Server 2022.
# Active Directory Homelab Environment

## 1. Overview & Architecture
* **Hypervisor:** VirtualBox 7.2
* **Network:** `AD-Lab-Network` (NAT Network)
* **Subnet:** `192.168.100.0/24`
* **DHCP:** Disabled on VirtualBox (Managed by Windows Server DC later)

---

## 2. Virtual Machine Specs (`DC01`)
* **Role:** Primary Domain Controller
* **OS:** Windows Server 2022 Standard Evaluation (Desktop Experience)
* **CPU:** 2 vCPUs
* **RAM:** 4096 MB (4 GB)
* **Disk:** 50 GB VDI
