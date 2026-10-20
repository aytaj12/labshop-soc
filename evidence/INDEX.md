# Evidence index

One file per figure of the Week 1 report; the number in the file name is the figure number.
No screenshot of docker-compose.yml is stored here, because that file contains passwords in plain text.

| Figure | File | What it shows |
|---|---|---|
| 1 | `fig01-lab-architecture-as-built-my-own.png` | Lab architecture as built (my own diagram; it matches the addresses in the table below). |
| 2 | `fig02-siem-host-vmware-ubuntu-server-16.png` | siem-host (VMware “Ubuntu server”): 16 GB RAM, 8 processors, 250 GB disk, Network Adapter on VMnet8 (NAT) and Network Adapter 2 on VMnet1 (host-only). |
| 3 | `fig03-ubuntu-web-vmware-ubuntu-server2-2.png` | ubuntu-web (VMware “Ubuntu server2”): 2 GB RAM, 2 processors, 40 GB disk, one network adapter on VMnet1 (host-only). |
| 4 | `fig04-win-client-vmware-windows-10-x64.png` | win-client (VMware “Windows 10 x64”): 4 GB RAM, 2 processors, 60 GB NVMe disk, one network adapter on VMnet1 (host-only). |
| 5 | `fig05-siem-host-ens37-192-168-1.png` | siem-host: ens37 = 192.168.1.10/24 (host-only, static), ens33 = 192.168.121.143 (NAT, DHCP). |
| 6 | `fig06-ubuntu-web-after-the-nat-adapter.png` | ubuntu-web after the NAT adapter was removed: the only interface is ens33 = 192.168.1.20/24 (host-only, static). |
| 7 | `fig07-win-client-one-ethernet-adapter-192.png` | win-client: one Ethernet adapter, 192.168.1.30, gateway 192.168.1.1. |
| 8 | `fig08-siem-host-ping-to-ubuntu-web.png` | siem-host: ping to ubuntu-web (192.168.1.20) and win-client (192.168.1.30), 0% packet loss. |
| 9 | `fig09-ubuntu-web-ping-to-siem-host.png` | ubuntu-web: ping to siem-host (192.168.1.10) and win-client (192.168.1.30), 0% packet loss. |
| 10 | `fig10-win-client-ping-to-siem-host.png` | win-client: ping to siem-host (192.168.1.10) and ubuntu-web (192.168.1.20), 0% packet loss. |
| 11 | `fig11-siem-host-asia-baku-clock-synchronized.png` | siem-host: Asia/Baku, clock synchronized, NTP active. |
| 12 | `fig12-ubuntu-web-asia-baku-clock-synchronized.png` | ubuntu-web: Asia/Baku, clock synchronized, NTP active. |
| 13 | `fig13-win-client-automatic-time-on-time.png` | win-client: automatic time on, time zone (UTC+04:00) Baku. |
| 14 | `fig14-hello-world-output-and-docker-compose.png` | hello-world output and Docker Compose version on siem-host. |
| 15 | `fig15-siem-host-docker-version-the-docker.png` | siem-host: docker --version, the Docker apt source, sysctl vm.max_map_count = 262144 and the permanent setting in /etc/sysctl.d/. |
| 16 | `fig16-siem-host-snapshot-manager-w1-clean.png` | siem-host Snapshot Manager: w1-clean-install, After install docker, Install wazuh, w1-wazuh-up, after changing …, w1-done (created 10/19/2026 8:50 AM). |
| 17 | `fig17-ubuntu-web-snapshot-manager-w1-clean.png` | ubuntu-web Snapshot Manager: w1-clean-install and w1-done (created 10/19/2026 8:51 AM). |
| 18 | `fig18-win-client-snapshot-manager-w1-clean.png` | win-client Snapshot Manager: w1-clean-install and w1-done (created 10/19/2026 8:51 AM). |
| 19 | `fig19-win-client-administrator-powershell-slmgr-xpr.png` | win-client, administrator PowerShell: slmgr /xpr reports “Windows(R), Education edition: Windows is in Notification mode”. |
| 20 | `fig20-cloning-wazuh-docker-at-v4-14.png` | Cloning wazuh-docker at v4.14.7 and entering single-node/. |
| 21 | `fig21-docker-compose-ps-wazuh-dashboard-wazuh.png` | docker compose ps: wazuh.dashboard, wazuh.indexer and wazuh.manager, all 4.14.7 and Up. |
| 22 | `fig22-dashboard-opened-from-my-dell-at.png` | Dashboard opened from my Dell at https://192.168.1.10. Chrome shows "Not secure". No agents are registered yet at this point. |
| 23 | `fig23-shell-inside-the-wazuh-indexer-container.png` | Shell inside the wazuh.indexer container with the variables for securityadmin.sh. |
| 24 | `fig24-securityadmin-sh-connected-clusterstate-green.png` | securityadmin.sh: connected, Clusterstate GREEN, configuration updated, "Done with success". |
| 25 | `fig25-dashboard-login-as-admin-with-the.png` | Dashboard login as admin with the new administrator password (masked). |
| 26 | `fig26-wazuh-overview-after-the-login-with.png` | Wazuh Overview after the login with the new password: Agents summary Active (2), Disconnected (0). |
| 27 | `fig27-docker-compose-stop-dashboard-manager-and.png` | docker compose stop: dashboard, manager and indexer Stopped. |
| 28 | `fig28-while-the-stack-is-stopped-https.png` | While the stack is stopped, https://192.168.1.10 gives ERR_CONNECTION_REFUSED. |
| 29 | `fig29-docker-compose-start-indexer-manager-and.png` | docker compose start: indexer, manager and dashboard Started. |
| 30 | `fig30-after-the-start-the-dashboard-answers.png` | After the start the dashboard answers again with its login page. |
| 31 | `fig31-docker-compose-ps-after-stop-and.png` | docker compose ps after stop and start: all three containers Up (52 seconds). |
| 32 | `fig32-endpoints-after-stop-and-start-active.png` | Endpoints after stop and start: Active (2), ubuntu-web (001) and win-client (002). |
| 33 | `fig33-siem-host-sudo-reboot.png` | siem-host: sudo reboot. |
| 34 | `fig34-after-the-reboot-docker-compose-ps.png` | After the reboot, docker compose ps already shows all three containers Up (About a minute) before docker compose start is run; start changes nothing (Up 3 minutes). |
| 35 | `fig35-endpoints-after-the-reboot-active-2.png` | Endpoints after the reboot: Active (2), ubuntu-web and win-client. |
| 36 | `fig36-threat-hunting-after-the-reboot-rule.png` | Threat Hunting after the reboot, rule.groups: sshd, 16–19 October: the 18 alerts from 16 October are still stored (rules 5760, 5762 and 5763). |
| 37 | `fig37-docker-stats-no-stream-on-siem.png` | docker stats --no-stream on siem-host. |
| 38 | `fig38-agent-package-installed-and-wazuh-agent.png` | Agent package installed and wazuh-agent service active (running) on ubuntu-web. |
| 39 | `fig39-dashboard-agent-list-with-the-first.png` | Dashboard agent list with the first agent: ubuntu-web, active. |
| 40 | `fig40-windows-agent-installed-with-msiexec-the.png` | Windows agent installed with msiexec; the Wazuh service is Running. |
| 41 | `fig41-both-agents-active-2-ubuntu-web.png` | Both agents Active (2): ubuntu-web and win-client, both v4.14.7. |
| 42 | `fig42-win-client-agent-002-overview-active.png` | win-client agent 002 overview: active, 192.168.1.30, Windows 10 Education, 2 cores, 4 GB. Registered 16 Oct 2026, 15:33:39. |
| 43 | `fig43-sysmon-downloaded-and-installed-with-the.png` | Sysmon downloaded and installed with the SwiftOnSecurity configuration; Sysmon64 is Running. |
| 44 | `fig44-ossec-conf-contains-the-sysmon-event.png` | ossec.conf contains the Sysmon event channel (line 218) and the agent was restarted. |
| 45 | `fig45-sysmon-events-in-threat-hunting-query.png` | Sysmon events in Threat Hunting (query data.win.system.providerName: "Microsoft-Windows-Sysmon", agent win-client). |
| 46 | `fig46-nginx-service-enabled-active-running.png` | nginx service: enabled, active (running). |
| 47 | `fig47-default-welcome-to-nginx-page-opened.png` | Default "Welcome to nginx!" page opened from the Dell at http://192.168.1.20. |
| 48 | `fig48-terminal-on-the-dell-several-permission.png` | Terminal on the Dell: several "Permission denied" attempts, then a successful login at the end. |
| 49 | `fig49-alert-details-agent-ubuntu-web-srcip.png` | Alert details: agent ubuntu-web, srcip 192.168.1.1, full_log "Failed password for ubuntu from 192.168.1.1", rule.description "sshd: authentication failed.". |
| 50 | `fig50-rule-fields-rule-id-5760-rule.png` | Rule fields: rule.id 5760, rule.level 5, MITRE T1110.001 and T1021.004. |
| 51 | `fig51-terminal-on-ubuntu-web-failed-sudo.png` | Terminal on ubuntu-web: failed sudo attempts, then sudo whoami returns root. |
| 52 | `fig52-alert-details-data-command-usr-bin.png` | Alert details: data.command /usr/bin/whoami, data.srcuser ubuntu, data.dstuser root, full_log with COMMAND=/usr/bin/whoami. |
| 53 | `fig53-rule-fields-rule-description-successful-sudo.png` | Rule fields: rule.description "Successful sudo to ROOT executed.", rule.id 5402, rule.level 3. |
| 54 | `fig54-alert-details-useradd-created-testuser1-uid.png` | Alert details: useradd created testuser1, UID 1001, home /home/testuser1, shell /bin/bash. |
| 55 | `fig55-rule-fields-rule-description-new-user.png` | Rule fields: rule.description "New user added to the system.", rule.id 5902, rule.level 8, T1136. |
| 56 | `fig56-sysmon-event-data-commandline-net1-user.png` | Sysmon event data: commandLine net1 user, image net1.exe, parentImage net.exe, user Aytaj, integrityLevel High. |
| 57 | `fig57-system-fields-channel-microsoft-windows-sysmo.png` | System fields: channel Microsoft-Windows-Sysmon/Operational, eventID 1, providerName Microsoft-Windows-Sysmon, message "Process Create". |
| 58 | `fig58-rule-fields-discovery-activity-executed-rule.png` | Rule fields: "Discovery activity executed", rule.id 92031, rule.level 3, T1087 Account Discovery. |
| 59 | `fig59-query-data-win-system-eventid-4625.png` | Query data.win.system.eventID: 4625 returns 6 alerts from agent win-client. |
| 60 | `fig60-event-data-logontype-2-status-0xc000006d.png` | Event data: logonType 2, status 0xc000006d, subStatus 0xc000006a, targetUserName Aytaj. |
| 61 | `fig61-rule-fields-rule-description-logon-failure.png` | Rule fields: rule.description "Logon Failure - Unknown user or bad password", rule.id 60122, rule.level 5. |
| 62 | `fig62-git-init-gitignore-created-git-status.png` | git init, .gitignore created, git status and the git ls-files check. |
| 63 | `fig63-labshop-soc-ls-la-the-gitignore.png` | ~/labshop-soc: ls -la, the .gitignore (*.pem, *.key, .env) and the git ls-files check, which returns nothing. |
