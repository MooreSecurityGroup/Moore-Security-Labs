# Ubuntu Server Hardening Guide

## Overview

This guide provides a basic hardening baseline for Ubuntu Server systems used in home labs, small businesses, and development environments.

---

# Step 1: Update the System

```bash
sudo apt update
sudo apt upgrade -y
sudo reboot
```

---

# Step 2: Create a Dedicated Administrator Account

```bash
sudo adduser adminuser
sudo usermod -aG sudo adminuser
```

Verify:

```bash
groups adminuser
```

---

# Step 3: Configure SSH Keys

Generate a key pair on your workstation:

```bash
ssh-keygen -t ed25519
```

Copy the key:

```bash
ssh-copy-id adminuser@SERVER_IP
```

Test login:

```bash
ssh adminuser@SERVER_IP
```

---

# Step 4: Secure SSH

Edit:

```bash
sudo nano /etc/ssh/sshd_config
```

Recommended settings:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
MaxAuthTries 3
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

---

# Step 5: Configure UFW

Install:

```bash
sudo apt install ufw -y
```

Allow SSH:

```bash
sudo ufw allow 22/tcp
```

Enable:

```bash
sudo ufw enable
```

Verify:

```bash
sudo ufw status verbose
```

---

# Step 6: Install Fail2Ban

Install:

```bash
sudo apt install fail2ban -y
```

Enable:

```bash
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

Verify:

```bash
sudo fail2ban-client status
```

---

# Step 7: Enable Automatic Security Updates

Install:

```bash
sudo apt install unattended-upgrades -y
```

Configure:

```bash
sudo dpkg-reconfigure unattended-upgrades
```

---

# Step 8: Verify Open Ports

```bash
sudo ss -tulpn
```

Review all listening services and disable unnecessary applications.

---

# Step 9: Verify Logs

```bash
sudo journalctl -p warning -b
```

Review warnings and errors.

---

# Conclusion

Following these steps provides a strong baseline for most Ubuntu servers. Additional hardening should be performed based on the specific services hosted on the system.
