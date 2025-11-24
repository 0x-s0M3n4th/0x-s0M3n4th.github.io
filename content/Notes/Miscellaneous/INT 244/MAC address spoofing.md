---
title: "Practical Guide: MAC Address Spoofing"
date: 2025-11-02T20:24:00+05:30  
draft: false                    
description: "A quick, hands-on guide to understanding and performing MAC address spoofing for network testing."
tags:
  - "Networking"
  - "MAC Address"
  - "Spoofing"
  - "Red Team"
  - "Practical"
---
# Requirements:
1. Install `tmac changer` and `angry ip scanner` tool.

# Practical demo:
1. Open up `angry ip scanner` , as well as open a command prompt and type `ipconfig` to see your ip address. Also check your mac address using the command `getmac` 
![[Pasted image 20251102175926.png]]
![[Pasted image 20251102175942.png]]
2. On `angry ip` set the ip address range as per your respective ip:
![[Pasted image 20251102180121.png]]
3. Click on the `ip` column , and double click on `mac address` which will be on right side, and it will come to the left:
![[Pasted image 20251102175322.png]]
4. Then start the scan.
![[Pasted image 20251102180250.png]]
5. Identified one MAC address, Now we will spoof it, by typing the address inside `tmac changer`:
![[Pasted image 20251102180412.png]]
6. Before and after `MAC address` of my device. Internet access will be unavailable for some time because the whole network interface will restart after the `mac address` change. You should be able to access someone else's internet without giving their login credentials for a private network, and perform critical attacks using the `MAC address` , we may trick the SOC team.
![[Pasted image 20251102180455.png]]

---
## Tracert: tracing internet route
1. We can trace our internet traffic route using the command `tracert`
![[Pasted image 20251102181159.png]]

---
# SAM file location:
```powershell
C:\Windows\System32\config\
```
![[Pasted image 20251102181309.png]]

## What is SAM?
**SAM: Security Accounts Manager Database**
The Security Accounts Manager (SAM) database is a [vital component](https://www.sciencedirect.com/topics/computer-science/vital-component) of Microsoft Windows operating systems, responsible for storing passwords locally on the computer system and maintaining user and account information for authentication to the local system when an account has been created for a user. 1 The SAM database [stores passwords](https://www.sciencedirect.com/topics/computer-science/store-password) in either `LAN Manager (LM) hash or NT LAN Manager (NTLM)` format, depending on the policies implemented and enforced for password storage. During normal operation, the SAM database cannot be copied due to restrictions enforced by the operating system kernel, and it is stored in two locations within Windows: `%systemroot%\system32\config\sam` for the main storage and `%systemroot%\repair\sam._` as a backup for recovery purposes. The SAM database plays a significant role in authentication and access control within Windows, providing system users the ability to authenticate to the local system.

- We can perform various types of attacks like `DLL injection` to dump the hashes directly from the memory by injecting a DLL into critical processes such as `LSASS(Local Security Authority Subsystem Service)` by using tools like `mimikatz, pwdump` 
