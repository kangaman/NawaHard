# 🛡️ NawaHard

**Linux VPS Security Audit & Hardening Recommendation Tool**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-2.0.0-green.svg)]()
[![Shell](https://img.shields.io/badge/Shell-Bash-orange.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)]()
[![Checks](https://img.shields.io/badge/Checks-158-blue.svg)]()
[![Categories](https://img.shields.io/badge/Categories-15-purple.svg)]()

> Pure rule-based VPS security audit — **NO AI, NO external API calls, NO dependencies.**
> Single bash script that generates comprehensive security reports with explanations.

---

## 📋 Overview

NawaHard is a comprehensive Linux VPS security audit tool that performs **158 security checks** across **15 categories** and generates detailed reports with:

- 📝 **Explanations** — Penjelasan kenapa setiap temuan penting
- 🔧 **Remediation** — Panduan langkah demi langkah untuk memperbaiki
- 📊 **Security Score** — Skor keamanan 0-100
- 📄 **Multi-format Output** — HTML dashboard, JSON, TXT

**100% rule-based. Tidak ada AI. Tidak ada API calls. Tidak ada dependencies.**

---

## 🖥️ Supported Operating Systems

| OS | Version | Status |
|----|---------|--------|
| **Ubuntu** | 18.04, 20.04, 22.04, 24.04 | ✅ Full support |
| **Debian** | 10 (Buster), 11 (Bullseye), 12 (Bookworm) | ✅ Full support |
| **Kali Linux** | 2023+ | ✅ Full support |
| **Linux Mint** | 20+ | ✅ Full support |
| **Pop!_OS** | 20.04+ | ✅ Full support |
| **CentOS** | 7, 8, 9 | ✅ Full support |
| **RHEL** | 7, 8, 9 | ✅ Full support |
| **Rocky Linux** | 8, 9 | ✅ Full support |
| **AlmaLinux** | 8, 9 | ✅ Full support |
| **Fedora** | 35+ | ✅ Full support |
| **Amazon Linux** | 2, 2023 | ✅ Full support |
| **Oracle Linux** | 7, 8, 9 | ✅ Full support |
| **Arch Linux** | Rolling | ⚠️ Basic support |
| **Manjaro** | Rolling | ⚠️ Basic support |

---

## 🚀 Quick Start

### One-liner (Recommended)

```bash
curl -sL https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh | sudo bash
```

### Manual Installation

```bash
# Download
wget https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh

# Make executable
chmod +x nawahard.sh

# Run
sudo ./nawahard.sh
```

### Git Clone

```bash
git clone https://github.com/kangaman/NawaHard.git
cd NawaHard
sudo ./nawahard.sh
```

---

## 📊 Usage

```bash
# Default: Console + HTML dashboard
sudo ./nawahard.sh

# All formats (HTML + JSON + TXT)
sudo ./nawahard.sh --all

# JSON only (for automation/CI-CD)
sudo ./nawahard.sh --json

# TXT only (for archival)
sudo ./nawahard.sh --txt

# Custom output directory
sudo ./nawahard.sh --all --output /path/to/reports

# Quiet mode (minimal console)
sudo ./nawahard.sh --all --quiet

# Disable colors
sudo ./nawahard.sh --no-color
```

---

## 📸 Screenshot

### Console Output
```
🛡 NawaHard v2.0.0 — Linux VPS Security Audit
OS: Ubuntu 24.04.4 LTS
Started: Thu Jul 17 13:17:55 WIB 2026

🖥 System Foundation
────────────────────────────────────────────────────────────
  i OS Version — Ubuntu 24.04.4 LTS
  ✓ OS Support — Ubuntu 24.04 — supported
  i Kernel — 6.8.0-124-generic
  ⚠ Boot Loader — No GRUB password
    i️ Tanpa GRUB password, akses fisik bisa bypass
    → Set GRUB password: grub2-setpassword

🔑 SSH Configuration
────────────────────────────────────────────────────────────
  ✗ Root Login — Enabled (yes)
    i️ Akses root langsung memudahkan attacker
    → Set 'PermitRootLogin no' in /etc/ssh/sshd_config
  ✗ Password Auth — Enabled
    i️ Password bisa di-brute force
    → Set 'PasswordAuthentication no'
  ⚠ SSH Port — Default port22
    i️ Port 22 target utama scanner otomatis
    → Change to non-standard port

🛡 Firewall & Network
────────────────────────────────────────────────────────────
  ✗ nftables — No rules
    i️ Pertahanan pertama dari serangan jaringan
    → Configure nftables rules
  ✓ SYN Cookies — Enabled
  ⚠ IP Forwarding — Enabled
    i️ IP forward aktif = pivot attack risk
    → sysctl -w net.ipv4.ip_forward=0

════════════════════════════════════════════════════════════
  AUDIT COMPLETE
════════════════════════════════════════════════════════════

  Security Score: 43/100

  ✓ Passed:   34
  ⚠ Warnings: 25
  ✗ Failed:   19
  i Info:      10
  ○ Skipped:   1
  ─────────────────────
  Total:      89

  Reports:
    HTML: /tmp/nawahard/nawahard-20260717_131755.html
    JSON: /tmp/nawahard/nawahard-20260717_131755.json
    TXT:  /tmp/nawahard/nawahard-20260717_131755.txt
```

### HTML Dashboard
```
┌─────────────────────────────────────────────────────────────┐
│  🛡️ NawaHard Security Audit                                │
│  Ubuntu 24.04.4 LTS — VM-13-98-ubuntu — Jul 17, 2026      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐             │
│  │  43  │ │  34  │ │  25  │ │  19  │ │  89  │             │
│  │Score │ │Passed│ │Warn  │ │Failed│ │Total │             │
│  └──────┘ └──────┘ └──────┘ └──────┘ └──────┘             │
│                                                             │
│  SYSTEM FOUNDATION                                          │
│  ┌──────────┬─────────────┬─────────────────────────────┐  │
│  │ Status   │ Check       │ Details                      │  │
│  ├──────────┼─────────────┼─────────────────────────────┤  │
│  │ INFO     │ OS Version  │ Ubuntu 24.04.4 LTS          │  │
│  │ PASS     │ ASLR        │ Full randomization          │  │
│  │ WARN     │ Boot Loader │ No GRUB password            │  │
│  │          │             │ ℹ️ Tanpa GRUB password...    │  │
│  │          │             │ 🔧 Set GRUB password...      │  │
│  └──────────┴─────────────┴─────────────────────────────┘  │
│                                                             │
│  SSH CONFIGURATION                                          │
│  ┌──────────┬─────────────┬─────────────────────────────┐  │
│  │ FAIL     │ Root Login  │ Enabled (yes)               │  │
│  │          │             │ ℹ️ Akses root langsung...    │  │
│  │          │             │ 🔧 Set 'PermitRootLogin no'  │  │
│  │ FAIL     │ Password    │ Enabled                     │  │
│  │          │             │ ℹ️ Password bisa di-brute... │  │
│  │          │             │ 🔧 Set 'PasswordAuth no'     │  │
│  └──────────┴─────────────┴─────────────────────────────┘  │
│                                                             │
│  Footer: NawaHard v2.0.0 — Generated Jul 17, 2026         │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔍 Audit Categories (158 Checks)

### 1. System Foundation (12 checks)
- OS version & EOL status
- Kernel version
- Boot loader password
- Package integrity verification
- ASLR configuration
- Core dump settings
- System clock sync
- System info (hostname, CPU, memory, disk)

### 2. SSH Configuration (14 checks)
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
- SSH protocol version
- SSH algorithm strength

### 3. Firewall & Network (12 checks)
- Firewall detection (UFW/Firewalld/nftables)
- IP forwarding
- ICMP redirects
- Source routing
- SYN cookies
- Reverse path filtering
- Broadcast ICMP
- IPv6 redirects
- Send redirects
- Log martians
- TCP timestamps
- Default interface settings

### 4. Intrusion Prevention (3 checks)
- Fail2ban status & jails
- CrowdSec status
- IPS general check

### 5. Authentication & Access (8 checks)
- Failed login attempts (24h)
- Sudo logging
- Password policy (minlen, complexity)
- Account lockout
- UID 0 accounts
- Empty password accounts
- SUID files
- SGID files

### 6. Kernel Hardening (20 checks)
- Reverse path filter (all & default)
- ICMP redirects (all & default)
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
- Kernel lockdown mode
- Unprivileged BPF
- User namespaces
- perf_event_paranoid

### 7. Service Management (6 checks)
- Running service count
- Dangerous services (telnet, rsh, tftp, etc.)
- Docker status
- Container count
- Service isolation

### 8. Open Ports (16 checks)
- Total listening ports
- Port count assessment
- Dangerous ports:
  - 21 (FTP), 23 (Telnet), 25 (SMTP)
  - 110 (POP3), 135 (RPC), 139 (NetBIOS)
  - 445 (SMB), 1433 (MSSQL), 1521 (Oracle)
  - 3306 (MySQL), 3389 (RDP)
  - 5432 (PostgreSQL), 5900 (VNC)
  - 6379 (Redis), 27017 (MongoDB)

### 9. Resource Usage (5 checks)
- Disk usage
- Memory usage
- CPU usage
- Swap configuration
- Inode usage

### 10. System Updates (4 checks)
- Reboot requirement
- Pending updates
- Automatic updates (unattended-upgrades)
- Security updates

### 11. File Permissions (4 checks)
- World-writable files in /etc
- /etc/shadow permissions
- /etc/passwd permissions
- SUID files in /tmp

### 12. Container Security (5 checks)
- Docker socket permissions
- Containers running as root
- Privileged containers
- Content trust
- Image scanning

### 13. Cloud Metadata (3 checks)
- Cloud provider detection (AWS/GCP/Azure)
- IMDSv2 status (AWS)
- Metadata access

### 14. Logging & Auditing (5 checks)
- Syslog daemon
- Audit daemon (auditd)
- Journal persistence
- Log rotation
- Remote logging

### 15. Miscellaneous (5 checks)
- USB storage module
- File integrity monitoring (AIDE/Tripwire)
- Login banner
- NTP configuration
- Core dump settings

---

## 📄 Output Formats

### HTML Dashboard (Default)
Visual, interactive report with:
- Security score visualization
- Color-coded findings (PASS/WARN/FAIL/INFO)
- Explanations for every finding
- Remediation guidance with commands
- Responsive design (mobile-friendly)
- Dark theme

### JSON Report
Machine-readable format for:
- CI/CD integration
- Automation scripts
- API consumption
- Trend analysis
- Custom dashboards

### TXT Report
Plain text for:
- Terminal viewing
- Log archival
- Email reports
- Documentation
- Compliance records

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

## 📊 Report Contents

Each finding includes:

| Field | Description |
|-------|-------------|
| **Status** | PASS / WARN / FAIL / INFO / SKIP |
| **Check Name** | Name of the security check |
| **Message** | Current value or status |
| **Explanation** | Why this check matters (ℹ️) |
| **Remediation** | How to fix it (🔧) |

Example:
```
✗ Root Login — Enabled (yes)
  ℹ️ Akses root langsung memudahkan attacker jika password bocor
  🔧 Set 'PermitRootLogin no' in /etc/ssh/sshd_config
```

---

## ⚙️ Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `NAWAHARD_REPORT_DIR` | Custom report directory | `/tmp/nawahard` |
| `NAWAHARD_WEBHOOK` | Webhook URL for notifications | - |
| `NO_COLOR` | Disable colored output | `0` |

---

## 🔧 CI/CD Integration

### GitHub Actions
```yaml
- name: Security Audit
  run: |
    curl -sL https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh | sudo bash -s -- --json --output ./reports
    
- name: Upload Report
  uses: actions/upload-artifact@v3
  with:
    name: nawahard-report
    path: ./reports/*.json
```

### GitLab CI
```yaml
security_audit:
  stage: test
  script:
    - curl -sL https://raw.githubusercontent.com/kangaman/NawaHard/master/nawahard.sh | sudo bash -s -- --json
  artifacts:
    paths:
      - /tmp/nawahard/*.json
```

---

## 📁 Project Structure

```
NawaHard/
├── nawahard.sh      # Main audit script (1,400+ lines)
├── README.md        # This documentation
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

### Areas for Contribution
- [ ] Add more OS-specific checks
- [ ] Add compliance scoring (CIS, PCI DSS, UU PDP)
- [ ] Add fix mode (auto-remediation)
- [ ] Add diff mode (compare before/after)
- [ ] Add email notification support
- [ ] Add Slack/Telegram integration
- [ ] Add more cloud provider checks (GCP, Azure)
- [ ] Add Kubernetes security checks
- [ ] Add Docker Compose security checks

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Saeful Bahri**
- GitHub: [@kangaman](https://github.com/kangaman)

---

## 🙏 Acknowledgments

- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) — Security best practices
- [NIST SP800-123](https://csrc.nist.gov/publications/detail/sp/800-123/final) — Server security guidelines
- [STIG](https://public.cyber.mil/stigs/) — Security Technical Implementation Guides
- [UU PDP](https://www.peraturan.go.id/id/uu-no-27-tahun-2022) — Indonesia Data Protection Law

---

## 📊 Roadmap

### v2.0.0 (Current)
- ✅ 158 security checks
- ✅ 15 audit categories
- ✅ Explanations for all findings
- ✅ Remediation for all WARN/FAIL
- ✅ HTML/JSON/TXT output
- ✅ Multi-distro support
- ✅ Cloud metadata detection

### v2.1.0 (Planned)
- [ ] Compliance scoring (CIS Level 1/2)
- [ ] PCI DSS basic checks
- [ ] UU PDP (Indonesia) compliance

### v2.2.0 (Planned)
- [ ] Fix mode (auto-remediation with confirmation)
- [ ] Diff mode (compare before/after)
- [ ] Custom check profiles

### v3.0.0 (Future)
- [ ] NawaHard for Windows Server
- [ ] NawaHard for macOS
- [ ] Web dashboard

---

## 🔗 Related Projects

| Project | Description | Status |
|---------|-------------|--------|
| **NawaHard** | Linux VPS Audit | ✅ Current |
| NawaHard-Win | Windows Server Audit | 🔜 Planned |
| NawaHard-Mac | macOS Audit | 🔜 Planned |
| NawaHard-Web | Web Dashboard | 🔜 Planned |

---

## 📞 Support

- 🐛 [Issues](https://github.com/kangaman/NawaHard/issues)
- 💡 [Discussions](https://github.com/kangaman/NawaHard/discussions)
- 📖 [Wiki](https://github.com/kangaman/NawaHard/wiki)

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/kangaman">Saeful Bahri</a>
</p>
