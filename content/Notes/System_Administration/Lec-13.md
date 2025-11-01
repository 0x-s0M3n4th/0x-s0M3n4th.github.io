---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 12"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Nework management:
    1.  TOOLS:
        1.  ip command
            1.  ip link show → list all interfaces
            2.  ip link set name_of_NIC up → to get up the network
            3.  ip link set name_of_NIC down → taking down the network
            4.  ip link set name_of_NIC promisc on → enabling the
                promiscious mode
            5.  

![[Pasted image 20251102004026.png]]

1.  ip addr show / ip a show → seeing ip address
2.  adding an address → ip addr add 192.168.1.10/24
3.  deleting and address → ip addr delete 192.168.1.10/24
4.  ip neighbour show

ifconfig

1.  ifconfig interface_name down/up

