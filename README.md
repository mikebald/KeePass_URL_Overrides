# URL Overrides for KeePass
Url override scripts for KeePass in Linux and Windows systems.

## Accessing the URL Override section
* Open KeyPass's Options by going to the Tools menu and selecting Options
* Select the Integration Tab
* Click the URL Overrides... button

## SSH

##### PuTTY [Windows]
* **Scheme:** `ssh`
* **Command:**
```
cmd://"{ENV_PROGRAMFILES_X86}\PuTTY\putty.exe" -ssh "{USERNAME}@{URL:HOST}" -P {URL:PORT} -pw "{PASSWORD}" 
```

##### OpenSSH Client [Linux]

* **Scheme:** `ssh`
* **Command:**
```
cmd://xterm -e sshpass -p {PASSWORD} ssh -o StrictHostKeyChecking=no {USERNAME}@{URL:RMVSCM}
```

## RDP

##### MSTSC [Windows]

* **Scheme:** `rdp`
* **Command:**
```
cmd://cmd /c "cmdkey /generic:TERMSRV/{URL:RMVSCM} /user:{USERNAME} /pass:{PASSWORD} && mstsc /v:{URL:RMVSCM} && timeout /t 5 /nobreak && cmdkey /delete:TERMSRV/{URL:RMVSCM}"
```

##### Remmina [Linux]

* **Scheme:** `rdp`
* **Command:**
```
cmd://bash -c "FILE=/tmp/connect.remmina ; echo -en '[remmina]\nname={TITLE}\nprotocol=RDP\nserver={URL:RMVSCM}\nscale=1\nviewmode=1\nusername={USERNAME}\npassword='`remmina-encode-password.py {PASSWORD}` > $FILE ; remmina -c $FILE ; rm -f $FILE"
```

## VNC

##### TightVNC [Windows]

* **Scheme:** `vnc`
* **Command:**
```
cmd://"C:\Program Files\TightVNC\tvnviewer.exe" -host={URL:RMVSCM} -password="{PASSWORD}"
```

##### Remmina [Linux]

* **Scheme:** `vnc`
* **Command:**
```
cmd://bash -c "FILE=/tmp/connect.remmina ; echo -en '[remmina]\nname={TITLE}\nprotocol=VNC\nserver={URL:RMVSCM}\nscale=1\nviewmode=1\nusername={USERNAME}\npassword='`remmina-encode-password.py {PASSWORD}` > $FILE ; remmina -c $FILE ; rm -f $FILE"
```

## SAMBA

##### Explorer [Windows]

* **Scheme:** `smb`
* **Command:**
```
cmd://cmd /c "net use "{URL:RMVSCM}" /user:"{USERNAME}" "{PASSWORD}" && start \\{URL:RMVSCM}"
```

##### Nautilus [Linux]

* **Scheme:** `smb`
* **Command:**
```
cmd://bash -c "echo -e '\n{PASSWORD}' | gvfs-mount 'smb://{USERNAME}@{URL:RMVSCM}' ; nautilus 'smb://{USERNAME}@{URL:RMVSCM}'"
```

## FTP

##### FileZilla FTP Client [Windows]

* **Scheme:** `ftp`
* **Command:**
```
cmd://"{ENV_PROGRAMFILES_X86}\FileZilla FTP Client\filezilla.exe" 'ftp://{USERNAME}:{PASSWORD}@{URL:RMVSCM}'
```

##### FileZilla FTP Client [Linux]

* **Scheme:** `ftp`
* **Command:**
```
cmd://filezilla 'ftp://{USERNAME}:{PASSWORD}@{URL:RMVSCM}'
```

## SFTP using Key Agent

#### Filezilla FTP Client [Windows]
 
* **Scheme:** `sftp_filezilla`
* **Command:**
```
cmd://"{ENV_PROGRAMFILES_X86}\FileZilla FTP Client\filezilla.exe" sftp://{USERNAME}@{URL:RMVSCM}
```

##### FileZilla FTP Client [Linux]

* **Scheme:** `ftp`
* **Command:**
```
cmd://filezilla 'sftp://{USERNAME}@{URL:RMVSCM}'
```
