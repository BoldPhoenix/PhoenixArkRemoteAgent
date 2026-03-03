# 🦖 Phoenix ARK Remote Agent

[![Version](https://img.shields.io/badge/version-3.0.0-blue.svg)](https://github.com/BoldPhoenix/PhoenixArkRemoteAgent)
[![Platform](https://img.shields.io/badge/platform-Windows-lightgrey.svg)](https://github.com/BoldPhoenix/PhoenixArkRemoteAgent)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](https://github.com/BoldPhoenix/PhoenixArkRemoteAgent)

A lightweight Windows service that enables remote management of ARK: Survival Ascended servers through the Phoenix ARK Discord Bot. Connect your servers from anywhere without direct RDP access.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔄 **Server Lifecycle** | Start, stop, and restart ARK servers remotely |
| 📊 **Real-Time Status** | Live server status, player count, and ARK version display |
| 📝 **Log Streaming** | View server logs directly from Discord |
| 🔧 **Mod Management** | Install, remove, and update mods via CurseForge |
| ⚙️ **INI Editing** | Edit GameUserSettings.ini and Game.ini remotely |
| 🔄 **Auto-Updates** | Trigger SteamCMD updates with progress tracking |
| 💾 **Backups** | Create and restore server backups |
| 🔒 **Secure** | Auth-key authentication, no arbitrary code execution |

---

## 📋 Requirements

- **OS**: Windows 10/11 or Windows Server 2016+
- **ARK**: ARK: Survival Ascended dedicated server
- **Network**: Port 8080 (configurable) accessible from bot
- **Permissions**: Administrator rights for installation

---

## 🚀 Quick Start

### Step 1: Download

Download the latest release from [GitHub Releases](https://github.com/BoldPhoenix/PhoenixArkRemoteAgent/releases).

### Step 2: Install

Run the installer as **Administrator**:

```powershell
PhoenixArkAgentInstaller.exe
```

The installer will:
- Create the service directory (`C:\Program Files\Phoenix Ark Agent\`)
- Install Windows service `PhoenixArkAgent`
- Generate a unique auth key
- Start the service automatically

### Step 3: Connect to Discord

1. Open the generated `config.json` in your install directory
2. Note the **port** and **auth_key** values
3. In your Discord server, run `/setup` and click **Remote Agent** → **Register Agent**
4. Enter your agent IP, port (default: 8080), and auth key

The setup wizard provides an easy interface to register, edit, remove, and check status of your remote agents.

### Step 4: Manage Servers

Use the `/setup` command in Discord to access all management features through an intuitive GUI:
- **Server Management** — Add/edit/remove ARK servers
- **Remote Agent** — Register, configure, and monitor your agent
- **Mod Management** — Install and manage mods (accessible via `/modmgmt`)
- **INI Editing** — Edit server configuration files (accessible via `/inimgmt`)
- **Backups & Updates** — Schedule maintenance (accessible via `/maintenance`)

---

## ⚙️ Configuration

The `config.json` file is created during installation:

```json
{
  "port": 8080,
  "auth_key": "agent_xxxxxxxxxxxxxxxx"
}
```

| Field | Description |
|-------|-------------|
| `port` | WebSocket port (default: 8080) |
| `auth_key` | Unique authentication key |

> **Note**: ARK servers are configured through the Discord bot's `/setup` interface, not in this file.

---

## 🔧 Service Management

### Using the Installer

The installer provides a menu-driven interface:

```
PhoenixArkAgentInstaller.exe
```

Options:
- **Install** - Install the Windows service
- **Remove** - Remove the Windows service
- **Start** - Start the service
- **Stop** - Stop the service
- **Restart** - Restart the service

### Using Windows Service Manager

```powershell
# Start
net start PhoenixArkAgent

# Stop
net stop PhoenixArkAgent

# Or use Services.msc
services.msc
```

---

## 🔒 Security

| Feature | Description |
|---------|-------------|
| **Auth Key** | Unique key required for all connections |
| **Key Binding** | Auth keys are bound to specific Discord guilds |
| **No Shell Access** | Commands are whitelisted, no arbitrary code execution |
| **No RCON Exposure** | Agent handles RCON locally, never exposed to network |

---

## 🐛 Troubleshooting

### Agent Won't Start

| Symptom | Solution |
|---------|----------|
| Service fails to start | Check Windows Event Viewer → Application logs |
| Port already in use | Verify port 8080 is available: `netstat -ano | findstr 8080` |
| Config error | Validate `config.json` syntax with a JSON validator |

### Bot Can't Connect

| Symptom | Solution |
|---------|----------|
| Connection refused | Ping the agent IP from bot machine |
| Auth failed | Verify auth key matches exactly (copy/paste) |
| Timeout | Check Windows Firewall allows port 8080 |

### Commands Fail

| Symptom | Solution |
|---------|----------|
| Server not found | Verify ARK service names in `config.json` |
| RCON timeout | Ensure RCON ports are open on ARK servers |
| Permission denied | Run installer as Administrator |

---

## 📁 File Locations

| File | Location |
|------|----------|
| Executable | `C:\Program Files\Phoenix Ark Agent\PhoenixArkAgent.exe` |
| Configuration | `C:\Program Files\Phoenix Ark Agent\config.json` |
| Logs | Windows Event Viewer → Application logs |
| Service | `services.msc` → PhoenixArkAgent |

---

## 📞 Support

Running into issues?

1. **Check Logs**: Windows Event Viewer → Application → PhoenixArkAgent
2. **Verify Network**: `ping <agent_ip>` and `telnet <agent_ip> 8080`
3. **Open a Ticket**: [Phoenix ARK Discord Server](https://dc.gg/phoenixarkbot)

---

## 📜 Version History

| Version | Date | Changes |
|---------|------|---------|
| 3.0.0 | 2026-03-03 | Initial public release |
| 2.5.0 | 2026-02-15 | Added backup/restore operations |
| 2.0.0 | 2026-02-01 | Added mod management support |

---

## 📄 License

This software is proprietary. Use is restricted to licensed users of the Phoenix ARK Discord Bot service.

---

<p align="center">
  <strong>Phoenix ARK Remote Agent</strong><br>
  <sub>Part of the <a href="https://github.com/BoldPhoenix/PhoenixArkDiscordBot">Phoenix ARK Bot</a> ecosystem</sub>
</p>
