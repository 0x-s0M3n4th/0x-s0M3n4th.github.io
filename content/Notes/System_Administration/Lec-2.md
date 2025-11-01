---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 1"
date: 2025-11-01T10:00:00+05:30
draft: false
weight: 2
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---

1. purpose of `touch` command →
    1.  creating a new file
    2.  changing / modifying the timestamp of a file
2.  `stat` command is used to show the timestamp of any file in directory.
3.  `touch {1..10}.txt` → creating simultaneous file at sme time
4.  Creating recursive directories altogether → `mkdir LPU/CSE LPU/ECE LPU/ME`
5.  `ls -R /LPU`


1.  `tty` → terminal interface
![SYSADMIN_1](/images/System_administration/Lec_1/Lec_1_ss_1_sysadmin.png)
2.  user info enumueration → `id`,`whoami`,`who`,`id`,`w`
3.  `logname` → to see current login name
4.  `uptime` → current session on system is active on how much time
5.   `last` → This command will provide us all successful login,logout and system reboot details

11.  `last b` → failed login details
![SYSADMIN_2](/images/System_administration/Lec_1/Lec_1_ss_2_sysadmin.png)
12.  `last log` → recent user login details

![SYSADMIN_3](/images/System_administration/Lec_1/Lec_1_ss_3_sysadmin.png)

1.  `uname -a` → kernel info 
2.   `last reboot` →
![SYSADMIN_4](/images/System_administration/Lec_1/Lec_1_ss_4_sysadmin.png)
1.   `uname -r` → kernel release , uname -v → kernel build date, uname -n →
![SYSADMIN_5](/images/System_administration/Lec_1/Lec_1_ss_5_sysadmin.png)
    kernel node name
1.   `uname -m` → machine arch info , uname -p → processor info , uname -o
![SYSADMIN_6](/images/System_administration/Lec_1/Lec_1_ss_6_sysadmin.png)
    → OS info 
![SYSADMIN_7](/images/System_administration/Lec_1/Lec_1_ss_7_sysadmin.png)
![SYSADMIN_8](/images/System_administration/Lec_1/Lec_1_ss_8_sysadmin.png)

1.   changing the hostname → `hostnamectl set-hostname MARVEL[the new name]`
2.   `timedatctl set-timezone Asia/Kolkata` → changing timezone


19.  `ls -ld` , `ls -li` - Listing inode number.