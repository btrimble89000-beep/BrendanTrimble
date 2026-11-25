# IT Infrastructure & Cybersecurity Lab Portfolio

**Brendan Trimble** | Cybersecurity, B.S. | Purdue University  
CNIT 242 · CNIT 340 · CNIT 344 | Spring–Fall 2026

---

## Overview

This repository documents hands-on enterprise IT infrastructure and cybersecurity labs completed at Purdue's Polytechnic University in the Computer Information Technology (CIT) department. Across ten labs and an individual project, I designed, deployed, and administered multi-server Windows environments, Nutanix hyperconverged infrastructure, Linux systems, physical network architectures, and security monitoring tools — mirroring the toolsets and workflows used in professional IT and cybersecurity operations.

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
| 8 | Linux/UNIX Network Administration | CNIT 340 | Oct 2026 |
| 9 | Wireless Router & Enterprise Router | CNIT 344 | Oct 2026 |
| 10 | Spanning Tree Protocol and Physical Security | CNIT 344 | Nov 2026 |

---

## Individual Projects

| Project | Description |
|---------|-------------|
| [Splunk: Direct Install vs. Home Lab VM](#project-splunk-setup-direct-install-vs-home-lab-vm) | Compared Splunk deployment methods and analyzed security event data |

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

### Lab 8: Linux/UNIX Network Administration (CNIT 340)
**Platform:** Rocky Linux 9.8 | Ubuntu 24.04 | Windows Server | OpenSSH | NFS | Samba | SELinux | X-Windows

Configured and administered cross-platform network file and remote access services across a three-OS environment (Rocky Linux, Ubuntu, and Windows Server). Deployed OpenSSH on Rocky Linux and Ubuntu, enabling remote shell access from both Linux hosts and Windows PowerShell via `ssh` and `scp` for secure file transfer. Configured NFS servers on both Linux distributions: exported `/var/nfs` directories with `no_root_squash` permissions, enforced SELinux boolean (`nfs_export_all_rw`) for read/write access, opened NFS ports in `firewalld` (`nfs`, `rpc-bind`, `mountd`), and mounted exports cross-platform (Rocky to Ubuntu, Ubuntu to Rocky, and both to Windows via `mount -o anon`). Installed and configured NFS server and client features on Windows Server via PowerShell (`Install-WindowsFeature FS-NFS-Service`). Installed Samba on both Linux distributions, created password-authenticated SMB shares (`/var/smb`), set SELinux contexts with `semanage fcontext`, and mounted Samba shares from all three operating systems. Installed a Windows SMB share via `New-SmbShare` and mounted it from Linux clients using `mount -t cifs` with `vers=3.0`. Hardened each system by identifying and disabling non-required services (`avahi-daemon`, `cups`, `cockpit.socket`, `chronyd`) with `systemctl` and removing their firewall rules. Enabled process accounting (`psacct`/`acct`) to log command execution by user. Configured X-Windows (X11/XLib) on Rocky Linux and Ubuntu for graphical session forwarding. Applied system patches on both distributions.

**Key skills:** OpenSSH, SCP, NFS (Linux/Windows), Samba/CIFS, SELinux enforcement, `firewalld`, cross-platform file sharing, service hardening, process accounting (`psacct`), X-Windows (X11), `systemctl`

---

### Lab 9: Wireless Router & Enterprise Router (CNIT 344)
**Platform:** VyOS 1.5 | Cisco ISR 4331 | Cisco 3750A/3750B | HP/Aruba Switch | Wireshark | PuTTY

Deployed and configured a complete enterprise network from physical hardware to routed, segmented VLANs with internet access. Installed VyOS on a mini PC via Rufus-formatted USB, configured a WAN interface (`eth5`, 44.34.12.254/24) with a static default route, and established wireless access point settings including SSID, WPA2 passphrase, and 802.11g channel. Configured DHCP server pools on VyOS for the wireless subnet (`172.16.12.0/24`, range .100–.200) and three VLANs (`121: 10.1.12.0/24`, `122: 10.2.12.0/24`, `123: 10.3.12.0/24`) with correct gateway and DNS options. Enabled NAT masquerading for all internal subnets through the WAN interface and configured SSH remote access on the WAN address. Created VLAN sub-interfaces (VIFs) on VyOS for inter-VLAN routing. Configured access and trunk ports on two Cisco 3750 switches and an HP/Aruba switch via Cisco IOS CLI, assigning each physical port to its respective VLAN and setting trunk links between devices. Enabled SSH on all three switches with RSA key generation and VTY line authentication. Replaced VyOS with a Cisco ISR 4331 as the enterprise router: performed factory reset, configured WAN and hostname, created 802.1Q sub-interfaces for each VLAN (`encapsulation dot1Q`), set DHCP pools, configured NAT overload with access lists, and enabled SSH. Captured and analyzed 802.1Q-tagged traffic in Wireshark on a Linux host, comparing outgoing frames across VLAN-tagged uplink paths to verify correct encapsulation.

**Key skills:** VyOS, Cisco ISR 4331, Cisco IOS CLI, VLAN access/trunk port configuration, 802.1Q trunking, inter-VLAN routing, NAT/masquerading, DHCP, SSH (router/switch), HP/Aruba CLI, Wireshark 802.1Q analysis, PuTTY serial console

---

### Lab 10: Spanning Tree Protocol and Physical Security (CNIT 344)
**Platform:** Cisco ISR 4331 | Cisco ISR 1921 | Cisco 3750E (×2) | HP/Aruba Switch | PuTTY | Wireshark

Designed and implemented a redundant, loop-tolerant enterprise switching network with physical security hardening. The lab scenario involved rebuilding the switching layer for a growing business that had experienced broadcast storms and unauthorized device access due to unmanaged redundant links and open switch ports. Cabled three switches (two Cisco 3750E and one HP/Aruba) in a physical loop using CAT6 uplinks, then configured Multiple Spanning Tree Protocol (MSTP) in a single MST region (`G12`) to manage loop prevention. Assigned VLAN 121 to MST Instance 1 with Cisco g12switch2 as the Root Bridge (via `spanning-tree mst 1 priority 0`), and VLANs 122 and 123 to MST Instance 2 with the HP/Aruba switch (g12switch1) as Root Bridge. The third Cisco switch (g12switch3) remained a non-root bridge for load balancing. Configured both Cisco ISR routers (4331 and 1921) with static WAN addresses, 802.1Q sub-interfaces for all three VLANs, DHCP pools, and NAT overload. Applied physical security hardening to all devices: renamed every switch and router to the `gXXswitchY`/`gXXrouterY` naming convention, added descriptions to every active port and VLAN, changed default passwords, enabled PortFast and BPDU Guard on all end-device ports, and shut down all unused ports. Verified traffic paths using traceroute and MAC address table inspection to confirm correct Root Bridge election and designated/blocked port assignments per VLAN. Conducted a failover test by disabling the HP switch's uplink port, confirming traffic rerouted through the loop to maintain connectivity.

**Key skills:** MSTP (Multiple Spanning Tree Protocol), Root Bridge election, PortFast, BPDU Guard, Cisco IOS (ISR 4331 & 1921), 802.1Q sub-interfaces, NAT overload, DHCP, physical security hardening, unused port shutdown, switch/router naming conventions, failover testing

---

## Individual Projects

### Project: Splunk Setup — Direct Install vs. Home Lab VM

**Tools:** Splunk Enterprise | Kali Linux | VirtualBox/VMware | Windows 10/11

Explored two distinct methods of deploying Splunk Enterprise for security event monitoring and log analysis: a direct installation on a host OS versus a virtualized home lab deployment within a VM. The project evaluated trade-offs between both approaches across performance, isolation, portability, and ease of reconfiguration — simulating the decision-making process a security analyst faces when standing up a SIEM in resource-constrained environments.

**Direct Install approach:** Installed Splunk Enterprise natively on the host operating system, configured the web interface on the default port (`8000`), and began ingesting local system logs and Windows Event Logs. Direct access to host hardware provided faster indexing and simpler initial setup, but changes to the host environment (updates, software conflicts) could disrupt the Splunk instance.

**Home Lab VM approach:** Deployed Splunk inside a virtual machine (Kali Linux or a dedicated Ubuntu Server VM), isolating the SIEM from the host. Configured network adapters to allow log forwarding from other VMs in the lab environment (using Universal Forwarders or syslog). This approach offered snapshot-based rollback, clean separation from the production host, and the ability to simulate a multi-node network for forwarding logs from attack simulation machines to the Splunk indexer.

**Analysis:** The VM-based deployment proved more practical for security research and CTF-style lab work: snapshots allow reverting after destructive testing, the network namespace supports realistic forwarder-to-indexer topologies, and the isolated environment prevents Splunk's resource usage from impacting the host. Direct install was faster for quick event ingestion on a single machine but lacked the flexibility needed for multi-system log correlation.

**Key skills:** Splunk Enterprise, SIEM deployment, log ingestion, Universal Forwarder, Windows Event Log monitoring, VirtualBox/VMware VM configuration, network adapter bridging, snapshot management

---

## Technical Skills Demonstrated

**Operating Systems:** Windows Server 2022/2025, Windows 11, Rocky Linux 9.8, Ubuntu 24.04, Kali Linux, TrueNAS Core, VyOS  
**Virtualization:** Nutanix AHV, Prism Element, Prism Central, VMware Workstation, VirtualBox  
**Directory Services:** Active Directory Domain Services (AD DS), multi-domain forests, OU design, FSMO roles, Group Policy (GPO), OpenLDAP  
**Networking:** Cisco IOS (3750/ISR 4331/ISR 1921), VLAN, 802.1Q trunking, MSTP/STP, inter-VLAN routing, NAT, DHCP, SPAN/RSPAN, SSH, DNS, Wireshark, PuTTY, TIA-568 cabling, HP/Aruba CLI, VyOS  
**Network Services:** NFS, Samba/CIFS, OpenSSH, SCP, X-Windows (X11), CUPS printing  
**Storage:** TrueNAS Core (SMB/CIFS, ACL, storage pools), DFS Namespaces/Replication, Windows Server Backup, LVM  
**Security Monitoring:** Splunk Enterprise, SIEM deployment, log ingestion, Universal Forwarder, Windows Event Log analysis  
**Automation & Scripting:** PowerShell, PowerShell Remoting (WinRM), Bash, batch scripting, Task Scheduler  
**Security:** Group Policy hardening, ACL/RBAC design, PAM password policy, SELinux enforcement, service hardening, PortFast/BPDU Guard, BPDU Guard, unused port shutdown, process accounting, network monitoring (SPAN/Wireshark)  
**Systems Management:** WSUS, Windows Admin Center (WAC), disk quotas, Nutanix Guest Tools, OS patching (`dnf`/`apt`)

---

## Environment

All CNIT 242 labs were completed in Purdue's CIT lab environment using physical Dell workstations and Nutanix hyperconverged nodes, networked via the CIT-NET infrastructure and accessed through OpenVPN. CNIT 344 labs used physical Cisco and HP switching hardware with console access via PuTTY. CNIT 340 labs ran on the Nutanix virtual lab cluster. The Splunk project was completed independently as a home lab setup.
