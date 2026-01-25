---
title: "Practical Wazuh"
date: 2025-10-12T12:48:03+05:30
lastmod: 2025-10-12T12:42:03+05:30
comments: true
draft: false
author: "0x-s0M3n4th"
tags: ["Blue Team", "Lab"]
description: "A practical guide to use Wazuh."
weight: 3
---
![WAZUH_INTRO_1](/images/WAZUH_TUT/WAZUH_INTRO_1.png)
![WAZUH_INTRO_2](/images/WAZUH_TUT/WAZUH_INTRO_2.png)
![WAZUH_INTRO_3](/images/WAZUH_TUT/WAZUH_INTRO_3.png)
![WAZUH_INTRO_4](/images/WAZUH_TUT/WAZUH_INTRO_4.png)
![WAZUH_INTRO_5](/images/WAZUH_TUT/WAZUH_INTRO_5.png)

# Installing wazuh in ubuntu 20.04 LTS
1. step 1:
```bash
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```

2. This will take some time, and it will install all wazuh services, at the end it will provide the username and password of the wazuh server as well as in which port it is running.
![[Pasted image 20250725160156.png]]
3. Then you need to disable auto update wazuh using this command ->
```bash
sed -i "s/^deb /#deb /" /etc/apt/sources.list.d/wazuh.list
apt update
```

> [!note] 
>   You can find the passwords for all the Wazuh indexer and Wazuh API users in the `wazuh-passwords.txt` file inside `wazuh-install-files.tar`. To print them run the following command ->
>   ```bash
>   sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt

4. Now i will set up the wazuh agent inside a windows machine .
5. First install the wazuh GUI inside your windows machine using this doc page ![WAZUH_AGENT_INSTALLATION](/images/WAZUH_TUT/WAZUH_AGENT_INST.png)
source -> [wazuh-agent](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html)
1. Then use this command inside the command prompt of the windows machine 
```cmd
cd Downloads
wazuh-agent-4.12.0-1.msi /q WAZUH_MANAGER="wazuh_manager_IP"
```
1. For powershell -> 
```powershell
.\wazuh-agent-4.12.0-1.msi /q WAZUH_MANAGER="wazuh_manager_ip"
```
1. Or you can directly double click on the installer file and provide the wazuh manager IP address -> click on manage -> start
2. Onto the ubuntu machine wazuh manager refresh the page and you should see your agent running -> ![WAZUH_DASHBOARD_1](/images/WAZUH_TUT/WAZUH_DASHBOARD_1.png)
![WAZUH_DASHBOARD_2](/images/WAZUH_TUT/WAZUH_DASHBOARD_2.png)
