# 🎮 Fade Backend - Complete Setup Guide

<p align="center">
  <img src="https://cdn.discordapp.com/attachments/1395852791091560458/1404548256570151095/Logotipo_moderno_com_computador_e_escudo.png?ex=689b96ff&is=689a457f&hm=59f0803c91c48158ea85c6989641e5f2dcb1ad96ff7640d5da0023a3e9cdb723&" width="200" alt="Fade Logo">
</p>

<p align="center">
  <strong>A powerful Fortnite backend supporting both Battle Royale and Save The World</strong>
  <br>
  <em>Created by sickfff</em>
</p>

---

## 📋 Table of Contents
- [🎯 Overview](#-overview)
- [🏗️ Architecture](#️-architecture)
- [⚙️ Prerequisites](#️-prerequisites)
- [🚀 Quick Setup](#-quick-setup)
- [🔧 VPS Backend Setup](#-vps-backend-setup)
- [🧪 Beta Test Backend Setup](#-beta-test-backend-setup)
- [📊 Environment Configuration](#-environment-configuration)
- [🔐 Discord Bot Setup](#-discord-bot-setup)
- [🛠️ Troubleshooting](#️-troubleshooting)
- [📞 Support](#-support)

---

## 🎯 Overview

Fade Backend is a comprehensive Fortnite backend solution that comes in **two distinct configurations**:

### 🖥️ VPS Backend (`Fade-Backend-for-projects-with-vps/`)
- **Purpose**: Production-ready backend for live projects
- **Features**: Full account system, Discord bot integration, XMPP support
- **Requirements**: VPS/Cloud server with Node.js 18+
- **Use Case**: Public servers, tournaments, community projects

### 🧪 Beta Test Backend (`Fade-Backend-for-beta-tests-preboot/`)
- **Purpose**: Testing custom paks and features
- **Features**: Lightweight backend for Reboot Launcher
- **Requirements**: Local development environment
- **Use Case**: Mod testing, private development, custom content testing

---

## ⚙️ Prerequisites

### System Requirements
- **Node.js**: v18.0.0 or higher
- **npm**: Latest stable version
- **Git**: For cloning and updates
- **Discord Bot**: For VPS backend (optional for beta)

### Required Software
```bash
# Windows
- Node.js: Download from nodejs.org
- Git: Download from git-scm.com

# Linux/macOS
sudo apt update && sudo apt install nodejs npm git  # Ubuntu/Debian
brew install node git                                # macOS
```

---

## 🚀 Quick Setup

### 1. Clone the Repository
```bash
git clone https://github.com/sickfff/FadeBackend.git
cd FadeBackend
```

### 2. Choose Your Backend Type

#### For VPS Production:
```bash
cd Fade-Backend-for-projects-with-vps/
```

#### For Beta Testing:
```bash
cd Fade-Backend-for-beta-tests-preboot/
```

---

## 🔧 VPS Backend Setup

### Step 1: Install Dependencies
```bash
cd Fade-Backend-for-projects-with-vps/
npm install
```

### Step 2: Environment Configuration
Create a `.env` file in the root directory:

```env
# Discord Bot Configuration
DISCORD_TOKEN=your_discord_bot_token_here
DISCORD_CLIENT_ID=your_discord_client_id_here
DISCORD_GUILD_ID=your_discord_server_id_here

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/fade
REDIS_URL=redis://localhost:6379

# Server Configuration
PORT=3551
HOST=0.0.0.0

# Security Keys
JWT_SECRET=your_super_secret_jwt_key_here
ENCRYPTION_KEY=your_32_character_encryption_key

# Webhook URLs
WEBHOOK_URL=https://discord.com/api/webhooks/your_webhook_url

# Fortnite API Keys
FORTNITE_API_KEY=your_fortnite_api_key
```

### Step 3: Discord Channel Setup
**Critical Step**: You MUST configure the Discord channel for account creation.

1. Open `build/bot/commands/user/register.js`
2. Find line 11:
   ```javascript
   const ALLOWED_CHANNEL_ID = "PUT_THE_CHANNEL_ID_HERE";
   ```
3. Replace `"PUT_THE_CHANNEL_ID_HERE"` with your actual Discord channel ID:
   ```javascript
   const ALLOWED_CHANNEL_ID = "123456789012345678";
   ```

### Step 4: Build and Start
```bash
npm run build
npm start
```

---

## 🧪 Beta Test Backend Setup

### Step 1: Install Dependencies
```bash
cd Fade-Backend-for-beta-tests-preboot/
npm install
```

### Step 2: Start the Server
```bash
npm start
```

### Step 3: Configure Reboot Launcher
1. Open Reboot Launcher
2. Set backend URL to: `http://localhost:3551`
3. Launch your desired Fortnite build

---

## 📊 Environment Configuration Details

### VPS Backend Variables
| Variable | Description | Example |
|----------|-------------|---------|
| `DISCORD_TOKEN` | Bot token from Discord Developer Portal | `MTA2N...` |
| `DISCORD_CLIENT_ID` | Application ID from Discord Developer Portal | `1066...` |
| `DISCORD_GUILD_ID` | Your Discord server ID | `123456789012345678` |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/fade` |
| `REDIS_URL` | Redis connection string | `redis://localhost:6379` |
| `JWT_SECRET` | Secret key for JWT tokens | `your-secret-key-here` |
| `PORT` | Server port | `3551` |

### Getting Discord IDs
1. **Enable Developer Mode** in Discord settings
2. **Right-click** on your server name → Copy Server ID (Guild ID)
3. **Right-click** on your channel → Copy Channel ID
4. **Right-click** on your bot → Copy Application ID

---

## 🔐 Discord Bot Setup

### 1. Create Discord Application
1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **"New Application"**
3. Name your application (e.g., "Fade Backend")
4. Go to **"Bot"** tab → **"Add Bot"**

### 2. Configure Bot Permissions
Required permissions:
- `Send Messages`
- `Embed Links`
- `Read Message History`
- `Manage Messages`
- `Add Reactions`

### 3. Invite Bot to Server
1. Go to **"OAuth2"** → **"URL Generator"**
2. Select `bot` scope
3. Select required permissions
4. Copy the generated URL and invite your bot

---

## 🛠️ Troubleshooting

### Common Issues

#### ❌ "Cannot find module" error
```bash
npm install --force
```

#### ❌ Port already in use
```bash
# Check what's using port 3551
netstat -ano | findstr :3551  # Windows
lsof -i :3551                  # Linux/macOS
```

#### ❌ Discord bot not responding
1. Check bot token in `.env`
2. Verify bot has necessary permissions
3. Ensure bot is in your server

#### ❌ Database connection failed
1. Verify MongoDB is running
2. Check connection string in `.env`
3. Ensure database exists

### Debug Mode
Enable debug logging by adding to `.env`:
```env
DEBUG=true
```

---

## 📞 Support

### Community
- **Discord**: [Fade Community Server](https://discord.gg/JM5hVsjnrb)
- **GitHub Issues**: [Report bugs here](https://github.com/sickfff/FadeBackend/issues)

### Credits
- **Developer**: sickfff
- **Contributors**: [See GitHub contributors](https://github.com/sickfff/FadeBackend/graphs/contributors)
- **Special Thanks**: Zetax, Nexus-FN team

---

## 🔄 Updates & Maintenance

### Updating the Backend
```bash
git pull origin main
npm install
npm run build
```

### Backup Recommendations
- **Database**: Regular MongoDB dumps
- **User Profiles**: Backup `profiles/` directory
- **Configuration**: Keep `.env` file secure

---

<p align="center">
  <strong>Made with ❤️ by sickfff</strong>
  <br>
  <em>Bringing custom Fortnite experiences to life</em>
</p>
