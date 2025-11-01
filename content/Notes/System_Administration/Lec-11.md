---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 10"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  File archiving:
    1.  It means group of files or directories etc.....
    2.  ‘tar’ command:
        1.  SYNTAX: tar option arguments
            1.  ‘-c’ → create
            2.  ‘-f’ → Files
            3.  ‘-j’ → compression\[bzip\]
            4.  ‘-r’ → appending a files
            5.  ‘-t’ → list the content of tarwall
            6.  ‘-x’ → extracting a file
            7.  ‘-z’ → compression\[gzip\]
        2.  practical:
            1.  

![[Pasted image 20251102003659.png]]

1.  

![[Pasted image 20251102003706.png]]-> seeing the content of the .tar file

1.  Appending and deleting files from the .tar archive:
    1.  

![[Pasted image 20251102003715.png]]

1.  Extracting:
    1.  tar -xf lpu.tar\[.tar file\]
    2.  Extracting into a directory: tar -xf lpu.tar -C
        /home/\[DIR_PATH\]
2.  Compression: It means reducing the size of file .tar
    1.  bzip2 :
        1.  bzip2 lpu.tar → to know info about the zip file → file
            lpu.tar.bzip2
        2.  gzip lpu.tar
3.  Decompression :
    1.  gzip -d lpu.tar.gz
    2.  bzip2 -d lpu.tar.bzip2
4.  Archieving + compression :
    1.  tar -cjf lpu1.tar.bzip2 new.txt new2.txt\[Files\]
    2.  tar -czf lpu2.tar.gz FILE_NAMES\[seperated by space\]

Process:

1.  

![[Pasted image 20251102003819.png]]

1.  Running → R
2.  stopped → T
3.  Zombie → z/x
4.  Practical:
    1.  ping 127.0.0.1 -> ctrl+z / ‘bg’ command for stopping the
        process, ctrl+c used for killing the process
    2.  jobs
    3.  fg \[job_num\]
    4.  

![[Pasted image 20251102003829.png]]

1.  ps aux
2.  

![[Pasted image 20251102003837.png]]


