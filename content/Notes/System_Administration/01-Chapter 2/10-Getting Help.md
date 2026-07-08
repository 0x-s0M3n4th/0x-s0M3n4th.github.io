---
title: How to get help when you are stuck in any command? 
date:  2026-07-06T12:10:10+05:30
params:
    author: 0x-s0M3n4th
draft: false
weight: 10 
tags: ["Linux", "Basics"]
---

## man pages:
- ![img_1](/images/System_administration/Chap-1/10_img_1.png)
- ![img_2](/images/System_administration/Chap-1/10_img_2.png)
- `Press h` to get help on navigation, `press q` to quit and return to the command prompt, use the `Up and Down arrow keys` to scroll up and down, and the `PgUp` and `PgDn` keys to scroll one page at a time.
- KEYS WHICH  CAN HELP IN NAVIGATION:
	- ![img_3](/images/System_administration/Chap-1/10_img_3.png)
## apropos command:
- It is alias of the command `man -k {half_remembered_cmd_name}` → This command allows us to perform keyword search on manual pages incase we have forgot what the command name is.
> [!Note]
>  Before we run the keyword search we need to run the command `mandb`
- Once you have identified the command you were looking for, you can check that command’s manual pages for usage.

## `--help` :
- Some commands also support the use of the **--help and -?** parameters. These parameters provide a brief list of options and a description without going through the manual pages. For example, to get quick help on the passwd command, run either **passwd --help or passwd -?**

## Short description:
- The `whatis` command searches for a short description of the specified command or file in the manual database. It quickly scans through the installed manual pages for the specified string and displays all matching entries.
![img_4](/images/System_administration/Chap-1/10_img_4.png)
- You may alternatively run `man -f yum.conf` and `man -f passwd` for the exact same results. Both `man -f and whatis` produce identical output.
## Documentation in the /usr/share/doc directory:
- Checking the documentation of `gzip` 
![img_5](/images/System_administration/Chap-1/10_img_5.png)

## RHEL portal:
- The website at `docs.redhat.com` hosts documentation for Red Hat’s various products including RHEL 9 in `HTML, PDF, and EPUB` formats.
