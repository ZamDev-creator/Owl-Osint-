# Changelog

All notable changes to OWL OSINT project akan didokumentasikan di file ini.

Format berdasarkan [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
dan project ini mengikuti [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2025-01-27

### 🎉 Initial Release - v2.0

Peluncuran versi pertama OWL OSINT Framework dengan fitur-fitur lengkap.

### ✨ Added

#### Core Features
- 🔍 **Username Hunter**: Search username across 30+ platforms
  - Async HTTP requests untuk kecepatan maksimal
  - Support untuk GitHub, Instagram, Twitter, LinkedIn, Reddit, dll
  - Database tracking untuk search history
  - Concurrent checking dengan rate limiting

- 📧 **Email OSINT**: Comprehensive email analysis
  - Email format validation dengan regex
  - DNS MX record verification
  - Disposable email detection
  - Have I Been Pwned integration (dengan API key)
  - Hunter.io integration (opsional)
  - Detailed HTML reports

- 🖼️ **Image Metadata Extractor**: EXIF data extraction
  - Support untuk JPEG, TIFF, PNG formats
  - Camera information extraction
  - GPS coordinates dengan Google Maps integration
  - Photo settings (ISO, aperture, shutter speed)
  - Datetime metadata
  - Software dan edit history detection
  - Metadata removal tool

- 🔔 **Change Monitor**: Website change detection
  - SHA-256 hash-based change detection
  - Multiple URL monitoring
  - Continuous monitoring mode
  - Change history tracking
  - Alert system

#### User Interface
- 🎨 Beautiful ASCII owl banner dengan purple/blue theme
- Interactive CLI dengan questionary
- Color-coded output dengan termcolor
- Table formatting dengan tabulate
- Progress indicators dengan tqdm
- Clear navigation menu

#### Database & Storage
- 🗄️ SQLite database untuk persistence
- Dedicated tables untuk each module:
  - username_searches
  - email_searches
  - monitored_urls
  - change_history
- Automatic schema creation
- Query optimization

#### Reporting
- 📊 HTML report generation dengan Jinja2 templates
- Professional styling dengan CSS
- Export functionality
- Visual charts dengan matplotlib
- Timestamp tracking
- Metadata preservation

#### Configuration
- ⚙️ Flexible configuration file (config.py)
- Environment variables support (.env)
- Customizable timeouts dan limits
- Network settings (workers, timeout, user agent)
- Logging configuration
- Path management

#### Documentation
- 📖 Comprehensive README.md
- 📥 Detailed INSTALLATION.md guide
- 👥 Complete USER_GUIDE.md
- 🔌 API_REFERENCE.md untuk developers
- 📝 CHANGELOG.md (this file)
- ⚖️ MIT License dengan disclaimer

### 🔧 Technical Details

#### Dependencies
- aiohttp==3.9.1 - Async HTTP client
- requests==2.31.0 - HTTP library
- beautifulsoup4==4.12.2 - HTML parsing
- pillow==10.1.0 - Image processing
- piexif==1.1.3 - EXIF manipulation
- questionary==2.0.1 - Interactive prompts
- termcolor==2.4.0 - Terminal colors
- pyfiglet==1.0.2 - ASCII art
- tabulate==0.9.0 - Table formatting
- python-dotenv==1.0.0 - Environment variables
- jinja2==3.1.2 - Template engine
- matplotlib==3.8.2 - Plotting
- nest-asyncio==1.6.0 - Async loop patching

#### Architecture
- Modular design dengan separation of concerns
- Async/await pattern untuk performance
- Database abstraction layer
- Centralized logging
- Configuration management
- Error handling dan recovery

#### Platform Support
- ✅ Linux (Ubuntu, Debian, Fedora, Arch)
- ✅ macOS (10.15+)
- ✅ Windows (10/11)
- Python 3.8+ required

### 📋 Known Issues

- None reported yet (initial release)

### 🔐 Security

- API keys stored in .env file (not committed)
- Secure password handling
- Rate limiting untuk prevent abuse
- Input validation
- SQL injection prevention
- XSS protection in reports

### 🎯 Developer Info

- **Developer**: AZM
- **Contact**: Telegram [@azm101222](https://t.me/azm101222)
- **License**: MIT
- **Repository**: GitHub (link TBA)

---

## [Unreleased]

### 🚀 Planned Features

#### v2.1.0 (Q1 2025)
- [ ] Phone number OSINT module
- [ ] IP address geolocation
- [ ] Domain WHOIS lookup
- [ ] SSL certificate analysis
- [ ] Email notifications untuk change monitor
- [ ] Webhook integration
- [ ] PDF report generation
- [ ] Export ke JSON/CSV

#### v2.2.0 (Q2 2025)
- [ ] Social media post scraper
- [ ] Blockchain address tracking
- [ ] Dark web search capabilities
- [ ] Facial recognition integration
- [ ] OCR text extraction
- [ ] Bulk processing mode
- [ ] API endpoint (REST)
- [ ] Rate limit management

#### v3.0.0 (Q3 2025)
- [ ] Web interface (Flask/FastAPI)
- [ ] User authentication
- [ ] Multi-user support
- [ ] Dashboard dengan analytics
- [ ] Scheduled tasks
- [ ] Docker containerization
- [ ] Cloud deployment guides
- [ ] Mobile app (React Native)

### 🔧 Improvements Planned
- [ ] Performance optimization
- [ ] Better error messages
- [ ] More comprehensive tests
- [ ] CI/CD pipeline
- [ ] Automated releases
- [ ] Internationalization (i18n)
- [ ] Plugin system
- [ ] Theme customization

---

## Version History

### Semantic Versioning

Format: MAJOR.MINOR.PATCH

- **MAJOR**: Incompatible API changes
- **MINOR**: New features (backwards compatible)
- **PATCH**: Bug fixes (backwards compatible)

### Release Schedule

- Major releases: Yearly
- Minor releases: Quarterly
- Patch releases: As needed

---

## How to Upgrade

### From v1.x to v2.0

Tidak ada v1.x (ini adalah initial release).

### General Upgrade Process

```bash
# 1. Backup data
cp osint_data.db osint_data.db.backup
cp .env .env.backup

# 2. Download new version
# Extract files

# 3. Restore config
cp .env.backup .env

# 4. Update dependencies
pip install -r requirements.txt --upgrade

# 5. Run migration (if needed)
python migrate.py

# 6. Test
python main.py
```

---

## Support & Feedback

### Reporting Issues

Jika menemukan bug atau memiliki feature request:

1. Check [Known Issues](#-known-issues)
2. Search existing GitHub issues
3. Create new issue dengan template
4. Contact developer via Telegram: [@azm101222](https://t.me/azm101222)

### Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) untuk guidelines.

### Recognition

Semua contributors akan disebutkan dalam:
- Release notes
- CONTRIBUTORS.md file
- Project README

---

## License

OWL OSINT is released under the MIT License.
See [LICENSE](LICENSE) file untuk details.

---

## Acknowledgments

Terima kasih kepada:
- Python community
- Open source contributors
- OSINT framework developers
- Security researchers
- Beta testers
- Everyone who provided feedback

---

**Developer**: AZM  
**Contact**: [@azm101222](https://t.me/azm101222)  
**Version**: 2.0.0  
**Last Updated**: January 27, 2025

---

*Keep checking this file untuk updates dan new releases!* 🦉
