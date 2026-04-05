# Server Storage

![Platform](https://img.shields.io/badge/platform-linux-lightgrey.svg)
![Go](https://img.shields.io/badge/Go-1.24-blue.svg)

บริการ Storage Server สำหรับจัดเก็บและให้บริการไฟล์วิดีโอ รองรับการอัพโหลด/ดาวน์โหลดไฟล์ผ่าน HTTP พร้อมเชื่อมต่อ MongoDB สำหรับจัดการข้อมูล

## ✨ Features

- HTTP API สำหรับอัพโหลด/ดาวน์โหลดไฟล์
- เชื่อมต่อ MongoDB สำหรับจัดการข้อมูล storage
- รองรับ STORAGE_ID สำหรับระบุ storage server
- กำหนด path สำหรับจัดเก็บไฟล์ได้
- รองรับ x86_64 และ ARM64

## 📋 Requirements

- Linux (Ubuntu/Debian recommended)
- MongoDB

## 🚀 Quick Install (One-line)

```bash
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-storage-releases/main/install.sh | sudo -E bash -s -- \
    --port 8888 \
    --mongodb-uri "mongodb+srv://user:pass@host/dbname" \
    --storage-id "your-storage-id" \
    --storage-path "/home/files"
```

## 🛠️ Manual Installation

```bash
# Download install script
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-storage-releases/main/install.sh -o install.sh
chmod +x install.sh

# Install with default settings
sudo ./install.sh --mongodb-uri "mongodb+srv://user:pass@host/dbname"

# Install with custom settings
sudo ./install.sh \
    --port 8888 \
    --mongodb-uri "mongodb+srv://user:pass@host/dbname" \
    --storage-id "your-storage-id" \
    --storage-path "/home/files"
```

## 🗑️ Uninstall

```bash
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-storage-releases/main/install.sh | sudo -E bash -s -- \
    --uninstall
```

## ⚙️ Service Management

```bash
# Status
systemctl status server-storage

# Logs
journalctl -u server-storage -f

# Start / Stop / Restart
sudo systemctl start server-storage
sudo systemctl stop server-storage
sudo systemctl restart server-storage

# Enable / Disable on boot
sudo systemctl enable server-storage
sudo systemctl disable server-storage
```

## 📂 File Structure

```
/opt/server-storage/
├── server-storage          # Main binary (Go)
├── .env                    # Environment config
└── uploads/                # Upload directory
```

## 🔧 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `MONGODB_URI` | — | MongoDB connection string |
| `PORT` | `8888` | HTTP port |
| `STORAGE_ID` | — | Storage server identifier |
| `STORAGE_PATH` | `/home/files` | Path สำหรับจัดเก็บไฟล์ |

## 📋 Install Options

| Option | Default | Description |
|--------|---------|-------------|
| `-p, --port` | `8888` | HTTP port |
| `--mongodb-uri` | — | MongoDB connection string |
| `--storage-id` | — | Storage server identifier |
| `--storage-path` | `/home/files` | Path จัดเก็บไฟล์ |
| `--uninstall` | — | ลบทั้งหมด (binary, service, config) |
| `-h, --help` | — | แสดง help |

## 🔄 Update

```bash
# Re-run install script (will download latest binary & update config)
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-storage-releases/main/install.sh | sudo -E bash -s -- \
    --port 8888 \
    --mongodb-uri "mongodb+srv://user:pass@host/dbname" \
    --storage-id "your-storage-id" \
    --storage-path "/home/files"
```
