---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 7"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Group management:
    1.  groupadd → for creating a new group
        1.  groupadd GRP_NAME → groupadd SALES
            1.  

![[Pasted image 20250724110517.png]]

1.  cat /etc/group | tail -2
    1.  

![[Pasted image 20250724110522.png]]

1.  groupadd -g 1111 TECH → ‘-g’ means giving custom gid
    1.  

![[Pasted image 20250724110531.png]]

1.  

![[Pasted image 20250724110542.png]]

1.  groupmod → modifying the groups
    1.  groupmod -n NEW_NAME OLD_GRP_NAME → modifying group name
        1.  

![[Pasted image 20250724110548.png]]

1.  

![[Pasted image 20250724110553.png]]

1.  groupmod -g NEW_GID OLD_GID → modifying group id
    1.  

![[Pasted image 20250724110606.png]]

1.  

![[Pasted image 20250724110611.png]]

1.  groupdel → deleting a group
    1.  

![[Pasted image 20250724110617.png]]

1.  

![[Pasted image 20250724110622.png]]

1.  Adding members into Groups:
    1.  gpasswd → set group password, add user in group , Remove user
        from group , Assign group admin
        1.  ‘-a’ → adding user in group
        2.  ‘-d’ → deleting a user from group
        3.  ‘-A’ → set Administrator
        4.  ‘-r’ → remove password
        5.  If no option is given -> by default it will set group
            password.
    2.  Proper Syntax →
        1.  gpasswd -a USER_NAME GROUP_NAME \[adding\]
            1.  

![[Pasted image 20250724110629.png]]

1.  gpasswd -d USER_NAME GROUP_NAME \[deleting\]
    1.  

![[Pasted image 20250724110636.png]]

1.  gpasswd -A USER_NAME GROUP_NAME \[admin adding\]
2.  gpasswd GROUP_NAME → setting group password
3.  gpasswd -r GROUP_NAME \[removing\]

Permissions :

\[File\] \[Dir\]

1.  R → content of a file Listing of files in a directory
2.  W → Modify file's content Create and delete files from a directory
3.  X → Executing the file cd command
4.  

<table class="table">
<thead>
<tr>
<th>Roles</th>
<th>symbolic permission</th>
<th>Numeric</th>
</tr>
</thead>
<tbody>
<tr>
<td>u=user</td>
<td>r</td>
<td>4</td>
</tr>
<tr>
<td>g=group</td>
<td>w</td>
<td>2</td>
</tr>
<tr>
<td>o=other</td>
<td>x</td>
<td>1</td>
</tr>
<tr>
<td>a=all[u,g,o]</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

1.  
2.  

![[Pasted image 20250724110646.png]]

1.  Assigning permissions using symbolic →
    1.  chmod → command used for changing user's permissions
        1.  chmod u+rw FILE_NAME
    2.  chmod g+r FILE_NAME
    3.  chmod o+rwx FILE_NAME
    4.  chmod u+rwx,g+rw,o+r file.txt
2.  Operators:
    1.  \+ → assign
    2.  \- → revoke
    3.  = → overwrite
3.  

![[Pasted image 20250724110652.png]]

4. Modify the global login scripts. Normal users should have a umask setting that prevents others from viewing or modifying new files and directories -> create this file -> `/etc/profile.d/local-umask.sh`
```bash
# Overrides default umask configuration
if [ $UID -gt 199 ] && [ "`id -gn`" = "`id -un`" ]; then
    umask 007
else
    umask 022
fi
```
-> set the umask to `007` for users with a UID greater than `199` and with a username and primary group name that match, and to `022` for everyone else: