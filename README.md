
# Suricata IDS/IPS Home Lab

This project demonstrates how to deploy and use Suricata as an IDS/IPS in a home lab environment. The lab includes custom rule creation, traffic simulation, and alert validation.

## 🔧 Features

- Local Suricata setup with custom rules
- Real-time traffic detection and alerting
- `alert` and `reject` rules with practical HTTP and ICMP tests
- Apache server used to simulate HTTP traffic

## 🧪 Custom Rules Example

```suricata
alert http any any -> any any (msg:"Found login in HTTP URI"; content:"login"; http_uri; nocase; sid:1000003; rev:1;)
reject http any any -> any any (msg:"Access Blocked: 'login' keyword detected"; content:"login"; http_uri; nocase; sid:1000006; rev:1;)
alert tcp any any -> any 22 (msg:"Custom Rule: SSH Traffic Detected"; sid:1000004; rev:1;)
alert icmp any any -> any any (msg:"Custom Rule: ICMP Detected"; sid:1000005; rev:1;)
```

## 📷 Screenshots

- `fast.log` entries showing detection and rejections
- Custom rule examples in local.rules

## 🖼️ Lab Topology

```
Kali (Attacker) ---> Suricata ---> Apache (Target)
```

![Lab Topology](lab_topology.png)

## 📂 Project Structure

```
Suricata-HomeLab/
├── README.md
├── setup_instructions.md
├── rules/
│   └── local.rules
├── screenshots/
│   ├── alert_login.png
│   ├── reject_login.png
│   └── lab_topology.png
├── logs/
│   └── fast.log
```

## 📘 Learn More

- https://docs.suricata.io
- https://rules.emergingthreats.net/

---

> Created by Abdulrahman – https://abdurahman.pro
