---
title: Identifying terminal devices 
date:  2026-07-06T12:13:10+05:30
params:
    author: 0x-s0M3n4th
draft: false
weight: 4
tags: ["Linux", "Basics"]
---

- Linux allocates unique pseudo (or virtual) numbered device files to represent terminal sessions opened by users on the system. It uses these files to communicate with individual sessions. By default, these files are stored in the **/dev/pts** (<mark style="background:#ff4d4f">pseudo terminal session</mark>) directory. These files are created by the system when a user opens a new terminal session and they are removed on its closure.
- We can see it via the command `tty(teletype)` 
  ![img_1](/images/System_administration/Chap-1/04_img_1.png)
