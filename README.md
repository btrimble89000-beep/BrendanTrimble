# IT Infrastructure & Systems Administration Lab Portfolio

**Brendan Trimble** | Cybersecurity, B.S. — Purdue University  
CNIT 242 · CNIT 340 · CNIT 344 | Spring–Fall 2026

---

## Overview

This repository documents a series of hands-on enterprise IT infrastructure labs completed at Purdue's Polytechnic University in the Computer Information Technology (CIT) department. Across seven labs, I designed, deployed, and administered multi-server Windows environments, Nutanix hyperconverged infrastructure, Linux systems, and physical network architectures, mirroring the toolsets and workflows used in professional IT and cybersecurity operations.

---

## Lab Summary

| # | Lab Title | Course | Completed |
|---|-----------|--------|-----------|
| 1 | Microsoft Windows Infrastructure | CNIT 242 | Jan 2026 |
| 2 | Microsoft Windows Administration | CNIT 242 | Feb 2026 |
| 3 | Enterprise Virtualization | CNIT 242 | Mar 2026 |
| 4 | Enterprise Windows Server Administration | CNIT 242 | Apr 2026 |
| 5 | Enterprise Windows Server Administration — Part II | CNIT 242 | May 2026 |
| 6 | Physical Layer and Ethernet Overview | CNIT 344 | Sep 2026 |
| 7 | UNIX/Linux System Administration | CNIT 340 | Sep 2026 |

---

## Lab Details

### Lab 1: Microsoft Windows Infrastructure (CNIT 242)
**Platform:** Dell OptiPlex 5060 & Dell Pro Tower Plus workstations | Windows Server 2022 | Windows 11

Established foundational enterprise infrastructure from the ground up. Prepared bootable USB media using Ventoy, performed bare-metal installations of Windows Server 2022 across multiple physical workstations, and configured Active Directory Domain Services (AD DS) to create a new forest. Configured DNS with primary (`44.2.1.44`) and alternate (`44.2.1.45`) resolvers, assigned static IP addressing within the `44.38.3.0/24` subnet across three member machines, and set enterprise time synchronization via internal time servers (`tick.cit.lcl` / `tock.cit.lcl`). Applied local Group Policy hardening using `gpedit.msc` and `secpol.msc`.

**Key skills:** Ventoy bootable media, bare-metal OS deployment, AD DS forest creation, DNS configuration, Group Policy, static IP addressing

---

### Lab 2: Microsoft Windows Administration (CNIT 242)
**Platform:** Windows Server 2022 (G03SRV01–G03SRV03) | Windows 11 VMs | VMware Workstation

Built a fully operational multi-domain Active Directory environment simulating the "WoodRock" enterprise (a fictional wood sales company). Administered three domain controllers across a parent domain (`group03.c24200.cit.lcl`) and two child domains (`c242-03-a` and `c242-03-b`), each mapped to distinct business units. Configured Organizational Unit (OU) hierarchies with department-level structure (Accounting, HR, Executive, Warehouse, Shipping, Marketing, Outside Sales, Inside Sales, Account Management), provisioned domain users, and implemented role-based access via Domain Local and Global security groups. Deployed Group Policy Objects (GPOs) for registry editor restrictions (`regedit.msc` disablement), folder redirection, roaming profiles, disk quotas, and network printer deployment. Validated cross-domain trust, DNS resolution, and policy inheritance across the forest.

**Key skills:** Multi-domain AD DS forests, OU hierarchy design, GPO creation and linking, user/group provisioning, folder redirection, roaming profiles, disk quotas, network printing, VMware Workstation

---

### Lab 3: Enterprise Virtualization (CNIT 242)
**Platform:** Nutanix AHV (Acropolis Hypervisor) | Prism Element | Prism Central | Windows Server 2025 | Windows 11

Migrated an existing physical Windows Server infrastructure to a Nutanix hyperconverged environment. Demoted domain controllers and stripped existing partitions from physical hosts before installing Nutanix Community Edition on bare metal. Configured Nutanix clusters via the Prism Element web interface, set up iSCSI Data Service IP and virtual IPs, deployed Prism Central for multi-cluster management, and created storage containers. Built Windows Server 2025 and Windows 11 VM templates by deploying VMs, installing VirtIO drivers, running Sysprep for generalization, installing Nutanix Guest Tools (NGT), and capturing snapshots as reusable templates. Deployed VMs from templates and re-promoted domain controllers, transferring FSMO roles (`RID Master`, `PDC Emulator`, `Infrastructure Master`, `Schema Master`, `Domain Naming Master`) to new virtual domain controllers. Integrated Active Directory domains with Nutanix Prism Central for centralized identity management.

**Key skills:** Nutanix AHV, Prism Element, Prism Central, VM templates, Sysprep, VirtIO drivers, Nutanix Guest Tools (NGT), FSMO role transfer, iSCSI, hyperconverged infrastructure migration

---

### Lab 4: Enterprise Windows Server Administration (CNIT 242)
**Platform:** Nutanix AHV | TrueNAS Core | Windows Server 2022/2025 | SMB/CIFS

Extended the virtualized infrastructure with enterprise-grade storage and backup solutions. Deployed TrueNAS Core as a VM on the Nutanix cluster, configured IP and DNS settings, joined TrueNAS to the Active Directory domain, and created storage pools and datasets. Configured SMB shares with granular Access Control Lists (ACLs), setting distinct permissions for `BackupSet03` (backup-restricted access) and `GeneralSet03` (general use). Implemented Windows Server Backup on a domain controller VM, wrote PowerShell/batch scripts for automated backup renaming and deletion, and scheduled these scripts via Task Scheduler for hands-off daily execution. Deployed additional domain controllers (G03SRV04, G03SRV05) as VMs, promoted them, configured Active Directory Sites and Services with subnet associations, and set up OpenLDAP GPOs across the domain.

**Key skills:** TrueNAS Core, SMB/CIFS, ACL configuration, Windows Server Backup, PowerShell scripting, Task Scheduler automation, AD Sites and Services, OpenLDAP GPO

---

### Lab 5: Enterprise Windows Server Administration — Part II (CNIT 242)
**Platform:** Windows Server 2025 | Nutanix AHV | Windows Admin Center | WSUS | DFS

Completed the capstone of the CNIT 242 sequence by deploying enterprise patch management, distributed file services, print infrastructure, and remote management capabilities. Installed and configured Windows Server Update Services (WSUS) on a dedicated VM (G03SRV07), created computer groups, and pushed GPOs to client machines to redirect Windows Update traffic to the internal WSUS server. Deployed Distributed File System (DFS) Namespaces and Replication across two servers (G03SRV01VM and G03SRV04), configured folder targets, set share permissions, and established replication groups for high-availability file access. Set up a print server with multiple print queues, configured printer GPOs for automatic deployment, set priority levels, and managed print operator permissions. Enabled PowerShell Remoting (WinRM) across all VMs for remote administration, and installed Windows Admin Center (WAC) on a dedicated management server, enrolling all Windows Server 2025 and Windows 11 machines for centralized monitoring and management.

**Key skills:** WSUS, DFS Namespaces/Replication, print server administration, GPO-based printer deployment, PowerShell Remoting (WinRM), Windows Admin Center (WAC)

---

### Lab 6: Physical Layer and Ethernet Overview (CNIT 344)
**Platform:** Cisco 3750 Series switches (×2) | HP ProCurve/Aruba switch | Fedora Linux | Windows 11 | Wireshark | PuTTY

Designed and configured a physical multi-switch network from scratch using industry-standard equipment. Reset Cisco 3750A and 3750B switches and connected workstations via CAT6 cabling. Configured static IP addresses on Windows 11 and Fedora Linux hosts, confirmed end-to-end connectivity through file sharing, internet access, and printer connection tests. Managed switch configuration via serial console (PuTTY), documenting MAC address tables, VLAN assignments, and running/startup configurations. Performed packet capture with Wireshark to analyze OSI layer protocols and encapsulation during a live file transfer. Configured a SPAN session to mirror uplink traffic to a dedicated monitoring port for passive network visibility. Built and verified TIA-568A and TIA-568B straight-through and crossover Ethernet cables using a modular cable tester. Benchmarked bidirectional throughput under varying NIC speed and duplex configurations (auto, 10 Mbps, 100 Mbps; half/full duplex) by transferring 1 MB and 100 MB files and comparing measured performance to theoretical maximums. Reconfigured MAC addresses to observe Address Resolution Protocol (ARP) and MAC table refresh behavior.

**Key skills:** Cisco IOS (Cisco 3750), SPAN/RSPAN, Wireshark packet analysis, PuTTY serial console, VLAN configuration, TIA-568A/B cabling, NIC speed/duplex benchmarking, OSI model analysis

---

### Lab 7: UNIX/Linux System Administration (CNIT 340)
**Platform:** Rocky Linux 9.8 | Ubuntu 24.04 | Nutanix AHV | CUPS

Provisioned and administered Rocky Linux and Ubuntu virtual machines from scratch on the Nutanix cluster, configuring custom LVM partitions (`/home` 4096 MiB, `/` 45903 MiB, `/boot/efi` 600 MiB EFI, swap 6144 MiB, `/boot` 2000 MiB). Installed Nutanix Guest Tools (NGT) on both distributions. Hardened system security by configuring PAM-based password policies on Rocky Linux and Ubuntu. Set up disk quotas for individual users. Configured network printing via CUPS on both distributions, including printer driver installation and test page validation. Applied system patches using `dnf` (Rocky Linux) and `apt` (Ubuntu). Conducted a comparative analysis of both distributions' similarities and architectural differences, covering package management, init systems, file hierarchy, and security models.

**Key skills:** Rocky Linux 9.8, Ubuntu 24.04, LVM partitioning, PAM password policy, disk quotas, CUPS printing, `dnf`/`apt` patch management, Nutanix Guest Tools, OS comparison analysis

---

## Technical Skills Demonstrated

**Operating Systems:** Windows Server 2022/2025, Windows 11, Rocky Linux 9.8, Ubuntu 24.04, TrueNAS Core  
**Virtualization:** Nutanix AHV, Prism Element, Prism Central, VMware Workstation  
**Directory Services:** Active Directory Domain Services (AD DS), multi-domain forests, OU design, FSMO roles, Group Policy (GPO), OpenLDAP  
**Networking:** Cisco IOS (3750 Series), VLAN, SPAN, static IP, DNS, DHCP, Wireshark, PuTTY, TIA-568 cabling  
**Storage:** TrueNAS Core (SMB/CIFS, ACL, storage pools), DFS Namespaces/Replication, Windows Server Backup, LVM  
**Automation & Scripting:** PowerShell Remoting (WinRM), batch scripting, Task Scheduler  
**Systems Management:** WSUS, Windows Admin Center (WAC), CUPS, disk quotas, PAM  
**Security:** Group Policy hardening, ACL/RBAC design, password policy enforcement, network monitoring (SPAN/Wireshark)

---

## Environment

All CNIT 242 labs were completed in Purdue's CIT lab environment using physical Dell workstations and Nutanix hyperconverged nodes, networked via the CIT-NET infrastructure and accessed through OpenVPN. CNIT 344 labs used physical Cisco and HP switching hardware. CNIT 340 labs ran on the Nutanix virtual lab cluster.
