# MITRE ATT&CK Mapping

| Rule Name | Tactic | Technique | Technique ID | Description |
|------------|--------|------------|---------------|--------------|
| Encoded PowerShell Detection | Execution / Defense Evasion | Command & Scripting Interpreter: PowerShell / Obfuscated Command | T1059.001 / T1027 | Detects encoded PowerShell activity |
| Suspicious Execution from Downloads/Temp | Execution / Initial Access | User Execution: Malicious File | T1204.002 | Detects process creation in suspicious folders |
| Unexpected Network Connection from CLI | Command and Control | Application Layer Protocol: Web Protocols | T1071.001 | Detects C2 via PowerShell or cmd |
