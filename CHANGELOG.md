# Changelog

All notable changes to NawaHard will be documented in this file.

## [2.0.0] - 2026-07-17

### Added
- Explanations for ALL 158 checks (100% coverage)
- Remediation for ALL 78 WARN/FAIL checks (100% coverage)
- get_explanation() function with 168 cases
- Styled explanation boxes in HTML (blue left-border)
- Styled remediation boxes in HTML (green left-border)
- Kali Linux support
- Linux Mint support
- Pop!_OS support
- Oracle Linux support
- CI/CD integration examples (GitHub Actions, GitLab CI)

### Fixed
- VERSION variable overwritten by /etc/os-release
- Failed logins arithmetic error (whitespace in variables)
- SUID find command hanging (added timeout)
- Branch name in URLs (master, not main)
- HTML report now shows explanations
- JSON report now includes explanation field
- TXT report now shows explanations

### Changed
- Version bumped to 2.0.0
- README completely rewritten with screenshots
- Expanded get_explanation to 168 cases
- Added remediation to all WARN/FAIL checks

## [1.0.1] - 2026-07-17

### Fixed
- VERSION variable being overwritten by /etc/os-release
- Added Kali Linux to OS detection
- Corrected branch name in README URLs (master, not main)

### Added
- Kali Linux support in README

## [1.0.0] - 2026-07-17

### Added
- Initial release
- 158 security checks across 15 categories
- HTML dashboard output (default)
- JSON report output
- TXT report output
- Security scoring (0-100)
- Multi-distro support (Ubuntu, Debian, CentOS, RHEL, Rocky, Alma, Fedora, Amazon Linux)
- Remediation guidance for every finding
- CIS Benchmark alignment
- Webhook notification support
- Quiet mode
- Custom output directory

### Categories
1. System Foundation (12 checks)
2. SSH Configuration (14 checks)
3. Firewall & Network (12 checks)
4. Intrusion Prevention (3 checks)
5. Authentication & Access (8 checks)
6. Kernel Hardening (20 checks)
7. Service Management (6 checks)
8. Open Ports (16 checks)
9. Resource Usage (5 checks)
10. System Updates (4 checks)
11. File Permissions (4 checks)
12. Container Security (5 checks)
13. Cloud Metadata (3 checks)
14. Logging & Auditing (5 checks)
15. Miscellaneous (5 checks)
