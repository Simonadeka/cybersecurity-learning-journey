# Day 5 – SOC Analyst Challenge

## Objective
Detect successful logon events (Event ID 4624) on a Windows victim machine.

## Steps & Evidence
### 1️⃣ Lab Environment Setup
![screenshot1-lab-setup.png](screenshot1-lab-setup.png)  
*Figure 1: VirtualBox VMs – Windows victim & Kali attacker.*

### 2️⃣ Enable Windows Remote Desktop Service
![screenshot2-windows-service-enable.png](screenshot2-windows-service-enable.png)  
*Figure 2: Enabled RDP service on Windows.*

### 3️⃣ SSH Access to Attacker Machine
![screenshot3-ssh-login-linux.png](screenshot3-ssh-login-linux.png)  
*Figure 3: SSH login to Kali Linux attacker.*

### 4️⃣ Verify Windows IP & Connectivity
![screenshot4-windows-ip-check.png](screenshot4-windows-ip-check.png)  
*Figure 4: `ipconfig` & ping test to confirm Windows IP.*

### 5️⃣ MD5 Hash of Security Log
![screenshot5-md5-log-hash.png](screenshot5-md5-log-hash.png)  
*Figure 5: MD5 checksum of `Security.evtx` for integrity.*

### 6️⃣ Event Viewer Filter Setup (4624)
![screenshot6-event4624-filter.png](screenshot6-event4624-filter.png)  
*Figure 6: Filtering Security log for Event ID 4624.*

### 7️⃣ Filtered 4624 Event Results
![screenshot7-event4624-results.png](screenshot7-event4624-results.png)  
*Figure 7: Successful logon events (4624) displayed.*

## Commands Used
1. **Windows service** – GUI `services.msc`.
2. **SSH** – `ssh kali@<ip>`.
3. **IP check** – `ipconfig` & `ping`.
4. **MD5 hash** – `Get-FileHash -Path "Security.evtx" -Algorithm MD5`.
5. **Event filter** – Event Viewer GUI filter for ID 4624.

## Proof of Completion
All 7 screenshots + commands demonstrate ability to investigate Windows logon events as a SOC analyst.
