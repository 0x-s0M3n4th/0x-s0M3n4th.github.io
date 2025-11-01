---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 5"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Users:
    1.  with the help of users we are able to provide role based access
        control
    2.  Strict security boundaries
    3.  TYPES OF USERS :
        1.  Admin/root/super user \[UID = 0, when uid is 0 that means
            it's the most privileged user of the system.\]
        2.  System user → Related to services like FTP,SSH,web services
            \[UID = 1 to 999\]
        3.  Regular user account → Usernames \[Uid will varry from
            >=1000\]
        4.  With the help of id command we can get the details about the
            UID
    4.  Modification of file and directories:
        1.  /etc/passwd → List of all users
            1.  

![[Pasted image 20250724110114.png]] -> User name | Password shadow | UID | GID\[groupid\] | Comment | Path of home directory | Type of shell >

1.  etc/shadow → assign user password
    1.  

![[Pasted image 20250724110121.png]]

1.  username | encrypted pasword | The day when the password last
    changed \[Epoch time → (jan 1 1970 - last password change date)\] |
    Minimum number of days between password change \[for example , there
    is written ‘2’ → we can't change the password before 48hrs/2days\] |
    max age of the password | Number of password warning days before
    expiry\[like before 7 day of the expiry warnings will come\] |
    Inactive period \[after the expiry of the password till how many
    days we can change our password or else the account will be locked
    by the sysadmin\] | Account expiry date \[after how many days
    accounts will expire\] | Future use

/etc/group → when we create a new user account and by default a new
group will be created and stored over to this directory

1.  

![[Pasted image 20250724110156.png]] Group name | group password | GID | group members

1.  Dir -> /etc/skel → Basic configuration files will be copied from
    this dir \[when we create a new user the files present in /skel will
    get copied over to the new user's directory /home/NEW_USER\]
    1.  

![[Pasted image 20250724110203.png]]

1.  managing user accounts:
    1.  Useradd : Add new user → useradd option user_name → useradd
        somnath \[This will create a user without home directory\] →
        useradd -m somenath \[his will create a user with home dir\] →
        -d : change path of home directory → -c : making user with
        comment
    2.  usermod :
        1.  

![[Pasted image 20250724110209.png]]

1.  userdel : userdel -r user_name

Important options useradd/usermod :

1.  1.  -m → create home dir
    2.  -d → path of home directory
    3.  -u → change userid / create user with given user id
    4.  -g → change group id / create user with given group id
    5.  -L → locking given account → usermod
    6.  -U → unlocking account → usermod
    7.  -s → changing the shell
    8.  -e \[format-> YYYY-MM-DD\] → changing the expiry date of any
        user
    9.  -c → giving comments along with the user

