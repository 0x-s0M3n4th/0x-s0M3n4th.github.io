---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 8"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  file basics :
    1.  stat file_name
    2.  Access time -> file reading time
    3.  modify time -> writing to the file time\[when we changed the
        file that time is called modify time\]
    4.  change time → when we change the meta data of the file like
        changing name etc.

![[Pasted image 20250724110708.png]]

1.  if we use touch to the same file again over to the same file → touch
    will modify every time except the birth time → attacker mostly use
    this technique.

Special permissions:

1.  setuid → Inherit owner permission
    1.  symbolic notation: u+s , u-s
    2.  Numeric value: 4
    3.  when you set setuid on an executable file , then anyone use that
        exe he gets the privileges of owner.
    4.  If setuid is enabled in any executable, all of the user present
        in the pc will have the root privilege while executing that
        particular executable.
2.  setgid → Inherit group permission
    1.  symbolic notation: g+s
    2.  numeric value: 2
    3.  if you enable setguid on any executable and directory , it will
        inherit the group automatically.
3.  stickybit → only owner can delete files even other's having the
    right permissions.
    1.  chmod +t Dir
    2.  Numeric value: 1
    3.  Deletion is only done by the owner. \[this is actually using
        regex/scripting in low level to find the owner name is actually
        executing the delete command or not, if not it won't execute\]

SSH:

1.  provide encrypted tunnel
2.  Works on client server model.
    1.  sshclient → It will always log in over to ssh server
    2.  ssh server
3.  auth methods:
    1.  pasword based
    2.  key based auth/passwordless \[public and private key\]
        1.  /autorized key → hold the public key allowed to connect
    3.  ssh username@IP_addr -p 22
    4.  ssh username@DOMAIN_NAME -p 22
    5.  default: ssh username@ip_addr/domain_name \[if you are using
        default port 22\]
4.  Log in method:
    1.  using private keys:
        1.  iMPORTANT FILES:
            1.  inside the ‘.ssh/authorized_keys' → contains the public
                key of the users who are allowed to login to the server
            2.  .ssh/known-host → it is located on the client machine →
                it is going to store the ssh public key of remote server

