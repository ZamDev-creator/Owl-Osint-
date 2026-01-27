# 🦉 OWL OSINT - Open Source Intelligence Framework

![Version](https://img.shields.io/badge/version-2.0-blue.svg)
![Python](https://img.shields.io/badge/python-3.8+-green.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)

<div align="center">

```
                        .#@@@@@@@@@@@@@@@#.
                    *@@@@@@@@@@@@@@@@@@@@@@@*
                  #@@@@@@@@@@@@@@@@@@@@@@@@@@@#
                *@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*
               @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
              @@@@@#*.             .             .*#@@@@@
            .@@@@*.   .-=#@@@@=.   .   .=@@@@#=-.   .*@@@@.
            @@@*.   .#@@@@@@@@@@@. . .@@@@@@@@@@@#.   .*@@@
           #@@*   .@@@@@@###@@@@@@. .@@@@@@###@@@@@@.   *@@#
          .@@#   *@@@@@@##@@@##@@@@@.@@@@@##@@@##@@@@@@*   #@@.
          *@@.  .@@@@@@@##@@@##@@@@@@@@@@##@@@##@@@@@@@.  .@@*
          @@@   #@@@@@@@@###@@@@@@@@@@@###@@@@@@@@#   @@@
          @@@.  =@@@@@@@@@@@@@@*.###.*@@@@@@@@@@@@@@=  .@@@
          #@@*   -@@@@@@@@@@@@@#.###.#@@@@@@@@@@@@@-   *@@#
           @@@=    -*@@@@@@@@@@@#######@@@@@@@@@@@*-    =@@@
           *@@@#.     .=*#@@@@@@@@@@@@@@@@@#*=.     .#@@@*
            .@@@@*.          :########:          .*@@@@.
              -@@@@@*:         ########         :*@@@@@-
                :#@@@@#=:     #$#$#$#$     :=#@@@@#:
              .:**#@@@@@@@@@*:#$#$#$#$:*@@@@@@@@@#**:.
            -*@@@@@@@@@@@@@@@#$#$#$#$#@@@@@@@@@@@@@@@*-
           =@@@@@%*=---=*%@@@@@##$#$##@@@@@%*=---=*%@@@@@=
          *@@@@%=:     :=%@@@@####@@@@%=:     :=%@@@@*
          #@@@%-        -%@@@@@@@@@@@@@%-        -%@@@#
          *@@@%=.      .=%@@@@@@@@@@@@@%=.      .=%@@@*
           @@@@@%*====*%@@@@@@@@@@@@@@@@%*====*%@@@@@
            =@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@=
              -*@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*-
                 .=*#@@@@@@@@@@@@@@@@@@#*=.

    ███████╗ ██╗    ██╗ ██╗         ███████╗  ██████╗ ██╗███╗  ██╗████████╗
   ██╔═══██╗ ██║    ██║ ██║        ██╔═══██╗██╔════╝ ██║████╗ ██║╚══██╔══╝
   ██║   ██║ ██║ █╗ ██║ ██║        ██║   ██║╚█████╗  ██║██╔██╗██║   ██║
   ██║   ██║ ██║███╗██║ ██║        ██║   ██║ ╚═══██╗ ██║██║╚████║   ██║
   ╚██████╔╝ ╚███╔███╔╝ ███████╗    ╚██████╔╝██████╔╝ ██║██║ ╚███║   ██║
    ╚═════╝   ╚══╝╚══╝  ╚══════╝     ╚═════╝ ╚═════╝  ╚═╝╚═╝  ╚══╝   ╚═╝

        Open Source Intelligence Framework v2.0
        Advanced Reconnaissance & Analysis Suite
```

</div>

## 📋 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Fitur Utama](#-fitur-utama)
- [Persyaratan Sistem](#-persyaratan-sistem)
- [Instalasi](#-instalasi)
- [Konfigurasi](#-konfigurasi)
- [Cara Penggunaan](#-cara-penggunaan)
- [Modul-Modul](#-modul-modul)
- [API Keys (Opsional)](#-api-keys-opsional)
- [Output dan Laporan](#-output-dan-laporan)
- [Troubleshooting](#-troubleshooting)
- [Kontribusi](#-kontribusi)
- [Legal & Etika](#%EF%B8%8F-legal--etika)
- [Kontak Developer](#-kontak-developer)
- [Lisensi](#-lisensi)

## 🎯 Tentang Proyek

**OWL OSINT** adalah framework Open Source Intelligence (OSINT) yang komprehensif dan mudah digunakan. Dibangun dengan Python, tool ini dirancang untuk membantu peneliti keamanan, investigator digital, dan profesional IT dalam mengumpulkan dan menganalisis informasi dari sumber-sumber publik.

### Mengapa OWL OSINT?

- 🚀 **Mudah Digunakan**: Interface CLI interaktif dengan menu yang intuitif
- 🎨 **UI Menarik**: Tampilan terminal berwarna dengan ASCII art yang eye-catching
- ⚡ **Cepat & Efisien**: Menggunakan async programming untuk kecepatan maksimal
- 🔧 **Modular**: Arsitektur yang clean dan mudah dikembangkan
- 📊 **Laporan Lengkap**: Generate laporan dalam format HTML yang profesional
- 🔒 **Aman & Legal**: Hanya mengakses informasi publik yang tersedia

## ✨ Fitur Utama

### 🔍 Username Hunter
Cari keberadaan username di lebih dari 30+ platform media sosial dan situs web populer:
- GitHub, Instagram, Twitter/X, Facebook, LinkedIn
- Reddit, YouTube, TikTok, Telegram, Discord
- Medium, Dev.to, Stack Overflow, GitLab
- Dan banyak lagi!

### 📧 Email OSINT
Analisis mendalam terhadap alamat email:
- Validasi format dan domain email
- Cek domain MX records
- Deteksi disposable email addresses
- Integrasi dengan Have I Been Pwned (dengan API key)
- Generate report lengkap

### 🖼️ Image Metadata Extractor
Ekstrak metadata EXIF dari gambar:
- Informasi kamera dan settings
- GPS coordinates (lokasi foto diambil)
- Tanggal dan waktu pengambilan
- Software editing yang digunakan
- Dan metadata teknis lainnya

### 🔔 Website Change Monitor
Monitor perubahan pada website:
- Track perubahan content website
- Alert otomatis saat ada perubahan
- Continuous monitoring mode
- Hash-based change detection
- History tracking

## 💻 Persyaratan Sistem

### Minimum Requirements:
- **OS**: Linux, macOS, atau Windows 10/11
- **Python**: 3.8 atau lebih tinggi
- **RAM**: 2GB (4GB recommended)
- **Storage**: 500MB ruang kosong
- **Internet**: Koneksi internet aktif

### Recommended Setup:
- **OS**: Ubuntu 20.04+ atau macOS 12+
- **Python**: 3.10+
- **RAM**: 4GB atau lebih
- **Storage**: 1GB ruang kosong

## 📥 Instalasi

### 1. Clone atau Download Repository

```bash
# Ekstrak file zip yang telah didownload
unzip osint_core_only.zip
cd osint_core_only
```

### 2. Install Python Dependencies

```bash
# Pastikan Python 3.8+ terinstall
python3 --version

# Install semua dependencies
pip3 install -r requirements.txt

# Atau gunakan virtual environment (recommended)
python3 -m venv venv
source venv/bin/activate  # Di Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Setup Environment Variables

```bash
# Copy file .env.example ke .env
cp .env.example .env

# Edit file .env dan masukkan API keys (opsional)
nano .env  # atau gunakan text editor favorit Anda
```

### 4. Verifikasi Instalasi

```bash
# Jalankan tool untuk pertama kali
python3 main.py
```

Jika berhasil, Anda akan melihat banner OWL OSINT yang keren! 🦉

## ⚙️ Konfigurasi

### File Konfigurasi Utama

#### `config.py`
File ini berisi semua konfigurasi dasar aplikasi:

```python
# Network Settings
MAX_WORKERS = 10          # Jumlah concurrent requests
REQUEST_TIMEOUT = 10      # Timeout per request (detik)

# Change Monitor
MONITOR_INTERVAL = 300    # Interval check (5 menit)
MAX_CONTENT_SIZE = 5MB    # Max ukuran content untuk monitor

# Logging
LOG_LEVEL = "INFO"        # Level logging (DEBUG/INFO/WARNING/ERROR)
```

#### `.env`
File untuk API keys (buat dari .env.example):

```bash
# Have I Been Pwned API Key
HIBP_API_KEY=your_api_key_here

# Hunter.io API Key
HUNTER_IO_KEY=your_api_key_here
```

### Struktur Direktori

```
osint_core_only/
├── main.py                 # Entry point aplikasi
├── config.py               # File konfigurasi
├── requirements.txt        # Python dependencies
├── .env.example           # Template environment variables
├── LICENSE                # Lisensi MIT
│
├── modules/               # Modul-modul OSINT
│   ├── __init__.py
│   ├── username_hunter.py
│   ├── email_osint.py
│   ├── image_metadata.py
│   └── change_monitor.py
│
├── utils/                 # Utility functions
│   ├── __init__.py
│   ├── database.py
│   ├── logger.py
│   └── report_generator.py
│
├── data/                  # Data files
│   ├── platforms.json     # Daftar platform untuk username search
│   ├── patterns.json      # Pattern matching rules
│   └── social_patterns_config.json
│
└── output/               # Output directory
    ├── reports/          # HTML reports
    ├── screenshots/      # Screenshots (jika ada)
    └── logs/            # Log files
```

## 🚀 Cara Penggunaan

### Quick Start

```bash
# Jalankan aplikasi
python3 main.py

# Atau dengan Python virtual environment
source venv/bin/activate
python main.py
```

### Menu Utama

Setelah menjalankan aplikasi, Anda akan melihat menu interaktif:

```
🔍 Username Hunter - Search username across platforms
📧 Email OSINT - Analyze email addresses
🖼️ Image Metadata - Extract EXIF data from images
🔔 Change Monitor - Monitor websites for changes
❌ Exit
```

Gunakan arrow keys (↑/↓) untuk navigasi dan Enter untuk memilih.

### Contoh Penggunaan

#### 1. Username Hunter

```bash
# Pilih: 🔍 Username Hunter
# Input: johndoe
# Output: Daftar semua platform dimana username "johndoe" ditemukan
```

**Tips**:
- Gunakan username tanpa spasi atau karakter khusus
- Username case-sensitive tergantung platform
- Proses bisa memakan waktu 10-30 detik

#### 2. Email OSINT

```bash
# Pilih: 📧 Email OSINT
# Input: example@domain.com
# Output: Validasi email, domain info, breach check (jika ada API key)
```

**Tips**:
- Pastikan format email valid
- API key HIBP diperlukan untuk breach checking
- Domain harus aktif untuk MX record check

#### 3. Image Metadata

```bash
# Pilih: 🖼️ Image Metadata
# Input: /path/to/image.jpg
# Output: EXIF data lengkap termasuk GPS jika ada
```

**Supported Formats**:
- JPG/JPEG
- PNG
- TIFF
- HEIC/HEIF (dengan library tambahan)

#### 4. Change Monitor

```bash
# Pilih: 🔔 Change Monitor

Sub-menu:
- Add new URL to monitor
- Check all monitored URLs now
- List monitored URLs
- Remove URL from monitoring
- Start continuous monitoring
```

**Tips**:
- Gunakan URL lengkap (https://...)
- Continuous monitoring bisa di-stop dengan Ctrl+C
- Default check interval: 5 menit

## 🧩 Modul-Modul

### Username Hunter (`modules/username_hunter.py`)

**Fungsi Utama**:
- Async HTTP requests untuk kecepatan
- Concurrent checking di 30+ platform
- Smart error handling
- Database tracking untuk history

**Platform yang Didukung**:
```
GitHub, Instagram, Twitter/X, Reddit, YouTube, TikTok,
Facebook, LinkedIn, Pinterest, Tumblr, Medium, Dev.to,
Twitch, Spotify, SoundCloud, Telegram, Discord, Patreon,
Behance, Dribbble, Stack Overflow, GitLab, Bitbucket,
HackerNews, Keybase, About.me, Blogger, WordPress,
Vimeo, Flickr
```

### Email OSINT (`modules/email_osint.py`)

**Fitur**:
- Format validation menggunakan regex
- DNS MX record checking
- Disposable email detection
- Domain reputation check
- HIBP breach checking (dengan API key)
- Detailed report generation

### Image Metadata (`modules/image_metadata.py`)

**Data yang Diekstrak**:
- Camera make & model
- Lens information
- ISO, Aperture, Shutter Speed
- GPS coordinates (Latitude, Longitude)
- Timestamp (original & modified)
- Software used
- Image dimensions & format

### Change Monitor (`modules/change_monitor.py`)

**Cara Kerja**:
- Content fetching via HTTP
- SHA-256 hash calculation
- Database persistence
- Scheduled checking
- Change detection & alerting

## 🔑 API Keys (Opsional)

Tool ini bisa digunakan **tanpa API keys**, namun untuk fungsionalitas penuh, disarankan untuk mendapatkan:

### Have I Been Pwned (HIBP)

**Untuk apa**: Check email breach database

**Cara mendapatkan**:
1. Kunjungi: https://haveibeenpwned.com/API/Key
2. Subscribe (ada free tier)
3. Copy API key
4. Paste ke file `.env`:
   ```
   HIBP_API_KEY=your_key_here
   ```

**Harga**: 
- Free: Limited requests
- Paid: $3.50/month untuk unlimited

### Hunter.io

**Untuk apa**: Email verification & validation

**Cara mendapatkan**:
1. Kunjungi: https://hunter.io/
2. Sign up (free account available)
3. Go to Dashboard → API
4. Copy API key
5. Paste ke file `.env`:
   ```
   HUNTER_IO_KEY=your_key_here
   ```

**Harga**:
- Free: 25 requests/month
- Starter: $49/month untuk 500 requests

## 📊 Output dan Laporan

### Report Generation

Setiap pencarian menghasilkan laporan HTML yang bisa dibuka di browser:

```
output/
├── reports/
│   ├── username_johndoe_20250127_143052.html
│   ├── email_example_20250127_143152.html
│   └── image_metadata_20250127_143252.html
```

### Database

Tool menyimpan history di SQLite database:

```
osint_data.db
├── username_searches
├── email_searches
├── monitored_urls
└── change_history
```

**Query Database**:
```bash
sqlite3 osint_data.db
> SELECT * FROM username_searches;
> .exit
```

### Logs

Log files tersimpan di `output/logs/`:

```
output/logs/
├── osint_2025-01-27.log
├── osint_2025-01-28.log
└── osint_2025-01-29.log
```

## 🔧 Troubleshooting

### Problem: "ModuleNotFoundError"

**Solusi**:
```bash
pip3 install -r requirements.txt --force-reinstall
```

### Problem: "Permission denied"

**Solusi**:
```bash
chmod +x main.py
sudo chown -R $USER:$USER osint_core_only/
```

### Problem: "Connection timeout"

**Penyebab**: Internet lambat atau firewall

**Solusi**:
```python
# Edit config.py
REQUEST_TIMEOUT = 30  # Increase timeout
```

### Problem: "Too many requests"

**Penyebab**: Rate limiting dari platform

**Solusi**:
```python
# Edit config.py
MAX_WORKERS = 5  # Reduce concurrent requests
```

### Problem: Database locked

**Solusi**:
```bash
# Close semua instance yang running
pkill -f main.py

# Atau hapus lock file
rm -f osint_data.db-journal
```

## 🤝 Kontribusi

Kontribusi sangat welcome! Berikut cara berkontribusi:

### Reporting Bugs

1. Check existing issues di GitHub
2. Buat issue baru dengan detail:
   - OS dan Python version
   - Error message lengkap
   - Steps to reproduce

### Feature Requests

1. Fork repository
2. Buat branch baru: `git checkout -b feature/AmazingFeature`
3. Commit changes: `git commit -m 'Add AmazingFeature'`
4. Push ke branch: `git push origin feature/AmazingFeature`
5. Buat Pull Request

### Coding Guidelines

- Follow PEP 8 style guide
- Add docstrings untuk functions
- Write unit tests untuk fitur baru
- Update dokumentasi

## ⚖️ Legal & Etika

### ⚠️ PENTING - DISCLAIMER

Tool ini dibuat **HANYA untuk tujuan edukasi dan research yang legal**. 

### Aturan Penggunaan:

✅ **BOLEH digunakan untuk**:
- Security research yang legal
- Investigasi dengan proper authorization
- Educational purposes
- Personal privacy audit
- Open source intelligence gathering (legally)

❌ **TIDAK BOLEH digunakan untuk**:
- Harassment atau stalking
- Unauthorized access ke sistem
- Illegal surveillance
- Privacy invasion
- Cyberbullying
- Identity theft
- Doxxing

### Tanggung Jawab Pengguna

- User bertanggung jawab atas penggunaan tool ini
- Selalu patuhi hukum setempat
- Hormati privacy orang lain
- Dapatkan authorization sebelum investigate
- Gunakan hanya pada public information

### Developer Disclaimer

Developer **TIDAK bertanggung jawab** atas:
- Misuse atau abuse dari tool ini
- Legal consequences dari penggunaan
- Damage atau kerugian yang ditimbulkan
- Violations of terms of service

## 📞 Kontak Developer

Butuh bantuan atau ada pertanyaan?

### Developer Information

**Developer**: AZM  
**Telegram**: [@azm101222](https://t.me/azm101222)  
**Email**: Available via Telegram

### Bantuan & Support

Untuk bantuan teknis:
1. Baca dokumentasi ini terlebih dahulu
2. Check [Troubleshooting](#-troubleshooting) section
3. Contact via Telegram untuk support langsung

### Donasi & Sponsorship

Jika tool ini membantu Anda, pertimbangkan untuk:
- ⭐ Star repository di GitHub
- 🐛 Report bugs dan contribute
- ☕ Buy developer a coffee (info via Telegram)

## 📄 Lisensi

Project ini menggunakan **MIT License** - lihat file [LICENSE](LICENSE) untuk detail.

### MIT License Summary:

✅ **Permissions**:
- Commercial use
- Modification
- Distribution
- Private use

⚠️ **Conditions**:
- License and copyright notice must be included

❌ **Limitations**:
- No liability
- No warranty

---

## 🎓 Resources & Learning

### Recommended Reading:
- [OSINT Framework](https://osintframework.com/)
- [Bellingcat's Online Investigation Toolkit](https://www.bellingcat.com/)
- [SANS OSINT Summit](https://www.sans.org/cyber-security-courses/open-source-intelligence-gathering/)

### Similar Tools:
- Sherlock - Username search tool
- theHarvester - Email & subdomain discovery
- Recon-ng - Full-featured reconnaissance framework
- Maltego - Professional OSINT platform

---

## 🆕 Changelog

### Version 2.0 (Current)
- ✨ Beautiful ASCII owl banner
- 🎨 Enhanced purple/blue theme UI
- ⚡ Async username hunting
- 📊 HTML report generation
- 🗄️ SQLite database integration
- 🔔 Website change monitoring
- 📧 Advanced email OSINT
- 🖼️ EXIF metadata extraction

### Version 1.0
- 🔍 Basic username search
- 📧 Simple email validation
- 📝 Text-based reports

---

## 🙏 Acknowledgments

Special thanks to:
- Python community
- OSINT framework contributors
- All the open source libraries used
- Security researchers worldwide
- Everyone who contributed to this project

---

## 📈 Stats & Roadmap

### Current Stats:
- 30+ supported platforms
- 4 main modules
- 100% Python
- MIT licensed

### Upcoming Features:
- [ ] Phone number OSINT
- [ ] IP address geolocation
- [ ] Blockchain address tracking
- [ ] Social media post scraping
- [ ] PDF report generation
- [ ] API endpoint
- [ ] Web interface
- [ ] Docker support

---

<div align="center">

**Made with ❤️ by AZM**

*"Information is power, but knowledge is wisdom"*

[⬆ Back to top](#-owl-osint---open-source-intelligence-framework)

</div>
