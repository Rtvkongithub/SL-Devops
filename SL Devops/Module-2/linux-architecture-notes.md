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
| `sudo userdel abc`     | Delete the user            |


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

```
ps aux --sort=-%cpu | head -10
```
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

## ⚙️ Process Checks

| Command           | Usage                          |
| ----------------- | ------------------------------ |
| `ps aux`          | View all running processes     |
| `ps aux \| head`  | View first few processes       |
| `top`             | Real-time process monitoring   |
| `pgrep ssh`       | Find process by name           |

---

## 🔧 Service Checks

| Command                                           | Usage                              |
| ------------------------------------------------- | ---------------------------------- |
| `systemctl status nginx`                          | Check nginx service status         |
| `systemctl start nginx`                           | Start nginx service                |
| `systemctl stop nginx`                            | Stop nginx service                 |
| `systemctl restart nginx`                         | Restart nginx service              |
| `systemctl reload nginx`                          | Reload configuration without stop  |
| `systemctl enable nginx`                          | Enable service at boot             |
| `systemctl disable nginx`                         | Disable service at boot            |
| `systemctl is-active nginx`                       | Check if service is active         |
| `systemctl is-enabled nginx`                      | Check if service starts on boot    |
| `systemctl list-units --type=service`             | List active services               |
| `systemctl list-unit-files --type=service`        | List all installed services        |
| `systemctl --failed`                              | Show failed services               |
| `systemctl daemon-reload`                         | Reload systemd configuration       |
| `systemctl reboot`                                | Reboot the system                  |
| `systemctl poweroff`                              | Shut down the system               |
| `systemctl suspend`                               | Suspend the system                 |
| `systemctl get-default`                           | Show default boot target           |
| `systemctl set-default multi-user.target`         | Set CLI mode as default            |
| `systemctl set-default graphical.target`          | Set GUI mode as default            |
| `systemctl cat nginx`                             | View service file content          |
| `systemctl show nginx`                            | Show detailed service properties   |

---

## 📜 Log Checks

| Command                          | Usage                          |
| -------------------------------- | ------------------------------ |
| `journalctl -u ssh`              | View SSH service logs          |
| `tail -n 50 /var/log/syslog`     | View last 50 system log lines  |
| `journalctl -xe`                 | View recent system errors      |

---

## 🛠️ Mini Troubleshooting Flow

### Problem:
Docker service not responding.

| Step | Command                          | Purpose                    |
| ---- | -------------------------------- | -------------------------- |
| 1    | `systemctl status docker`        | Check Docker status        |
| 2    | `journalctl -u docker`           | Inspect Docker logs        |
| 3    | `sudo systemctl restart docker`  | Restart Docker service     |
| 4    | `systemctl status docker`        | Verify service is running  |

---

## ✅ Summary

Practiced:
- Process monitoring
- systemd service management
- Linux log inspection
- Basic troubleshooting workflow
