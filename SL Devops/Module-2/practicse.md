# Linux Core Components & Process Management

## 1. Core Components of Linux

### Kernel

The **kernel** is the heart of the Linux operating system.
It directly interacts with the hardware and manages:

* CPU
* Memory
* Devices
* File systems
* Processes

The kernel acts as a bridge between hardware and software.

Example:
When an application wants to read a file, it requests the kernel to access the disk.

---

### User Space

**User space** is where normal applications run.

Examples:

* Bash shell
* Chrome
* VS Code
* Python programs

Applications in user space cannot directly access hardware.
They communicate with the kernel using **system calls**.

---

### Init / systemd

After the Linux kernel boots, it starts the first process called **init**.

Modern Linux distributions mostly use **systemd** as the init system.

Its job is to:

* Start system services
* Manage background processes
* Handle boot process
* Monitor services

---

# 2. How Processes Are Created and Managed

A **process** is a running program.

## Process Creation

Linux usually creates a process using:

1. **fork()**

   * Creates a copy of the current process

2. **exec()**

   * Loads a new program into the process

Example:
When you run `ls` in terminal:

* Bash creates a child process using `fork()`
* The child runs `ls` using `exec()`

---

## Process Management

Linux tracks each process using a:

* **PID (Process ID)**

Common process states:

* Running
* Sleeping
* Stopped
* Zombie

Useful commands:

* `ps` → show processes
* `top` → monitor processes
* `kill` → stop processes

The kernel scheduler decides which process gets CPU time.

---

# 3. What systemd Does and Why It Matters

## What systemd Does

systemd is responsible for:

* Booting the system
* Starting services automatically
* Managing daemons/services
* Restarting failed services
* Logging with `journald`
* Handling dependencies between services

Example services:

* SSH server
* Docker
* Nginx

---

## Why systemd Matters

systemd improves:

* Faster boot times
* Better service management
* Automatic recovery
* Centralized logging
* Easier administration

Useful commands:

```bash
systemctl start nginx
systemctl stop nginx
systemctl status nginx
systemctl restart nginx
```

Without systemd, managing services manually would be harder and less reliable.
