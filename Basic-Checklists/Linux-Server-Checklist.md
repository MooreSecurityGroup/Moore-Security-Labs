# New Linux Server Deployment Checklist

## System Preparation

* [ ] Install operating system
* [ ] Verify system boots correctly
* [ ] Configure hostname
* [ ] Configure timezone
* [ ] Configure NTP time synchronization
* [ ] Apply all updates

```bash
sudo apt update
sudo apt upgrade -y
```

---

## User Management

* [ ] Create dedicated administrator account
* [ ] Add administrator account to sudo group
* [ ] Verify sudo access
* [ ] Disable direct root SSH access

```bash
sudo adduser adminuser
sudo usermod -aG sudo adminuser
```

---

## SSH Security

* [ ] Change SSH port (optional)
* [ ] Disable root login
* [ ] Disable password authentication
* [ ] Configure SSH key authentication
* [ ] Test SSH access before closing session

Example configuration:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

---

## Firewall

* [ ] Install UFW
* [ ] Allow SSH
* [ ] Deny unnecessary inbound traffic
* [ ] Enable firewall

```bash
sudo apt install ufw -y
sudo ufw allow 22/tcp
sudo ufw enable
```

---

## Protection Services

* [ ] Install Fail2Ban
* [ ] Verify jail configuration
* [ ] Enable automatic security updates

```bash
sudo apt install fail2ban unattended-upgrades -y
```

---

## Monitoring and Logging

* [ ] Verify system logs
* [ ] Configure disk monitoring
* [ ] Configure uptime monitoring
* [ ] Configure backup monitoring

---

## Backup Strategy

* [ ] Create backup schedule
* [ ] Verify backup retention
* [ ] Test backup restoration
* [ ] Document recovery procedures

---

## Documentation

* [ ] Record IP addresses
* [ ] Record installed services
* [ ] Record firewall rules
* [ ] Record administrator accounts
* [ ] Record backup procedures

---

## Final Validation

* [ ] Reboot server
* [ ] Verify services start correctly
* [ ] Verify firewall rules persist
* [ ] Verify SSH access
* [ ] Verify monitoring and backups

Deployment Complete.
