**Phase 6**

*DHCP*

<img width="1365" height="767" alt="Screenshot 2026-09-26 233847" src="https://github.com/user-attachments/assets/2e5ec6a7-b66a-4c1d-a8fc-cbb195a04054" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 233901" src="https://github.com/user-attachments/assets/9b42226b-17d7-4532-9890-559983b89a62" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 231158" src="https://github.com/user-attachments/assets/2d37ed82-aa26-48a4-b6f0-113f8bc85c38" />
<img width="1365" height="755" alt="Screenshot 2026-09-26 231205" src="https://github.com/user-attachments/assets/eb3f49f9-0029-4a3b-8051-2771edeb8e0b" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 231238" src="https://github.com/user-attachments/assets/8a6d61e2-29a2-48f3-a67e-004f19a64e09" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 231325" src="https://github.com/user-attachments/assets/cecca00f-e5be-4725-9b82-1ad95511e6f8" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 233435" src="https://github.com/user-attachments/assets/3a9e535b-8d53-49d3-a7b5-104d891eeb94" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 233727" src="https://github.com/user-attachments/assets/9afa0e05-b986-4129-833b-8f2a60970489" />
<img width="1365" height="767" alt="Screenshot 2026-09-26 233738" src="https://github.com/user-attachments/assets/4978d930-74bb-4efb-938c-e9750f8a397b" />


Phase 6 Report: DHCP Implementation & Cloud Architecture Analysis
1. Configuration Summary:

Role: Active Directory-authorized Windows DHCP Server.

Scope: 10.0.0.50 to 10.0.0.100 (/24 mask).

DHCP Options Configured:

Router / Default Gateway: 10.0.0.1 (Azure Virtual Network default gateway).

DNS Server (Option 006): Pointed to Domain Controller (10.0.0.4).

Domain Name (Option 015): contoso.local.

Reservation: Static reservation assigned to VM #2 (10.0.0.55) mapped to virtual NIC MAC address 00-0D-3A-XX-XX-XX.

2. Architectural Analysis: Azure Platform DHCP vs. Guest OS DHCP

The Conflict: In an Azure Virtual Network (VNet), the underlying Software-Defined Networking (SDN) fabric provides a built-in, unmanaged DHCP service running on internal platform IPs (such as 168.63.129.16). When a guest VM broadcasts a DHCPDISCOVER request on its NIC, the Azure SDN hypervisor layer intercepts and responds directly with the IP address statically or dynamically configured in the Azure portal for that network interface (NIC).

Why the Windows Scope is Bypassed: Because Azure SDN operates at Layer 3/Layer 4 interception rather than traditional Layer 2 broadcast domains, guest-level DHCP servers cannot broadcast leases across the VNet to peer VMs without specialized overlay configurations (e.g., VXLAN overlays or disabling platform DHCP).

Real-World Deployment Context:

In a physical or on-premises enterprise environment, this DHCP scope and reservation would control IP distribution and enforce DC-centric DNS via standard Layer 2 broadcast or DHCP Relay (IP Helper) on core switches.

In enterprise cloud architectures, native IaaS VMs rely on Azure VNet IP configurations (configured via Azure Portal, Terraform, or ARM/Bicep) and custom VNet DNS settings rather than running a guest-level DHCP role, avoiding split-brain IP allocation and routing collisions.


