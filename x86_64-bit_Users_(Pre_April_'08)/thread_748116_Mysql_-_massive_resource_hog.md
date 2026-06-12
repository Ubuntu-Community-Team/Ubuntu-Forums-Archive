---
title: "Mysql - massive resource hog"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tstaddon on 2008-04-07
Hi,

I recently built Ubuntu 64-bit onto a sandbox PC (Intel P4 550, 3.2ghz EM64T supported, 1.5gb RAM) and must say I'm impressed. 

Even a wireless card I'd never heard of before, and my TV tuner card, were installed no hassle. I'm running Kaffeine for TV watching/recording at the minute, and it runs very nicely, CPU utilisation very low, temperature low even with fan in silent mode, loads of RAM to spare.

No amount of kicking seems to enable my Radeon 1050 to work with a different driver other than the VESA one, but apart from that, I'm very happy.

I've heard great things about MythTV but as soon as I install mysql onto the machine, the machine turns into a complete resource hog to the point where it's utterly unusable even if nothing else is running. 

CPU utilization shoots up, most of my free memory vanishes, and I've even had the temperature warning siren going off because the fan can't cool the processor fast enough. 

I can probably live without MythTV but I have to say I'm truly disappointed with the performance of MYSQL. Any ideas?

---

### Post by LoneWolfJack on 2008-04-07
Please post the output of

```
top
```

when your CPU utilization goes up.

---

### Post by ericson578 on 2008-04-07
Last week I installed 7.10 server onto my home desktop to use as a sandbox too.  I included DNS, cups, apache 2, php 5, and mysql.  As a contract programmer I'm working on two separate e-commerce sites right now, and I was able to import two databases into my sandbox mysql db with no problems, and the machine still runs quite speedily.

My specs: Kernel Linux 2.6.22-14-server
Gnome 2.20.1
Ram 1gb
CPU: Amd sempron 2800+
60gb hd, but partioned roughly in half so I can dual boot windows (my partner is afraid of linux, lol, I'm working on him!)

I was quite suprised at how quickly I had everything up and running, less than 2 hours if I recall.  Finding instructions on how to use virtual hosts with apache 2 was really easy, and my sandbox is working perfectly.

I'm thinking maybe mysql might not be the root of the problem.  Do you have anything else running that is accessing your db?

-Eric

---

### Post by tstaddon on 2008-04-09
Absolutely nothing at all. I've literally got the standard Ubuntu install options from CD with no other apps. 

If I remove MySQL and MythTV the system hardly ever exceeds 40 degrees C / 10% CPU utilisation but as soon as I put them back on the temperature never drops below 55 degrees, even with the fan flat out, and both CPUs are showing 75% utilisation even when all I've done is boot up and log into the Gnome desktop.

---

### Post by ericson578 on 2008-04-09
I'm by no means a linux expert, but maybe if your video card were using better drivers rather than VESA it would run faster?  I'd focus on getting the video card working first.

Try this: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Sorry, maybe more experienced linux users will have some better insights. :)

---

### Post by syncrondi on 2008-04-10
I also am experiencing some similar serious issues with MySQL. In my case, we're running a standard LAMP web server and everything has been very smooth. Recently, we keep getting these spikes in MySQL activity, and it's slowing the site down (even grinding to a halt sometimes). We've restarted MySQL and even the server itself, but no good. Normally the processor usage is around 15% and the load average around 1-2. I also just noticed that there are three hundred and fourty seven processes with 43 running in this shot, where there are usually around 110/3. Usually top is filled with Apache processes with only a couple of MySQL processes in there. Would anyone have any ideas on why this would be? 

[IMG]http://xs226.xs.to/xs226/08153/untitled-1154.gif[/IMG]

---

### Post by ericson578 on 2008-04-10
I think it would be helpfull if you turned on some logging for mysql.  I'm not a mysql expert, but lots of things can cause resources to get clogged down.  For example, if several queries are running at the same time that need to join large tables, that kind of thing.

Mysql logging can usually identify what is causing mysql to hog resources. Let me try and find a good link for mysql logging; 

here's what I found that might be helpful:
[http://www.transcendlinux.com/mysql-performance-tuning](http://www.transcendlinux.com/mysql-performance-tuning)
[http://www.mysql.com/news-and-events/newsletter/2004-01/a0000000301.html](http://www.mysql.com/news-and-events/newsletter/2004-01/a0000000301.html)

(the query log part of this article): [http://www.databasejournal.com/features/mysql/article.php/2112011](http://www.databasejournal.com/features/mysql/article.php/2112011)

Hope that helps!  Personally I hate dealing with dba stuff! ack!

---

### Post by Steveway on 2008-04-10
Well I'm running a Mysql-database (For MythTV) a PostgreSQL-database (for Amarok) an Apache and many many more things on my old Laptop here.
I only have 512MB Ram and a Sempron 3000+ processor.
What I want to know; do you have a swap-partition?
If my Swap-partition accidently doesn't get mounted then my system will also slow down very fast.
So you should check for that.

---

### Post by tstaddon on 2008-04-23
Hi,

Sorry for the delay getting back to you. I'll answer your questions later.

Just to add, I've tried every Radeon installation guide going - I can get the drivers onto the system but they don't work. The only way I can get a picture is to switch back to the VESA drivers.

On the swap file side of things, I've got a dedicated partition for it. Can't remember how big, but 512mb springs to mind.

---

