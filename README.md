# wireshark-network-analysis-lab
Hands-on Wireshark lab for network traffic analysis, attack detection &amp; packet forensics

# 🧠 Wireshark Network Traffic Analysis Lab

A hands-on lab project simulating common cyber attacks (Nmap scans, brute-force SSH, reverse shells, malicious HTTP requests) and analyzing them using Wireshark.

## 🎯 Objective
Capture, analyze, and interpret network traffic between a simulated attacker (Kali Linux) and a victim system (Ubuntu). Learn practical packet analysis, filtering, and forensic techniques.

---

## 🧱 Lab Architecture

| Role         | OS         | IP Address      | Purpose                    |
|--------------|------------|-----------------|----------------------------|
| Attacker     | Kali Linux | 192.168.1.6   | Runs scans, exploits, shell|
| Victim       | Ubuntu     | 192.168.1.4   | Apache server, SSH target  |
| Analyzer     | Kali       | Wireshark GUI   | Captures all traffic       |

---

## 🛠 Tools Used
- **Wireshark** – Packet capture & inspection  
- **Nmap** – Reconnaissance & scan simulation  
- **Hydra** – SSH brute force  
- **Curl** – HTTP fuzzing and payload injection    
- **Apache2** – Victim-side HTTP server  

---

## ⚔️ Simulated Attacks

| Type                | Command Snippet |
|---------------------|-----------------|
| ICMP                | `ping`          |
| SYN Scan            | `nmap -sS`      |
| FIN Scan            | `nmap -sF`      |
| Xmas Scan           | `nmap -sX`      |
| SSH Brute Force     | `hydra`         |
| Reverse Shell       | `bash -i`       |
| Header Anomalies    | `curl -A`       |
| XSS Payload         | `curl -X POST`  |
| Spoofing IP Header  | `curl -H`       |

---

## 🔍 Wireshark Filters Used

```wireshark
icmp
tcp.flags.syn == 1 and tcp.flags.ack == 0
tcp.flags.fin == 1
tcp.flags.fin == 1 and tcp.flags.urg == 1 and tcp.flags.push == 1
tcp.port == 22
http
ip.addr == 192.168.1.4 and tcp.port == 4444
