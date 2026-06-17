# Network Intrusion Detection System (NIDS)

## Overview
This project implements a Network Intrusion Detection System using Suricata on Ubuntu VM.

## Tasks Completed

### 1. Suricata Installation
- Installed Suricata on Ubuntu VM
- Configured network interface (enp0s8)

### 2. Custom Rules Configuration
Created custom rules in `/etc/suricata/rules/local.rules`:
- Ping Detection (ICMP)
- SSH Connection Attempt (Port 22)
- Port Scan Detection (TCP SYN)
- Suspicious HTTP Access (.env file)

### 3. Alert Configuration
- Configured fast.log for text alerts
- Configured eve.json for JSON alerts
- Alerts successfully detected from Windows host

### 4. Continuous Monitoring
- Suricata runs as a system service
- Monitors network traffic 24/7
- Logs all suspicious activity

### 5. Response Mechanism (IPS Mode)
- Activated IPS mode using NFQUEUE
- Changed rules from `alert` to `drop`
- Suricata now automatically blocks malicious traffic
- Verified: Ping from Windows host times out

### 6. Testing Results
| Attack Type | Rule | Result |
|-------------|------|--------|
| Ping | ICMP | Blocked |
| Port Scan | TCP SYN | Blocked |
| SSH Attempt | Port 22 | Blocked |

## Network Interface
- VM IP: 192.168.56.101
- Interface: enp0s8

## Commands Used

-Start Suricata:

sudo systemctl start suricata

-Check Status of Suricata:

sudo systemctl status suricata

-View Alerts:

sudo cat /var/log/suricata/fast.log

-View Dashboard:

while true; do clear; echo "=== SURICATA ALERTS ==="; sudo tail -10 /var/log/suricata/fast.log; sleep 5; done

### Technologies Used
-Suricata
-Ubuntu VM
-VirtualBox
-iptables
-NFQUEUE

### Conclusion
Successfully implemented a working NIDS with Suricata that detects and blocks network intrusions in real-time.

---

## To create this file on your VM

```bash
sudo nano /home/harini/README.md

## To view it
cat /home/harini/README.md
