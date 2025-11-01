---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 9"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Access Control List(ACL): → used to give seperate diff permissions
    to diff individual users
    1.  getfacl → get file access control lists
        1.  getfacl FILE_NAME.txt
        2.  

![[Pasted image 20250724110722.png]]

1.  setfacl → setting file access control lists
    1.  setfacl -m u:USER_NAME:PERMISSION\[rwx\] FILE_NAME
        1.  -m = modify ACL
        2.  -x = Remove ACL
        3.  -K = Remove default ACL
        4.  -g = group permission
        5.  -o = ohter permission
2.  PRACTICAL:
    1.  

![[Pasted image 20250724110729.png]]

1.  \[Searching in linux\]
    1.  Locate → it uses mlocate database index , It is able to search
        files which are indexed by mlocate db
        1.  updatedb → for updating the database.
    2.  Find → it searches over full disk
        1.  ‘-name’
        2.  ‘-iname’
        3.  ‘-type’
        4.  ‘-size’
        5.  ‘-atime’
        6.  ‘-mtime’
        7.  ‘ctime’
        8.  ‘-user’
        9.  ‘-group’
        10. ‘-perm’
        11. ‘-exec’
            1.  

![[Pasted image 20250724110740.png]]

1.  

![[Pasted image 20250724110749.png]]

1.  SYNTAX : find \[path\] \[options\] \[argument\]
    1.  

![[Pasted image 20250724110755.png]]

