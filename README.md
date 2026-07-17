# 🛡️ NawaHard

**Linux VPS Security Audit & Hardening Recommendation Tool**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-green.svg)]()
[![Shell](https://img.shields.io/badge/Shell-Bash-orange.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)]()

> Pure rule-based VPS security audit — **NO AI, NO external API calls, NO dependencies.**
> Single bash script that generates comprehensive security reports.

---

## 📋 Overview

NawaHard is a comprehensive Linux VPS security audit tool that performs **167+ security checks** across **15 categories** and generates detailed reports with remediation guidance.

**Key Features:**
- ✅ Pure bash — no dependencies required
- ✅ Rule-based — no AI, no external API calls
- ✅ Multi-format output — HTML dashboard, JSON, TXT
- ✅ CIS Benchmark aligned
- ✅ Multi-distro support
- ✅ Remediation guidance for every finding
- ✅ Security scoring (0-100)
- ✅ Offline capable

---

## 🖥️ Supported Operating Systems

| OS | Version | Status |
|----|---------|--------|
| **Ubuntu** | 18.04, 20.04, 22.04, 24.04 | ✅ Full support |
| **Debian** | 10 (Buster), 11 (Bullseye), 12 (Bookworm) | ✅ Full support |
| **CentOS** | 7, 8, 9 | ✅ Full support |
| **RHEL** | 7, 8, 9 | ✅ Full support |
| **Rocky Linux** | 8, 9 | ✅ Full support |
| **AlmaLinux** | 8, 9 | ✅ Full support |
| **Fedora** | 35+ | ✅ Full support |
| **Amazon Linux** | 2, 2023 | ✅ Full support |
| **Arch Linux** | Rolling | ⚠️ Basic support |

---

## 🚀 Quick Start

### Installation

```bash
# Download
wget https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh

# Make executable
chmod +x nawahard.sh

# Run
sudo ./nawahard.sh
```

### One-liner

```bash
curl -sL https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh | sudo bash
```

---

## 📊 Usage

```bash
# Default: Console + HTML dashboard
sudo ./nawahard.sh

# All formats (HTML + JSON + TXT)
sudo ./nawahard.sh --all

# JSON only (for automation)
sudo ./nawahard.sh --json

# TXT only (for archival)
sudo ./nawahard.sh --txt

# Custom output directory
sudo ./nawahard.sh --all --output /path/to/reports

# Quiet mode (minimal console)
sudo ./nawahard.sh --all --quiet

# Disable colors
sudo ./nawahard.sh --no-color

# Send notification to webhook
sudo ./nawahard.sh --notify
```

---

## 🔍 Audit Categories (167 Checks)

### 1. System Foundation (15 checks)
- OS version & EOL status
- Kernel version
- Boot loader password
- Package integrity
- ASLR configuration
- Core dump settings
- System clock sync
- Hostname, CPU, Memory, Disk info

### 2. SSH Configuration (12 checks)
- Root login status
- Password authentication
- SSH port configuration
- Empty password policy
- X11 forwarding
- Max authentication tries
- Login grace time
- Client alive interval
- Access restrictions (AllowUsers/AllowGroups)
- Host key permissions
- Max sessions
- Login banner

### 3. Firewall & Network (9 checks)
- Firewall detection (UFW/Firewalld/nftables)
- IP forwarding
- ICMP redirects
- Source routing
- SYN cookies
- Reverse path filtering
- Broadcast ICMP
- IPv6 redirects

### 4. Intrusion Prevention (2 checks)
- Fail2ban status & jails
- CrowdSec status

### 5. Authentication & Access (8 checks)
- Failed login attempts (24h)
- Sudo logging
- Password policy (minlen)
- Account lockout
- UID 0 accounts
- Empty password accounts
- SUID files

### 6. Kernel Hardening (20 checks)
- Reverse path filter
- ICMP redirects
- Source routing
- Log martians
- SYN cookies
- ASLR (randomize_va_space)
- Kernel pointer restriction
- dmesg restriction
- ptrace scope
- Protected hardlinks/symlinks
- SUID core dump
- Magic SysRq
- TCP timestamps

### 7. Service Management (5 checks)
- Running service count
- Dangerous services (telnet, rsh, tftp, etc.)
- Docker status

### 8. Open Ports (6 checks)
- Total listening ports
- Dangerous ports (21, 23, 25, 110, 135, 139, 445, 1433, 1521, 3306, 3389, 5432, 5900, 6379, 27017)

### 9. Resource Usage (5 checks)
- Disk usage
- Memory usage
- CPU usage
- Swap configuration
- Inode usage

### 10. System Updates (3 checks)
- Reboot requirement
- Pending updates
- Automatic updates (unattended-upgrades)

### 11. File Permissions (4 checks)
- World-writable files in /etc
- /etc/shadow permissions
- /etc/passwd permissions
- SUID files in /tmp

### 12. Container Security (2 checks)
- Docker socket permissions
- Containers running as root

### 13. Cloud Metadata (3 checks)
- Cloud provider detection (AWS/GCP/Azure)
- IMDSv2 status (AWS)
- Metadata access

### 14. Logging & Auditing (4 checks)
- Syslog daemon
- Audit daemon (auditd)
- Journal persistence
- Log rotation

### 15. Miscellaneous (3 checks)
- USB storage module
- File integrity monitoring (AIDE/Tripwire)
- Login banner

---

## 📄 Output Formats

### HTML Dashboard (Default)
Visual, interactive report with:
- Security score visualization
- Color-coded findings
- Remediation guidance
- Responsive design

### JSON Report
Machine-readable format for:
- CI/CD integration
- Automation scripts
- API consumption
- Trend analysis

### TXT Report
Plain text for:
- Terminal viewing
- Log archival
- Email reports
- Documentation

---

## 🎯 Scoring System

| Score | Rating | Description |
|-------|--------|-------------|
| 90-100 | 🟢 Excellent | Minimal security issues |
| 80-89 | 🟡 Good | Few issues, mostly warnings |
| 70-79 | 🟠 Fair | Several issues need attention |
| 60-69 | 🔴 Poor | Significant security gaps |
| 0-59 | 🔴 Critical | Immediate action required |

**Formula:**
```
Score = (Pass × 100 + Info × 50) / Total Checks
```

---

## ⚙️ Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `NAWAHARD_REPORT_DIR` | Custom report directory | `/tmp/nawahard` |
| `NAWAHARD_WEBHOOK` | Webhook URL for notifications | - |
| `NO_COLOR` | Disable colored output | `0` |

---

## 📁 Project Structure

```
NawaHard/
├── nawahard.sh      # Main audit script
├── README.md        # This file
├── LICENSE          # MIT License
└── CHANGELOG.md     # Version history
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Saeful Bahri**
- GitHub: [@kangaman](https://github.com/kangaman)
- Role: CSIRT Lead, Diskominfo Subang

---

## 🙏 Acknowledgments

- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) — Security best practices
- [NIST SP800-123](https://csrc.nist.gov/publications/detail/sp/800-123/final) — Server security guidelines
- [STIG](https://public.cyber.mil/stigs/) — Security Technical Implementation Guides

---

## 📊 Roadmap

- [ ] v1.1.0 — Add compliance scoring (CIS, PCI DSS, UU PDP)
- [ ] v1.2.0 — Add fix mode (auto-remediation with confirmation)
- [ ] v1.3.0 — Add diff mode (compare before/after)
- [ ] v2.0.0 — NawaHard for Windows Server
- [ ] v3.0.0 — NawaHard for macOS
- [ ] v4.0.0 — NawaHard Web Dashboard

---

## 🔗 Related Projects

| Project | Description | Status |
|---------|-------------|--------|
| **NawaHard** | Linux VPS Audit | ✅ Current |
| NawaHard-Win | Windows Server Audit | 🔜 Planned |
| NawaHard-Mac | macOS Audit | 🔜 Planned |
| NawaHard-Web | Web Dashboard | 🔜 Planned |

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/kangaman">Saeful Bahri</a>
</p>
