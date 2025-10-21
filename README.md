# 👾 SSH Connection Manager (conn)

A bash script to easily manage SSH connections with custom aliases.

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

**Example:**

```
Type alias: myserver
Type user (default: root): andrea
Type host: 192.168.1.100
Type port (default: 22): 2222
```

### 2. List All Servers

```bash
conn list
```

Example output:

```
=== SSH Servers List ===

myserver - andrea@192.168.1.100:2222
production - root@prod.example.com:22
staging - deploy@staging.example.com:2222
```

### 3. Connect to a Server

```bash
conn to <alias>
```

**Example:**

```bash
conn to myserver
```

### 4. Remove a Connection

```bash
conn remove <alias>
```

You will be asked for confirmation before proceeding.

**Example:**

```bash
conn remove myserver
```

### 5. Reset SSH Keys

```bash
conn reset <alias>
```

Executes `ssh-keygen -R` to remove the host's SSH keys (useful in case of "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED").

**Example:**

```bash
conn reset myserver
```

### 6. Help

```bash
conn help
```

## 🗄️ Configuration File

Connections are saved in:

```
~/.ssh_connections.conf
```

The file uses the format: `alias|user|host|port`

## 🚀 Features

- ✅ Colorful and user-friendly interface
- ✅ Default values for user (root) and port (22)
- ✅ Input validation
- ✅ Confirmation before deleting connections
- ✅ Automatic SSH key management
- ✅ No external dependencies (bash only)

## 🔧 Requirements

- macOS (or any Unix-like system)
- Bash
- GIT
- SSH client installed
- SSH key pair (`id_rsa`) properly configured and installed on remote servers

## 📝 Notes

- Connections are saved in a simple text file
- Each user has their own configuration file
- The script does not save passwords (uses standard SSH authentication)

## 🗑️ Uninstallation

If you installed globally:

```bash
sudo rm /usr/local/bin/conn
rm ~/.ssh_connections.conf
```

## 📄 License

Free to use and modify.
