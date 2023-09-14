# File Transfers

### SSH
 - `scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2` (`-r` for recersive)
 - copy local file to remote: `scp file.txt remote_username@10.10.0.2:/remote/directory`
 - copy remote file to local: `scp remote_username@10.10.0.2:/remote/file.txt /local/directory`
   
### FTP
 - Dpload to server: `put c:\files\file1.txt`
 - Download from server: `get c:\files\file1.txt`
 - Dpload multiple files: use `lcd` to traverse kale; then `put *.txt` to put all files to server
 - Downlod multiple files: use `lcd` to traverse kale; then `mget *.txt` to pull all files to server
   
### SMB

### HTTP
