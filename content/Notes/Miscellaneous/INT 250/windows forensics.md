---
title: "Practical Demo: Windows Forensics"
date: 2025-11-08T20:15:00+05:30
comments: true
weight: 4
draft: false
description: "An introduction to viewing basic Windows artifacts like Recent files and Registry entries, Network informations etc."
tags:
  - "Forensics"
  - "Windows"
  - "Basics"
toc: true
---

## Volatile data collection:
### system uptime and current time:
_In command prompt:_

```cmd
(date /t) & (time /t)
systeminfo | find "Boot Time"
```
![wf_1](/images/UNI_PRACS/INT_250/prac_4/wf_1.png)

_In powershell:_
```powershell
(Get-Date) - (gcim Win32_OperatingSystem).LastBootUpTime  
```
![wf_2](/images/UNI_PRACS/INT_250/prac_4/wf_2.png)

### Network parameters(NetBIOS name cache, active connections, routing table etc):
```cmd
nbtstat -c
netstat -ano
netstat -rn
ipconfig /all
```

_Promiscous mode detection on NICs through powershell:_ 
```powershell
Get-NetAdapter | Format-List -Property ifAlias, PromiscuousMode
```

### Sysinternal tools:
#### logged on users info:
```cmd
PsLoggedon.exe -x
logonsessions.exe -p
net sessions
net user user_name
```
![wf_3](/images/UNI_PRACS/INT_250/prac_4/wf_3.png)
### Hash analysis:
_Using powershell:_

```powershell
Get-FileHash .\FTK_sample_00.E01 -Algorithm MD5 
Get-FileHash .\FTK_sample_00.E01 -Algorithm SHA128
```

### Open file information:
```cmd
net file
```

### list of running processes, services:
```cmd
tasklist /svc
```

### scheduled tasks info:
```cmd
schtasks /query
```

### history checking:
```cmd
doskey /history
```
_In powershell:_

```powershell
Get-History
```

### Examining print spool files:
```cmd
cd C:\Windows\System32\spool\PRINTERS # look for .SPL and .SHD files
```
### WMIC:
```cmd
wmic service list brief 
```
### File shares:
```cmd
net share
```

---
## Non-volatile data collection:
### File system examination:
```cmd
dir /o:d
```
### ESE database view:

`Install esedatabase view tool from internet -> then open the following dir inside the tool : C:\Windows\SoftwareDistribution\DataStore\DataStore.edb` 

![wf_4](/images/UNI_PRACS/INT_250/prac_4/wf_4.png)


### Registry analysis:
#### Collecting system information:
1. open registry editor
2. Then go to this path: 
![wf_5](/images/UNI_PRACS/INT_250/prac_4/wf_5.png)
3. Double click on the right side's `ComputerName` option to see the name.
4. To see current version of windows -> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion` 
5. Last shutdown time information: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Windows` 
6. time zone settings -> `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation` 
7. Share information -> `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Shares` 
---
### Evaluating account management events:
1. win + r -> `secpol.msc` -> enter -> double click local policies -> click audit policy

### browser cache analysis:
1. History and cookies location for google chrome:
`C:\Users\{user_name}\AppData\Local\Google\Chrome\UserData\Default` 
2. cache location:
`C:\Users\{user_name}\AppData\Local\Google\Chrome\UserData\Default\Cache` 

> [!Note]
> Location is identical for every browser, just choose the proper name of the browser.


