# 🔐 Linux SSH Hardening Audit

Automated SSH security audit script for Linux servers with compliance checks and remediation recommendations.

## 📋 Overview

This Bash script audits critical SSH security configurations on Linux systems to ensure proper hardening against unauthorized access. It checks common security misconfigurations and provides actionable recommendations.

## ✅ Security Checks

- **PermitRootLogin** - Verifies root login is disabled
- **PasswordAuthentication** - Ensures password-based auth is disabled
- **PubkeyAuthentication** - Confirms SSH key authentication is enabled
- **SSH Port** - Displays current SSH port configuration
- **SSH Service Status** - Checks if SSH daemon is running
- **UFW Firewall** - Validates firewall is active and configured

## 🚀 Usage

### Run the Audit

```bash
chmod +x audit_ssh.sh
sudo ./audit_ssh.sh
```

### Sample Output

```
======================================
     🔐 SSH Hardening Audit Report
======================================
[OK]   Root login is disabled (PermitRootLogin no).
[WARN] Password login is NOT clearly disabled.
[INFO] Recommendation: set PasswordAuthentication no
[OK]   Public key login is enabled.
[INFO] SSH is running on port: 22 (default)
[OK]   SSH service is running.
[OK]   UFW firewall is active.
======================================
     ✅ Audit finished successfully
======================================
```

## 🛠️ Remediation

If warnings are found, apply these fixes:

```bash
# Edit SSH config
sudo nano /etc/ssh/sshd_config

# Apply these settings:
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes

# Restart SSH service
sudo systemctl restart sshd

# Enable UFW firewall
sudo ufw enable
sudo ufw allow 22/tcp
```

## 📦 Requirements

- Linux system (Ubuntu/Debian/RHEL/CentOS)
- SSH server installed
- Root/sudo access
- UFW (optional but recommended)

## 🎯 Use Cases

- Pre-deployment security audits
- Compliance verification
- Regular security assessments
- DevSecOps automation

## 📝 License

MIT
