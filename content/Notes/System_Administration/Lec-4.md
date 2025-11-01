---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 3"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Terminal shortcuts :
    1.  CTRL + a → It is going to jump my cursor to the beginning of the
        command line
    2.  CTRL + e → End of command line
    3.  CTRL + k → Cut from the specific location's words of the command
        using the cursor
    4.  CTRL + r → Search the command history in that terminal
    5.  executing command from history → \[!COMMAND_NUMBER\]
    6.  CTRL + arrow keys\[left,right\] → use to move my cursor word by
        word
2.  Deleting files and directories :
    1.  Deleting file → rm FILE_NAME
    2.  Deleting directories → rmdir DIRECTORY_NAME → This is used to
        delete empty directory
    3.  rm -r DIR_NAME → Delete Non-empty directories
    4.  rm -rf DIR_NAME → Forceful Deletion of all files inside
        directories
3.  Wildcards :
    1.  ‘ \* ’ → all matching
    2.  ‘ ? ’ → Match one character , ‘??’ → match two chars → It is
        used for exact match
    3.  ‘\[ \]’ → for example we are having two files named a.txt and
        b.txt → ls \[ab\].txt → either starting from a.txt or b.txt
    4.  We can combine all three according to our convinience
4.  Copy command \[cp\] :
    1.  cp SOURCE_PATH DESTINATION_PATH → cp abc.txt /home/Downloads
    2.  cp -r → recursive copy → used for diretory copying
    3.  cp -i → ‘i’ interactive copy → for example if we are
        overwritting a file by copying it will give us a warning
    4.  cp -p → Preserve attributes like permission,timestamp,all other
        etc..
    5.  cp -v → more readability detailed output
    6.  cp -u \*.txt DESTINATION_PATH → copying only unique files from
        the SOURCE dir
5.  Move command :
    1.  File is get deleted from Source while using the ‘mv’ command /
        moving from source to dest
    2.  -i → Prompt before overwrite
    3.  -v → verbose output
    4.  -f → forcefully moving
6.  Managing links :
    1.  

![[Pasted image 20250724110059.png]]

