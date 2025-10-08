# Pattern-Based-IDS-with-Dry-Run-Firewall
A simple, educational Intrusion Detection System (IDS) built with Python and Scapy. It inspects TCP packet payloads, matches configurable patterns (e.g., domain names), logs activity, and can optionally trigger a “firewall” response (dry-run by default).

This project is intended for learning and demos, not for production security.

## Features
- Live packet sniffing with Scapy (TCP by default).
- Configurable pattern matching via config.ini.
- Human-readable activity and alert logs.
- Pluggable “firewall” action (disabled by default; implemented as logging/dry-run).
- Jupyter notebook for interactive exploration.

## Legal and Ethical Notice
- Only sniff traffic on networks you own or have explicit permission to monitor.
- Packet capture often requires administrative/root privileges.
- Misuse can be illegal and unethical. This project is for educational purposes only, with no warranty.

## Project Structure
- Assignment1.ipynb — main notebook with the Matcher class and live sniffing.
- config.ini — configuration for detection patterns, firewall toggle, and logging.
- alert_generated.log — appended alert messages (human-readable).
- network_activity.log — activity log (created by the program).
- requirements.txt — Python dependencies (recommended to add).

## Requirements
- OS: Linux or macOS recommended. Windows may require additional setup for libpcap/WinPcap/Npcap.
- Python: 3.9+ (project tested with 3.9).
- Privileges: root/admin typically required to sniff interfaces.
- Libraries:
  - scapy
  - (optional) iptables/nftables if you later implement real blocking

## Installation
- Clone the repository
  - git clone https://github.com/your-username/pattern-ids.git
  - cd pattern-ids
- Create and activate a virtual environment
  - python3 -m venv .venv
  - source .venv/bin/activate # Windows: .venv\Scripts\activate
- Install dependencies
  - pip install -r requirements.txt
If you don’t have a requirements.txt yet, a minimal one:
  - scapy
- Optional system setup
  - Linux: ensure libpcap is installed (usually already present).
  - macOS: you may need to grant terminal full disk/network capture permissions.
 
## Configuration
Edit config.ini to control behavior.

Example (matches your current config):
[Detection]
WebsitePatterns = reddit.com,amazon.com,psl-t20.com,instagram.com

[Firewall]
Enabled = true

[Logging]
LogFile = network_activity.log
AlertLogFile = alert_generated.log
LogLevel = INFO
LogFormat = %(asctime)s - %(message)s
LogDateFormat = %Y-%m-%d %H:%M:%S

### Notes
- Patterns are treated as regular expressions. If you intend to match domains exactly, escape dots and consider word boundaries (e.g., reddit.com).
- The current code compiles patterns without re.IGNORECASE. Add case-insensitive flag in code if desired.
- Firewall Enabled = true only logs a “Blocking IP” message; it does not enforce rules unless you extend the code.

## Running
Option A: Jupyter Notebook (recommended for exploration)
1. Start Jupyter
  - pip install notebook # if needed
  - jupyter notebook
2. Open Assignment1.ipynb and run all cells
  - You will see “Starting the IDS with Firewall...” in the output.
  - Alerts will print to stdout and append to alert_generated.log.

