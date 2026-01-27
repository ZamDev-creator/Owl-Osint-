# 📖 User Guide - OWL OSINT

Panduan lengkap penggunaan OWL OSINT Framework untuk semua modul.

## Daftar Isi

- [Getting Started](#getting-started)
- [Username Hunter](#1-username-hunter)
- [Email OSINT](#2-email-osint)
- [Image Metadata](#3-image-metadata)
- [Change Monitor](#4-change-monitor)
- [Tips & Best Practices](#tips--best-practices)
- [FAQ](#faq)

---

## Getting Started

### Menjalankan Aplikasi

```bash
# Navigate ke direktori project
cd osint_core_only

# Aktifkan virtual environment (jika menggunakan)
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows

# Jalankan aplikasi
python3 main.py
```

### Navigasi Menu

- **Arrow Keys (↑/↓)**: Navigasi menu
- **Enter**: Select option
- **Ctrl+C**: Cancel operation atau keluar dari continuous mode
- **Esc**: Back (di beberapa prompt)

---

## 1. Username Hunter

### Deskripsi

Mencari keberadaan username di 30+ platform media sosial dan website populer.

### Cara Menggunakan

#### Basic Search

1. Dari main menu, pilih: **🔍 Username Hunter**
2. Input username yang ingin dicari
3. Tunggu proses scanning (10-30 detik)
4. Lihat hasil:
   - ✅ **FOUND**: Platform dimana username ditemukan
   - ❌ **NOT FOUND**: Platform dimana username tidak ada

#### Contoh

```
Enter username to search: johndoe

🔎 Hunting for 'johndoe' across platforms...

✅ FOUND (8 profiles):
┌──────────────┬─────────────────────────────────────────┐
│ Platform     │ URL                                     │
├──────────────┼─────────────────────────────────────────┤
│ GitHub       │ https://github.com/johndoe             │
│ Instagram    │ https://www.instagram.com/johndoe      │
│ Twitter/X    │ https://twitter.com/johndoe            │
│ Reddit       │ https://www.reddit.com/user/johndoe    │
│ YouTube      │ https://www.youtube.com/@johndoe       │
│ Medium       │ https://medium.com/@johndoe            │
│ Dev.to       │ https://dev.to/johndoe                 │
│ GitLab       │ https://gitlab.com/johndoe             │
└──────────────┴─────────────────────────────────────────┘

❌ NOT FOUND (22 platforms)
```

### Platform yang Didukung

**Social Media**:
- Instagram, Twitter/X, Facebook, TikTok
- Reddit, Pinterest, Tumblr

**Professional**:
- LinkedIn, GitHub, GitLab, Bitbucket
- Stack Overflow, HackerNews

**Content Creators**:
- YouTube, Twitch, Medium, Dev.to
- Patreon, SoundCloud, Spotify

**Design & Art**:
- Behance, Dribbble, Flickr, Vimeo

**Communication**:
- Telegram, Discord, Keybase

**Blogs**:
- WordPress, Blogger, About.me

### Tips untuk Username Search

1. **Case Sensitivity**: 
   - Beberapa platform case-sensitive (GitHub, Twitter)
   - Coba variasi: johndoe, JohnDoe, JOHNDOE

2. **Special Characters**:
   - Hindari spasi
   - Underscore (_) dan dash (-) biasanya diperbolehkan
   - Contoh valid: john_doe, john-doe

3. **Username Length**:
   - Min: 3 karakter
   - Max: 30 karakter (tergantung platform)

4. **Common Variations to Try**:
   ```
   johndoe
   john_doe
   john-doe
   johndoe123
   johndoe_official
   ```

### Understanding Results

**Status Codes**:
- ✅ **200 OK**: Username exists dan profile public
- ❌ **404 Not Found**: Username tidak ditemukan
- ⚠️ **403 Forbidden**: Blocked atau private profile
- ⏱️ **Timeout**: Platform tidak respond

### Report Output

Hasil otomatis tersimpan di:
```
output/reports/username_johndoe_20250127_143052.html
```

Buka di browser untuk melihat:
- Summary results
- Detailed platform list
- Timestamp
- Search metadata

---

## 2. Email OSINT

### Deskripsi

Analisis mendalam terhadap alamat email untuk mendapatkan informasi dan validasi.

### Cara Menggunakan

1. Dari main menu, pilih: **📧 Email OSINT**
2. Input email address yang valid
3. Tunggu proses analisis (5-15 detik)
4. Lihat hasil analisis

#### Contoh

```
Enter email address to analyze: john.doe@example.com

📧 Analyzing email address...

📊 EMAIL ANALYSIS RESULTS

Basic Info:
  • Email: john.doe@example.com
  • Username: john.doe
  • Domain: example.com
  • Format: ✅ Valid

Domain Analysis:
  • DNS: ✅ Active
  • MX Records: ✅ Found (2 servers)
    - mx1.example.com (Priority: 10)
    - mx2.example.com (Priority: 20)
  • Domain Age: ~15 years
  • Status: Active & Receiving

Email Type:
  • Personal/Business: Business
  • Disposable: ❌ No
  • Free Provider: ❌ No

Security Check:
  • Data Breaches: ✅ No breaches found
  • Spam Reports: Clean
  • Reputation: Good

Recommendations:
  • Email appears to be legitimate business email
  • Domain has good reputation
  • No security concerns detected
```

### Features

#### 1. Format Validation
- Regex-based email format check
- RFC 5322 compliant
- Detects invalid characters

#### 2. Domain Analysis
- DNS lookup
- MX record verification
- Domain age & reputation
- WHOIS information (jika available)

#### 3. Disposable Email Detection
Mendeteksi temporary/disposable email dari provider seperti:
- tempmail.com
- guerrillamail.com
- 10minutemail.com
- mailinator.com
- Dan 100+ provider lainnya

#### 4. Breach Detection (Requires HIBP API Key)

Dengan HIBP API key, tool akan check:
- Data breaches history
- Exposed passwords count
- Breach dates
- Compromised services

**Setup HIBP API Key**:

1. Dapatkan key dari: https://haveibeenpwned.com/API/Key
2. Edit `.env` file:
   ```
   HIBP_API_KEY=your_key_here
   ```
3. Restart aplikasi

**Contoh dengan HIBP**:
```
Security Check:
  • Data Breaches: ⚠️ 3 breaches found
    - Adobe (2013): 152M accounts
    - LinkedIn (2016): 164M accounts
    - Dropbox (2012): 68M accounts
  • Exposed Passwords: Yes
  • Action: Change password immediately!
```

#### 5. Hunter.io Integration (Optional)

Dengan Hunter.io API key:
- Email deliverability score
- Source detection
- Email pattern analysis
- Company information

**Setup Hunter.io**:
```
HUNTER_IO_KEY=your_hunter_key
```

### Use Cases

1. **Email Verification**:
   - Before sending important emails
   - Validate customer emails
   - Clean email lists

2. **Security Audit**:
   - Check if your email in breaches
   - Monitor company emails
   - Security assessment

3. **Investigation**:
   - Background checks
   - Digital footprint analysis
   - Fraud detection

4. **Lead Generation**:
   - Validate business emails
   - Find company patterns
   - Build contact lists

### Report Output

```
output/reports/email_johndoe_20250127_143152.html
```

Contains:
- Complete analysis results
- Visual charts
- Recommendation summary
- Export to PDF option

---

## 3. Image Metadata

### Deskripsi

Ekstraksi metadata EXIF dari image files untuk mendapatkan informasi tersembunyi.

### Cara Menggunakan

1. Dari main menu, pilih: **🖼️ Image Metadata**
2. Input path ke image file
   - Absolute path: `/home/user/Photos/image.jpg`
   - Relative path: `./images/photo.jpg`
3. Lihat hasil ekstraksi

#### Contoh

```
Enter path to image file: /home/user/vacation.jpg

🖼️ Extracting metadata from image...

📸 IMAGE METADATA REPORT

File Information:
  • Filename: vacation.jpg
  • Size: 2.4 MB
  • Dimensions: 4000 x 3000 pixels
  • Format: JPEG
  • Color Space: RGB

Camera Information:
  • Make: Canon
  • Model: Canon EOS 5D Mark IV
  • Lens: EF 24-70mm f/2.8L II USM
  • Serial Number: 1234567890

Photo Settings:
  • ISO: 400
  • Aperture: f/2.8
  • Shutter Speed: 1/500s
  • Focal Length: 50mm
  • Flash: Off
  • Exposure Mode: Manual

Date & Time:
  • Original: 2024-07-15 14:32:18
  • Digitized: 2024-07-15 14:32:18
  • Modified: 2024-07-20 10:15:30

GPS Location:
  • Latitude: 48.8584° N
  • Longitude: 2.2945° E
  • Altitude: 35 meters
  • Location: Near Eiffel Tower, Paris, France
  • Map: https://maps.google.com/?q=48.8584,2.2945

Software:
  • Software: Adobe Photoshop CC 2024
  • Edit History: Available
  • Color Profile: Adobe RGB

Additional Metadata:
  • Artist: John Doe
  • Copyright: © 2024 John Doe
  • Description: Summer vacation in Paris
  • Keywords: travel, paris, vacation
```

### Supported Formats

**Fully Supported** (dengan EXIF):
- JPEG (.jpg, .jpeg)
- TIFF (.tif, .tiff)
- RAW formats (.cr2, .nef, .arw) - dengan library tambahan

**Partial Support**:
- PNG (.png) - limited metadata
- HEIC/HEIF (.heic, .heif) - requires pillow-heif

**Not Supported**:
- GIF, BMP, WebP - no EXIF data

### GPS Location Features

Jika image memiliki GPS data:

1. **Coordinates**: Exact latitude/longitude
2. **Altitude**: Height above sea level
3. **Direction**: Compass direction when taken
4. **Google Maps Link**: Direct link to location
5. **Reverse Geocoding**: City/country name (requires internet)

**Privacy Concern**: 
⚠️ Many smartphone photos include GPS data by default!

### Use Cases

1. **Digital Forensics**:
   - Verify photo authenticity
   - Track photo origin
   - Timeline reconstruction

2. **Privacy Audit**:
   - Check your photos before sharing
   - Remove sensitive metadata
   - Clean photos for social media

3. **Photography Analysis**:
   - Learn camera settings
   - Study lighting conditions
   - Analyze professional photos

4. **Investigation**:
   - Location verification
   - Timestamp validation
   - Equipment identification

### Metadata Removal

Tool juga menyediakan option untuk remove metadata:

```
Options after viewing metadata:
1. Save detailed report
2. Remove all metadata
3. Export to JSON
4. Back to menu

Select: 2

✅ Metadata removed!
New file saved: vacation_clean.jpg
```

### Report Output

```
output/reports/image_metadata_20250127_143252.html
```

Includes:
- All extracted metadata
- GPS map visualization
- Camera settings chart
- Photo thumbnails
- Download cleaned image option

---

## 4. Change Monitor

### Deskripsi

Monitor website atau web pages untuk detect perubahan content.

### Cara Menggunakan

#### Add New URL to Monitor

1. Pilih: **🔔 Change Monitor**
2. Select: **Add new URL to monitor**
3. Input URL lengkap: `https://example.com/page`
4. Tool akan fetch initial content
5. ✅ URL ditambahkan ke monitoring list

```
Enter URL to monitor: https://example.com/news

📡 Fetching initial content from https://example.com/news...
✅ URL added to monitoring successfully!

Initial content hash: a3f8b4c9d2e1f5g6h7i8j9k0
```

#### Check All URLs Now

Manual check semua URLs:

```
🔍 Checking all monitored URLs for changes...

Checking: https://example.com/news ... ✅ No changes
Checking: https://example.com/blog ... ⚠️ CHANGED!
Checking: https://competitor.com/prices ... ✅ No changes

⚠️ CHANGES DETECTED in 1 URL(s):
  • https://example.com/blog
    - Last check: 2025-01-27 14:30:00
    - Change detected at: 2025-01-27 15:45:23
```

#### List Monitored URLs

Lihat semua URLs yang dimonitor:

```
📋 MONITORED URLs (3):

┌────┬──────────────────────────┬──────────────────┬─────────────────────┬─────────┐
│ #  │ URL                      │ Hash             │ Last Check          │ Changed │
├────┼──────────────────────────┼──────────────────┼─────────────────────┼─────────┤
│ 1  │ https://example.com/news │ a3f8b4c9d2e1f... │ 2025-01-27 14:30:00│ No      │
│ 2  │ https://example.com/blog │ b4c9d2e1f5g6h... │ 2025-01-27 15:45:00│ Yes     │
│ 3  │ https://competitor.com/  │ c9d2e1f5g6h7i... │ 2025-01-27 14:25:00│ No      │
└────┴──────────────────────────┴──────────────────┴─────────────────────┴─────────┘
```

#### Remove URL from Monitoring

```
Select URL to remove:
› https://example.com/news
  https://example.com/blog
  https://competitor.com/prices
  Cancel

✅ Removed: https://example.com/news
```

#### Start Continuous Monitoring

Automated checking dengan interval:

```
Enter check interval in seconds (default: 300): 600

🔄 Starting continuous monitoring (Ctrl+C to stop)...

[14:30:15] Checking 3 URLs...
[14:30:16] ✅ All OK - No changes detected

[14:40:15] Checking 3 URLs...
[14:40:17] ⚠️ Change detected at https://example.com/blog
[14:40:17] ✅ 2 URLs unchanged

[14:50:15] Checking 3 URLs...
[14:50:16] ✅ All OK - No changes detected

^C
✋ Monitoring stopped
```

### How It Works

1. **Initial Fetch**:
   - Download page content
   - Calculate SHA-256 hash
   - Store in database

2. **Change Detection**:
   - Fetch current content
   - Calculate new hash
   - Compare with stored hash
   - Alert if different

3. **Storage**:
   - URL tracking in SQLite
   - Hash history
   - Change timestamps
   - Alert logs

### Use Cases

1. **Competitor Monitoring**:
   - Track price changes
   - Monitor product launches
   - Watch for updates

2. **Content Tracking**:
   - News websites
   - Blog posts
   - Documentation pages

3. **Security Monitoring**:
   - Defacement detection
   - Unauthorized changes
   - Content integrity

4. **Legal Compliance**:
   - Terms of Service changes
   - Privacy policy updates
   - Regulatory notices

### Advanced Features

#### Custom Check Interval

Edit `config.py`:
```python
MONITOR_INTERVAL = 300  # 5 minutes
```

Or use command line:
```bash
python main.py --monitor-interval 600
```

#### Email Alerts (Coming Soon)

Setup email notifications:
```python
# config.py
ALERT_EMAIL = "your@email.com"
SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 587
```

#### Webhook Integration (Coming Soon)

Post changes to webhook:
```python
# config.py
WEBHOOK_URL = "https://hooks.slack.com/your-webhook"
```

### Report Output

```
output/reports/change_monitor_20250127.html
```

Contains:
- All monitored URLs
- Change history
- Timeline visualization
- Diff comparison
- Export options

---

## Tips & Best Practices

### General Tips

1. **Run with Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```

2. **Keep Database Backup**:
   ```bash
   cp osint_data.db osint_data.db.backup
   ```

3. **Regular Updates**:
   ```bash
   git pull origin main
   pip install -r requirements.txt --upgrade
   ```

### Username Hunter Tips

- Use common username formats
- Try variations (username, user_name, user-name)
- Check multiple times untuk accuracy
- Beware of false positives

### Email OSINT Tips

- Get HIBP API key untuk full features
- Validate before sending bulk emails
- Check disposable email lists
- Monitor company email breaches

### Image Metadata Tips

- Always check GPS before sharing photos
- Use metadata removal for privacy
- Verify image authenticity
- Check edit history

### Change Monitor Tips

- Set reasonable check intervals
- Monitor specific pages, not entire sites
- Use for critical pages only
- Clean old entries regularly

### Performance Optimization

1. **Reduce Concurrent Requests**:
   ```python
   # config.py
   MAX_WORKERS = 5  # Default: 10
   ```

2. **Increase Timeout**:
   ```python
   REQUEST_TIMEOUT = 15  # Default: 10
   ```

3. **Use Proxy** (if needed):
   ```python
   # config.py
   PROXY = "http://proxy-server:port"
   ```

### Security Best Practices

1. **Never Share API Keys**:
   - Keep `.env` in `.gitignore`
   - Use environment variables
   - Rotate keys regularly

2. **Respect Rate Limits**:
   - Don't spam platforms
   - Use delays between requests
   - Follow ToS

3. **Legal Compliance**:
   - Only public information
   - Get proper authorization
   - Respect privacy laws

---

## FAQ

### Q: Berapa lama proses username search?

**A**: Tergantung jumlah platform dan koneksi internet:
- Fast connection: 10-15 seconds
- Average: 20-30 seconds
- Slow: 30-60 seconds

### Q: Apakah tool ini gratis?

**A**: Ya, tool ini open source dan gratis. Namun beberapa fitur memerlukan API keys berbayar (HIBP, Hunter.io).

### Q: Apakah aman menggunakan tool ini?

**A**: Ya, tool ini hanya mengakses informasi publik. Namun gunakan secara bertanggung jawab dan legal.

### Q: Bisa monitoring berapa URL sekaligus?

**A**: Tidak ada limit hard-coded, namun disarankan max 50 URLs untuk performance optimal.

### Q: Format image apa yang didukung?

**A**: JPEG, TIFF fully supported. PNG partial support. RAW formats butuh library tambahan.

### Q: Apakah perlu API keys?

**A**: Tidak wajib. Tool bisa jalan tanpa API keys, tapi dengan limited features.

### Q: Bagaimana update tool?

**A**: Download versi baru, backup `.env` dan database, replace files, reinstall dependencies.

### Q: Error "ModuleNotFoundError"?

**A**: Run `pip install -r requirements.txt --force-reinstall`

### Q: Tool tidak bisa akses internet?

**A**: Check firewall, proxy settings, atau antivirus yang mungkin blocking.

### Q: Database corrupt?

**A**: Restore dari backup atau delete `osint_data.db` untuk fresh start.

---

## Need Help?

- 📖 Read [README.md](README.md) untuk overview
- 📥 Check [INSTALLATION.md](INSTALLATION.md) untuk install issues
- 🔧 See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) untuk error fixes
- 💬 Contact developer: [@azm101222](https://t.me/azm101222)

---

**Happy OSINT-ing! 🦉**

Developer: AZM | Telegram: @azm101222
