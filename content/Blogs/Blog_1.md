---
title: "Why i choose books over certs!"
date: 2025-10-19T18:45:11+05:30
draft: false
weight: 2
# tags: ["red team", "Penetration Testing"]
params:
  author: 0x-s0M3n4th
---
Radhe Radhe!
This is going to be a very raw blog, mostly about what I am going to post in the next few months, and what I have been doing for the past few weeks.
So, _let's start with what I was doing..._
After completing `eJPT` certification and learning the basics as well as core concepts of `system administration`, I got my hands dirty on `CTF platforms` like `HTB`. I took a one-month subscription just to get the experience of it. But not gonna lie, it was not what I expected. First of all, playing `CTFs` on these platforms is very good for many people, and the platforms do a great job. But I didn't like its experience because I thought the normal boxes of the `HTB` platform would replicate real-world scenarios where, against hardened systems, normal scans easily fail. We can't even see a door except phishing/social engineering/hardcore OSINT for the initial access.
Later I realized that I could get this experience through `HTB pro boxes`, but I didn't have the money for it. So I decided to make my own home lab. I took the `PNPT` course offered by `TCM Security`. It was hands-on, very good for beginners who want to learn how actual real-world pentest workflows work.
After that, I expanded my lab. Let me give you an overview of what my lab includes:
1.  ATTACK-NET : kali linux
2.  PENTEST-NET : metasploitable2 linux, kioptrix, DEV, Black Pearl, UBUNTU-SERVER
3.  EXTERNAL-RED : Win server 2019(fully custom, I do the administrative configs on it)
4.  PIVOT-NET : THEPUNISHER(win 10 enterprise), THESUPERMAN(win 10 enterprise)
5.  SECURE-NET : Windows server 2022

_This is my home lab_. I do all of my experiments in this whole lab. I have made 3 custom networks to simulate a real-world scenario in vmware. My `PIVOT-NET` and `SECURE-NET` machines are totally isolated from the internet. Later I will share the entire lab setup I created for my home lab through a blog/sharing my notes.

Along with all of this stuff, I was confused about whether I should do any more certifications or learn by myself through blogs/articles/books. After 1.5 months of procrastination, I got stuck in a situation where I couldn't decide whether I should do `HTB CPTS` for knowledge or learn from books.

Finally, I convinced myself that I would go for books, not certifications. But the problem is that I don't have a lot of money to purchase `hacking` books, because they are all so expensive for me. So I downloaded PDF copies that are available on the internet for free and started learning.

I started reading books this month. Currently, I am reading `The Ultimate Kali Linux Book, Third Edition`, and `Automation using Python`. These two are my go-tos. Let me tell you now after reading half of both books that this was my best decision for learning and moving forward in this field. Maybe this can differ for you, but for me, this is the right way. I have noticed significant changes in my notes and knowledge since I started using books consistently. I will also share those notes in my blog's `notes` section.

Takeaway from all this thinking: Take your time and think wisely about what you want to do and how you want to do it... don't just believe my opinion, either. This is very important. If you don't think carefully and just jump into something, maybe it can work, but that's just gambling. Take your time to think.

I don't know how much this strategy will work for me in the future, but I will just keep moving with this because I am loving this way.

---
_Now what I will be posting next:_
In the next few months, I will try to post my Pentesting notes along the way of the book's progress. I will also post about different forensics techniques.git 
Starting in November, I might jump into `web application security` if possible.