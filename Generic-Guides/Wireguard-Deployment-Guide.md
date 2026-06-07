# Deploying WireGuard on Ubuntu

## Overview

WireGuard is a modern VPN solution designed to be fast, secure, and easy to configure.

This guide demonstrates how to deploy a basic WireGuard VPN server on Ubuntu.

---

# Install WireGuard

```bash
sudo apt update
sudo apt install wireguard qrencode -y
```

Verify installation:

```bash
wg --version
```

---

# Generate Server Keys

```bash
wg genkey | tee server_private.key | wg pubkey > server_public.key
```

Protect keys:

```bash
chmod 600 server_private.key
```

---

# Enable IP Forwarding

Create configuration:

```bash
sudo nano /etc/sysctl.d/99-wireguard.conf
```

Contents:

```text
net.ipv4.ip_forward=1
```

Apply:

```bash
sudo sysctl --system
```

---

# Create WireGuard Configuration

File:

```bash
sudo nano /etc/wireguard/wg0.conf
```

Example:

```text
[Interface]
Address = 10.8.0.1/24
ListenPort = 51820
PrivateKey = SERVER_PRIVATE_KEY

PostUp = iptables -A FORWARD -i wg0 -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

PostDown = iptables -D FORWARD -i wg0 -j ACCEPT
PostDown = iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
```

---

# Start WireGuard

```bash
sudo systemctl enable wg-quick@wg0
sudo systemctl start wg-quick@wg0
```

Verify:

```bash
sudo wg
```

---

# Create Client Configuration

Example:

```text
[Interface]
PrivateKey = CLIENT_PRIVATE_KEY
Address = 10.8.0.2/32
DNS = 1.1.1.1

[Peer]
PublicKey = SERVER_PUBLIC_KEY
Endpoint = SERVER_IP:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

---

# Generate QR Code

```bash
qrencode -t ansiutf8 < client.conf
```

Scan using the WireGuard mobile application.

---

# Verification

Verify tunnel:

```bash
sudo wg
```

Verify routing:

```bash
ip route
```

Verify firewall:

```bash
sudo ufw status
```

---

# Conclusion

WireGuard provides a lightweight and secure VPN solution suitable for remote administration, remote access, and secure connectivity.
