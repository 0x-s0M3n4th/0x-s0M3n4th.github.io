---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 6"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Disabling shadow configs for /etc/passwd:
    1.  set password for the user first → `passwd lpu101 student_5455@#%`
    2.  `pwunconv`
    3.  cat /etc/passwd → it will show user passwords and disable shadow
        folder
    4.  for enabling shadow configs → `pwconv` → This is going to again
        enable
    5.  

![[Pasted image 20250724110225.png]]

1.  

![[Pasted image 20250724110231.png]]

1.  Password management:
    1.  passwd → changing password , manage age attributes → \[Regular
        user can create password for own account, but Root user can do
        for all account\]
        1.  Root user:
            1.  `passwd USER_NAME` → e.g `passwd lpu` \[This will never ask
                for old pass as it's executed via root user\]
            2.  `passwd -e lpu` \[for expiration as soon as the user
                login\]
            3.  `passwd -n User_name {minimum validity of pass}`
            4.  `passwd -x User_name {maximum validity of passwords}`
            5.  `passwd -i User_name [inactive days]`  ##refer to Lec -
                6 for more revision
            6.  passwd -L USER_NAME \[locking the account\]
            7.  passwd -U user_name \[unlocking account\]
    2.  chage → control age info of password\[validity,expiration
        details\]
        1.  chage -l USER_NAME
        2.  chage -m 2 \[It means nobody is allowed to change the
            password btw 48 hrs\]
        3.  chage -M 100 USER_NAME\[max age/validity of the password is
            100 days\]
        4.  chage -W 5 USER_NAME \[warning day\]
        5.  chage -I 10 USER_NAME \[inactive day\] → in 110th day my
            account will get blocked if i don't change password till
            109th day
        6.  chage -E 2026-01-31 USER_NAME → expiry date of the account
        7. In the scenario of account expiry, we need to calculate the future dates to set the expiration date. For example to expire the account after 90 days , now to calculate this we can use this command -> `date -d "+90 days" +%F` then use this -> `sudo chage -E the_date account_name` 
    3.  Default location from where default configs are added into new
        users by default → cat /etc/login.defs
	4. We can directly set the maximum password inside the`/etc/login.defs` file -> `sudo vim /etc/login.defs` ->change the `PASS_MAX_DAYS` option to your need.
<!-- -->

1.  Switching users :
    1.  `SU - Username` → SU - lpu101 → it will switch along with the env
        variable of the target user
    2.  `SU Username` → The env variable will remain same as the current
        user not the target user.
    3. `sudo -i` -> This will switch to the `root` account and run that user's default shell (usually **bash**) and associated shell login scripts. 
    4. The command **su** starts a _non-login shell_, while the command **su -** (with the dash option) starts a _login shell_. The main distinction between the two commands is that **su -** sets up the shell environment as if it were a new login as that user, while **su** just starts a shell as that user, but uses the original user's environment settings.
    5.  Sudoers file → specifically configure any user's permission over
        to the commands:
        1.  location → /etc/sudoer
        2.  

![[Pasted image 20250724110241.png]]

1.  Adding user in sudoer file :
    1.  Login in root account
    2.  visudo
    3.  user_name ALL = (ALL:ALL) ALL → All hosts \[local / Ip based
        remote login\] | (All type of users : Groups ) | User can use
        all the commands \## ‘|’ → is used for seperation
	4.  
![[Pasted image 20250724110246.png]]
2. Separate way to add users into the `sudoers` files : when we add a user we can make a sudoers file for them separately, for example i have created a user named ram -> now observe :
```bash
echo "%ram ALL=(ALL) ALL" >> /etc/sudoers.d/ram
```

