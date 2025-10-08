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
