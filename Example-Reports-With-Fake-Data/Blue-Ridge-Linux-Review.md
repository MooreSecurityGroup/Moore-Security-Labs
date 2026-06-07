# Linux Server Security Review

## Client Information

**Client Name:** Blue Ridge Manufacturing

**Assessment Date:** 15 May 2026

**Assessor:** Moore Security Labs

**Report Version:** 1.0

---

# Executive Summary

A security review was conducted on a Linux server supporting internal business operations for Blue Ridge Manufacturing.

The objective of the review was to identify security weaknesses, evaluate current configurations, and provide recommendations for improving the overall security posture of the system.

The assessment identified:

| Severity | Findings |
| -------- | -------- |
| Critical | 0        |
| High     | 2        |
| Medium   | 1        |
| Low      | 1        |

Immediate remediation is recommended for the High severity findings.

---

# Scope

The assessment included:

* SSH configuration review
* Firewall review
* User account review
* Service review
* System update review
* Logging review

The review did not include exploitation activities or penetration testing.

---

# System Information

| Item             | Value                       |
| ---------------- | --------------------------- |
| Operating System | Ubuntu Server 24.04         |
| Function         | File and Application Server |
| Environment      | Internal Network            |
| Assessment Type  | Configuration Review        |

---

# Risk Rating Definitions

| Severity | Description                            |
| -------- | -------------------------------------- |
| Critical | Immediate compromise likely            |
| High     | Significant security exposure          |
| Medium   | Security weakness requiring correction |
| Low      | Best-practice improvement              |

---

# Finding BR-001

## SSH Password Authentication Enabled

### Severity

High

### Description

The server permits password-based SSH authentication.

Configuration observed:

```text
PasswordAuthentication yes
```

### Risk

Password authentication is susceptible to:

* Brute-force attacks
* Password spraying
* Credential reuse attacks

### Recommendation

Disable password authentication and require SSH keys.

Recommended configuration:

```text
PasswordAuthentication no
PubkeyAuthentication yes
```

### Priority

High

---

# Finding BR-002

## Firewall Disabled

### Severity

High

### Description

The host-based firewall was not enabled at the time of assessment.

### Risk

Unnecessary services may be exposed to unauthorized users.

### Recommendation

Enable UFW and explicitly allow only required services.

Example:

```bash
sudo ufw allow 22/tcp
sudo ufw enable
```

### Priority

High

---

# Finding BR-003

## Fail2Ban Not Installed

### Severity

Medium

### Description

No automated protection was identified for repeated authentication failures.

### Risk

Attackers may perform unlimited login attempts.

### Recommendation

Install and configure Fail2Ban.

Example:

```bash
sudo apt install fail2ban -y
```

### Priority

Medium

---

# Finding BR-004

## Unused Services Running

### Severity

Low

### Description

Several services were running without documented business justification.

Examples included:

* Legacy file sharing services
* Test applications
* Development tools

### Risk

Additional services increase the attack surface.

### Recommendation

Review all active services and remove unnecessary software.

Example review command:

```bash
sudo ss -tulpn
```

### Priority

Low

---

# Remediation Plan

## Immediate (0-30 Days)

* Disable SSH password authentication
* Enable host firewall

## Short Term (30-60 Days)

* Deploy Fail2Ban
* Review administrative accounts
* Validate backup procedures

## Long Term (60-90 Days)

* Remove unnecessary services
* Establish quarterly configuration reviews
* Develop server hardening standards

---

# Overall Security Posture

Current security posture is assessed as:

```text
Moderate Risk
```

The identified findings are common and can be remediated relatively quickly through standard hardening practices.

---

# Conclusion

The server demonstrates a reasonable baseline configuration but would benefit from additional hardening controls.

Implementing the recommendations contained in this report will significantly reduce exposure to common attacks and improve the system's overall security posture.

---

# Disclaimer

This report contains fictional data and was created for educational and portfolio purposes only. No actual organization was assessed.
