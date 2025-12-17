---
title: "Practical Demo: Linux Forensics"
date: 2025-11-06T19:00:00+05:30
weight: 3
draft: false
description: "A simple walkthrough of checking command history and system logs for suspicious activity."
tags:
  - "Forensics"
  - "Linux"
  - "Basics"
toc: true
---

## Volatile:
### Collecting hostname, date and time:
```bash
hostname
hostnamectl
date
cat /etc/timezone
timedatectl
```
![lf_1](/images/UNI_PRACS/INT_250/prac_2/lf_1.png)
![lf_2](/images/UNI_PRACS/INT_250/prac_2/lf_2.png)
### epoch time:
```bash
date +%s
```

### system uptime:
```bash
uptime
```

### Network information:
```bash
ip a # short form of ip addr show
ifconfig 

# promisc mode detection:
ifconfig eth0
ip link show eth0

# other network info commands:
netstat -i 
netstat -rn # routing tables
ip r # routing tables
```

### open port info:
```bash
nmap -sT localhost
nmap -sU localhost # UDP port

sudo lsof -i tcp # checking tcp listening connections of localhost
sudo lsof -n -P | grep LISTEN

netstat -tulpn
```

### listing current user's open processes:
```bash
sudo lsof -u user_name
```

### mounted file system info:
```bash
mount # info about file systems
df -h # file systems info but in human readable format
```
### kernel module info, sound driver info:
```bash
modinfo ufs # kernel module
modinfo snd # sound module info
```
### user event collection:
```bash
id
```
### Reading ELF file:
```bash
readelf -h file_name # file header reading
```
### running processes:
```bash
ps aux -ww
```
### swap area and disk partition info:
```bash
cat /proc/partitions # disk partition
cat /proc/swaps # swap info
```
### kernel message - kernel ring buffer info:
```bash
dmesg
```


## Non-volatile:
### Collecting system info:
```bash
cat /proc/cpuinfo
cat /proc/self/mounts
```

### kernel info:
```bash
uname -r
cat /proc/version
hostnamectl | grep Kernel
```
### local user account information:
```bash
cat /etc/passwd 
cat /etc/passwd | cut -d: -f1 # seperating users from the output
```
### logged on user information:
```bash
w
last # login history information
```
### collecting system logs:
```bash
cat /var/log/syslog
cat /var/log/kern.log # linux kernel logs
cat /var/log/fail.log
cat /var/log/mail.*
cat /var/log/mysql.*
cat /var/log/daemon.log
cat /var/log/debug

journalctl
```

### history and hidden file information:
```bash
history
ls -al # hidden files
```
### suspicious info:
```bash
sudo rkhunter --check --rwo
sudo chkrootkit # rootkit checker
```

### file signature analysis:
```bash
xxd file_name | head -n 10
```
### basic file information:
```bash
file file_name
strings -t -d file_name 

# finding writable files inside /var/log directory :
find / -writeable -type f 2> /dev/null | grep "/var/log" 
```
### Directory permission checking:
```bash
ls -ld Desktop
```


## File system analysis using The Sleuth Kit:
### Creating an file system image using dd:
> [!Important]
> Before that add a virtual hard disk of 1gb for testing purpose on your vm through vmware -> vm settings -> add -> hard disk -> SCSI -> Create new virtual disk -> 1 gb -> Done.



Then use the following guide.
```bash
sudo dd if=/dev/sdb of=/home/user_name/Desktop/virtual_disk.img bs=4M status=progress

# do every process as a root user
mkfs.ext4 Desktop/virtual_disk.img 
# mounting the file system
mkdir /mnt/my_image
mount -o loop Desktop/virtual_disk.img /mnt/my_image

# creating evidences
echo "This is a secret message" > /mnt/my_image/secret.txt
touch /mnt/my_image/evidence.dat

# unmount then
umount /mnt/my_image
```
![lf_3](/images/UNI_PRACS/INT_250/prac_2/lf_3.png)
![lf_4](/images/UNI_PRACS/INT_250/prac_2/lf_4.png)

### analysis:
```bash
# install sleuth kit
sudo apt install sleuthkit
sudo fsstat -i raw Desktop/virtual_disk.img
sudo fls Desktop/virtual_disk.img
istat Desktop/virtual_disk.img 12
```
![lf_5](/images/UNI_PRACS/INT_250/prac_2/lf_5.png)
