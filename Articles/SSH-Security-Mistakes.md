# 5 SSH Security Mistakes That Put Servers at Risk

## Introduction

Secure Shell (SSH) is one of the most commonly used tools for administering Linux servers.

When configured properly, SSH provides secure remote access. However, poor configuration can expose servers to unnecessary risk.

This article highlights five common SSH security mistakes and provides recommendations for improving security.

---

# Mistake #1: Allowing Root Login

Many Linux distributions permit root logins by default or leave the option enabled.

Example:

```text
PermitRootLogin yes
```

Why this is risky:

* Attackers already know the username
* Root has unrestricted privileges
* Successful compromise results in full system access

Recommended configuration:

```text
PermitRootLogin no
```

Administrators should log in using a standard account and elevate privileges using sudo when necessary.

---

# Mistake #2: Using Password Authentication

Password authentication remains one of the most common attack targets.

Attackers routinely perform:

* Brute force attacks
* Password spraying attacks
* Credential stuffing attacks

Example:

```text
PasswordAuthentication yes
```

Recommended configuration:

```text
PasswordAuthentication no
PubkeyAuthentication yes
```

SSH key authentication is significantly more secure than passwords.

---

# Mistake #3: Exposing SSH to the Entire Internet

Many administrators leave SSH accessible from anywhere.

Example:

```text
0.0.0.0/0
```

This allows anyone on the Internet to attempt a connection.

Better options include:

* Restricting access by IP address
* Using a VPN
* Using a jump host
* Implementing firewall restrictions

Reducing exposure lowers risk.

---

# Mistake #4: Ignoring Updates

Outdated software may contain vulnerabilities that attackers can exploit.

Administrators should regularly update:

* Operating systems
* SSH packages
* Security tools

Example:

```bash
sudo apt update
sudo apt upgrade -y
```

Keeping systems current is one of the most effective security controls available.

---

# Mistake #5: Failing to Monitor Login Activity

Many administrators configure SSH and never review logs.

Important logs include:

```bash
sudo journalctl -u ssh
```

or

```bash
sudo tail -f /var/log/auth.log
```

Reviewing logs helps identify:

* Failed login attempts
* Brute force attacks
* Suspicious activity
* Misconfigurations

---

# Recommended SSH Configuration

A secure baseline configuration may include:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
MaxAuthTries 3
```

Additional protections:

* Fail2Ban
* UFW Firewall
* VPN-based access
* Security monitoring

---

# Example Hardening Process

1. Create a non-root administrator account
2. Configure SSH key authentication
3. Disable password authentication
4. Disable root login
5. Configure firewall rules
6. Install Fail2Ban
7. Verify access before closing the current session

---

# Quick Security Checklist

```text
[ ] Root login disabled
[ ] Password authentication disabled
[ ] SSH keys configured
[ ] Firewall enabled
[ ] Fail2Ban installed
[ ] Updates applied
[ ] Logs reviewed
```

---

# Conclusion

SSH is an essential tool for Linux administration, but its security depends heavily on proper configuration.

Disabling root access, using SSH keys, limiting exposure, applying updates, and monitoring logs can significantly improve a server's security posture.

A few minutes spent hardening SSH can prevent many common attacks and help protect critical systems from unauthorized access.
