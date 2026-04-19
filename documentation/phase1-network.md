# Phase 1: Virtualization & Networking

## Hypervisor Selection: KVM/QEMU (Virt-Manager) on Fedora
Initially, VirtualBox was considered but faced compatibility issues with the Fedora host environment. Switching to **Virt-Manager with KVM/QEMU** provided a more stable, kernel-native virtualization experience.

### Host Machine Specifications:
- **OS:** Fedora
- **Tools Used:** `virt-manager`, `libvirt`, `kvm`

## Virtual Network Design
To ensure secure isolation of the lab environment while maintaining essential communication between nodes, the following networking configuration is used:

### Initial Setup (Configuration Phase):
- **Mode:** NAT
- **Reason:** To allow VMs to access the internet for initial updates, software downloads (Splunk, Sysmon), and OS activation.

### Final Target Configuration:
- **Network Name:** `SOC_Lab_Net` (Internal Network)
- **Subnet:** (e.g., 10.0.0.0/24)
- **IP Assignment:** (e.g., Static IPs for Splunk server)

## Virtual Machine Inventory:
| VM Name | OS | RAM | Storage | Role |
| :--- | :--- | :--- | :--- | :--- |
| **Windows-11-Target** | Windows 11 Pro | 4GB+ | 60GB | Splunk Server & Telemetry Source |
| **Kali-Linux** | Kali Rolling | 2GB | 30GB | Attack Simulation Node |

---
*Documentation updated as of: April 15, 2026*
