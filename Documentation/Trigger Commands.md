For RULE 1:-
 ON POWERSHELL:-
PS C:\WINDOWS\system32> $command = "Write-Host 'Hello from Encoded PowerShell'"
PS C:\WINDOWS\system32> $bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
PS C:\WINDOWS\system32> $encoded = [Convert]::ToBase64String($bytes)
PS C:\WINDOWS\system32> $encoded
VwByAGkAdABlAC0ASABvAHMAdAAgACcASABlAGwAbABvACAAZgByAG8AbQAgAEUAbgBjAG8AZABlAGQAIABQAG8AdwBlAHIAUwBoAGUAbABsACcA
PS C:\WINDOWS\system32>
PS C:\WINDOWS\system32> powershell -enc VwByAGkAdABlAC0ASABvAHMAdAAgACcASABlAGwAbABvACAARgByAG8AbQAgAEUAbgBjAG8AZABlAGQAIABQAG8AdwBlAHIAUwBoAGUAbABsACcA


For RULE 2:-
ON POWERSHELL:-
PS C:\WINDOWS\system32>
>> .\notepad.exe
>> copy C:\Windows\System32\notepad.exe .
>> cd $env:USERPROFILE\Downloads




For RULE3:-
ON POWERSHELL:-
PS C:\Users\saman\Downloads> powershell.exe -NoProfile -Command "Invoke-WebRequest google.com"
