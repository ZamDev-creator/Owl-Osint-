# 🔒 Security Policy - OWL OSINT

Dokumen keamanan untuk OWL OSINT Framework.

## 🛡️ Security Overview

OWL OSINT dirancang dengan mempertimbangkan keamanan, namun sebagai pengguna Anda juga bertanggung jawab untuk:
- Menjaga API keys tetap rahasia
- Menggunakan tool secara legal dan etis
- Melindungi data yang dikumpulkan
- Mengikuti best practices

---

## 🔐 Supported Versions

Berikut versi yang masih menerima security updates:

| Version | Supported          |
| ------- | ------------------ |
| 2.0.x   | ✅ Yes             |
| < 2.0   | ❌ No              |

---

## 📢 Reporting a Vulnerability

### How to Report

Jika Anda menemukan security vulnerability:

1. **JANGAN** buat public issue di GitHub
2. **JANGAN** discuss di public channels
3. **DO** report privately via:
   - **Telegram**: [@azm101222](https://t.me/azm101222)
   - Subject: "SECURITY: [Brief Description]"

### What to Include

```
Subject: SECURITY: SQL Injection in email module

Details:
- Vulnerability type: SQL Injection
- Affected component: modules/email_osint.py
- Line number: 142
- Severity: High
- Steps to reproduce:
  1. ...
  2. ...
- Proof of concept: [code/screenshot]
- Suggested fix: [if any]
```

### Response Timeline

- **Initial Response**: Within 48 hours
- **Assessment**: 3-5 days
- **Fix Development**: 1-2 weeks (depending on severity)
- **Public Disclosure**: After fix released

### Responsible Disclosure

We request that security researchers:
- Give us reasonable time to fix (90 days)
- Don't exploit vulnerability
- Don't disclose publicly before fix
- We'll credit you in security advisory

---

## 🔒 Security Best Practices

### For Users

#### 1. Protect API Keys

**DO**:
```bash
# Keep .env in .gitignore
echo ".env" >> .gitignore

# Use environment variables
export HIBP_API_KEY="your-key-here"

# Set proper permissions
chmod 600 .env
```

**DON'T**:
```python
# ❌ Never hardcode keys
HIBP_API_KEY = "abc123..."

# ❌ Don't commit .env
git add .env

# ❌ Don't share keys
print(f"My key is: {api_key}")
```

#### 2. Secure Database

```bash
# Set proper permissions
chmod 600 osint_data.db

# Regular backups
cp osint_data.db osint_data.db.backup

# Encrypt sensitive data (optional)
# Use SQLCipher for encryption
```

#### 3. Network Security

```python
# config.py

# Use HTTPS only
VERIFY_SSL = True

# Set proper timeouts
REQUEST_TIMEOUT = 10

# Use proxy if needed (for privacy)
PROXY = {
    'http': 'http://proxy:port',
    'https': 'https://proxy:port'
}
```

#### 4. Input Validation

Tool sudah implement input validation, tapi selalu:
- Sanitize user inputs
- Validate file paths
- Check URL formats
- Escape special characters

#### 5. Log Security

```python
# Don't log sensitive data
logger.info(f"Checking email: {email}")  # ✅ OK

# Don't log API keys
logger.debug(f"API key: {api_key}")  # ❌ BAD

# Sanitize logs
logger.info(f"Checking: {email.split('@')[0]}@***")  # ✅ Better
```

---

## 🚨 Known Security Considerations

### 1. API Key Exposure

**Risk**: API keys di .env file bisa ter-expose jika:
- Accidentally committed to Git
- Shared screenshots dengan .env visible
- Server compromise

**Mitigation**:
```bash
# Add to .gitignore
.env
*.env
.env.*

# Use secret management tools
# AWS Secrets Manager, HashiCorp Vault, etc.
```

### 2. SQL Injection

**Risk**: User input bisa contain malicious SQL

**Mitigation**: Tool uses parameterized queries:
```python
# ✅ Safe - Parameterized query
cursor.execute(
    "SELECT * FROM searches WHERE username = ?", 
    (username,)
)

# ❌ Unsafe - String concatenation
cursor.execute(
    f"SELECT * FROM searches WHERE username = '{username}'"
)
```

### 3. Command Injection

**Risk**: Malicious input in system commands

**Mitigation**: Tool avoids system calls dengan user input:
```python
# ❌ Avoid
os.system(f"wget {user_url}")

# ✅ Use library
import requests
requests.get(user_url)
```

### 4. XSS in Reports

**Risk**: Malicious content dalam HTML reports

**Mitigation**: Reports use Jinja2 auto-escaping:
```python
# Jinja2 auto-escapes by default
{{ username }}  # Safe from XSS
{{ username|safe }}  # Only if you trust input
```

### 5. Path Traversal

**Risk**: Malicious file paths

**Mitigation**: Path validation implemented:
```python
# Validate paths
from pathlib import Path

def safe_path(user_path):
    # Resolve and check if within allowed directory
    path = Path(user_path).resolve()
    if not str(path).startswith(str(OUTPUT_DIR)):
        raise ValueError("Invalid path")
    return path
```

---

## 🔐 Authentication & Authorization

### Current Status

**v2.0**: No authentication (single-user tool)

### Future (v3.0+)

Planned authentication features:
- User accounts
- Role-based access control
- API token authentication
- Session management
- 2FA support

---

## 🛡️ Data Protection

### What Data is Collected?

Tool stores locally:
- Search history (usernames, emails checked)
- Monitored URLs
- Change history
- Log files

**No data sent to external servers** except:
- API calls (HIBP, Hunter.io)
- Platform checks (GitHub, Instagram, etc.)

### Data Retention

```python
# Implement data retention policy
# Example: Delete old searches after 30 days

import sqlite3
from datetime import datetime, timedelta

def cleanup_old_data(days=30):
    conn = sqlite3.connect('osint_data.db')
    cutoff = datetime.now() - timedelta(days=days)
    
    conn.execute(
        "DELETE FROM username_searches WHERE timestamp < ?",
        (cutoff,)
    )
    conn.commit()
```

### GDPR Compliance

For EU users:
- Data stored locally (no central server)
- User has full control
- Can delete anytime
- No third-party tracking
- Transparent data usage

**User Rights**:
- Right to access (view database)
- Right to deletion (delete database)
- Right to portability (export data)

---

## 🔍 Security Auditing

### Code Security Tools

Recommended tools untuk audit:

```bash
# Install security tools
pip install bandit safety

# Run security scan
bandit -r modules/ utils/

# Check dependencies for vulnerabilities
safety check -r requirements.txt

# Static analysis
pylint --disable=all --enable=security modules/
```

### Dependency Security

```bash
# Check outdated packages
pip list --outdated

# Update dependencies
pip install -r requirements.txt --upgrade

# Audit with pip-audit
pip install pip-audit
pip-audit
```

---

## 🚨 Incident Response

### If Compromised

1. **Immediate Actions**:
   ```bash
   # Rotate all API keys
   # Change .env file
   nano .env
   
   # Check for unauthorized changes
   git diff
   
   # Scan for malware
   clamscan -r .
   ```

2. **Investigation**:
   - Check logs: `output/logs/`
   - Review database: `osint_data.db`
   - Analyze network traffic

3. **Recovery**:
   - Restore from backup
   - Update all dependencies
   - Change credentials

4. **Prevention**:
   - Enable 2FA on accounts
   - Use firewall
   - Regular security audits

---

## 🔐 Encryption

### Database Encryption (Optional)

Untuk encrypt database:

```bash
# Install SQLCipher
pip install sqlcipher3

# Use encrypted database
python
>>> from pysqlcipher3 import dbapi2 as sqlite
>>> conn = sqlite.connect('osint_data.db')
>>> conn.execute("PRAGMA key='your-encryption-key'")
```

### File Encryption

```bash
# Encrypt reports (using GPG)
gpg --encrypt --recipient your@email.com report.html

# Decrypt
gpg --decrypt report.html.gpg > report.html
```

---

## 🎯 Security Checklist

### Before First Use

- [ ] Review LICENSE dan disclaimer
- [ ] Understand legal implications
- [ ] Setup .env properly
- [ ] Configure .gitignore
- [ ] Set file permissions

### Regular Maintenance

- [ ] Update dependencies monthly
- [ ] Rotate API keys quarterly
- [ ] Backup database weekly
- [ ] Review logs regularly
- [ ] Clean old data
- [ ] Check for updates

### Before Sharing

- [ ] Remove API keys
- [ ] Clean sensitive data
- [ ] Sanitize logs
- [ ] Review reports
- [ ] Check file permissions

---

## 🛠️ Security Configuration

### Recommended config.py Settings

```python
# Security settings

# Force HTTPS
VERIFY_SSL = True

# Request timeout (prevent hanging)
REQUEST_TIMEOUT = 10

# Rate limiting
MAX_WORKERS = 10
RATE_LIMIT_DELAY = 1  # seconds between requests

# User agent (don't pretend to be browser)
USER_AGENT = "OWL-OSINT/2.0 (Security Research)"

# Logging (don't log sensitive data)
LOG_LEVEL = "INFO"  # Not DEBUG in production
LOG_SANITIZE = True  # Redact sensitive info

# Database
DB_BACKUP_ENABLED = True
DB_BACKUP_INTERVAL = 86400  # 24 hours

# API keys validation
REQUIRE_API_KEYS = False  # Optional features
VALIDATE_API_KEYS = True  # Check before use
```

---

## 📞 Security Contact

**Security Team**: Developer AZM  
**Contact**: Telegram [@azm101222](https://t.me/azm101222)  
**PGP Key**: Available on request  
**Response Time**: 48 hours for security issues

---

## 📚 Security Resources

### Learning Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Python Security Best Practices](https://python.readthedocs.io/en/stable/library/security_warnings.html)
- [SQLite Security](https://www.sqlite.org/security.html)
- [API Security](https://apisecurity.io/)

### Security Tools

- **Bandit**: Python security linter
- **Safety**: Dependency vulnerability scanner
- **Snyk**: Security monitoring
- **OWASP ZAP**: Security testing

---

## 🏆 Security Hall of Fame

Contributors who reported security issues:

*None yet - Be the first!*

---

## ⚖️ Legal Notice

**This tool is for authorized security research and educational purposes only.**

Users must:
- Comply with all applicable laws
- Obtain proper authorization
- Respect privacy and ToS
- Use responsibly

**The developers are not responsible for misuse.**

---

## 📝 Security Updates

Security advisories will be posted:
- In CHANGELOG.md
- Via Telegram channel
- On GitHub releases

Subscribe untuk security notifications!

---

## 🔄 Version History

### v2.0.0 (2025-01-27)
- Initial security policy
- Input validation
- SQL injection prevention
- XSS protection
- Secure API key handling

---

**Last Updated**: January 27, 2025  
**Version**: 2.0.0  
**Security Policy Version**: 1.0

---

*Security is everyone's responsibility. Report issues responsibly.* 🔒

Developer: AZM | Telegram: @azm101222
