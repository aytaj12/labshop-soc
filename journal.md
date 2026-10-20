# Journal - Week 1

## 16 Oct 2026 - Three VMs and the host-only network

- **Tried:** created siem-host, ubuntu-web and win-client in VMware on the host-only network VMnet1 (192.168.1.0/24) with static addresses. siem-host also got a NAT adapter for Docker images, and ubuntu-web a temporary one for software installs. Set all machines to the Asia/Baku time zone.
- **What failed:** win-client shows its last successful time synchronisation on 06/10/2026. It is host-only now and cannot reach time.windows.com.
- **What fixed it:** nothing was needed: the displayed time still matches the Linux machines (report figures 11 to 13).

## 16 Oct 2026 - Docker Engine and the indexer kernel setting

- **Tried:** installed Docker Engine and the Compose plugin from Docker's official apt repository on siem-host; ran hello-world.
- **Why it matters:** the Wazuh indexer needs `vm.max_map_count` of at least 262144. It is stored in `/etc/sysctl.d/`, so it survives a reboot (figure 15).
- **Lesson:** the indexer is the fussy container. It needs the host kernel setting and enough memory (1.5 GiB idle).

## 16 Oct 2026 - Wazuh 4.14.7 single-node in Docker

- **Tried:** read the Wazuh Docker deployment page, cloned wazuh-docker at tag v4.14.7 into `~/wazuh-docker` (outside my Git repository `~/labshop-soc`), and started the single-node stack.
- **Result:** all three containers Up; dashboard opens over HTTPS from the Dell with the "Not secure" warning (self-made lab CA). Idle memory measured with docker stats: about 2.44 GiB in total.

## 16 Oct 2026 - Changing the default administrator password

- **Tried:** followed the documented procedure for the Docker deployment: (1) logged out of the dashboard and ran `docker compose down` in `~/wazuh-docker/single-node` (no `-v`, so the volumes stay); (2) created the hash of the new password with `docker run --rm -ti wazuh/wazuh-indexer:4.14.7 bash .../tools/hash.sh` (the documentation names 4.14.9, I used my own 4.14.7 so no new image is downloaded); (3) wrote the hash into the `hash:` line of the `admin` block in `config/wazuh_indexer/internal_users.yml`, leaving `kibanaserver` alone; (4) replaced every `INDEXER_PASSWORD` in `docker-compose.yml` (manager and dashboard), writing a `$` twice; (5) `docker compose up -d` and `docker ps`; (6) opened a shell in the indexer container (`docker exec -it single-node-wazuh.indexer-1 bash`), set the variables for `securityadmin.sh` (config directory, root CA, admin certificate and key, Java home), waited 1-5 minutes and ran `securityadmin.sh -cd $CONFIG_DIR/opensearch-security/ -nhnv ... -p 9200 -icl`. It ended with Clusterstate GREEN and "Done with success" (figures 23 and 24).
- **What I noticed:** after the change, `docker-compose.yml` holds the passwords in plain text.
- **What fixed it:** that file stays in `~/wazuh-docker`, outside Git, and I do not put screenshots of it into `evidence/`. Login with the new password works (figures 25 and 26); the password is not written anywhere in this repository.

## 16 Oct 2026 - Agents and Sysmon

- **Tried:** installed the Linux agent 4.14.7 on ubuntu-web (agent 001) and the Windows agent through the MSI with `WAZUH_MANAGER='192.168.1.10'` and `WAZUH_AGENT_NAME='win-client'` (agent 002). Installed Sysmon 15.22 with the SwiftOnSecurity configuration.
- **What failed:** installing Sysmon alone does not send its events to Wazuh.
- **What fixed it:** I added the Sysmon event channel `Microsoft-Windows-Sysmon/Operational` to the agent's `ossec.conf` (line 218) and restarted the agent service. Sysmon events then appeared in Threat Hunting for win-client.

## 16 Oct 2026 - Five deliberate events

- **Tried:** failed SSH login (rule 5760, level 5), `sudo whoami` (5402, level 3), `adduser testuser1` (5902, level 8), `net user` on win-client seen by Sysmon (92031, level 3) and a failed Windows logon (60122, level 5). I found all five in the dashboard.
- **Lesson:** different log sources give different rule families: 5xxx for Linux system logs, 60xxx for the Windows Security log, 92xxx for Sysmon detections.

## 19 Oct 2026 - Isolation, network checks and the persistence test

- **What failed:** ubuntu-web still had its NAT adapter after the software installation, so S2 (no VM other than siem-host has a route to the internet) was not met.
- **What fixed it:** I removed the NAT adapter in VMware. `ip a` on ubuntu-web now shows only ens33 = 192.168.1.20 (figures 3 and 6). win-client has one adapter on VMnet1 (figure 4).
- **Tried:** ping between all three VMs, 0% loss (figures 8 to 10).
- **Persistence test:** `docker compose stop` made the dashboard refuse connections; `docker compose start` brought it back with both agents Active. After `sudo reboot` the three containers were already Up without any command, both agents were Active and the 18 sshd alerts of 16 October were still there (figures 27 to 36).
- **Lesson:** stop and start keep the data; only `docker compose down -v` deletes the volumes.

## 19 Oct 2026 - Windows licence check

- **Tried:** `slmgr /xpr` on win-client. **Result:** "Windows is in Notification mode", so there is no expiry date to note (figure 19).

## 19 Oct 2026 - Snapshots and repository

- **Done:** took `w1-done` on all three VMs after the persistence test (siem-host 08:50, ubuntu-web 08:51, win-client 08:51; figures 16 to 18). Wrote README.md, this journal and the evidence index. `.gitignore` blocks `*.pem`, `*.key` and `.env`, and `git ls-files | grep -E "pem|key|env"` returns nothing.
