# System Diagnostics to Markdown

This one-liner shell command gathers key system diagnostics and security audit data, then saves it into a well-formatted Markdown file (`system_report.md`) for easy documentation or sharing—perfect for admins maintaining server records in GitHub repos.

---

## What It Captures

- Hostname  
- Operating System details  
- Current Date & Time  
- Disk usage  
- Memory usage  
- CPU info  
- Kernel message logs (errors/failures)  
- Auth log failures (e.g., SSH failed logins)  
- Open TCP/UDP ports  
- Active `iptables` firewall rules  
