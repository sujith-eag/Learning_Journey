
## Installation and Configuration of FTP Server using ProFTPD

Install and configure an FTP server on PC1 using ProFTPD, allowing FTP clients to upload and download files successfully.

### Step-by-Step Procedure


1. Install ProFTPD
    
```bash
sudo apt-get update
sudo apt-get install proftpd
```
    
- During installation, select **standalone mode** and press **Enter** to complete.
        
2. Configure ProFTPD
    
```bash
sudo nano /etc/proftpd/proftpd.conf
```
    
Make the following changes in the configuration file:
- Set `UseIPv6 off`
	
- Set `ServerName "CNLAB.com"`
	
- Uncomment `DefaultRoot ~`
	
- Set `RequireValidShell on`
	
- Uncomment `AuthOrder mod_auth_unix.c`
	
- Save and exit: **Ctrl + O**, **Enter**, then **Ctrl + X**.
	
3. **Add `/bin/false` to Valid Shells**
    
```bash
sudo nano /etc/shells
```
    
Add the following line at the end of the file:    
```
/bin/false
```
    
4. **Create FTP User**
    
```bash
sudo useradd -d /var/www/ -s /bin/false ftpuser
sudo passwd ftpuser
```    
When prompted, enter and confirm a password (e.g., `myftp123`).
    
5. **Create FTP Directory and Set Permissions**
    
```bash
sudo mkdir -p /var/www/
sudo chown ftpuser:ftpuser /var/www/
```
    
6. **Restart ProFTPD Service**
    
```bash
sudo systemctl restart proftpd
```
    
7. **Access FTP Server from Client (PC2 or PC3)**
    
```bash
ftp 172.20.10.X
```
Replace `X` with the correct IP address of PC1.  Enter the FTP username and password when prompted.
    
8. **Test File Transfer Commands**  
Inside the FTP session:
    
```
ftp> put Hello.txt      # To upload
ftp> get Hello.txt      # To download
ftp> ls                 # To list files
ftp> quit               # To exit
```
    
9. **Fixing "Permission Denied" Error (if encountered)**  
    
If you receive the error:
```
550 Hello.txt: Permission denied
```
    
Run the following commands:
```bash
sudo chown ftpuser:ftpuser /var/www/
sudo chmod 755 /var/www/
sudo systemctl restart proftpd
```


The FTP server should allow a successful login using the `ftpuser` account. File uploads and downloads should function correctly without any permission issues.
