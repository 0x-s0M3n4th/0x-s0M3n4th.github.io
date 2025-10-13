---
title: "Practical Snort"
date: 2025-10-12T12:17:03+05:30
lastmod: 2025-10-12T12:42:03+05:30
draft: false
author: "0x-s0M3n4th"
tags: ["Blue Team", "Lab"]
description: "A practical guide to use Snort."
weight: 2
---
![SNORT_INTRO_1](/images/SNORT_TUT/SNORT_INTRO_1.png)
### How snort works:
![SNORT_INTRO_2](/images/SNORT_TUT/SNORT_INTRO_2.png)

### snort IDS network implementation:
![SNORT_INTRO_3](/images/SNORT_TUT/SNORT_INTRO_3.png)

### Lab environment:
![SNORT_LAB_ENV](/images/SNORT_TUT/SNORT_LAB_ENV.png)
- we are not going to use this lab env just for the sake of simplicity of this excersise.

### Installing snort on ubuntu 20.04 LTS :
1. Before installing make sure `promisc` mode is on. While installing you will be prompted with to provide the `interface` name and `subnet range` 
```bash
sudo apt-get install snort -y
cd /etc/snort # The snort config files are sotred there only
```

2. Now we need to make a backup of the snort config files -> to copy the file we need to have elevated privileges.
```bash
cp snort.conf snort-backup.conf
```
![SNORT_FOLD_STRUCT](/images/SNORT_TUT/SNORT_FOLD_STRUCT.png)
1. We are going to make most of the changes inside the `snort.conf` , the first thing we need to do is to setup the subnet-range that will be used by snort ->
```bash
vim snort.conf
```
![SNORT_CONF](/images/SNORT_TUT/SNORT_CONF.png)
1. Now we need to disable all the community rules provided inside the config files as we are going to make our own rules. Comment down all the community rules.
![SNORT_RULE_1](/images/SNORT_TUT/SNORT_RULE_1.png)
2. Except the local rules file, comment everything below it, till this line ->
![SNORT_RULE_2](/images/SNORT_TUT/SNORT_RULE_2.png)
3. After  that we will set up our own rules. Come inside the `rules` folder, there will be a file named `local.rules` ->
```bash
vim /rules/local.rules
```
1. I have made a first rule for detecting `ICMP` packets inside our network ->
![SNORT_LOC_RULE_1](/images/SNORT_TUT/SNORT_LOCAL_RULE_1.png)
2. Breakdown of the command ->
	- `alert` -> It is used for sending an alert when ICMP packets will get detected.
	- `icmp` -> protocol name, also ping sweeps essentially utilizes ICMP requests. 
	- `any` -> The first 'any' is to detect incoming ICMP request from any external network.
	- `any` -> second 'any' is to detect request coming from any port.
	- `$HOME_NET` -> This means any ICMP ping is coming to our home network, which has been configured inside the `snort.conf` file. Remember the subnet range.
	- `any` -> Here we usually specify the port number, as `ping` does not utilize any specific port that's why we are setting it as 'any' port.
	- After this we need to specify an alert message -> `(msg: "YOUR MESSAGE" ` 
	- `sid` -> signature id, provide any unique value
	- `rev` -> Revisions for specified rules.
3. Now we need to run snort ->
```bash
snort -q -l /var/log/snort/ -i ens33 -A console -c /etc/snort/snort.conf
```
1.  Then ping from any device to any other device within your network subnet, it will capture those pings and give us alerts.
![SNORT_RESULTS_1](/images/SNORT_TUT/SNORT_RESULTS_1.png)
1.  Now i will setup another rule for ssh auth ->
```bash
vim /etc/snort/rules/local.rules
```
1.  Rule ->
![SNORT_RULE_3](/images/SNORT_TUT/SNORT_RULE_3.png)
1.  In this scenario i am using a vulnerable machine `metasploitable2`
2.  Now start snort again with the same command.
3.  Then i will ssh from my kali machine to 'metasploitable2' 
![SNORT_RESULTS_2](/images/SNORT_TUT/SNORT_RESULTS_2.png)
-> And everything is detected.
## SNORPY tool:
1. Making of an `ftp` alert message using `snorpy` tool specifically for traffic coming inside the `metasploitable2` machine -> 
![SNORPY](/images/SNORT_TUT/SNORPY.png) 
2. Adjust the rules and Copy paste it inside the local.rules file.
![SNORT_RULE_4](/images/SNORT_TUT/SNORT_RULE_4.png)
3. I ftp'ed inside the vulnerable machine and snort detected it->
![SNORT_RESULTS_3](/images/SNORT_TUT/SNORT_RESULTS_3.png)

# Community rules ->
1. If you want to download the snort community rules ->
![COMM_RULE_1](/images/SNORT_TUT/COMM_RULE_1.png)
2. Extract the rules, and you can use the community rules by copying pasting them directly inside your `snort.conf` 
![COMM_RULE_2](/images/SNORT_TUT/COMM_RULE_2.png)
3. snort rule for `Eternal blue` exploit ->
![COMM_RULE_3](/images/SNORT_TUT/COMM_RULE_3.png)
4. If you want to store your logs into an alert file, don't want to be shown in the screen then use this option ->
```bash
snort -q -l /var/log/snort/ -i ens33 -A fast -c /etc/snort/snort.conf
```
5. This will store the logs into `/vat/log/alert` file, and it won't show the output over to the display.

> [!TIP]
> To edit bulk lines in vim use this format `:563,695s/^/#/` ':starting_line,last_line{s}/^/character_you_want_to_add{#}/'
