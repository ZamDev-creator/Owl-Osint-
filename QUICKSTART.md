# 🚀 Quick Start Guide - OWL OSINT

Panduan cepat untuk mulai menggunakan OWL OSINT dalam 5 menit!

## 📋 Prerequisites

Pastikan Anda sudah punya:
- ✅ Python 3.8+ installed
- ✅ pip (Python package manager)
- ✅ Internet connection

Cek Python version:
```bash
python3 --version
```

---

## ⚡ Installation (3 menit)

### Step 1: Extract Files

```bash
unzip osint_core_only.zip
cd osint_core_only
```

### Step 2: Install Dependencies

```bash
pip3 install -r requirements.txt
```

### Step 3: Setup Environment (Optional)

```bash
cp .env.example .env
# Edit .env untuk add API keys (opsional)
```

---

## 🎯 First Run (1 menit)

### Start the Application

```bash
python3 main.py
```

Anda akan melihat ASCII owl banner yang keren! 🦉

---

## 💡 Try Each Module (5 menit)

### 1. Username Hunter 🔍

```
Menu → Select: 🔍 Username Hunter
Input: testuser
Wait: 15-30 seconds
Result: List of platforms where username found
```

**Example Output**:
```
✅ FOUND (5 profiles):
- GitHub: https://github.com/testuser
- Instagram: https://www.instagram.com/testuser
- Twitter: https://twitter.com/testuser
```

### 2. Email OSINT 📧

```
Menu → Select: 📧 Email OSINT
Input: test@example.com
Wait: 5-10 seconds
Result: Email validation & analysis
```

**Example Output**:
```
Format: ✅ Valid
MX Records: ✅ Found
Disposable: ❌ No
```

### 3. Image Metadata 🖼️

```
Menu → Select: 🖼️ Image Metadata
Input: /path/to/your/image.jpg
Result: EXIF data & GPS location
```

**Example Output**:
```
Camera: Canon EOS 5D Mark IV
GPS: 48.8584°N, 2.2945°E (Paris, France)
Date: 2024-07-15 14:32:18
```

### 4. Change Monitor 🔔

```
Menu → Select: 🔔 Change Monitor
Option: Add new URL to monitor
Input: https://example.com
```

---

## 📊 View Results

### Check Reports

```bash
# Navigate to reports directory
cd output/reports/

# List reports
ls -la

# Open in browser
# Linux
xdg-open username_testuser_20250127.html

# macOS
open username_testuser_20250127.html

# Windows
start username_testuser_20250127.html
```

### Check Database

```bash
sqlite3 osint_data.db
> SELECT * FROM username_searches LIMIT 5;
> .exit
```

---

## 🎓 Learn More

### Next Steps

1. **Read Full Docs**:
   - [USER_GUIDE.md](USER_GUIDE.md) - Detailed usage
   - [API_REFERENCE.md](API_REFERENCE.md) - For developers
   - [FAQ.md](FAQ.md) - Common questions

2. **Setup API Keys** (Optional):
   - Get HIBP key: https://haveibeenpwned.com/API/Key
   - Get Hunter.io key: https://hunter.io/
   - Add to `.env` file

3. **Customize Settings**:
   - Edit `config.py` untuk:
     - Timeout values
     - Worker count
     - Log levels

---

## 🔧 Common Commands

### Quick Commands

```bash
# Run application
python3 main.py

# With virtual environment
source venv/bin/activate && python main.py

# View logs
tail -f output/logs/osint_$(date +%Y-%m-%d).log

# Backup database
cp osint_data.db osint_data.db.backup

# Clean old reports (older than 30 days)
find output/reports/ -mtime +30 -delete
```

---

## 🎯 Use Cases

### Quick Examples

#### 1. Check Your Digital Footprint
```
1. Username Hunter → Your username
2. Review all platforms
3. Decide what to keep/delete
```

#### 2. Verify Email Before Sending
```
1. Email OSINT → Target email
2. Check MX records
3. Verify not disposable
```

#### 3. Check Photo Before Sharing
```
1. Image Metadata → Your photo
2. Check GPS data
3. Remove metadata if needed
```

#### 4. Monitor Competitor Website
```
1. Change Monitor → Add URL
2. Set check interval
3. Get alerts on changes
```

---

## ⚙️ Basic Configuration

### config.py - Quick Tweaks

```python
# Faster but more aggressive
MAX_WORKERS = 15
REQUEST_TIMEOUT = 5

# Slower but more stable
MAX_WORKERS = 5
REQUEST_TIMEOUT = 20

# Log everything
LOG_LEVEL = "DEBUG"

# Minimal logging
LOG_LEVEL = "ERROR"
```

---

## 🐛 Quick Troubleshooting

### Problem: Module not found
```bash
pip3 install -r requirements.txt --force-reinstall
```

### Problem: Permission denied
```bash
chmod +x main.py
chmod -R 755 .
```

### Problem: Database locked
```bash
pkill -f main.py
rm -f osint_data.db-journal
```

### Problem: Slow performance
```python
# Edit config.py
MAX_WORKERS = 5
REQUEST_TIMEOUT = 15
```

---

## 📱 Contact Support

**Need help?**

**Developer**: AZM  
**Telegram**: [@azm101222](https://t.me/azm101222)

**Response time**: Usually within 24 hours

---

## ✅ Checklist

Before you start:
- [ ] Python 3.8+ installed
- [ ] Dependencies installed
- [ ] Can run `python3 main.py`
- [ ] See the owl banner
- [ ] Try each module once
- [ ] Check output/reports/

Optional:
- [ ] Setup virtual environment
- [ ] Add API keys to .env
- [ ] Configure settings in config.py
- [ ] Read full documentation

---

## 🎉 You're Ready!

Congratulations! Anda siap menggunakan OWL OSINT.

**Pro Tips**:
- Start dengan simple searches
- Save useful results
- Backup database regularly
- Read USER_GUIDE untuk advanced features
- Join community untuk tips & tricks

---

## 🔗 Quick Links

- 📖 [Full README](README.md)
- 📥 [Installation Guide](INSTALLATION.md)
- 👥 [User Guide](USER_GUIDE.md)
- 🔌 [API Reference](API_REFERENCE.md)
- ❓ [FAQ](FAQ.md)
- 📝 [Changelog](CHANGELOG.md)

---

**Happy OSINT-ing! 🦉**

*Time to start: ~5 minutes*  
*Time to master: Practice makes perfect!*

Developer: AZM | Telegram: @azm101222
