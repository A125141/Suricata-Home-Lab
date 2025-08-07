
# Suricata Home Lab Setup Guide

## 1. 🖥️ Environment Overview
This guide helps you set up a simple Suricata IDS/IPS lab using Virtual Machines.

**Components:**
- Kali Linux (Attacker)
- Ubuntu (Target with Apache)
- Suricata Host (can be on attacker or separate VM)

## 2. 📦 Install Apache on Target
```bash
sudo apt update
sudo apt install apache2 -y
```

## 3. 🧰 Install Suricata
```bash
sudo apt update
sudo apt install suricata -y
```

## 4. 📝 Configure Suricata Rules
Edit the config:
```bash
sudo nano /etc/suricata/suricata.yaml
```
Ensure this is present:
```yaml
default-rule-path: /etc/suricata/rules
rule-files:
  - local.rules
```

Place your custom rules inside:
```
/etc/suricata/rules/local.rules
```

## 5. 🔁 Restart Suricata
```bash
sudo systemctl restart suricata
```

## 6. ⚙️ Generate Test Traffic
```bash
curl http://<target-ip>/login
ping <target-ip>
```

## 7. 📊 View Logs
```bash
tail -f /var/log/suricata/fast.log
```

## 8. ✅ Validate Detection
Ensure alerts show up in `fast.log` indicating Suricata is triggering your custom rules.
