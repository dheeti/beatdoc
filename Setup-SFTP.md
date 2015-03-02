Step 1 
Create Instance on EC2
Step 2
Backup your sshd config file

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup.sftpmod
```

Step 3
Open your sshd config file in your favorite editor

```
sudo nano /etc/ssh/sshd_config
```

Change the following line (near the end of the file) 

```
Subsystem sftp /usr/lib/openssh/sftp-server
```

to

```
Subsystem sftp internal-sftp
```
Add the following to the very end of your sshd config (MUST be at the end of the file).

```
Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no
```