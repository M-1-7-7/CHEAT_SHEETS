# File Sharing Options for Windows

### SMB Shares
We can set up smb shared to allow files to be shared between devices on the netword

1. set up SMB Share:
   - `New-SmbShare -Name ShareName -Path "C:\Folder\On\TheServer" -FullAccess "Everyone"`

2. connect to share from remote PC:
    - `New-SmbMapping -RemotePath '\\server' -Username "domain\username" -Password "password"`

3. Upload and Downlowd:
     - run `Get-SmbMapping` to get the local drive letter assigned to the share
     - move files in and out as see fit
  
