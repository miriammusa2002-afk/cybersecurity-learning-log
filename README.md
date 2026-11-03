# Cybersecurity Learning Log: Linux Fundamentals on Kali

**Period:** 11 October – 3 November 2026
**Environment:** Kali Linux (virtual machine)
**Focus:** Linux fundamentals, networking basics, user privileges and process management

This is my hands-on record of learning the Linux skills that cybersecurity work depends on. Every command below is something I ran and practiced myself.

---

## 1. File navigation and management (Days 1–8)

| Command | What it does |
|---|---|
| `pwd` | Shows the current working directory |
| `ls` | Lists files and directories |
| `ls -a` | Includes hidden files |
| `cd ~` | Goes to the home directory |
| `cd ..` | Moves up one directory |
| `mkdir cybersecurity` | Creates a directory |
| `touch notes.txt` | Creates an empty file |
| `echo "Hello" > report.txt` | Writes text to a file, replacing existing content |
| `echo "More text" >> notes.txt` | Appends text to a file |
| `cat notes.txt` | Displays file contents |
| `cp notes.txt backup.txt` | Copies a file |
| `mv backup.txt saved_notes.txt` | Renames or moves a file |
| `head notes.txt` | Shows the first lines of a file |
| `tail notes.txt` | Shows the last lines of a file |
| `wc -l notes.txt` | Counts lines in a file |
| `grep "word" notes.txt` | Searches for matching text |

### Saving notes and command output

```bash
mkdir -p ~/Cybersecurity/Notes
nano ~/Cybersecurity/Notes/day1.txt
cat ~/Cybersecurity/Notes/day1.txt

ls > command-results.txt
pwd >> command-results.txt
```

- `mkdir -p` creates a directory and any missing parent directories.
- `nano` opens a terminal text editor.
- `>` overwrites a file; `>>` appends to it.

---

## 2. Linux permissions

`chmod` controls who can read, write or execute a file.

```bash
chmod 755 script.sh
```

Owner gets read, write and execute (7). Group and others get read and execute (5).

---

## 3. Networking fundamentals (Day 12)

| Command | What it does |
|---|---|
| `ip addr` | Shows network interfaces and IP addresses |
| `ip route` | Shows routing information and the default gateway |
| `ping -c 4 127.0.0.1` | Tests connectivity to my own machine with four packets |
| `ss -tuln` | Lists listening TCP and UDP sockets |

My VM showed the default gateway `10.0.2.2`.

---

## 4. Users and privileges (Day 16)

| Command | What it does |
|---|---|
| `whoami` | Shows the current username |
| `id` | Shows user ID and group memberships |
| `sudo -l` | Lists commands I am allowed to run with sudo |

These help when investigating who has access to what, and spotting unauthorized access.

---

## 5. Process management (Day 17)

**Inspecting processes**

```bash
ps          # processes in my terminal
ps aux      # all processes on the system
top         # live view; press q to exit
```

**Finding and inspecting a process**

```bash
pgrep sleep
ps -p <PID> -f
```

**Starting and stopping a background process**

```bash
sleep 300 &
jobs
pgrep sleep
ps -p $(pgrep sleep) -f
kill $(pgrep sleep)
```

- `&` runs the command in the background.
- `jobs` lists background jobs from the current shell.
- `$(pgrep sleep)` inserts the process ID returned by `pgrep`.
- `kill` sends a signal to terminate the process.

---

## 6. Logging terminal sessions

```bash
script session1.txt   # start recording
exit                  # stop recording
ls -l                 # confirm the file was saved
```

---

## Progress summary

- **6 skill areas:** file management, permissions, networking, users and privileges, process management, session logging
- **30+ commands and command patterns**

I have moved from basic terminal navigation to inspecting system processes and managing background tasks. These are foundations for Linux administration, system monitoring and incident investigation.

## Next

Deeper permissions (`chown`, symbolic `chmod`, `umask`), log analysis, SSH, and network scanning in a safe lab.
