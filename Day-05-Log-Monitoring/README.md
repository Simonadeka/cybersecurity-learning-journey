

# Day 5: Log Monitoring & Detection

**Date:** 2026-04-20  
**Goal:** Detect and analyze authentication logs from Linux SSH and Windows RDP using a lab setup.

### Lab Setup
VirtualBox lab with 3 VMs:
- **Attacker:** Kali Linux
- **Target 1:** Ubuntu Desktop - SSH service
- **Target 2:** Windows 10 - RDP service

![Lab Setup](screenshots/screenshot1-setup-openssh.png)

### Part 1: Linux SSH Log Monitoring

1. **Enable SSH service on Ubuntu**
![SSH Service Status](screenshots/screenshot2-ssh-service-status.png)

2. **View authentication logs**
Monitored `/var/log/auth.log` for login attempts
![Auth Log](screenshots/screenshot3-ssh-authlog.png)

3. **Verify SSH port listening**
![Netstat SSH](screenshots/screenshot4-netstat-ssh.png)

### Part 2: Windows RDP Log Monitoring

1. **Filter Event Viewer for successful logons**
Filtered for Event ID 4624
![Event 4624 Filter](screenshots/screenshot5-event4624-filter.png)

2. **Review successful logon events**
![Event 4624 Results](screenshots/screenshot6-event4624-results.png)

### Key Learnings
- Linux stores SSH logs in `/var/log/auth.log`
- Windows logs RDP logons as Event ID 4624 in Security log
- `netstat -tlnp` confirms SSH is listening on port 22
- Log monitoring is critical for detecting brute force and unauthorized access

### Tools Used
VirtualBox, Ubuntu, Windows 10, Kali Linux, SSH, Event Viewer

### All commands Used

