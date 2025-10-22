# Detection Rules

## Rule 1: Encoded PowerShell Detection
**Description:** Detects encoded PowerShell commands to identify obfuscated script execution.  
**AQL:**  
```
UTF8(payload) ILIKE '%Sysmon%' 
AND (UTF8(payload) ILIKE '%powershell%' AND (UTF8(payload) ILIKE '%-enc%' OR UTF8(payload) ILIKE '%EncodedCommand%'))
```
**MITRE:** T1059.001, T1027  
**Response:** Dispatch event, annotate offense, add to `suspicious_endpoints` set  
**Trigger Command:**
```powershell
powershell -enc VwByAGkAdABlAC0ASABvAHMAdAAgACcASABlAGwAbABvACAAZgByAG8AbQAgAEUAbgBjAG8AZABlAGQAIABQAG8AdwBlAHIAUwBoAGUAbABsACcA
```

---

## Rule 2: Suspicious Execution from Downloads/Temp
**Description:** Detects when executables are launched from Temp or Downloads folder.  
**AQL:**
```
UTF8(payload) ILIKE '%sysmon%' AND (UTF8(payload) ILIKE '%downloads%' OR UTF8(payload) ILIKE '%Temp%')
```
**MITRE:** T1204.002, T1105  
**Trigger:**
```powershell
copy C:\Windows\System32\notepad.exe $env:USERPROFILE\Downloads
cd $env:USERPROFILE\Downloads
.\notepad.exe
```

---

## Rule 3: Unexpected Network Connection from CLI
**Description:** Detects PowerShell or cmd.exe initiating network connections on common ports (80/443/53).  
**AQL:**
```
UTF8(payload) ILIKE '%Network connection detected%' 
AND (UTF8(payload) ILIKE '%powershell.exe%' OR UTF8(payload) ILIKE '%cmd.exe%')
```
**MITRE:** T1071.001, T1059  
**Trigger:**
```powershell
powershell.exe -NoProfile -Command "Invoke-WebRequest google.com"
```
