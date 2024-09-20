SSH (Secure Shell) is a network protocol used to securely connect to remote systems. It allows encrypted data transfer and remote command execution over insecure networks, such as the internet. SSH is widely used for tasks like:

1. **Remote login**: Securely logging into another machine over a network.
2. **File transfers**: Transferring files securely between systems using SCP (Secure Copy Protocol) or SFTP (SSH File Transfer Protocol).
3. **Tunneling**: SSH can tunnel traffic between two networks or systems through an encrypted connection.
4. **Running commands**: Executing commands on a remote system securely.
5. **Port forwarding**: Enabling network traffic to pass securely through SSH.

SSH operates over port 22 by default and typically uses key-based authentication (public/private keys) or password-based authentication to verify users. For increased security, key-based authentication is preferred.

## Remote login
1. Find the ubuntu server ip address

```
ifconfig
```
or
```
ip addr show
```

```
ssh username@ip_address
```
## File transfers
To transfer files securely using SSH, we can use either SCP (Secure Copy Protocol) or SFTP (SSH File Tranfer Protocol).

1. Using SCP (Secure Copy Protocol)
SCP is used to copy files between a local machine and a remote host, or between two remote hosts.
- Copy a file from the locol system to a remote system:
```
scp /path/to/local/file username@remote_host:/path/to/remote/directory
```
- Copy a file from a remote system to local system:
```
scp username@remote_host:path/to/remote/file /path/to/locol/directory
```
- Copy a directory recursively from local to remote:
```
scp -r /path/to/locol/directory username@remote_host:/path/to/remote/directory
```
2. Using SFTP (SSH File Transfer Protocol)
SFTP provids an interactive file transfer interface. Here's how you can use it:
- Start an SFTP session:
```
sftp username@remote_host
```
- List local files
```
lls
```
- List remote files
```
ls
```
- look at the current remote direction
```
pwd
```
- Look at the current local direction
```
lpwd
```
- change the remote direction
```
cd
```
- change the local direction
```
lcd
```
- Upload a file from local to remote:
```
put filename
```
- Download a file from remote:
```
get filename
```



