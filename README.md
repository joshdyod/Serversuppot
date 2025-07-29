System Diagnostics to Markdown

This one-liner shell command gathers key system diagnostics and security audit data, then saves it into a well-formatted Markdown file (system_report.md) for easy documentation or sharing—perfect for admins maintaining server records in GitHub repos.

   What It Captures
	•	Hostname
	•	Operating System details
	•	Current Date & Time
	•	Disk usage
	•	Memory usage
	•	CPU info
	•	Kernel message logs (errors/failures)
	•	Auth log failures (e.g., SSH failed logins)
	•	Open TCP/UDP ports
	•	Active iptables firewall rules


Run this single-line command from the terminal on any Linux server:

{ echo "## Hostname for the Server" ; hostname ; echo -e "\n## OS for the Server" ; cat /etc/os-release ; echo -e "\n## Date and Time" ; date ; echo -e "\n## Disk Usage" ; df -h ; echo -e "\n## Memory Usage" ; free -h ; echo -e "\n## CPU Info" ; cat /proc/cpuinfo ; echo -e "\n## Message Logs (Errors and Failures)" ; dmesg | grep -Ei "error|failed" ; echo -e "\n## Secure Logs (Last Failed Login Attempts)" ; grep Failed /var/log/auth.log | tail ; echo -e "\n## Open Common Ports" ; netstat -tulpnv ; echo -e "\n## IPTables Rules" ; iptables -L ; echo -e "\n## SYN Packets (Possible Scans)" ; sudo /usr/sbin/tcpdump -Nnn -i any -s0 'tcp[13] & 2 != 0' ; } > system_report.md

Note: You may need sudo privileges for tcpdump, and ensure auth.log exists (varies by distro).
