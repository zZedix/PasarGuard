<div align="center">
  <a href="https://github.com/PasarGuard/panel" target="_blank" rel="noopener noreferrer">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/PasarGuard/docs/raw/main/logos/PasarGuard-white-logo.png">
      <img width="160" height="160" src="https://github.com/PasarGuard/docs/raw/main/logos/PasarGuard-black-logo.png" alt="PasarGuard Logo">
    </picture>
  </a>
</div>

<div align="center">
  <h1>PasarGuard</h1>
  <p><strong>Unified GUI Censorship Resistant Solution</strong></p>
</div>

<div align="center">
  <a href="https://github.com/PasarGuard/panel/actions/workflows/build.yml" target="_blank">
    <img src="https://img.shields.io/github/actions/workflow/status/PasarGuard/panel/build.yml?style=flat-square&logo=github" alt="Build Status">
  </a>
  <a href="https://hub.docker.com/r/PasarGuard/panel" target="_blank">
    <img src="https://img.shields.io/docker/pulls/PasarGuard/panel?style=flat-square&logo=docker" alt="Docker Pulls">
  </a>
  <a href="https://github.com/PasarGuard/panel/blob/main/LICENSE" target="_blank">
    <img src="https://img.shields.io/github/license/PasarGuard/panel?style=flat-square" alt="License">
  </a>
  <a href="https://t.me/Pasar_Guard" target="_blank">
    <img src="https://img.shields.io/badge/telegram-group-blue?style=flat-square&logo=telegram" alt="Telegram Group">
  </a>
  <a href="https://github.com/PasarGuard/panel" target="_blank">
    <img src="https://img.shields.io/github/stars/PasarGuard/panel?style=social" alt="GitHub Stars">
  </a>
</div>

<div align="center">
  <p>
    <a href="./README.md">English</a> •
    <a href="./README-fa.md">فارسی</a> •
    <a href="./README-zh-cn.md">简体中文</a> •
    <a href="./README-ru.md">Русский</a>
  </p>
</div>

<div align="center">
  <a href="https://github.com/PasarGuard/panel" target="_blank" rel="noopener noreferrer">
    <img src="https://github.com/PasarGuard/docs/raw/master/screenshots/preview.png" alt="PasarGuard Dashboard Preview" width="600" height="auto">
  </a>
</div>

## Table of Contents

-   [Overview](#overview)
    -   [Why using PasarGuard?](#why-using-PasarGuard)
        -   [Features](#features)
-   [Installation guide](#installation-guide)
-   [Configuration](#configuration)
-   [Documentation](#documentation)
-   [API](#api)
-   [Backup](#backup)
-   [Telegram Bot](#telegram-bot)
-   [PasarGuard CLI](#PasarGuard-cli)
-   [PasarGuard Node](#node)
-   [Webhook notifications](#webhook-notifications)
-   [Donation](#donation)
-   [License](#license)
-   [Contributors](#contributors)

# Overview

PasarGuard is a proxy management tool that provides a simple and easy-to-use user interface for managing hundreds of proxy accounts powered by [Xray-core](https://github.com/XTLS/Xray-core) and built using Python and Reactjs.

## Why using PasarGuard?

PasarGuard is user-friendly, feature-rich and reliable. It lets you to create different proxies for your users without any complicated configuration. Using its built-in web UI, you are able to monitor, modify and limit users.

### Features

#### 🎯 **Core Features**
- **Built-in Web UI** - Modern, responsive dashboard
- **REST API** - Complete backend API for integration
- **Multi-Node Support** - Distributed infrastructure management
- **Multi-Protocol Support** - VMess, VLESS, Trojan, Shadowsocks

#### 👥 **User Management**
- **Multi-Protocol per User** - Single user, multiple protocols
- **Multi-User per Inbound** - Efficient resource utilization
- **Multi-Inbound per Port** - Fallback support
- **Traffic & Expiry Limits** - Flexible user restrictions
- **Periodic Limits** - Daily, weekly, monthly quotas

#### 🔗 **Subscription & Sharing**
- **Universal Subscription Links** - Compatible with V2RayNG, SingBox, Nekoray, Clash, ClashMeta
- **Auto-Generated Links** - Share links and QR codes
- **Custom Templates** - Configurable subscription formats

#### 🔧 **Advanced Features**
- **System Monitoring** - Real-time traffic statistics
- **Custom Xray Config** - Flexible configuration options
- **TLS & REALITY** - Modern security protocols
- **Telegram Bot** - Integrated management bot
- **CLI & TUI** - Command-line and terminal interfaces
- **Multi-Language** - International support
- **Multi-Admin** - Multiple administrator support (WIP)

# Installation Guide

> ⚠️ **Note**: The following commands will install pre-release versions (alpha/beta)

## Quick Install

Choose your preferred database:

### SQLite (Default)
```bash
sudo bash -c "$(curl -sL https://github.com/PasarGuard/scripts/raw/main/pasarguard.sh)" @ install --pre-release
```

### MySQL
```bash
sudo bash -c "$(curl -sL https://github.com/PasarGuard/scripts/raw/main/pasarguard.sh)" @ install --database mysql --pre-release
```

### MariaDB
```bash
sudo bash -c "$(curl -sL https://github.com/PasarGuard/scripts/raw/main/pasarguard.sh)" @ install --database mariadb --pre-release
```

### PostgreSQL
```bash
sudo bash -c "$(curl -sL https://github.com/PasarGuard/scripts/raw/main/pasarguard.sh)" @ install --database postgresql --pre-release
```

## Post-Installation

After installation completes:

### 📁 **File Locations**
- **Application files**: `/opt/pasarguard`
- **Configuration file**: `/opt/pasarguard/.env`
- **Data files**: `/var/lib/pasarguard`

### 🌐 **Access Dashboard**

#### Option 1: With Domain (Recommended)
1. [Obtain SSL certificate](https://PasarGuard.github.io/PasarGuard/en/examples/issue-ssl-certificate)
2. Access: `https://YOUR_DOMAIN:8000/dashboard/`

#### Option 2: SSH Port Forwarding (Testing)
```bash
ssh -L 8000:localhost:8000 user@serverip
```
Then open: `http://localhost:8000/dashboard/`

> ⚠️ **Note**: SSH method is for testing only - access is lost when terminal closes

### 👤 **Create Admin User**
```bash
pasarguard cli admin create --sudo
```

### 📖 **Get Help**
```bash
pasarguard --help
```

## Manual Installation (Advanced)

For developers who want to run from source code:

### Prerequisites
- Python >= 3.12.7
- Xray-core

### Step 1: Install Xray
```bash
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```

### Step 2: Clone & Setup
```bash
git clone https://github.com/PasarGuard/panel.git
cd PasarGuard
curl -LsSf https://astral.sh/uv/install.sh | sh
uv sync
```

### Step 3: Database Migration
```bash
uv run alembic upgrade head
```

### Step 4: Setup CLI (Optional)
```bash
sudo ln -s $(pwd)/PasarGuard-cli.py /usr/bin/pasarguard-cli
sudo chmod +x /usr/bin/pasarguard-cli
pasarguard-cli completion install
```

### Step 5: Configuration
```bash
cp .env.example .env
nano .env  # Edit configuration
```

> See [Configuration](#configuration) section for details

### Step 6: Launch Application
```bash
uv run main.py
```

### Step 7: System Service (Optional)
```bash
# Copy service file
cp PasarGuard.service /var/lib/pasarguard/

# Enable and start service
systemctl enable /var/lib/pasarguard/PasarGuard.service
systemctl start PasarGuard
```

### Step 8: Nginx Configuration (Optional)

#### Option 1: Subdomain Setup
```nginx
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name PasarGuard.example.com;

    ssl_certificate      /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key  /etc/letsencrypt/live/example.com/privkey.pem;

    location / {
        proxy_pass http://0.0.0.0:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

#### Option 2: Path-based Setup
```nginx
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name example.com;

    ssl_certificate      /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key  /etc/letsencrypt/live/example.com/privkey.pem;

    # PasarGuard dashboard and API
    location ~* /(dashboard|statics|sub|api|docs|redoc|openapi.json) {
        proxy_pass http://0.0.0.0:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    # Xray WebSocket proxy
    # Pattern: /PasarGuard/{username}/{xray-port}
    location ~* /PasarGuard/.+/(.+)$ {
        proxy_redirect off;
        proxy_pass http://127.0.0.1:$1/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

> **Default Access**: `http://localhost:8000/dashboard`  
> Configure via `UVICORN_HOST` and `UVICORN_PORT` environment variables

# Configuration

> You can set settings below using environment variables or placing them in `.env` file.

## Core Settings

| Variable | Description | Default |
|----------|-------------|---------|
| `SUDO_USERNAME` | Superuser's username | - |
| `SUDO_PASSWORD` | Superuser's password | - |
| `SQLALCHEMY_DATABASE_URL` | Database URL ([SQLAlchemy docs](https://docs.sqlalchemy.org/en/20/core/engines.html#database-urls)) | - |
| `SQLALCHEMY_POOL_SIZE` | Database connection pool size | `10` |
| `SQLALCHEMY_MAX_OVERFLOW` | Maximum overflow connections | `30` |

## Server Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `UVICORN_HOST` | Bind application to this host | `0.0.0.0` |
| `UVICORN_PORT` | Bind application to this port | `8000` |
| `UVICORN_UDS` | Bind application to a UNIX domain socket | - |
| `UVICORN_SSL_CERTFILE` | SSL certificate file for HTTPS | - |
| `UVICORN_SSL_KEYFILE` | SSL key file for HTTPS | - |
| `UVICORN_SSL_CA_TYPE` | SSL certificate authority type (`private` for self-signed) | `public` |

## Xray Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `XRAY_JSON` | Path of Xray's JSON config file | `xray_config.json` |
| `XRAY_SUBSCRIPTION_PATH` | API path for subscription | `sub` |

## Template Settings

| Variable | Description | Default |
|----------|-------------|---------|
| `CUSTOM_TEMPLATES_DIRECTORY` | Customized templates directory | `app/templates` |
| `CLASH_SUBSCRIPTION_TEMPLATE` | Template for generating Clash configs | `clash/default.yml` |
| `XRAY_SUBSCRIPTION_TEMPLATE` | Template for generating Xray configs | `xray/default.yml` |
| `SINGBOX_SUBSCRIPTION_TEMPLATE` | Template for generating SingBox configs | `xray/default.yml` |
| `SUBSCRIPTION_PAGE_TEMPLATE` | Template for subscription info page | `subscription/index.html` |
| `HOME_PAGE_TEMPLATE` | Decoy page template | `home/index.html` |

## Security & Authentication

| Variable | Description | Default |
|----------|-------------|---------|
| `JWT_ACCESS_TOKEN_EXPIRE_MINUTES` | Access token expiration time (0 = infinite) | `1440` |

## Development & Debugging

| Variable | Description | Default |
|----------|-------------|---------|
| `DEBUG` | Debug mode for development | `False` |
| `DOCS` | Enable API docs on `/docs` and `/redoc` | `False` |

## User Management

| Variable | Description | Default |
|----------|-------------|---------|
| `USERS_AUTODELETE_DAYS` | Auto-delete expired users after N days (-1 = disabled) | `-1` |
| `USER_AUTODELETE_INCLUDE_LIMITED_ACCOUNTS` | Include limited accounts in auto-delete | `False` |

## Statistics & Monitoring

| Variable | Description | Default |
|----------|-------------|---------|
| `ENABLE_RECORDING_NODES_STATS` | Enable node statistics recording (PostgreSQL/TimescaleDB only) | - |

# Documentation

The [PasarGuard Documentation](https://PasarGuard.github.io/PasarGuard) provides comprehensive guides to get you started, available in multiple languages:

- 🇺🇸 **English** - Complete setup and usage guide
- 🇮🇷 **فارسی** - راهنمای کامل نصب و استفاده  
- 🇷🇺 **Русский** - Полное руководство по установке и использованию

> 📚 **Contributing**: We welcome contributions to improve our documentation. Help us make it better on [GitHub](https://github.com/PasarGuard/PasarGuard.github.io).

# API

PasarGuard provides a comprehensive **REST API** for programmatic access to all features.

## 📖 **API Documentation**

Enable API documentation by setting `DOCS=True` in your configuration, then access:

- **Swagger UI**: `/docs` - Interactive API explorer
- **ReDoc**: `/redoc` - Clean, readable documentation

## 🔧 **Key Features**

- **Complete CRUD operations** for all resources
- **Authentication & Authorization** via JWT tokens
- **Rate limiting** and security controls
- **Webhook support** for real-time notifications
- **Bulk operations** for efficient management

# Backup

Protect your data with PasarGuard's comprehensive backup solutions.

## 📁 **Manual Backup**

### File Locations
- **Data files**: `/var/lib/pasarguard` (Docker) or `/opt/pasarguard` (Script install)
- **Configuration**: `/opt/pasarguard/.env`
- **Xray config**: Custom location (check your settings)

### Backup Steps
1. Copy entire data directory to secure location
2. Backup configuration files
3. Store Xray configuration files
4. Test restore process regularly

## 🤖 **Automated Backup Service**

PasarGuard includes an intelligent backup service with Telegram integration:

### Features
- **Automated scheduling** (hourly backups)
- **Multi-database support** (SQLite, MySQL, MariaDB)
- **Telegram delivery** with file splitting for large backups
- **On-demand backups** anytime
- **No size limitations** - files are automatically split

### Setup

#### 1. Install Latest Script
```bash
sudo bash -c "$(curl -sL https://github.com/PasarGuard/scripts/raw/main/pasarguard.sh)" @ install-script
```

#### 2. Configure Backup Service
```bash
pasarguard backup-service
```

#### 3. Create Immediate Backup
```bash
pasarguard backup
```

> 💡 **Pro Tip**: Set up automated backups to run during low-traffic hours for optimal performance.

# Telegram Bot

PasarGuard includes a powerful **integrated Telegram bot** for remote management and notifications.

## 🤖 **Bot Features**

- **User Management** - Create, modify, and delete users
- **Server Monitoring** - Real-time status and statistics  
- **Notifications** - Automated alerts and updates
- **Remote Control** - Manage PasarGuard without server access
- **Multi-Admin Support** - Multiple administrators

## ⚙️ **Setup**

### 1. Get Bot Token
1. Message [@BotFather](https://t.me/BotFather) on Telegram
2. Create a new bot with `/newbot`
3. Copy the API token

### 2. Get Your User ID
1. Message [@userinfobot](https://t.me/userinfobot)
2. Copy your numeric user ID

### 3. Configure Environment
Add to your `.env` file:
```bash
TELEGRAM_API_TOKEN=your_bot_token_here
TELEGRAM_ADMIN_ID=your_user_id_here
```

### 4. Restart PasarGuard
```bash
systemctl restart PasarGuard
```

> 🎉 **Ready!** Your bot is now active and ready to use.

# Command Line Tools

PasarGuard provides powerful command-line tools for efficient management.

## 💻 **CLI (Command Line Interface)**

Direct command-line access to all PasarGuard features.

### Usage
```bash
pasarguard cli [OPTIONS] COMMAND [ARGS]...
```

### Key Commands
- `admin create` - Create administrator accounts
- `user list` - List all users
- `user create` - Create new users
- `backup` - Create immediate backup
- `status` - Check system status

### Documentation
📖 [Complete CLI Documentation](./cli/README.md)

## 🖥️ **TUI (Terminal User Interface)**

Interactive terminal-based management interface.

### Usage
```bash
pasarguard tui
```

### Features
- **Interactive menus** - Easy navigation
- **Real-time updates** - Live data display
- **Full functionality** - Complete feature access
- **Keyboard shortcuts** - Efficient operation

### Documentation
📖 [Complete TUI Documentation](./tui/README.md)

# Multi-Node Architecture

PasarGuard's **distributed node system** revolutionizes infrastructure management.

## 🌐 **Node Benefits**

- **High Availability** - Multiple server redundancy
- **Geographic Distribution** - Global server placement
- **Load Balancing** - Automatic traffic distribution
- **Scalability** - Easy infrastructure expansion
- **Flexibility** - Users can choose preferred servers

## 🚀 **Key Features**

- **Centralized Management** - Control all nodes from one dashboard
- **Automatic Failover** - Seamless server switching
- **Load Distribution** - Intelligent traffic routing
- **Health Monitoring** - Real-time node status
- **Easy Deployment** - Simple node setup process

## 📖 **Documentation**

For detailed installation and configuration instructions, visit:
[PasarGuard Node Documentation](https://github.com/PasarGuard/node)

# Webhook Notifications

PasarGuard supports **webhook notifications** for real-time event delivery to external services.

## 🔗 **Configuration**

Set these environment variables in your `.env` file:

```bash
WEBHOOK_ADDRESS=https://your-webhook-endpoint.com/webhook
WEBHOOK_SECRET=your-secret-key-here
```

## 📡 **How It Works**

PasarGuard sends HTTP POST requests to your webhook endpoint with:

### Headers
```
Content-Type: application/json
x-webhook-secret: your-secret-key-here
```

### Request Body
```json
{
  "username": "PasarGuard_test_user",
  "action": "user_updated", 
  "enqueued_at": 1680506457.636369,
  "tries": 0
}
```

## 📋 **Supported Events**

| Event | Description |
|-------|-------------|
| `user_created` | New user created |
| `user_updated` | User information updated |
| `user_deleted` | User account deleted |
| `user_limited` | User traffic limit reached |
| `user_expired` | User account expired |
| `user_disabled` | User account disabled |
| `user_enabled` | User account enabled |

## 🔒 **Security**

- **Secret verification** - Validate requests using `x-webhook-secret` header
- **HTTPS recommended** - Secure transmission
- **Retry mechanism** - Automatic retry on failures

# Support & Community

## 💝 **Donation**

If you find PasarGuard useful and want to support its development:

[![Donate](https://img.shields.io/badge/Donate-Support%20Development-green?style=for-the-badge&logo=heart)](https://donate.gozargah.pro)

Your support helps us maintain and improve PasarGuard! 🙏

## 📄 **License**

PasarGuard is published under the [AGPL-3.0 License](./LICENSE).

## 🤝 **Contributing**

We ❤️ contributors! Help us make PasarGuard better:

### How to Contribute
1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your changes
4. **Submit** a pull request

### Resources
- 📖 [Contributing Guidelines](CONTRIBUTING.md)
- 💬 [Telegram Community](https://t.me/Pasar_Guard)
- 🐛 [Report Issues](https://github.com/PasarGuard/panel/issues)

## 👥 **Contributors**

<div align="center">
  <p>Thanks to all contributors who have helped improve PasarGuard:</p>
  <a href="https://github.com/PasarGuard/panel/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=PasarGuard/panel" alt="Contributors" />
  </a>
  <p>Made with <a href="https://contrib.rocks" target="_blank" rel="noopener noreferrer">contrib.rocks</a></p>
</div>
