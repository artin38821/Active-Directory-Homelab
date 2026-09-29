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
---

## 3. Deployment Log

### Phase 1: Base Operating System & Network Setup
* **Hypervisor Configuration:**
  * Created isolated VirtualBox NAT Network (`AD-LAB-NETWORK` - `192.168.100.0/24`).
  * Explicitly disabled hypervisor-level DHCP to prevent conflicts with future Active Directory DHCP services.
* **VM Provisioning (`DC01`):**
  * Allocated 2 vCPUs, 4GB RAM, and 50GB dynamically allocated VDI disk storage.
  * Mapped primary network adapter to `AD-LAB-NETWORK`.
* **OS Deployment:**
  * Mounted `SERVER_EVAL_x64FRE_en-us` ISO.
  * Selected **Windows Server 2022 Standard Evaluation (Desktop Experience)** for full GUI administrative access.
  * Executed custom clean disk installation to 50GB unallocated partition.
  #### Architecture & Configuration Verification

[NAT Network Configuration]
*Figure 1: Isolated NAT Network setup (`AD-LAB-NETWORK`) with hypervisor-level DHCP disabled.*

[DC01 Network Adapter Setup]
*Figure 2: Mapping DC01 network interface adapter to the custom NAT network.*
