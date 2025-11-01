---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 14"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---

1.  nmcli → Network manager command Line interface
    1.  nmcli general status
    2.  nmcli device → all NICs →

![[Pasted image 20251102004114.png]]

1.  nmcli device show INTERFACE_NAME →

![[Pasted image 20251102004120.png]]

1.  nmcli device wifi list
2.  nmcli device wifi connect “SSID” \[wifiname = SSID\]
    “password_of_your_system”
3.  nmcli device disconnect INTERFACE_NAME\[ens33\] → disabling to an
    interface\[NIC\]
4.  nmcli device connect INTER_FACE_NAME → enabling to an
    interface\[NIC\]
5.  nmclie connection show →

![[Pasted image 20251102004129.png]]

1.  ADD STATIC IP ETHERNET\[wired\] CONNECTION:
    1.  nmcli connection add type ethernet con-name RH_01 ifname ens33
        ipV4 192.168.83.129/24 gw4 192.168.83.2 \[for ipv4 -> gw4,
        ipv6 -> gw6\]
    2.  nmcli connection delete con-name RH_01
    3.  nmcli networking off
    4.  nmcli networking on / systemctl restart networkmanager → used to
        restart network manager \[alternative to the nmcli command\]
    5.  nmcli connection monitor ens33 → monitoring the connection
    6.  systemctl restart NetworkManager

Major directories available for netrowrking:

1.  /etc/sysconfig/network-scripts → config files for the network NICs
    \[for RHEL\]
2.  /etc/sysconfig/network → store the global network settings -> for
    RHEL
3.  /etc/NetworkManager → all the network management files are stored
    here.
4.  /etc/resolve.conf → DNS information
5.  /etc/hosts → Local hostnames → Here the IPs are resoluted with the
    Domain name
6.  /etc/nsswitch.conf → Defines the order of DNS Name Resolution → the
    time of resolving Domain names with ip addresses in which file it is
    going to search first -> either /etc/hosts and then
    /etc/resolv.conf or vise versa.

Socket stats → ss command

1.  IP_ADDR:PORT_NUM = socket
2.  ss -t → To check the TCP connections
3.  ss -t -a
4.  ss -l → show all the listeneing port
5.  ss -lt → listening TCP ports
6.  ss -lu → Listening UDP ports and connections
7.  ss -s → summary of connections

