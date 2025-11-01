---
title: "SYSTEM ADMINISTRATION TUTORIAL SERIES - Part 11"
date: 2025-11-02T18:45:11+05:30
draft: true
weight: 1
# tags: ["system administration", "Linux"]
params:
  author: 0x-s0M3n4th
---
1.  Monitoring and managing Linux processes:
    1.  

![[Pasted image 20251102003949.png]]

1.  ps :
    1.  ps aux →
        1.  ‘-a’ : all
        2.  ‘-u’ : users
        3.  ‘x’ : list the process which are running in all the sessions
            , including all the users .
        4.  ps aux | grep “root”
    2.  ps -au :
        1.  it will only show the process of specific user who is
            executing the command
        2.  systemd is the process whose PID is always 1.
    3.  top command:
        1.  Interactive process shower , live processes
        2.  ‘-20’ is the highest priority and ‘19’ is the lowest
            priority value. range \[-20 to 19\]
            1.  with the help of ‘nice’ command we can assign priority
                values to processes
                1.  sudo nice -n -19 top
                2.  

![[Pasted image 20251102003957.png]]

1.  we can use ‘renice’ to change the priority value
    1.  sudo renice -n -18 24903\[PID_of_the_process\]
    2.  

![[Pasted image 20251102004004.png]]

1.  pidof , pgrep commad:
    1.  pidof cat : pidof PROCESS_NAME → we need to know exact details
        of the process
    2.  pgrep PROCESS_NAME → it is used for searching for when i don't
        have exact detais of the process
2.  /proc in this directory where every process is stored :
    1.  for example we have started a process -> cat
    2.  Then we will go into /proc → cd /proc/
    3.  do an ls
    4.  pidof cat → it will show the pid
    5.  cd PID_of_cat
    6.  ls
    7.  cat maps → there will be information about heap, we can use it
        to perform attacks like buffer overflow etc...
3.  ‘|| -> or operator’ , ‘&& -> and operator’
    1.  ‘||’ is used when only one situation is correct .
        1.  ls -al lpu10200101010.txt || pwd
    2.  ‘&&’ is used when both situations are correct.
        1.  ls -al lpu10200101010.txt && pwd
4.  we can use ‘;’ to seperate multiple commands altogether:
    1.  ls;pwd;ps;top
5.  Backgrounding processes:
    1.  ps aux &
6.  ‘kill’ command:
    1.  

![[Pasted image 20251102004012.png]]

1.  Graceful termination: kill -19 PID → it will stop the process
2.  kill -18 PID → resuming the process
3.  Forcefully killed → kill -9 PID

Daemons:

1.  Types:
    1.  service unit files → for controlling services like FTP,SSH etc
    2.  socket unit → represents IPC sockets → when a socket recieves
        connection
    3.  path unit →
2.  systemctl list-unit-files → to list various types of unit files
3.  To see all the daemons : systemctl list-unit --type=service
4.  To see all the sockets : systemctl list-unit --type=socket
5.  To see all the path : systemctl list-unit --type=path
6.  To see all the target : systemctl list-unit --type=target
7.  How to control any service / daemons using systemctl:
    1.  systemctl status ssh , if it's disabled by default we can enbale
        it using → systemctl enable ssh, to remove it systemctl disable
        ssh
    2.  to reload → systemctl restart sshd, systemctl reload sshd

LOGGING:

1.  directories: /var/log → it contains all the logs
2.  /var/log/secure → contains the security and authentication logs
3.  /var/log/mailog → syslogs related to mail server
4.  /var/log/message → most major system logs are contained here
5.  /var/log/boot.log → it contains booting related logs

