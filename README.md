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

### Phase 2: Host & Network Initialization

* **Base OS Provisioning:** Windows Server 2022 Standard (Desktop Experience) successfully deployed and post-install boot loop resolved.
* **Host Identification:** Hostname changed from default auto-generated name to `DC01`.
* **Network Adapter Configuration:** Static IP address assigned (`192.168.100.10/24`) with loopback address (`127.0.0.1`) assigned as primary DNS in preparation for AD DS/DNS installation.

### Phase 3: Active Directory Domain Services (AD DS) & Forest Promotion

* **AD DS Role Installation:**
* Added **Active Directory Domain Services** role and core management features (`Remote Server Administration Tools`) to `DC01`.
* Configured installation via Server Manager wizard without post-install dependency errors.

* **Forest Promotion & Domain Initialization:**
* Promoted `DC01` to the first Domain Controller in a new Active Directory forest (`lab.local`).
* Set Forest and Domain Functional Levels to **Windows Server 2016** baseline.
* Provisioned integrated **Domain Name System (DNS) Server** and **Global Catalog (GC)** roles on the host.

* **DNS Delegation & Network Verification:**
* Identified and validated expected DNS delegation warning (`A delegation for this DNS server cannot be created...`).
* Confirmed standard behavior for an isolated root forest operating without an upstream public Internet DNS hierarchy.
* Configured Directory Services Restore Mode (DSRM) administrator credentials for emergency recovery operations.
