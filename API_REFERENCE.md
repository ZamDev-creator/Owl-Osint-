# 🔌 API Reference - OWL OSINT

Dokumentasi lengkap untuk developer yang ingin mengintegrasikan atau extend OWL OSINT.

## Daftar Isi

- [Architecture Overview](#architecture-overview)
- [Core Modules](#core-modules)
- [Database Schema](#database-schema)
- [Configuration](#configuration)
- [Extending Functionality](#extending-functionality)
- [API Integration](#api-integration)
- [Code Examples](#code-examples)

---

## Architecture Overview

### Directory Structure

```
osint_core_only/
├── main.py                      # Entry point
├── config.py                    # Configuration
├── patch_eventloop.py           # Async patch untuk Windows
├── requirements.txt             # Dependencies
│
├── modules/                     # Core OSINT modules
│   ├── __init__.py
│   ├── username_hunter.py      # Username search functionality
│   ├── email_osint.py          # Email analysis
│   ├── image_metadata.py       # EXIF extraction
│   └── change_monitor.py       # Website monitoring
│
├── utils/                       # Utility functions
│   ├── __init__.py
│   ├── database.py             # SQLite operations
│   ├── logger.py               # Logging configuration
│   └── report_generator.py     # HTML report generation
│
├── data/                        # Data files
│   ├── platforms.json          # Platform definitions
│   ├── patterns.json           # Pattern matching rules
│   └── social_patterns_config.json
│
└── output/                      # Output directory
    ├── reports/                # Generated reports
    ├── screenshots/            # Screenshots (if any)
    └── logs/                   # Application logs
```

### Technology Stack

- **Language**: Python 3.8+
- **Async Framework**: asyncio, aiohttp
- **Database**: SQLite3
- **CLI**: questionary, click
- **Visualization**: matplotlib, termcolor
- **HTTP Requests**: requests, aiohttp
- **Image Processing**: Pillow, piexif

---

## Core Modules

### 1. Username Hunter

**File**: `modules/username_hunter.py`

#### Class: `UsernameHunter`

```python
class UsernameHunter:
    """
    Async username search across multiple platforms.
    
    Attributes:
        platforms (list): List of platform definitions
        db (DatabaseManager): Database connection
        session (aiohttp.ClientSession): Async HTTP session
    """
    
    def __init__(self):
        """Initialize username hunter with platform data and database."""
        
    async def hunt(self, username: str) -> list:
        """
        Search for username across all platforms.
        
        Args:
            username (str): Username to search for
            
        Returns:
            list: List of dicts with platform results
                [{
                    'platform': str,
                    'url': str,
                    'found': bool,
                    'status_code': int,
                    'response_time': float
                }, ...]
        """
        
    async def check_platform(self, username: str, platform: dict) -> dict:
        """
        Check single platform for username.
        
        Args:
            username (str): Username to check
            platform (dict): Platform definition
                {
                    'name': str,
                    'url': str (with {} placeholder),
                    'error_type': 'status_code' | 'message'
                }
                
        Returns:
            dict: Result with status and metadata
        """
```

#### Usage Example

```python
from modules.username_hunter import UsernameHunter
import asyncio

async def search_username():
    hunter = UsernameHunter()
    results = await hunter.hunt("johndoe")
    
    for result in results:
        if result['found']:
            print(f"Found on {result['platform']}: {result['url']}")

# Run
asyncio.run(search_username())
```

#### Adding New Platform

Edit `data/platforms.json`:

```json
{
  "name": "NewPlatform",
  "url": "https://newplatform.com/user/{}",
  "error_type": "status_code"
}
```

---

### 2. Email OSINT

**File**: `modules/email_osint.py`

#### Class: `EmailOSINT`

```python
class EmailOSINT:
    """
    Email analysis and validation toolkit.
    
    Features:
        - Format validation
        - Domain verification
        - MX record checking
        - Disposable email detection
        - HIBP breach checking (with API key)
    """
    
    def __init__(self):
        """Initialize with API keys from config."""
        
    def validate_email(self, email: str) -> dict:
        """
        Validate email format and domain.
        
        Args:
            email (str): Email address to validate
            
        Returns:
            dict: Validation results
                {
                    'valid_format': bool,
                    'username': str,
                    'domain': str,
                    'has_mx': bool,
                    'mx_records': list,
                    'is_disposable': bool
                }
        """
        
    def check_breaches(self, email: str) -> dict:
        """
        Check email against HIBP database.
        
        Requires: HIBP_API_KEY in .env
        
        Args:
            email (str): Email to check
            
        Returns:
            dict: Breach information
                {
                    'breached': bool,
                    'breach_count': int,
                    'breaches': [
                        {
                            'name': str,
                            'date': str,
                            'compromised_data': list
                        }
                    ]
                }
        """
        
    def get_mx_records(self, domain: str) -> list:
        """
        Get MX records for domain.
        
        Args:
            domain (str): Domain to query
            
        Returns:
            list: MX records with priority
                [('mx1.domain.com', 10), ('mx2.domain.com', 20)]
        """
```

#### Usage Example

```python
from modules.email_osint import EmailOSINT

osint = EmailOSINT()

# Validate email
result = osint.validate_email("test@example.com")
print(f"Valid: {result['valid_format']}")
print(f"MX Records: {result['mx_records']}")

# Check breaches (requires API key)
breaches = osint.check_breaches("test@example.com")
if breaches['breached']:
    print(f"Found in {breaches['breach_count']} breaches!")
```

---

### 3. Image Metadata

**File**: `modules/image_metadata.py`

#### Class: `ImageMetadata`

```python
class ImageMetadata:
    """
    EXIF metadata extraction from images.
    
    Supported formats:
        - JPEG/JPG (full support)
        - TIFF (full support)
        - PNG (limited)
        - RAW (with additional libraries)
    """
    
    def __init__(self):
        """Initialize metadata extractor."""
        
    def extract_metadata(self, image_path: str) -> dict:
        """
        Extract all metadata from image.
        
        Args:
            image_path (str): Path to image file
            
        Returns:
            dict: Complete metadata
                {
                    'file_info': {
                        'filename': str,
                        'size': int,
                        'format': str,
                        'dimensions': tuple
                    },
                    'camera': {
                        'make': str,
                        'model': str,
                        'lens': str,
                        'serial': str
                    },
                    'settings': {
                        'iso': int,
                        'aperture': float,
                        'shutter_speed': str,
                        'focal_length': str
                    },
                    'gps': {
                        'latitude': float,
                        'longitude': float,
                        'altitude': float,
                        'timestamp': str
                    },
                    'datetime': {
                        'original': str,
                        'digitized': str,
                        'modified': str
                    },
                    'software': str
                }
        """
        
    def get_gps_coordinates(self, exif_data: dict) -> dict:
        """
        Extract and convert GPS coordinates.
        
        Args:
            exif_data (dict): Raw EXIF data
            
        Returns:
            dict: GPS information
                {
                    'latitude': float,
                    'longitude': float,
                    'altitude': float,
                    'maps_url': str
                }
        """
        
    def remove_metadata(self, image_path: str, output_path: str) -> bool:
        """
        Remove all EXIF metadata from image.
        
        Args:
            image_path (str): Input image
            output_path (str): Output path
            
        Returns:
            bool: Success status
        """
```

#### Usage Example

```python
from modules.image_metadata import ImageMetadata

extractor = ImageMetadata()

# Extract metadata
metadata = extractor.extract_metadata("photo.jpg")

if metadata['gps']:
    lat = metadata['gps']['latitude']
    lon = metadata['gps']['longitude']
    print(f"Location: {lat}, {lon}")
    
# Remove metadata
extractor.remove_metadata("photo.jpg", "photo_clean.jpg")
```

---

### 4. Change Monitor

**File**: `modules/change_monitor.py`

#### Class: `ChangeMonitor`

```python
class ChangeMonitor:
    """
    Website content monitoring and change detection.
    
    Features:
        - SHA-256 hash-based detection
        - Scheduled monitoring
        - Change history tracking
        - Alert system
    """
    
    def __init__(self):
        """Initialize with database connection."""
        
    def add_url(self, url: str) -> bool:
        """
        Add URL to monitoring list.
        
        Args:
            url (str): URL to monitor
            
        Returns:
            bool: Success status
        """
        
    def check_url(self, url: str) -> dict:
        """
        Check single URL for changes.
        
        Args:
            url (str): URL to check
            
        Returns:
            dict: Check results
                {
                    'url': str,
                    'changed': bool,
                    'old_hash': str,
                    'new_hash': str,
                    'timestamp': str
                }
        """
        
    def check_all(self) -> list:
        """
        Check all monitored URLs.
        
        Returns:
            list: Changed URLs
                [{'url': str, 'timestamp': str}, ...]
        """
        
    def monitor_continuously(self, interval: int = 300):
        """
        Start continuous monitoring.
        
        Args:
            interval (int): Check interval in seconds
        """
        
    def list_monitored_urls(self) -> list:
        """
        Get all monitored URLs.
        
        Returns:
            list: URLs with metadata
                [(id, url, hash, last_check, changed), ...]
        """
```

#### Usage Example

```python
from modules.change_monitor import ChangeMonitor

monitor = ChangeMonitor()

# Add URLs
monitor.add_url("https://example.com/news")
monitor.add_url("https://competitor.com/prices")

# Check for changes
changes = monitor.check_all()
for change in changes:
    print(f"Changed: {change['url']}")

# Start continuous monitoring (runs until Ctrl+C)
monitor.monitor_continuously(interval=600)  # 10 minutes
```

---

## Database Schema

**File**: `utils/database.py`

### Tables

#### username_searches

```sql
CREATE TABLE username_searches (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL,
    platform TEXT NOT NULL,
    found BOOLEAN NOT NULL,
    url TEXT,
    status_code INTEGER,
    response_time REAL,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

#### email_searches

```sql
CREATE TABLE email_searches (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    email TEXT NOT NULL,
    valid_format BOOLEAN,
    has_mx BOOLEAN,
    is_disposable BOOLEAN,
    breached BOOLEAN,
    breach_count INTEGER,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

#### monitored_urls

```sql
CREATE TABLE monitored_urls (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    url TEXT UNIQUE NOT NULL,
    content_hash TEXT NOT NULL,
    last_check DATETIME,
    changed BOOLEAN DEFAULT 0,
    check_count INTEGER DEFAULT 0
);
```

#### change_history

```sql
CREATE TABLE change_history (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    url TEXT NOT NULL,
    old_hash TEXT,
    new_hash TEXT,
    detected_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (url) REFERENCES monitored_urls(url)
);
```

### DatabaseManager Class

```python
class DatabaseManager:
    """
    SQLite database operations manager.
    """
    
    def __init__(self, db_path: str = None):
        """Initialize database connection."""
        
    def insert_username_search(self, data: dict):
        """Insert username search result."""
        
    def insert_email_search(self, data: dict):
        """Insert email search result."""
        
    def get_search_history(self, search_type: str) -> list:
        """Get search history by type."""
        
    def close(self):
        """Close database connection."""
```

---

## Configuration

**File**: `config.py`

### Environment Variables

```python
# API Keys (from .env file)
HIBP_API_KEY = os.getenv("HIBP_API_KEY", "")
HUNTER_IO_KEY = os.getenv("HUNTER_IO_KEY", "")
```

### Network Settings

```python
MAX_WORKERS = 10          # Concurrent request limit
REQUEST_TIMEOUT = 10      # Timeout per request (seconds)
USER_AGENT = "Mozilla/5.0 ..."  # HTTP User-Agent
```

### Paths

```python
BASE_DIR = Path(__file__).parent
DATA_DIR = BASE_DIR / "data"
OUTPUT_DIR = BASE_DIR / "output"
REPORTS_DIR = OUTPUT_DIR / "reports"
SCREENSHOTS_DIR = OUTPUT_DIR / "screenshots"
LOGS_DIR = OUTPUT_DIR / "logs"
DB_PATH = BASE_DIR / "osint_data.db"
```

### Monitoring

```python
MONITOR_INTERVAL = 300    # Default check interval (seconds)
MAX_CONTENT_SIZE = 5 * 1024 * 1024  # 5MB limit
```

### Logging

```python
LOG_LEVEL = "INFO"        # DEBUG | INFO | WARNING | ERROR
LOG_FORMAT = '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
```

---

## Extending Functionality

### Adding New OSINT Module

1. Create new file in `modules/`:

```python
# modules/phone_osint.py

class PhoneOSINT:
    """Phone number OSINT module."""
    
    def __init__(self):
        self.db = DatabaseManager()
        
    def analyze_phone(self, phone: str) -> dict:
        """Analyze phone number."""
        # Implementation
        return {
            'valid': True,
            'country': 'US',
            'carrier': 'Verizon',
            'type': 'mobile'
        }
```

2. Add to `modules/__init__.py`:

```python
from .phone_osint import PhoneOSINT
```

3. Integrate in `main.py`:

```python
from modules.phone_osint import PhoneOSINT

class OSINTSuite:
    def __init__(self):
        # ... existing code ...
        self.phone_osint = PhoneOSINT()
        
    def phone_analysis(self):
        """Phone OSINT interface."""
        # Implementation
```

### Adding New Platform

Edit `data/platforms.json`:

```json
{
  "name": "CustomPlatform",
  "url": "https://custom.com/profile/{}",
  "error_type": "status_code",
  "headers": {
    "Custom-Header": "value"
  }
}
```

### Custom Report Templates

```python
# utils/report_generator.py

def generate_custom_report(data: dict) -> str:
    """Generate custom HTML report."""
    
    template = """
    <!DOCTYPE html>
    <html>
    <head>
        <title>Custom Report</title>
        <style>
            /* Your CSS */
        </style>
    </head>
    <body>
        <h1>{{ title }}</h1>
        <!-- Your template -->
    </body>
    </html>
    """
    
    # Render with Jinja2
    from jinja2 import Template
    return Template(template).render(**data)
```

---

## API Integration

### External API Integration

#### HIBP Integration

```python
import requests

def check_hibp(email: str, api_key: str) -> dict:
    """Check Have I Been Pwned API."""
    
    url = f"https://haveibeenpwned.com/api/v3/breachedaccount/{email}"
    headers = {
        "hibp-api-key": api_key,
        "user-agent": "OWL-OSINT"
    }
    
    response = requests.get(url, headers=headers)
    
    if response.status_code == 200:
        return {
            'breached': True,
            'breaches': response.json()
        }
    elif response.status_code == 404:
        return {'breached': False}
    else:
        raise Exception(f"API Error: {response.status_code}")
```

#### Hunter.io Integration

```python
def verify_email_hunter(email: str, api_key: str) -> dict:
    """Verify email with Hunter.io."""
    
    url = "https://api.hunter.io/v2/email-verifier"
    params = {
        'email': email,
        'api_key': api_key
    }
    
    response = requests.get(url, params=params)
    data = response.json()
    
    return {
        'deliverable': data['data']['status'] == 'valid',
        'score': data['data']['score'],
        'sources': data['data']['sources']
    }
```

### REST API (Coming Soon)

Future version will include REST API:

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/api/username/<username>', methods=['GET'])
def api_username_search(username):
    """API endpoint for username search."""
    hunter = UsernameHunter()
    results = asyncio.run(hunter.hunt(username))
    return jsonify(results)

@app.route('/api/email/<email>', methods=['GET'])
def api_email_analysis(email):
    """API endpoint for email analysis."""
    osint = EmailOSINT()
    results = osint.validate_email(email)
    return jsonify(results)
```

---

## Code Examples

### Complete Username Search

```python
import asyncio
from modules.username_hunter import UsernameHunter
from utils.report_generator import ReportGenerator

async def main():
    # Initialize
    hunter = UsernameHunter()
    report_gen = ReportGenerator()
    
    # Search
    username = "johndoe"
    results = await hunter.hunt(username)
    
    # Filter found
    found = [r for r in results if r['found']]
    
    # Generate report
    report_path = report_gen.generate_username_report(
        username, 
        results
    )
    
    print(f"Found on {len(found)} platforms")
    print(f"Report: {report_path}")

asyncio.run(main())
```

### Email Analysis with Breach Check

```python
from modules.email_osint import EmailOSINT
import os

def analyze_email_complete(email: str):
    osint = EmailOSINT()
    
    # Validate
    validation = osint.validate_email(email)
    print(f"Format valid: {validation['valid_format']}")
    print(f"MX records: {validation['mx_records']}")
    
    # Check breaches (if API key available)
    if os.getenv('HIBP_API_KEY'):
        breaches = osint.check_breaches(email)
        if breaches['breached']:
            print(f"⚠️ Found in {breaches['breach_count']} breaches!")
            for breach in breaches['breaches']:
                print(f"  - {breach['name']} ({breach['date']})")

analyze_email_complete("test@example.com")
```

### Batch Username Search

```python
async def batch_username_search(usernames: list):
    hunter = UsernameHunter()
    
    all_results = {}
    for username in usernames:
        results = await hunter.hunt(username)
        found = [r for r in results if r['found']]
        all_results[username] = found
        
    return all_results

# Usage
usernames = ["user1", "user2", "user3"]
results = asyncio.run(batch_username_search(usernames))

for user, platforms in results.items():
    print(f"{user}: Found on {len(platforms)} platforms")
```

### Automated Change Monitoring

```python
from modules.change_monitor import ChangeMonitor
import schedule
import time

def monitor_job():
    monitor = ChangeMonitor()
    changes = monitor.check_all()
    
    if changes:
        # Send alert (email, webhook, etc.)
        for change in changes:
            print(f"⚠️ Change detected: {change['url']}")
            # send_alert(change)

# Schedule every 10 minutes
schedule.every(10).minutes.do(monitor_job)

while True:
    schedule.run_pending()
    time.sleep(60)
```

---

## Testing

### Unit Tests

```python
# tests/test_username_hunter.py

import unittest
from modules.username_hunter import UsernameHunter
import asyncio

class TestUsernameHunter(unittest.TestCase):
    
    def setUp(self):
        self.hunter = UsernameHunter()
    
    def test_hunt(self):
        results = asyncio.run(self.hunter.hunt("testuser"))
        self.assertIsInstance(results, list)
        self.assertGreater(len(results), 0)
    
    def test_invalid_username(self):
        results = asyncio.run(self.hunter.hunt(""))
        self.assertEqual(len(results), 0)

if __name__ == '__main__':
    unittest.main()
```

### Running Tests

```bash
python -m unittest discover tests/
```

---

## Contributing

### Code Style

- Follow PEP 8
- Use type hints
- Add docstrings
- Write unit tests

### Pull Request Process

1. Fork repository
2. Create feature branch
3. Make changes
4. Add tests
5. Update documentation
6. Submit PR

---

## Support & Contact

**Developer**: AZM  
**Telegram**: [@azm101222](https://t.me/azm101222)

For API questions, feature requests, or bug reports, please contact via Telegram.

---

**Last Updated**: January 2025  
**Version**: 2.0
