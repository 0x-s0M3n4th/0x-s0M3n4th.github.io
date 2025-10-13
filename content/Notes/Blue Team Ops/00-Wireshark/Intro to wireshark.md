---
title: "Practical Wireshark"
date: 2025-10-12T11:26:03+05:30
lastmod: 2025-10-12T11:26:03+05:30
draft: false
author: "0x-s0M3n4th"
tags: ["Blue Team", "Lab"]
description: "A practical guide to using Wireshark for network analysis."
weight: 1
---
1. Wireshark: ![Wireshark-intro](/images/WIRESHARK_TUT/Wireshark-intro.png)

2. Packets: ![Packets](/images/WIRESHARK_TUT/Packets.png)
3. In a real world blue team operation usually the threat analysts are given with 'PCAP' files to analyze which systems are getting affected by the malware / what is the C2 server of the attacker/ where did the malware spread from which time, what's the IP of those infected systems etc. . . 
4. _What are PCAP files?_ -> PCAP file is a exported format of the captured data from Layer 2-7 of the OSI model by wireshark. We can share that captured data to anyone to analyze what happened within this timeframe in the network.
## Practical DEMO:
- Install the PCAP file from this page: [PCAP_FILE](https://github.com/AlexisAhmed/Wireshark-Traffic-Analysis) 
1. Open up wireshark -> `sudo wireshark` 
2. Display filters:
	1. Filtering `http requests` -> {http.request}
	2. Source IP filtering -> `ip.src==IP_ADDR` 
	3. HTTP,DNS,FTP,ICMP capture filter -> `http` , `ftp` , `dns` , `icmp` 
	4. `ip.addr == IP_ADDR && http.request.method == "POST/GET" ` 
	5. `http.host =="HOST_NAME"` 
	6. `eth.addr==MAC_ADDR` 
	7. We can filter out services using port number also -> `tcp.port==80/21/22/23/25/3306/445/139` 
3. Analyzing a PCAP file of infections regarding 'dridex' malware ->
	- `tls.handshake.type eq 1` ![PCAP](/images/WIRESHARK_TUT/PCAP_analyze_1.png)
	- right click on TLSv1.2 -> follow -> TCP stream ->  ![PCAP_2](/images/WIRESHARK_TUT/PCAP_analyze_2.png)
	- Everything is encrypted here.
	- Command used to identify the connections made from the client to execute the actual DLL -> `(http.request or tls.handshake.type eq 1) and !(ssdp)` 
	- We are having the TLS keys to decrypt them 
	- Identified the actual dll file -> ![PCAP_3](/images/WIRESHARK_TUT/PCAP_analyze_3.png)
	- We will export this file as an object file and then upload it on virus total -> ![PCAP_4](/images/WIRESHARK_TUT/PCAP_analyze_4.png)
	- Importing system32 files : ![PCAP_5](/images/WIRESHARK_TUT/PCAP_analyze_5.png)
	- Identified the C2 server  -> ![PCAP_6](/images/WIRESHARK_TUT/PCAP_analyze_6.png)
	- After executing the malware the client is acutally getting connected with the C2 server of the attacker.
	- Device identification using `nbns` {NetBios Name Service} -> ![PCAP_7](/images/WIRESHARK_TUT/PCAP_analyze_7.png)
