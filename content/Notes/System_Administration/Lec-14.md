---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 13"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  IPV4:
    1.  32 bit address → divided into 4 octets each of 8 bit
    2.  octet\[1\] : octet\[1\] : octet\[3\] : octet\[4\]
    3.  0-255 0-255 0-255 0-255
    4.  Class-A → \[0-127\] → Unicast → 255.0.0.0 → /8 → ‘0.0.0.0' is
        reserved for DHCP client
    5.  Class-B → \[128-191\] → Unicast → 255.255.0.0 → /16
    6.  Class-C → \[192-223\] → Unicast → 255.255.255.0 → /24
    7.  Class-D → \[224-239\] → used in Multicasting
    8.  Class-E → \[239-255\] → Reserved
    9.  Network id bits are by default represented by → 1
    10. Host id bits are by default represented by → 0
2.  IPV6:
    1.  types:
        1.  Global unicast → public ip
        2.  unique local \[Fe00/7\] → communication between 2 subnets
        3.  Link local \[Fe80/10\] → communication within subnet
        4.  Localhost → ::1 → scope resolution\[we can use it only once
            on thr longest sequence\]

