In Linux, every process stays in a **process state** depending on what it’s doing.

# Main Process States

| State                         | Meaning                                             |
| ----------------------------- | --------------------------------------------------- |
| **R (Running)**               | Process is currently running or ready to run on CPU |
| **S (Sleeping)**              | Waiting for something (very common state)           |
| **D (Uninterruptible Sleep)** | Waiting for disk/network I/O                        |
| **T (Stopped)**               | Process paused/stopped manually                     |
| **Z (Zombie)**                | Process finished but parent didn’t clean it         |
| **X (Dead)**                  | Process completely terminated                       |

---

# 1. Running State (R)

Process is actively using CPU.

Example:

* Chrome rendering
* Python script executing
* `npm run build`

Check:

```bash
ps aux
```

You may see:

```bash
R
```

---

# 2. Sleeping State (S)

Most common state.

Process is alive but waiting:

* keyboard input
* file access
* timer
* network response

Example:

* Terminal waiting for command
* VS Code idle

Types:

* **Interruptible sleep (S)** → can wake up easily
* **Uninterruptible sleep (D)** → waiting for hardware/disk

---

# 3. Uninterruptible Sleep (D)

Process waiting for:

* disk read/write
* NFS/network storage
* hardware response

Cannot be interrupted easily.

Example:

```bash
cp hugefile /mnt/nfs
```

If storage hangs → process enters `D`.

Danger:

* Too many `D` states may indicate:

  * disk issue
  * storage issue
  * NFS problem

---

# 4. Stopped State (T)

Process paused.

Usually caused by:

```bash
Ctrl + Z
```

Example:

```bash
nano test.txt
```

Press:

```bash
Ctrl + Z
```

Now process becomes stopped.

Commands:

```bash
jobs
fg
bg
```

---

# 5. Zombie State (Z)

Most interesting one.

Zombie = process completed execution BUT:

* parent process didn’t collect exit status

Process is technically dead but still visible.

Example flow:

```text
Child process finishes
↓
Parent forgets to clean it
↓
Zombie appears
```

Why dangerous?

* Few zombies = okay
* Thousands = process table issue

Check zombies:

```bash
ps aux | grep Z
```

Kill zombie:

* Usually kill/restart parent process

---

# 6. Dead State (X)

Process fully removed from system.

Rarely visible.

---

# Visual Lifecycle

```text
Created
   ↓
Running (R)
   ↓
Sleeping (S/D)
   ↓
Running again
   ↓
Stopped (T) [optional]
   ↓
Zombie (Z) [if not cleaned]
   ↓
Dead (X)
```

# Check Process States Live

Use:

```bash
top
```

or:

```bash
htop
```

or:

```bash
ps -eo pid,ppid,state,cmd
```

Example:

```bash
PID  STATE CMD
1234 R     python app.py
1235 S     nginx
1236 Z     node
```

Especially:

* Many `R` → CPU overload
* Many `D` → disk/storage problem
* Many `Z` → bad application handling

# Command Im daily using
- ssh
- cd
- mv
- cp
- cat
