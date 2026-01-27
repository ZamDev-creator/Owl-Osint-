# 📥 Panduan Instalasi OWL OSINT

Dokumen ini menjelaskan langkah-langkah detail untuk menginstall OWL OSINT di berbagai sistem operasi.

## Daftar Isi

- [Persiapan](#persiapan)
- [Instalasi di Linux](#instalasi-di-linux)
- [Instalasi di macOS](#instalasi-di-macos)
- [Instalasi di Windows](#instalasi-di-windows)
- [Instalasi dengan Virtual Environment](#instalasi-dengan-virtual-environment)
- [Instalasi dengan Docker](#instalasi-dengan-docker-coming-soon)
- [Verifikasi Instalasi](#verifikasi-instalasi)
- [Troubleshooting](#troubleshooting)

---

## Persiapan

### Cek Versi Python

Pastikan Python 3.8 atau lebih tinggi terinstall di sistem Anda.

```bash
python3 --version
# atau
python --version
```

Output yang diharapkan: `Python 3.8.x` atau lebih tinggi.

### Download OWL OSINT

1. Download file `osint_core_only.zip`
2. Ekstrak ke direktori pilihan Anda

```bash
unzip osint_core_only.zip
cd osint_core_only
```

---

## Instalasi di Linux

### Ubuntu/Debian

#### 1. Update System Packages

```bash
sudo apt update
sudo apt upgrade -y
```

#### 2. Install Python dan Dependencies

```bash
# Install Python 3 dan pip
sudo apt install python3 python3-pip python3-venv -y

# Install dependencies sistem (jika diperlukan)
sudo apt install build-essential libssl-dev libffi-dev python3-dev -y
```

#### 3. Install Python Dependencies

```bash
# Masuk ke direktori project
cd osint_core_only

# Install requirements
pip3 install -r requirements.txt

# Atau dengan sudo jika ada error permission
sudo pip3 install -r requirements.txt
```

#### 4. Setup Environment Variables

```bash
# Copy template .env
cp .env.example .env

# Edit file .env (opsional - untuk API keys)
nano .env
```

#### 5. Set Permission

```bash
chmod +x main.py
chmod -R 755 modules/ utils/ data/
```

#### 6. Jalankan Aplikasi

```bash
python3 main.py
```

### Fedora/CentOS/RHEL

#### 1. Install Python dan Pip

```bash
# Fedora
sudo dnf install python3 python3-pip -y

# CentOS/RHEL
sudo yum install python3 python3-pip -y
```

#### 2. Install Dependencies

```bash
cd osint_core_only
pip3 install -r requirements.txt --user
```

#### 3. Setup dan Jalankan

```bash
cp .env.example .env
python3 main.py
```

### Arch Linux

```bash
# Install Python
sudo pacman -S python python-pip

# Install dependencies
cd osint_core_only
pip install -r requirements.txt

# Setup dan jalankan
cp .env.example .env
python main.py
```

---

## Instalasi di macOS

### Method 1: Homebrew (Recommended)

#### 1. Install Homebrew (jika belum ada)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### 2. Install Python

```bash
brew install python3
```

#### 3. Install Dependencies

```bash
cd osint_core_only
pip3 install -r requirements.txt
```

#### 4. Setup dan Jalankan

```bash
cp .env.example .env
python3 main.py
```

### Method 2: Python.org Installer

#### 1. Download Python

- Kunjungi https://www.python.org/downloads/macos/
- Download installer untuk macOS
- Install seperti biasa

#### 2. Install Dependencies

```bash
cd osint_core_only
pip3 install -r requirements.txt
```

#### 3. Setup dan Jalankan

```bash
cp .env.example .env
python3 main.py
```

---

## Instalasi di Windows

### Method 1: Menggunakan Python.org Installer

#### 1. Download dan Install Python

1. Kunjungi https://www.python.org/downloads/windows/
2. Download "Windows installer (64-bit)"
3. Jalankan installer
4. **PENTING**: Centang "Add Python to PATH"
5. Click "Install Now"

#### 2. Verifikasi Instalasi

Buka Command Prompt atau PowerShell:

```cmd
python --version
pip --version
```

#### 3. Install Dependencies

```cmd
cd osint_core_only
pip install -r requirements.txt
```

Jika error, coba:

```cmd
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

#### 4. Setup Environment Variables

```cmd
copy .env.example .env
notepad .env
```

Edit file `.env` dengan API keys Anda (opsional).

#### 5. Jalankan Aplikasi

```cmd
python main.py
```

### Method 2: Menggunakan Anaconda

#### 1. Install Anaconda

- Download dari: https://www.anaconda.com/download
- Install seperti biasa

#### 2. Buat Environment Baru

```cmd
conda create -n osint python=3.10
conda activate osint
```

#### 3. Install Dependencies

```cmd
cd osint_core_only
pip install -r requirements.txt
```

#### 4. Jalankan

```cmd
python main.py
```

---

## Instalasi dengan Virtual Environment

### Mengapa Menggunakan Virtual Environment?

- Isolasi dependencies per project
- Avoid conflicts dengan system Python
- Mudah manage multiple projects
- Best practice dalam Python development

### Linux/macOS

```bash
# Masuk ke direktori project
cd osint_core_only

# Buat virtual environment
python3 -m venv venv

# Aktifkan virtual environment
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Setup .env
cp .env.example .env

# Jalankan aplikasi
python main.py

# Deaktivasi saat selesai
deactivate
```

### Windows (Command Prompt)

```cmd
cd osint_core_only
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
copy .env.example .env
python main.py
deactivate
```

### Windows (PowerShell)

```powershell
cd osint_core_only
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
copy .env.example .env
python main.py
deactivate
```

**Note**: Jika PowerShell error "execution policy", jalankan:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

---

## Instalasi dengan Docker (Coming Soon)

Docker installation guide akan ditambahkan di versi mendatang.

Sementara ini, Anda bisa membuat Dockerfile sendiri:

```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "main.py"]
```

```bash
docker build -t owl-osint .
docker run -it owl-osint
```

---

## Verifikasi Instalasi

### Test Import Modules

```python
python3 -c "import aiohttp, requests, pyfiglet; print('All modules imported successfully!')"
```

### Check Database

```bash
ls -lh osint_data.db
```

Database file harus dibuat otomatis saat pertama kali run.

### Check Directories

```bash
ls -la output/
# Harus ada: reports/, screenshots/, logs/
```

### Run Quick Test

```bash
python3 main.py
# Pilih "Exit" untuk memastikan aplikasi bisa start
```

---

## Troubleshooting

### Problem: "pip: command not found"

**Linux**:
```bash
sudo apt install python3-pip
# atau
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```

**macOS**:
```bash
python3 -m ensurepip --upgrade
```

**Windows**:
- Reinstall Python dengan centang "Add to PATH"

### Problem: "Permission denied" (Linux/macOS)

```bash
# Install dengan --user flag
pip3 install -r requirements.txt --user

# Atau fix ownership
sudo chown -R $USER:$USER .
```

### Problem: SSL Certificate Error

```bash
# Linux
sudo apt install ca-certificates

# macOS
pip3 install --upgrade certifi

# Windows
pip install python-certifi-win32
```

### Problem: "ModuleNotFoundError" setelah install

```bash
# Clear pip cache dan reinstall
pip3 cache purge
pip3 install -r requirements.txt --force-reinstall
```

### Problem: Encoding Error di Windows

```cmd
# Set UTF-8 encoding
chcp 65001
python main.py
```

Atau tambahkan di awal script:

```python
import sys
import io
sys.stdout = io.TextIOWrapper(sys.stdout.buffer, encoding='utf-8')
```

### Problem: Virtual Environment Not Activating

**Linux/macOS**:
```bash
# Pastikan ada execute permission
chmod +x venv/bin/activate

# Atau gunakan full path
source /full/path/to/venv/bin/activate
```

**Windows PowerShell**:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Problem: Pip Install Sangat Lambat

```bash
# Gunakan mirror server terdekat
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

### Problem: Can't Create Database

```bash
# Check write permission
touch test.db
# Jika error, fix permission:
chmod 755 .
```

---

## Post-Installation

### Optional: Add to PATH (Linux/macOS)

Buat alias untuk mudah run dari mana saja:

```bash
# Tambahkan ke ~/.bashrc atau ~/.zshrc
alias owl-osint='cd /path/to/osint_core_only && python3 main.py'

# Reload shell
source ~/.bashrc
```

### Optional: Create Desktop Shortcut (Windows)

1. Right-click di desktop → New → Shortcut
2. Location: `C:\Python310\python.exe "C:\path\to\osint_core_only\main.py"`
3. Name: "OWL OSINT"

### Optional: Setup API Keys

Edit file `.env`:

```bash
nano .env  # Linux/macOS
notepad .env  # Windows
```

Tambahkan:

```
HIBP_API_KEY=your_hibp_key_here
HUNTER_IO_KEY=your_hunter_key_here
```

---

## Update OWL OSINT

Untuk update ke versi terbaru:

```bash
# Backup database dan konfigurasi
cp osint_data.db osint_data.db.backup
cp .env .env.backup

# Download versi baru
# Ekstrak dan replace files

# Restore konfigurasi
cp .env.backup .env
cp osint_data.db.backup osint_data.db

# Update dependencies
pip3 install -r requirements.txt --upgrade
```

---

## Uninstall

Untuk menghapus OWL OSINT:

```bash
# Hapus virtual environment (jika ada)
rm -rf venv/

# Hapus direktori project
cd ..
rm -rf osint_core_only/

# Hapus dependencies (opsional)
# Jika menggunakan virtual env, sudah terhapus
# Jika global install:
pip3 uninstall -r requirements.txt -y
```

---

## Bantuan Lebih Lanjut

Jika masih ada masalah:

1. Baca [README.md](README.md)
2. Check [FAQ.md](FAQ.md)
3. Contact developer: [@azm101222](https://t.me/azm101222)

---

**Happy Hunting! 🦉**

Developer: AZM | Telegram: @azm101222
