# Small Business Security Checklist

## Overview

Cybersecurity does not have to be complicated. Many successful attacks occur because basic security controls are missing or misconfigured.

This checklist provides a practical starting point for improving the security posture of a small business.

---

# User Accounts and Authentication

## Multi-Factor Authentication (MFA)

* [ ] MFA enabled for email accounts
* [ ] MFA enabled for cloud applications
* [ ] MFA enabled for administrative accounts
* [ ] MFA enabled for VPN access

Why it matters:

Multi-factor authentication can prevent unauthorized access even if a password is compromised.

---

## Password Security

* [ ] Password manager deployed
* [ ] Unique password for each account
* [ ] Administrative passwords are unique
* [ ] Shared passwords eliminated
* [ ] Default vendor passwords changed

Recommended password managers:

* Bitwarden
* 1Password
* Keeper

---

# Endpoint Security

## Workstations and Laptops

* [ ] Operating systems updated
* [ ] Antivirus or endpoint protection installed
* [ ] Local administrator access restricted
* [ ] Screen lock enabled
* [ ] Full disk encryption enabled

Examples:

* Windows Defender
* Microsoft Defender for Business
* BitLocker
* FileVault

---

## Mobile Devices

* [ ] Device passcode required
* [ ] Automatic screen lock enabled
* [ ] Device encryption enabled
* [ ] Remote wipe capability enabled
* [ ] Operating system updated

---

# Network Security

## Firewall

* [ ] Business firewall installed
* [ ] Firewall firmware updated
* [ ] Unnecessary inbound ports blocked
* [ ] Administrative access restricted
* [ ] Firewall configuration documented

---

## Wireless Security

* [ ] WPA3 enabled (if supported)
* [ ] Strong Wi-Fi password configured
* [ ] Guest network separated
* [ ] Default wireless credentials changed
* [ ] Unused wireless networks removed

---

## Remote Access

* [ ] VPN implemented
* [ ] Remote Desktop restricted
* [ ] SSH restricted
* [ ] Remote access documented
* [ ] Unused remote access services disabled

Recommended:

```text
Internet
    |
VPN
    |
Internal Resources
```

Avoid exposing services directly to the Internet whenever possible.

---

# Server Security

## Linux Servers

* [ ] Security updates installed
* [ ] Root login disabled
* [ ] SSH key authentication enabled
* [ ] Password authentication disabled
* [ ] Firewall enabled
* [ ] Fail2Ban installed

---

## Windows Servers

* [ ] Security updates installed
* [ ] Administrative accounts reviewed
* [ ] Unused services disabled
* [ ] Backups verified
* [ ] Logging enabled

---

# Backup and Recovery

## Data Protection

* [ ] Daily backups configured
* [ ] Backups encrypted
* [ ] Backup retention documented
* [ ] Recovery procedures documented
* [ ] Test restoration completed

Recommended:

* Local backup
* Offsite backup
* Cloud backup

Follow the 3-2-1 backup rule:

* 3 copies of data
* 2 different storage media
* 1 offsite copy

---

# Email Security

## Email Protection

* [ ] MFA enabled
* [ ] Spam filtering enabled
* [ ] Phishing protection enabled
* [ ] User awareness training completed
* [ ] Administrative accounts reviewed

Email remains one of the most common attack vectors for small businesses.

---

# Employee Security Awareness

## Training

* [ ] Security awareness training completed
* [ ] Phishing awareness training completed
* [ ] Password training completed
* [ ] Incident reporting process documented

Employees should know:

* How to recognize phishing emails
* How to report suspicious activity
* How to protect company information

---

# Vendor and Third-Party Access

## Vendor Management

* [ ] Vendor accounts reviewed
* [ ] Unused accounts removed
* [ ] MFA required
* [ ] Access documented
* [ ] Contracts reviewed annually

---

# Monitoring and Logging

## Visibility

* [ ] Firewall logs reviewed
* [ ] Server logs reviewed
* [ ] Administrative logins reviewed
* [ ] Backup jobs reviewed
* [ ] Alerts configured

You cannot respond to security incidents you cannot see.

---

# Incident Response

## Preparation

* [ ] Incident response plan documented
* [ ] Emergency contacts documented
* [ ] Recovery procedures documented
* [ ] Backup restoration tested

At minimum, the organization should know:

* Who to call
* What systems are affected
* How to restore operations

---

# Documentation

## Inventory Management

* [ ] Device inventory maintained
* [ ] Software inventory maintained
* [ ] Network diagram maintained
* [ ] Administrator accounts documented
* [ ] Security controls documented

Good documentation reduces downtime and improves incident response.

---

# Security Health Score

Count the number of completed items:

| Score | Security Maturity |
| ----- | ----------------- |
| 0-20  | High Risk         |
| 21-40 | Moderate Risk     |
| 41-60 | Good              |
| 61+   | Strong            |

---

# Final Notes

This checklist is intended to provide a baseline assessment for small businesses. Security requirements vary by industry, size, and regulatory obligations.

Organizations should periodically review and update security controls to address evolving threats and business needs.

---

**Version:** 1.0
**Author:** Moore Security Labs
