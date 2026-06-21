# Day 5: Log Monitoring & File Integrity Detection
**30-Day Cybersecurity Challenge | Blue Team Edition**

###  Objective
Today I switched from attacker mindset to defender mindset. Instead of just breaking in, I learned how defenders monitor systems to detect intrusions using logs and file integrity checks.

###  Lab Environment

| Role | OS | IP Address | Credentials |
| --- | --- | --- | --- |
| Attacker | Kali Linux | 192.168.56.100 | kali:kali |

| Target | Ubuntu Server 22.04 | 192.168.56.101 | simon:password |
| Host | Windows 11 | - | Local Admin |

###  Step 1: Real-Time SSH Log Monitoring
Defenders watch `/var/log/auth.log` to catch login attempts.

**On Ubuntu Target:**
```bash
sudo tail -f /var/log/auth.log

On Kali Attacker:
ssh simon@192.168.56.101
Type yes for host key verification, then enter password.Result: Every SSH login attempt appears live in the auth.log terminal.![screenshot1-ssh-authlog.png]
Figure 1: SSH login from Kali + auth.log showing "Accepted password for simon"

Step 2: File Integrity Monitoring with MD5
MD5 hashes detect if files are modified. This is how Wazuh/SIEM tools catch ransomware.On Ubuntu:javascriptbash
# Create baseline file and hash
echo "original" > day5-test.txt
md5sum day5-test.txt

# Simulate attacker tampering
echo "attacker was here" >> day5-test.txt
md5sum day5-test.txt
Result: The MD5 hash changes after file modification, proving tampering.![screenshot2-md5-hashes.png]
Figure 2: MD5 hash changed from [first hash] to [second hash] after file modification

Step 3: Windows Security Event Log
Windows logs every logon as Event ID 4624.Steps:Press Win + R → type eventvwr.msc → EnterNavigate to Windows Logs > SecurityRight-click Security → Filter Current LogEnter Event ID: 4624 → Click OKResult: Shows timestamp, username, logon type, and source IP for every successful login.![screenshot3-event4624.png]
Figure 3: Windows Event Viewer filtered to Event ID 4624 - Successful Logon

All Commands Used
javascriptbash
# Fix apt lock if needed
sudo killall unattended-upgrades 2>/dev/null
sudo rm /var/lib/dpkg/lock-frontend
sudo dpkg --configure -a

# Install + start SSH
sudo apt update && sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl status ssh

# Monitor logs
sudo tail -f /var/log/auth.log

# File integrity test
echo "original" > day5-test.txt
md5sum day5-test.txt
echo "attacker was here" >> day5-test.txt
md5sum day5-test.txt

Key Takeaways
Logs = Evidence: Every action on Linux gets logged. auth.log tracks SSH, syslog tracks system events.Hash = Integrity: MD5/SHA256 hashes prove if files changed. Different hash = file tampered.Windows Audits Everything: Event ID 4624 = successful logon. 4625 = failed logon. SOC analysts filter these daily.Mindset Shift: Attackers focus on exploits. Defenders focus on detection. You can’t respond to what you don’t monitor.🚀 Next Steps
Day 6: Install Wazuh agent on Ubuntu to automate log collection + alerting. No more manual tail -f.Progress: Day 5/30 Complete ✅
Tools Learned: SSH, tail, md5sum, Event Viewer, auth.log
Skills: Log analysis, File integrity monitoring, Blue team basics#30DayCyberChallenge #SOCAnalyst #BlueTeam #SIEM #Linux #Cybersecurity #HomeLabjavascript
#### **Step 3: Upload Screenshots**
1. In the same `Day-05-Log-Monitoring` folder, click **Add file** → **Upload files**
2. Upload your 3 screenshots and name them:
   - `screenshot1-ssh-authlog.png`
   - `screenshot2-md5-hashes.png`
   - `screenshot3-event4624.png`

#### **Step 4: Commit Changes**
1. Scroll down to **Commit changes**
2. Write commit message: `Day 5: Added log monitoring + file integrity lab`
3. Click **Commit changes**

**Done! ** Your Day 5 is now on GitHub.

### **Optional: Sync to Local Git (if you want CLI practice)**
```bash
# Clone your repo (if not cloned already)
git clone https://github.com/yourname/30-Day-Cybersecurity-Challenge.git

# Go to Day 5 folder
cd 30-Day-Cybersecurity-Challenge/Day-05-Log-Monitoring

# Pull latest changes
git pull

# Make changes locally if needed, then:
git add README.md screenshot*.png
git commit -m "Day 5: Added log monitoring + file integrity lab"
git push
