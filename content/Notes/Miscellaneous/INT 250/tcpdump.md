---
title: "Practical Demo: tcpdump"
date: 2025-11-05T20:15:00+05:30
weight: 2
draft: false
description: "A step-by-step walkthrough of capturing and filtering network traffic using tcpdump, a fundamental command-line tool for packet analysis."
tags:
  - "Networking"
  - "tcpdump"
  - "Packet Analysis"
  - "Traffic Sniffing"
toc: true
---

> [!Note]
> Tcpdump is a network sniffing tool. Same as Wireshark but tcpdump is CLI based.

## Practical usecase:
1. Listing all the network interfaces in our machine:
```bash
tcpdump -D
```
![tcp_1](/images/UNI_PRACS/INT_250/prac_3/tcp_1.png)
2. Sniffing traffic from our interface:
```bash
sudo tcpdump -i ens33{mention_your_own_interface_name}
```
_ICMP traffic(ping):_
`To get the desired output as shown use your kali machine to ping the machine which is running tcpdump`

![tcp_2](/images/UNI_PRACS/INT_250/prac_3/tcp_2.png)
_format of the traffic:_ {timeframe`{hh:mm:ss}:microsecond`} {source_ip} > {Destination_ip} {request/reply}, {id}, {sequence number} {data length}

_nmap SYN scan traffic:_

`To get the desired output as shown use your kali machine to run nmap to the machine which is running tcpdump. Used nmap command for this practical - {nmap -sS target_ip_running_tcpdump}`
 
![tcp_3](/images/UNI_PRACS/INT_250/prac_3/tcp_3.png)
_**Traffic format:**_ {timeframe`{hh:mm:ss}:microsecond`} {source_ip:source port} > {Destination_ip:destination_port} {Flags {SYN/S}} {packet sequence number} {window size} {maximum segment size/mss} {data length} 

1. Other useful commands of tcpdump:
```bash
tcpdump -c N # capturing N number of packets where N > 0
tcpdump -w captured_packet.pcap # capture the packets and write into a file
tcpdump -r captured_packet.pcap # reading from a pre-saved pcap file
tcpdump -ttt # capture packets with proper readable timestamp
tcpdump -i eth0 port 22 # capturing incoming traffic specific to ssh/port 22
tcpdump -i eth0 src 192.168.83.128 # capturing traffic those are having source ip as 192.168.83.128
tcpdump -i eth0 dst 192.168.83.145 # capturing traffic that are having destination ip as 192.168.83.145 
```
