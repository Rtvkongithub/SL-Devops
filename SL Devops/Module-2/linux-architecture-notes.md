# Linux Command Cheat Sheet

## 📂 File & Directory Commands

| Command                 | Usage                                |
| ----------------------- | ------------------------------------ |
| `pwd`                   | Show current directory path          |
| `ls -l`                 | List files with detailed permissions |
| `ls -a`                 | Show hidden files                    |
| `cd dir`                | Change directory                     |
| `mkdir test`            | Create a new directory               |
| `rmdir test`            | Remove empty directory               |
| `touch file.txt`        | Create empty file                    |
| `cp a.txt b.txt`        | Copy file                            |
| `mv a.txt b.txt`        | Move or rename file                  |
| `rm file.txt`           | Delete file                          |
| `rm -rf dir`            | Force delete directory               |
| `find . -name file.txt` | Search for file                      |

---

## 📄 File Viewing & Editing

| Command            | Usage                        |
| ------------------ | ---------------------------- |
| `cat file.txt`     | Display file contents        |
| `less file.txt`    | View large file page by page |
| `head -5 file.txt` | Show first 5 lines           |
| `tail -5 file.txt` | Show last 5 lines            |
| `tail -f logs.txt` | Monitor file in real time    |
| `nano file.txt`    | Edit file using Nano         |
| `vim file.txt`     | Edit file using Vim          |

---

## 👤 User & Permission Commands

| Command                | Usage                      |
| ---------------------- | -------------------------- |
| `whoami`               | Show current user          |
| `id`                   | Display user and group IDs |
| `sudo command`         | Run command as admin       |
| `useradd name`         | Create new user            |
| `passwd name`          | Set user password          |
| `chmod 755 file`       | Change file permissions    |
| `chown user:user file` | Change file ownership      |

---

## ⚙️ Process Management

| Command       | Usage                      |
| ------------- | -------------------------- |
| `ps aux`      | Show running processes     |
| `top`         | Real-time process monitor  |
| `htop`        | Interactive process viewer |
| `kill PID`    | Stop process by PID        |
| `kill -9 PID` | Force kill process         |
| `jobs`        | Show background jobs       |
| `bg`          | Run job in background      |
| `fg`          | Bring job to foreground    |

---

## 💾 Disk & System Commands

| Command      | Usage                   |
| ------------ | ----------------------- |
| `df -h`      | Show disk space usage   |
| `du -sh dir` | Show directory size     |
| `free -h`    | Display memory usage    |
| `uptime`     | Show system uptime      |
| `uname -a`   | Show system information |
| `history`    | Show command history    |

---

## 🌐 Networking Commands

| Command                    | Usage                      |
| -------------------------- | -------------------------- |
| `ping google.com`          | Test network connectivity  |
| `ip addr`                  | Show IP addresses          |
| `curl https://example.com` | Fetch webpage/API response |
| `dig google.com`           | DNS lookup information     |
| `netstat -tulnp`           | Show listening ports       |
| `ss -tulnp`                | Display socket statistics  |

---

## 📦 Package Management (Ubuntu/Debian)

| Command                  | Usage                      |
| ------------------------ | -------------------------- |
| `sudo apt update`        | Refresh package list       |
| `sudo apt upgrade`       | Upgrade installed packages |
| `sudo apt install nginx` | Install package            |
| `sudo apt remove nginx`  | Remove package             |

---
