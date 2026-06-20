# Cybersecurity Learning Journey: Day 4
## Exploiting vsftpd 2.3.4 Backdoor
I exploited the vsftpd 2.3.4 backdoor on Metasploitable2, gaining full admin access with 4 Metasploit commands.

### Process
1. Nmap scan revealed open port 21
2. Loaded `exploit/unix/ftp/vsftpd_234_backdoor` in Metasploit
3. Set RHOSTS and LHOST
4. Gained `uid=0(root)` access

### Screenshots
![Metasploit Exploit Execution](screenshots/metasploit-exploit.png)
![id Command Output](screenshots/id-root-access.png)

### Key Takeaway
Finding vulnerabilities is step 1. Proving impact is what matters.

### Learning Objectives
- Understand exploitation basics
- Recognize vulnerability impact
- Practice defensive strategies

### Tools Used
- Metasploit Framework
- Nmap
- Metasploitable2

### Tags
#Cybersecurity #EthicalHacking #Metasploit #Pentesting #TSAcademy
