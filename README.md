ARK Server Agent - Remote Management System
============================================

This agent allows your Discord bot to manage ARK servers remotely across different machines.

QUICK START
-----------

1. INSTALLATION
   - Download the entire Installer folder or extract the folder from the downloaded zip archive to the server hosting your Ark Maps 
   - Run PhoenixArkAgentInstaller.exe - Installs Remote Agent as Windows service
   - Open the config.json from where the remote agent was installed (default: c:\program files\phoenix ark agent) and note the port and auth_key, as you will need to input this in to the setup in Discord.
   
2. DISCORD SETUP
   - In Discord, use /setup to register your remote agent IP and auth key with the Phoenix Ark Bot.
   - Manage servers remotely through Discord

FEATURES
--------
- Remote server start/stop/restart
- Real-time status monitoring
- Log streaming
- Mod and INI management
- Server updates
- Backup operations
- Progress tracking
- Live User Count
- Ark Server Version Display

SECURITY
--------
- JWT authentication between bot and agents
- Encrypted WebSocket communication
- Command whitelisting (no arbitrary code execution)
- Audit logging of all operations

TROUBLESHOOTING
---------------
1. Agent won't start:
   - Check Windows Event Viewer
   - Verify config.json syntax
   - Ensure port 8080 is not blocked (check firewall or something else using the port)

2. Bot can't connect:
   - Ping agent IP from bot machine
   - Check firewall settings
   - Verify auth key matches

3. Commands fail:
   - Check agent logs in Windows Application Event Log
   - Verify ARK services are running
   - Check RCON connectivity

SERVICE COMMANDS
----------------
PhoenixArkAgentInstaller.exe, when run provides all needed service control commands
Install: Install PhoenixArkAgent
Remove:  Remove PhoenixArkAgent
Start:   start PhoenixArkAgent
Stop:    stop PhoenixArkAgent
Restart: stop PhoenixArkAgent & start PhoenixArkAgent

DEFAULT PORTS
-------------
- Remote Agent Secure WebSocket: 8080 (configurable at install)

FILE LOCATIONS
--------------
- Executable: PhoenixArkAgent.exe
- Config: config.json
- Logs: Windows Application Event Log
- Service: Windows Services > PhoenixArkAgent

SUPPORT
-------
For issues, check:
1. Windows Event Viewer > Application logs
2. logs\agent.log
3. Network connectivity (ping, telnet)
4. Open ticket/issue on Phoenix Ark Bot Discord Site

VERSION: 3.0.0
UPDATED: 2026-03-03
