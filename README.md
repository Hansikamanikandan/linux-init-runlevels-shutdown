# 🐧 Linux System Administration – Experiment 03
> **Managing System Shutdown, Reboot, and Runlevels using `init`, `shutdown`, and `reboot` Commands**

![Linux](https://img.shields.io/badge/OS-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Shell](https://img.shields.io/badge/Shell-Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Status](https://img.shields.io/badge/Experiment-Completed-success?style=for-the-badge)

---

# 📌 Objective

This experiment demonstrates Linux system administration commands used to:

- Safely shut down the operating system
- Restart the system immediately or after a delay
- Cancel scheduled shutdowns
- Send warning messages to logged-in users
- Perform emergency reboots
- Understand Linux runlevels
- Learn the role of the **init** process during system boot

---

# 📂 Commands & Examples

## 1️⃣ Shutdown the System

```bash
sudo init 0
```

**Purpose**

Stops all running services and powers off the system safely.

---

## 2️⃣ Restart the System

```bash
sudo init 6
```

**Purpose**

Terminates running processes and immediately reboots the machine.

---

## 3️⃣ Boot into Single User Mode

```bash
sudo init 1
```

**Purpose**

Starts the system in maintenance mode with only the root user.

Useful for:

- Password recovery
- Filesystem repair
- System maintenance

---

## 4️⃣ Switch to Multi User Mode

```bash
sudo init 3
```

**Purpose**

Starts networking and allows multiple users to log in without a graphical interface.

---

## 5️⃣ Schedule a Shutdown After 10 Minutes

```bash
sudo shutdown -h +10
```

**Purpose**

Schedules a graceful shutdown after ten minutes.

---

## 6️⃣ Restart Immediately

```bash
sudo shutdown -r now
```

**Purpose**

Restarts the computer instantly.

---

## 7️⃣ Schedule a Restart After 5 Minutes

```bash
sudo shutdown -r +5
```

**Purpose**

Schedules a reboot after five minutes.

---

## 8️⃣ Display Scheduled Shutdown Information

```bash
shutdown
```

**Purpose**

Shows whether a shutdown or reboot has already been scheduled.

---

## 9️⃣ Cancel Scheduled Shutdown

```bash
sudo shutdown -c
```

**Purpose**

Cancels any pending shutdown or reboot.

---

## 🔟 Force an Emergency Reboot

```bash
sudo reboot -f
```

**Purpose**

Forces the kernel to reboot immediately without performing a clean shutdown.

> ⚠️ Use only during emergency situations.

---

## 1️⃣1️⃣ Shutdown with a Warning Message

```bash
sudo shutdown -h now "System will shut down for maintenance in 5 minutes."
```

**Purpose**

Displays the specified message to all logged-in users before shutting down.

---

## 1️⃣2️⃣ Shutdown Immediately

```bash
sudo shutdown -h now
```

**Purpose**

Immediately powers off the computer safely.

---

## 1️⃣3️⃣ Check Current Runlevel

```bash
runlevel
```

or

```bash
who -r
```

**Purpose**

Displays the current operating runlevel of the Linux system.

---

# 🧠 Understanding the `init` Process

The **init** process is the very first userspace process started by the Linux kernel.

- Process ID (**PID**) = **1**
- Parent of every running process
- Responsible for system initialization
- Starts background services (daemons)
- Executes startup scripts
- Determines the system runlevel
- Remains active until shutdown

The kernel launches `init` immediately after booting, making it one of the most critical processes in a Linux operating system.

---

# ⚙️ Linux Runlevels

| Runlevel | Mode | Description |
|:---------:|------|-------------|
| **0** | Halt | Shutdown the system |
| **1** | Single User | Maintenance mode without networking |
| **2** | Multi User | Multi-user mode (distribution dependent) |
| **3** | Multi User + Networking | Normal command-line mode |
| **4** | Custom | Reserved for user-defined purposes |
| **5** | Graphical Mode | Multi-user mode with GUI |
| **6** | Reboot | Restart the system |

---

# 🔄 Boot Sequence Overview

```text
Power On
    │
    ▼
BIOS / UEFI
    │
    ▼
Boot Loader (GRUB)
    │
    ▼
Linux Kernel
    │
    ▼
init (PID 1)
    │
    ├── Hardware Initialization
    ├── Mount File Systems
    ├── Start Network Services
    ├── Launch Daemons
    └── Enter Default Runlevel
```

---

# 💡 Key Commands Summary

| Task | Command |
|------|---------|
| Shutdown | `sudo init 0` |
| Restart | `sudo init 6` |
| Single User Mode | `sudo init 1` |
| Multi User Mode | `sudo init 3` |
| Shutdown in 10 Minutes | `sudo shutdown -h +10` |
| Restart Now | `sudo shutdown -r now` |
| Restart in 5 Minutes | `sudo shutdown -r +5` |
| Cancel Shutdown | `sudo shutdown -c` |
| Force Reboot | `sudo reboot -f` |
| Shutdown with Message | `sudo shutdown -h now "message"` |
| Immediate Shutdown | `sudo shutdown -h now` |
| Current Runlevel | `runlevel` |

---

# 🎯 Learning Outcomes

✔ Understood the Linux boot process.

✔ Learned the purpose of the `init` process.

✔ Performed system shutdown and reboot operations.

✔ Scheduled and cancelled shutdown tasks.

✔ Explored Linux runlevels.

✔ Practiced essential Linux administration commands.

---

## ⭐ Technologies Used

- Linux
- Bash Shell
- init
- shutdown
- reboot
- runlevel

---

## 📚 Conclusion

This experiment provided hands-on experience with Linux system administration commands used for managing system startup, shutdown, reboot, and runlevels. Understanding these commands is fundamental for Linux administrators, DevOps engineers, system engineers, and cybersecurity professionals.
