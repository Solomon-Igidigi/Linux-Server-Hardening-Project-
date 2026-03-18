# Linux-Server-Hardening-Project-
This project focuses on securing a Linux server by implementing industry-standard hardening techniques. Using an Ubuntu Server hosted on VirtualBox, I simulated a real-world environment and applied multiple security measures to reduce vulnerabilities, restrict unauthorized access, and monitor suspicious activities.
# Objectives
- Secure remote access to the server

- Minimize attack surface

- Implement access control and least privilege

- Detect and prevent brute-force attacks

- Validate system security through testing

# Environment Setup

- Platform: VirtualBox

- OS: Ubuntu Server 22.04

- Network Mode: Bridged Adapter

- Access Method: SSH from host machine
  
# Hardening Steps Implemented
1. System Update & Patch Management: Updated all packages to fix known vulnerabilities

sudo apt update && sudo apt upgrade -y

2. User Management & Least Privilege: Created a non-root user with sudo privileges

sudo adduser solomon
sudo usermod -aG sudo solomon

3. SSH Hardening

- Disabled root login

- Changed default SSH port

- Disabled password authentication

sudo nano /etc/ssh/sshd_config

- Key configurations:

PermitRootLogin no
Port 2222
PasswordAuthentication no

4. Firewall Configuration (UFW): Allowed only necessary ports (SSH, HTTP/HTTPS)

Blocked all other incoming traffic

sudo ufw allow 2222/tcp
sudo ufw enable
sudo ufw status

5. Intrusion Prevention (Fail2Ban)

Installed and configured Fail2Ban to prevent brute-force attacks

sudo apt install fail2ban -y
sudo systemctl enable fail2ban

6. Port Scanning: Used nmap to verify only allowed ports were open

sudo apt install nmap -y
nmap 192.168.43.140

# Results

- Reduced exposed ports and services

- Secured SSH access against unauthorized entry

- Successfully simulated and mitigated brute-force attacks

# Key Concepts Learned

- Linux system hardening

- SSH security best practices

- Firewall configuration (UFW)

- Intrusion prevention (Fail2Ban)

- Principle of least privilege
