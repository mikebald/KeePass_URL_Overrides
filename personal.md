# My Custom URL Overrides

rdp :: cmd://cmd /c "cmdkey /generic:TERMSRV/{URL:RMVSCM} /user:{USERNAME} /pass:{PASSWORD} && mstsc /v:{URL:RMVSCM} && timeout /t 5 /nobreak && cmdkey /delete:TERMSRV/{URL:RMVSCM}"
vnc :: cmd://"C:\Program Files\TightVNC\tvnviewer.exe" -host={URL:RMVSCM} -password="{PASSWORD}"
steam :: cmd://"S:\Program Files\Steam\Steam.exe" -login {USERNAME} {PASSWORD}
iexplore :: cmd://"c:\Program Files\Internet Explorer\iexplore.exe" "http://{URL:RMVSCM}"
iexplores :: cmd://"c:\Program Files\Internet Explorer\iexplore.exe" "https://{URL:RMVSCM}"
sftp :: cmd://"{ENV_PROGRAMFILES_X86}\WinSCP\WinSCP.exe" {BASE:SCM}://{USERNAME}:{PASSWORD}@{BASE:HOST}:{T-REPLACE-RX:/{BASE:PORT}/-1//}
ftp :: cmd://"{ENV_PROGRAMFILES_X86}\WinSCP\WinSCP.exe" {BASE:SCM}://{USERNAME}:{PASSWORD}@{BASE:HOST}:{T-REPLACE-RX:/{BASE:PORT}/-1//}
ssh_altport :: cmd://PuTTY.exe -ssh {USERNAME}@{URL:HOST} -P 2222
