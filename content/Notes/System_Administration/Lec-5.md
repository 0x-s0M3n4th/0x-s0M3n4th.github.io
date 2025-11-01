---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 4"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---

1.  Soft links:
    1.  ln -s
    2.  It is also called symbolic links
    3.  With the help of soft links , we can link two files on different
        file systems
    4.  Soft link can point out the directory/special files
    5.  In the case if soft links both the files and softlinks have
        different inode numbers
    6.  syntax: ls -s file_dir softlink_file
    7.  If we delete the softlink main file , we can't access the data
        of the file
2.  Redirection operator: \[Give us the capability to manipulate i/o\]
    1.  ‘0’ → used for stdin
    2.  ‘1’ → stdout
    3.  ‘2’ → stderr
    4.  ‘>’ → overwrite
    5.  ‘>>’ → append
    6.  ‘2>’ → Error redirection → only error message will get
        redirected
3.  pipping → ‘|’ → cat /etc/shadow | head -15 | tail -1
4.  Text editors:
    1.  nano
    2.  vi → most used \[CTRL + o, ctrl + x, ctrl + w\]
        1.  By default command mode
        2.  insert mode\[i\]
        3.  CLI mode \[exc:\] → operations \[search. search and
            replace\]
        4.  
    3.  Gedit
    4.  emacs
5. Vim tips:
	1. `Line based visual mode` -> press `shift + v` , navigate using arrow keys. After selecting press `x` to delete the lines.
	2. `single line based editing` -> press `v` select line ,and remember to place the cursor on a certain place from where you want to delete and then press `v` . After selecting press `x` to delete.
	3. `Multi line based editing` -> press `ctrl + v` to enter visual block mode and select then delete using `x` 
6. Command line tip to add date inside a filename ->
```bash
cp editing_final_lab.txt editing_final_lab_$(date +%s).txt
```
