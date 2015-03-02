Links for further reference

[SSH Account Setup](https://rmtheis.wordpress.com/2011/07/03/setting-up-an-sftp-site-on-amazon-web-services-ec2-creating-an-account-to-share-with-a-third-party-and-restricting-that-account-to-allow-only-sftp/)
[SFTP Setup](http://ubuntuforums.org/showthread.php?t=1057657)

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
        PasswordAuthentication yes

```
Restart SSH service to reflect these changes
```
sudo service ssh restart
```

Step 4 Creating and adding users to the sftp group

4a. Create the group 'sftponly'

```
sudo groupadd sftponly
```
4b Create a new user 

```
sudo useradd -m username
```
4c Add the new user to the sftponly group 

```
sudo usermod -g sftponly username
```
4d Remove the new users shell access

```
sudo usermod -s /bin/false username
```
4e Change the ownership/group of the users home directory to root:root

```
sudo chown root:root /home/username
```
4f Unless we change the users home directory to '/' or create '/home/username' inside the chroot they will be unable to login! i would suggest you opt for creating a the home directory inside the chroot as you can also make it writable for them.

Create the 'fake' home directory 

```
sudo mkdir -p /home/username/home/username
```
4g Make the user the owner of their fake home directory

```
sudo chown username:username /home/username/home/username
```

Step 5 Setup SSH access for this user

5a On the server, create the .ssh directory for the new user

```
sudo mkdir /home/username/.ssh
```
5b Add public key to the server

Retrieve public key

```
ssh-keygen -y
```
Create authorized_keys file

```
cd /home/username/.ssh
sudo touch authorized_keys
sudo nano authorized_keys
```
Paste contents of public key into this file & Save the file

Step 6
Change permissions of files

```
sudo chmod 700 /home/username/.ssh

sudo chmod 600 /home/username/.ssh/authorized_keys

sudo chown -R username:username /home/newusername/.ssh
```

Step 7

Using your favourite SFTP client FileZill for example test & verify that you are able to transfer files