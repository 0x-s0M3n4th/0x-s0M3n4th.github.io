---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 2"
date: 2025-11-01T10:00:00+05:30
draft: false
weight: 3
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  which → Exact location of the exeutable file
2.  whereis → local documentation
3.  Linux help commands :
    1.  man → manual pages , docs of the command → we must aware about
        the exact command name of the command
        1.  Total 9 categories of the man pages are available
            1.  exe , config , kernel files etc categories.
        2.  If man doesnot work for newer systems we need to update the
            ‘man’ databse → sudo mandb
        3.  man man
        4.  man -k ANY_COMMAND_YOU_KNOW_PARTIALLY like password

![SYSADMIN_9](/images/System_administration/Lec_2/Lec_2_ss_1_sysadmin.png)

4.  man 5 shadow

whatis → short description about the commands → exact command

apropos → short description about commands → keywords

5.  This works same as man -k

info → Documentation

pinfo → Docs → GUI of info command , but we need to use arrow to
navigate

![SYSADMIN_10](/images/System_administration/Lec_2/Lec_2_ss_2_sysadmin.png)

6.  cd - → This used for switching between CWD and Previous working dir
    1.  cd . → Current directory pointer
7.  Absolute path → Full path means starting from root to destination
    location
8.  Relative path means we need to start from the location we are
    currently are now to the destination location.
9.  Viewing the contents of the file:
    1.  cat
    2.  head
        1.  By default it is going to show the top 10 lines of the file
    3.  tail
    4.  less → line by line scrolling of the output
    5.  more → percentage of screen filling content

