# Day 5: Log Monitoring & SSH Analysis

[Day](https://img.shields.io/badge/Day-5/30-blue?style=flat-square) 
[Focus](https://img.shields.io/badge/Focus-Blue%20Team-green?style=flat-square) 
[Skills](https://img.shields.io/badge/Skills-SSH%2C%20Log%20Analysis-orange?style=flat-square)

### 🎯 Objective
Shift from attacker to defender mindset. Monitor SSH & Windows logs to detect authentication activity.

### Lab Environment

| Role | OS | IP | Purpose |
| --- | --- | --- | --- |
| Target | Ubuntu 22.04 | 192.168.x | SSH server & log source |
| Attacker | Kali Linux | 192.168.x | SSH client |
| Host | Windows 11 | – | Event Viewer analysis |

### Steps & Commands with Screenshots
#### 1. Enable SSH Service on Ubuntu
**Commands:**
```bash
sudo systemctl start ssh
sudo systemctl status ssh

Result:
!screenshots/screenshot1-ssh-service.png
Fig 1: SSH service active (running) on port 222. Monitor Linux Authentication Log (auth.log)
Commands:javascriptbash
sudo tail -f /var/log/auth.log

Result:
!screenshots/screenshot2-tail-authlog.png
Fig 2: Real‑time auth.log showing login attempts3. SSH Login from Kali to Ubuntu
Commands:javascriptbash
ssh simon@192.168.x

Result:
!screenshots/screenshot3-ssh-login.png
Fig 3: Successful SSH login from Kali to Ubuntu4. Verify SSH Listening Port with netstat
Commands:javascriptbash
sudo netstat -tlnp | grep ssh

Result:
!screenshots/screenshot4-netstat-ssh.png
Fig 4: netstat confirms SSH listening on 0.0.0.0:225. Windows Event Viewer – Filter Event ID 4624
Commands (GUI):Open eventvwr.msc → Windows Logs → Security.Filter Current Log → Event ID 4624.Result:
!screenshots/screenshot5-event4624-filter.png
Fig 5: Event Viewer filter applied for ID 4624 (successful logon)6. View Windows Logon Events (Event 4624 Results)

Result:
!screenshots/screenshot6-event4624-results.png
Fig 6: List of successful logon events (Event ID 4624)

Key Takeaways
SSH logs in /var/log/auth.log are the first line of defense for Linux remote access.Event ID 4624 in Windows logs every successful logon – essential for SOC monitoring.netstat confirms service exposure (port 22).Pairing commands with screenshots proves lab execution.

Next Steps
Day 6: File integrity checks with md5sum + Wazuh agent setup for automated log collection.Progress:

Day 5/30 ✅
Tools: SSH, systemctl, tail, netstat, Event Viewer
Skills: Log analysis, service management, blue‑team monitoring

#30DayCyberChallenge #SOCAnalyst #BlueTeam #Linux #Windows #Cybersecurity
