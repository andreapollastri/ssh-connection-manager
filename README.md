# 👾 SSH Connection Manager (conn)

![Bash](https://img.shields.io/badge/bash-4.0+-green.svg)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

A bash script to easily manage SSH connections with custom aliases.

**Manage your SSH connections like a pro!** Add, edit, list and connect to your servers with simple commands. Features password clipboard integration, auto-update, SSH key management and a beautiful interface.

## 🎯 Quick Example

```bash
# Add a new connection
conn add

# List all your servers
conn list

# Connect to a server
conn to myserver
```

## 🪄 Installation

### Method 1: Global Installation (Recommended)

Clone the repository from GitHub:

```bash
git clone https://github.com/andreapollastri/ssh-connection-manager.git
cd ssh-connection-manager
```

Run the installation script:

```bash
chmod +x install.sh
./install.sh
```

After installation, you can use the `conn` command from any directory!

### Method 2: Direct Usage

If you prefer not to install globally:

```bash
chmod +x conn
./conn <command>
```

## 📋 Commands Overview

| Command               | Description                                        |
| --------------------- | -------------------------------------------------- |
| `conn add`            | Add a new SSH connection                           |
| `conn list`           | Display all saved connections in a beautiful table |
| `conn to <alias>`     | Connect to a server by alias                       |
| `conn edit <alias>`   | Edit an existing connection                        |
| `conn remove <alias>` | Remove a connection                                |
| `conn reset <alias>`  | Reset SSH host keys                                |
| `conn key <action>`   | Manage SSH keys (public/private/create)            |
| `conn update`         | Update script to latest version                    |
| `conn help`           | Show help message                                  |

## ⌨️ Available Commands

### 1. Add a New Connection

```bash
conn add
```

You will be prompted to enter:

- **Alias**: short name to identify the server
- **User**: SSH username (default: root)
- **Host**: IP address or hostname of the server
- **Port**: SSH port (default: 22)
- **Password**: (optional) will be copied to clipboard during connection

**Example:**

```
Type alias: myserver
Type user (default: root): andrea
Type host: 192.168.1.100
Type port (default: 22): 2222
Password (optional - will be copied to clipboard during connection): ********
```

### 2. List All Servers

```bash
conn list
```

Example output:

```
╔════════════════════════════════════════════════════════════════════════════╗
║                          SSH SERVERS LIST                                  ║
╚════════════════════════════════════════════════════════════════════════════╝

  ALIAS                 USER                       HOST                  PORT
  ────────────────────────────────────────────────────────────────────────────
  myserver              andrea                     192.168.1.100         2222
  production            root                       prod.example.com      22     🔑
  staging               deploy                     staging.example.com   2222

────────────────────────────────────────────────────────────────────────────
  💡 Tip: Use conn to <alias> to connect
```

🔑 = Connection with saved password

### 3. Connect to a Server

```bash
conn to <alias>
```

**Example:**

```bash
conn to myserver
```

The script will:

- Check if SSH key exists (warns if missing)
- Check for script updates (warns if available)
- Copy saved password to clipboard (if present)
- Connect via SSH

### 4. Edit a Connection

```bash
conn edit <alias>
```

Allows you to modify an existing connection. Press Enter to keep the current value, or type a new one to change it.

**Example:**

```bash
conn edit myserver
```

### 5. Remove a Connection

```bash
conn remove <alias>
```

You will be asked for confirmation before proceeding.

**Example:**

```bash
conn remove myserver
```

### 6. Reset SSH Keys

```bash
conn reset <alias>
```

Executes `ssh-keygen -R` to remove the host's SSH keys (useful in case of "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED").

**Example:**

```bash
conn reset myserver
```

### 7. Manage SSH Keys

```bash
conn key <action>
```

Available actions:

- `public` - Show your SSH public key
- `private` - Show your SSH private key (⚠️ keep it secret!)
- `create` - Generate a new SSH key pair (id_rsa)

**Examples:**

```bash
conn key public   # Show public key
conn key create   # Create new SSH key pair
```

### 8. Update Script

```bash
conn update
```

Downloads and installs the latest version from GitHub. Automatically uses `sudo` if the script is installed in a system directory.

### 9. Help

```bash
conn help
```

## 🗄️ Configuration File

Connections are saved in:

```
~/.ssh_connections.conf
```

The file uses the format: `alias|user|host|port|password`

You can manually edit this file to backup or modify connections.

## 🚀 Features

- ✅ **Beautiful table interface** with colors and Unicode characters
- ✅ **Password management** - automatically copied to clipboard during connection
- ✅ **Edit connections** - modify existing connections without recreating them
- ✅ **SSH key management** - create, view public/private keys
- ✅ **Auto-update** - check and install updates from GitHub
- ✅ **Smart checks** - warns if SSH key is missing or updates are available
- ✅ **Alphabetically sorted** connections list
- ✅ **Default values** for user (root) and port (22)
- ✅ **Input validation** and confirmation prompts
- ✅ **Automatic SSH key reset** for host identification issues
- ✅ **No external dependencies** (bash + standard Unix tools)

## 🔧 Requirements

- macOS (or any Unix-like system)
- Bash
- Git
- SSH client installed
- Optional: SSH key pair (`id_rsa`) - can be created with `conn key create`

## 📝 Notes

- Connections are saved in a simple text file (`~/.ssh_connections.conf`)
- Each user has their own configuration file
- **Passwords are stored in plain text** - use SSH keys when possible for better security
- Passwords (if saved) are automatically copied to clipboard during connection
  - macOS: uses `pbcopy` (native)
  - Linux: uses `xclip` or `xsel` (install if needed)
- The script automatically checks for updates when connecting
- Backups are created when updating the script

## 🗑️ Uninstallation

If you installed globally:

```bash
sudo rm /usr/local/bin/conn
```

To remove SSH connections data:

```bash
sudo rm /usr/local/bin/conn
```

To remove SSH connections data:

```bash
rm ~/.ssh_connections.conf
```

## 🤝 Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest new features
- Submit pull requests

## 💬 Support

If you have questions or need help:

- Open an issue on GitHub
- Check existing issues for solutions

## 📄 License

MIT License - Free to use and modify.

---

Made with ❤️ by [Andrea Pollastri](https://web.ap.it)
