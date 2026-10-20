# Address table

Host-only lab network: VMware VMnet1, 192.168.1.0/24, static addresses. The Dell host is 192.168.1.1.

| Machine | Role | OS | Host-only IP | NAT adapter | RAM | vCPU | Disk |
|---|---|---|---|---|---|---|---|
| siem-host | Runs Wazuh 4.14.7 in Docker | Ubuntu Server | 192.168.1.10 | ens33, VMnet8 (DHCP), kept for Docker image pulls | 16 GB | 8 | 250 GB |
| ubuntu-web | Linux endpoint and web server (nginx) | Ubuntu Server 26.04 LTS | 192.168.1.20 | none (removed after the software installation) | 2 GB | 2 | 40 GB |
| win-client | Windows endpoint (staff PC) with Sysmon | Windows 10 Education 10.0.19045.6456 | 192.168.1.30 | none | 4 GB | 2 | 60 GB (NVMe) |
| Dell host | Hypervisor (VMware) and browser | Windows | 192.168.1.1 (VMnet1) | n/a | | | |

The diagram is `lab-diagram.png` (report figure 1). Evidence: report figures 2 to 4 (VMware settings), 6 (ubuntu-web `ip a`), 8 to 10 (ping tests).
