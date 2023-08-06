# Linux Privilege Escalation Methodology

1. check history
2. check sudo -l
3. check for SUID binaries - find / -perm -u=s -type f 2>/dev/null
4. check running processes using "pspy"


Notes* = 
1. check permission in the /etc/passwd file , if it has write access for the user
