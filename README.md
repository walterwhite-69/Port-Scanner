<div align="center">

```
  ██████╗  ██████╗ ██████╗ ████████╗    ███████╗ ██████╗ █████╗ ███╗   ██╗
  ██╔══██╗██╔═══██╗██╔══██╗╚══██╔══╝    ██╔════╝██╔════╝██╔══██╗████╗  ██║
  ██████╔╝██║   ██║██████╔╝   ██║       ███████╗██║     ███████║██╔██╗ ██║
  ██╔═══╝ ██║   ██║██╔══██╗   ██║       ╚════██║██║     ██╔══██║██║╚██╗██║
  ██║     ╚██████╔╝██║  ██║   ██║       ███████║╚██████╗██║  ██║██║ ╚████║
  ╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝       ╚══════╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═══╝
```

**Advanced Network Scanner & RDP Credential Auditor**

*Made By Walter*

---

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/walterwhite-69/Port-Scanner)
[![Stars](https://img.shields.io/github/stars/walterwhite-69/Port-Scanner?style=for-the-badge&color=FFD700&logo=github)](https://github.com/walterwhite-69/Port-Scanner/stargazers)
[![Forks](https://img.shields.io/github/forks/walterwhite-69/Port-Scanner?style=for-the-badge&color=orange&logo=github)](https://github.com/walterwhite-69/Port-Scanner/network/members)
[![Downloads](https://img.shields.io/github/downloads/walterwhite-69/Port-Scanner/total?style=for-the-badge&color=brightgreen&logo=github&label=Downloads)](https://github.com/walterwhite-69/Port-Scanner/releases)
[![License](https://img.shields.io/badge/License-MIT-red?style=for-the-badge)](LICENSE)
[![Visitors](https://visitor-badge.laobi.icu/badge?page_id=walterwhite-69.Port-Scanner&left_color=black&right_color=00c4ff&left_text=Visitors)](https://github.com/walterwhite-69/Port-Scanner)

</div>

---

## 😩 Tired of Googling "free rdp checker 2024 no virus"?

Yeah, we've all been there. Scrolling through sketchy Telegram channels, downloading ZIP files called `rdp_crack_v3_REAL.exe`, and wondering why your antivirus is crying.

**Port Scanner** is a clean, open-source, terminal-based tool that does two things properly:

1. **Scans IP ranges** (TCP/UDP) at high speed across thousands of hosts
2. **Audits RDP credentials** (NLA/CredSSP) using real NTLM authentication — not some fake "connection test"

No shady EXE. No hidden RAT (probably). Just Python.

---

## ✨ Features

### 🔍 Port Scanner
- Scan any IP, CIDR range, or list of networks
- TCP and UDP support
- Configurable ports: single, list (`80,443,3389`) or range (`1-1000`)
- Up to 1000+ concurrent threads
- Live dashboard with real-time Open/Closed/Filtered stats
- Results auto-saved to `scan_results.txt`
- Press `Ctrl+D` to gracefully stop mid-scan

### 🔐 RDP Credential Auditor
- Real **NLA (CredSSP/NTLM)** authentication — not just a port ping
- Auto-loads targets from your `scan_results.txt`
- Smart early-exit: if a host is dead/incompatible on first attempt, skip all remaining credentials instantly (no wasting 11 minutes per dead host)
- **Custom wordlist files**: load your own username list + password list (one per line)
- Or use the built-in cross-product list: **21 usernames × 54 passwords = 1,134 pairs** — every user tries every password
- Clean log codes: `WRONG_CREDS`, `TLS_ERR`, `TIMEOUT`, `NTLM_NEG_FAIL`, etc.
- All attempts logged instantly to `rdp_debug.log`
- Hits saved to `rdp_hits.txt` with IP, credentials, and OS type
- Live dashboard with accurate progress tracking

### 🎨 UI
- Animated ASCII banner with word-by-word 
- Rich terminal UI (tables, panels, live stats)
- Centered layout

---

## 📋 Requirements

- **Python 3.9+** (3.11 or 3.12 recommended)
- **Windows** (uses `msvcrt` for Ctrl+D listener)
- Dependencies listed in `requirements.txt`

---

## ⚡ Installation

### 1. Clone the repo

```bash
git clone https://github.com/walterwhite-69/Port-Scanner.git
cd Port-Scanner
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

That's it. No C extensions, no DLLs, no "run as admin and disable your antivirus".

### Or download directly from Releases

Head to the [**Releases**](https://github.com/walterwhite-69/Port-Scanner/releases) page and grab the latest zip. Extract it, install requirements, and run.

---

## 🚀 Usage

```bash
python scanner.py
```

You'll land on the main menu:

```
[1]  Port Scanner     (TCP/UDP)
[2]  RDP Brute Force  (Credential Audit)
[3]  Exit
```

---

### Option 1 — Port Scanner

```
➜ Enter targets file path (IP/CIDR):   ip_list.txt
➜ Enter port(s) (e.g. 3389 or 80,443): 3389
➜ Enter threads (default 100):          500
➜ Protocol - TCP or UDP (default TCP):  tcp
```

**Target file format** (`ip_list.txt`):
```
1.0.0.0/24
192.168.1.0/28
10.0.0.1
203.0.113.5
```

Results are saved to `scan_results.txt`. RDP Brute Force auto-reads this file.

---

### Option 2 — RDP Credential Auditor

```
➜ Use scan results? (y/n, default y):           y
➜ Enter threads (default 50):                   200
➜ Use custom wordlist files? (y/n, default n):  n
```

**Using custom wordlists:**
```
➜ Use custom wordlist files? (y/n, default n):  y
➜ Path to usernames file (one per line):        users.txt
➜ Path to passwords file (one per line):        passwords.txt
```

**Wordlist file format:**
```
# users.txt       # passwords.txt
administrator     Password123
admin             P@ssw0rd
root              Summer2024
```

Hits are saved to `rdp_hits.txt`, all attempts to `rdp_debug.log`.

---

## 📁 Output Files

| File | Description |
|------|-------------|
| `scan_results.txt` | Open ports from Port Scanner |
| `rdp_hits.txt` | Successful RDP credentials |
| `rdp_debug.log` | Every RDP attempt with status code |

### Log Status Codes

| Code | Meaning |
|------|---------|
| `SUCCESS` | Valid credentials found 🎉 |
| `WRONG_CREDS` | Host responded — wrong password, try next |
| `TIMEOUT` | Host didn't respond in 4 seconds |
| `TLS_ERR` | TLS cipher/version mismatch |
| `TLS_INTERNAL_ERR` | Server killed TLS after our CredSSP packet |
| `NTLM_NEG_FAIL` | TLS connected but server rejected NTLM |
| `RDP_NEG_FAIL` | Port open but not RDP |
| `CONN_REFUSED` | Port closed |

---

## 🔧 Performance Tips

- Use **500–1000 threads** for port scanning large CIDR ranges
- Use **100–300 threads** for RDP auditing (each connection does a full TLS + NTLM handshake)
- Timeout is fixed at **4 seconds** per RDP attempt — hosts either respond fast or not at all
- Dead hosts (any non-`WRONG_CREDS` status) are **skipped instantly** — no wasted attempts

---

## ⚠️ Legal Disclaimer

This tool is for **authorized security auditing and penetration testing only**.

Using this against systems you do not own or have explicit written permission to test is **illegal** under computer fraud laws in virtually every country (CFAA, Computer Misuse Act, etc.).

The author is not responsible for what you do with this. Don't be stupid.

---

## 🤝 Contributing

PRs welcome. Found a bug? Open an issue. Want a feature? Also open an issue, I might ignore it, but try.

---

## ⭐ Star History

If this saved you from downloading another sketchy `.exe` from a Telegram channel, consider leaving a star. It's free and makes me feel validated.

[![GitHub Stars](https://img.shields.io/github/stars/walterwhite-69/Port-Scanner?style=for-the-badge&color=FFD700&logo=github&label=Stars)](https://github.com/walterwhite-69/Port-Scanner/stargazers)

---

<div align="center">

**Made By Walter** &nbsp;|&nbsp; Python &nbsp;|&nbsp; No RATs Included (Probably)

</div>
