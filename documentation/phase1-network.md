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

## Troubleshooting & Networking Fixes

### Issue: VMs Unable to Access Internet on Fedora Host
When initially configuring the virtual bridge (`virbr0`) on the Fedora host, the guest VMs (Windows and Kali) were unable to route traffic to the internet through the physical Wi-Fi interface (`wlp3s0`).

### Resolution: Manual Firewall & Routing Configuration
To resolve this, I manually updated the Linux kernel's forwarding policies and configured Network Address Translation (NAT) via `iptables`:

1.  **Enable IP Forwarding:** 
    `iptables -I FORWARD -i virbr0 -o wlp3s0 -j ACCEPT`
    *   **Reason:** This explicitly allows the host to forward traffic originating from the virtual bridge (`-i virbr0`) and exiting the physical wireless interface (`-o wlp3s0`).

2.  **Configure NAT (Masquerade):**
    `iptables -t nat -I POSTROUTING -o wlp3s0 -j MASQUERADE`
    *   **Reason:** This allows the host to "mask" the VM's private IP address with its own physical IP, enabling the home router to properly route return traffic back to the VM.

---
*Documentation updated as of: April 15, 2026*
