---
title: "Practical Suricata"
date: 2025-10-12T12:48:03+05:30
lastmod: 2025-10-12T12:42:03+05:30
draft: false
author: "0x-s0M3n4th"
tags: ["Blue Team", "Network Security", "IDS", "SOC"]
description: "A practical beginner-friendly guide to Suricata with custom detection rules including ARP spoofing and SSH brute-force logging."
weight: 4
---

1. Follow these commands step by step ->
```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt-get update
sudo apt-get install suricata
```
2. It will be installed directly.
3. Use the github repo `testmynids.org` to generate malicious traffic inside the network and monitor the alerts.
4. Or follow the next steps for some adventure , adding custom rules and basic testing methods.

---

## Generating custom rules in suricata:

### ARP request alerts:
1. Open the **suricata.rules** file, where we will add the rule:

```bash
sudo vim /var/lib/suricata/rules/suricata.rules
```

2. Add the following rule in your desired location inside the file:

```bash
alert arp any any -> any any (msg:"LOCAL Testnet ARP Scanning Detected"; threshold: type both, track by_src, count 15, seconds 5; sid:1000002; rev:1;)
```
**Command debrief: _"If any device sends 15 or more ARP packets within 5 seconds, generate an alert with ID 1000002."_**

![suricata_1](/static/images/Blue%20Team%20Ops/Suricata/suricata_1.png)

3. Enable the ARP capturing:
![suricata_2](/static/images/Blue%20Team%20Ops/Suricata/suricata_3.png)

4. Save and exit.
5. Restart suricata using the following command:
```bash
sudo systemctl restart suricata
```

_command screenshots:_
![suricata_4](/static/images/Blue%20Team%20Ops/Suricata/suricata_4.png)

6. Use the following command to generate traffic from anyother/same machine itself from terminal:
```bash
sudo netdiscover -r 192.168.83.0/24
```

7. We can see the logs comming in.
![suricata_5](/static/images/Blue%20Team%20Ops/Suricata/suricata_5.png)


### SSH bruteforce rule:
8. Next add custom rule for logging **SSH brute force attempts** 

```bash
alert tcp any any -> any 22 (msg:"LOCAL SSH Brute Force Detected"; flags:S; flow:stateless; threshold: type both, track by_src, count 5, seconds 30; sid:1000003; rev:1;)
```

- We are checking for the initial handshake of **TCP** which is the _SYN_ flag.
- count 5, seconds 30: Triggers if one IP tries to initiate 5 connections in 30 seconds.

![suricata_2](/static/images/Blue%20Team%20Ops/Suricata/suricata_6.png)

9. Again restart suricata after adding this rule.

---

## Integrating suricata with wazuh:

**I have integrated suricata logs directly inside wazuh, i'll share now how i did that. It's much easier to see the logs in a GUI pane rather than in a cli view.(my preference)**

> [!Note]
> You must have already configured wazuh properly.

1. Configuring the `Wazuh-agent` :
   - Open the agent config file ->

```bash
sudo vim /var/ossec/etc/ossec.conf
```
   - Search inside vim `<ossec-config>` , if you don't know how to search, simply press `/` and then write whatever you are looking for like this `/<ossec-config>`
   - Then look for `<localfile>` block and add the suricata log location :
```XML
<localfile>
  <log_format>json</log_format>
  <location>/var/log/suricata/eve.json</location>
</localfile>
```
   - Save and exit
1. Restart `wazuh-agent` using the following command:

```bash
sudo systemctl restart wazuh-agent
```

3. You can see the logs inside wazuh's overview tab. Also to filter `suricata` specific logs , on the global search bar use the following command:

```text
rule.groups:suricata
```



