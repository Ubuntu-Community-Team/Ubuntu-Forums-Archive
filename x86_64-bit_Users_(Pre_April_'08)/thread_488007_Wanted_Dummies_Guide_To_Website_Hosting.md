---
title: "Wanted: Dummies Guide To Website Hosting"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by gargar934 on 2007-06-29
Hi all,

I am now trying to learn about website hosting, and would love to get a personal website up and running from my machine so that freinds and family (and anyone else) could view it. I am currently sitting behind a standard linksys router which has a dynamic IP through my service provider. 

So from my understanding, there are three main tasks here:
1. configure my computer as a webserver, and have a folder where I drop .html files which will be viewable on the internet
2. configure my router to send the appropriate requests to my computer on the LAN
3. register with a free dns website, and have software update it with my dynamic IP

Can someone take me step by step through doing this (like real small dumby steps, I'm a newby here), or point me towards guides which will. Most guides I am finding go into more detail than I would like to start off with, right now I just want to know the real basics of how-to, and then I can build up my understanding/skills from there.

Thanks a bunch!!

---

### Post by Kilz on 2007-06-29
> **gargar934 said:**
> Hi all,

I am now trying to learn about website hosting, and would love to get a personal website up and running from my machine so that freinds and family (and anyone else) could view it. I am currently sitting behind a standard linksys router which has a dynamic IP through my service provider. 

So from my understanding, there are three main tasks here:
1. configure my computer as a webserver, and have a folder where I drop .html files which will be viewable on the internet
2. configure my router to send the appropriate requests to my computer on the LAN
3. register with a free dns website, and have software update it with my dynamic IP

Can someone take me step by step through doing this (like real small dumby steps, I'm a newby here), or point me towards guides which will. Most guides I am finding go into more detail than I would like to start off with, right now I just want to know the real basics of how-to, and then I can build up my understanding/skills from there.

Thanks a bunch!!

I can help with a little bit of info
1. [Go here to]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29") learn how to setup a server.
2. Apache is setup to use port 80. You will have to open the admin for the router at [http://192.168.1.1/](http://192.168.1.1/) and setup UPnP Forwarding. There should be a setting for HTTP or port 80. Just tell it what ip your server is on. 
3. My ip is static, so I cant help you here.

Older computers make good small servers. My old pentium 3 got a new lease on life this way.

---

### Post by gargar934 on 2007-07-02
Thanks Kilz! =D>

That advice was precisely what I needed to get going, I'll get everything up and running and post back how I get the dynamic ip going in case there is anyone else out there trying to figure this all out for the first time as well.

---

### Post by aikishugyo on 2007-07-02
In case you did not yet know: including "howto" in a Google search (together with "linux" and "apache" or something) will usually guide you to some of the best How-To documents from for example the Linux Documentation Project. I would also recommend putting "debian" in a couple of the searches since although Ubuntu is very popular, especially among those who used to find it difficult to access linux in a user-friendly way, many debian users have written stuff on the building blocks that you'll find you need to know about anyway if you want to understand what it is you are doing (after your first "why can't I access my site" everyone kind of comes around to this way of thinking, hehe). Good luck! If you don't have a fixed IP, you might try dynamic hosting (not sure if I'm allowed to give names out here, but I'm doing okay with one of the popular free dynamic IP hosts for over a year now).

---

