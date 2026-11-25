# Splunk SIEM Home Lab

Designed and built a self-contained security monitoring lab to gain hands-on
experience with SIEM operations and detection engineering. Using VMware, I
deployed three virtual machines on an isolated network: a Splunk Enterprise
server on Ubuntu, a Windows Server 2025 Active Directory domain controller, and
a Kali Linux attack box. I configured endpoint logging on the Windows host and
forwarded its Windows and Sysmon telemetry into Splunk, then simulated
real-world attacks against the domain and wrote detection searches, alerts, and
a dashboard to catch them. The project covered the full blue-team workflow:
standing up log sources, building a detection pipeline, emulating adversary
behavior, and validating that each attack produced an alert mapped to the MITRE
ATT&CK framework.

## Skills Gained

### SIEM and Detection
- Splunk administration
- SPL (Search Processing Language)
- Detection engineering
- MITRE ATT&CK framework
- Security monitoring and alerting
- Dashboarding and data visualization

### Logging and Telemetry
- Log management and forwarding
- Microsoft Sysmon
- Windows event logging
- Endpoint telemetry configuration

### Systems and Infrastructure
- Active Directory
- Windows Server administration
- Linux (Ubuntu) administration
- VMware virtualization
- Network configuration (NAT, static IP, firewall rules)

### Offensive and Validation
- Adversary emulation (Atomic Red Team)
- Penetration testing tools (Kali Linux, NetExec)
- Attack simulation and detection validation
