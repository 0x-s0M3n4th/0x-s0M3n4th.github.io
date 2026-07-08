---
title: Directory Basics 
date:  2026-07-06T12:12:10+05:30
params:
    author: 0x-s0M3n4th
draft: false
weight: 3 
tags: ["Linux", "Basics"]
---

## pwd(Present working Directory):
- It shows the a user’s current working directory.
- `pwd` always returns the absolute path. 
![img_1](/images/System_administration/Chap-1/03_img_1.png)

- - -
## Navigating directories:

- `Absolute path:` It is the full path starting from the top level path which is `/` to my current working directory. The `absolute path` will always start with `/` at the beginning.
- `Relative path:` It is not a full path but rather a path which depicts the location relative to our own current working directory. 
- For example: we are in `/home/user1` directory. To move upwards either we can write using the `relative path` like this → `cd Desktop/` , or we can write using `absolute path` like this → `cd /home/user1/Desktop/` 
![img_2](/images/System_administration/Chap-1/03_img_2.png)

![img_3](/images/System_administration/Chap-1/03_img_3.png)

### To go back to home directory:
- Use the command `cd` or `cd ~` 
![img_4](/images/System_administration/Chap-1/03_img_4.png)

### Switching between current and previous directories:
- Command → `cd -` 
![img_5](/images/System_administration/Chap-1/03_img_5.png)

## Viewing directory hierarchy:
### `tree` command:
- `tree -a` → Includes hidden files in the output.
  ![img_6](/images/System_administration/Chap-1/03_img_6.png)
- `tree -d` → excludes files from the output.
  ![img_7](/images/System_administration/Chap-1/03_img_7.png)
- `tree -h` → Displays file size in a human readable format.
  ![img_8](/images/System_administration/Chap-1/03_img_8.png)
- `tree -f` → prints the full path of each file.
  ![img_9](/images/System_administration/Chap-1/03_img_9.png)
- `tree -p` → prints file permissions in the output.
  ![img_10](/images/System_administration/Chap-1/03_img_10.png)
