# WindowsLTSC
Steps to help to install windows LTSC

1. Download your windows ISO from below link
https://www.microsoft.com/en-in/evalcenter/download-windows-11-enterprise

2. Save your preinstalled drivers (maybe from manufacturer) [below command is AI gen, but tested]
```
Export-WindowsDriver -Online -Destination "C:\MyPCurrentDrivers"
```

3. Copy this folder to a safe location so that we can copy it back to C drive.

4. Create USB bootable stick and install windows erasing previous windows installation (well known process)

5. Install updates from windows update and restore the drivers using below command [below command is AI gen, but tested]
```
Get-ChildItem "C:\MyPCurrentDrivers" -Recurse -Filter "*.inf" | ForEach-Object { PNPUtil.exe /add-driver $_.FullName /install }
```

6. To convert your evaluation (trial) verion to full version. Download, extract and copy [LTSC SKUs.zip](./LTSC%20SKUs.zip) file to C:\Windows\System32\spp\tokens\skus\ folder.

9. And open CMD as administrator and run below command, then restart the computer.
```
cscript.exe %windir%\system32\slmgr.vbs /rilc
cscript.exe %windir%\system32\slmgr.vbs /upk >nul 2>&1
cscript.exe %windir%\system32\slmgr.vbs /ckms >nul 2>&1
cscript.exe %windir%\system32\slmgr.vbs /cpky >nul 2>&1
cscript.exe %windir%\system32\slmgr.vbs /ipk M7XTQ-FN8P6-TTKYV-9D4CC-J462D
sc config LicenseManager start= auto & net start LicenseManager
sc config wuauserv start= auto & net start wuauserv
```

7. This will not activate your windows. Please contact concerned individuals for the same.
