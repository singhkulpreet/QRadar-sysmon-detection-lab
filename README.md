# 🛡️ QRadar Sysmon Detection Lab

This project demonstrates practical SOC detection engineering by integrating **Windows Sysmon logs** with **IBM QRadar Community Edition**.  
It includes **three custom correlation rules** mapped to **MITRE ATT&CK**, detecting common PowerShell and process behaviors often used by attackers.

---

## ⚙️ Lab Setup

- **Attacker/Testing Machine**: Windows 10 (Sysmon installed)
- **SIEM**: IBM QRadar CE
- **Log Collection**: Winlogbeat or WinCollect forwarding Sysmon logs
- **Analysis**: Custom correlation rules written in AQL

---

## 🚨 Detection Rules

| Rule Name | Detection Focus | MITRE Techniques | Trigger Command |
|------------|-----------------|------------------|-----------------|
| Encoded PowerShell Detected | Detects use of Base64-encoded PowerShell commands | T1059.001, T1027 | `powershell -enc <base64>` |
| Suspicious Execution from Downloads/Temp | Detects process execution from suspicious folders | T1204.002, T1105 | Run notepad.exe from Downloads |
| Unexpected Network Connection from CLI | Detects network connections from PowerShell or cmd | T1071.001, T1059 | `Invoke-WebRequest google.com` |

---

## 🧠 MITRE ATT&CK Mapping

- **T1059.001** — PowerShell execution  
- **T1027** — Obfuscated command  
- **T1204.002** — User execution from Downloads  
- **T1105** — File transfer or drop  
- **T1071.001** — C2 communication via HTTP/HTTPS  

---

## 📸 Screenshots
Screenshots are located under `Documentation/Screenshots/`:
- Rule creation
- Offense triggered in QRadar
- Annotated MITRE mapping
- Log Activity proof

---

## 📂 Files
- `AQL_Filters/` — The AQL filter queries used inside QRadar
- `Reference_Sets/` — Reference sets used in the rules
- `Documentation/` — Detailed documentation and screenshots

---

## 🧩 Author
Created by **Kulpreet Singh**  
🎓 Demonstrating SOC Analyst skills in detection engineering using Sysmon, QRadar CE, and MITRE ATT&CK.
