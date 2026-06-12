---
title: "Not able to browse sites other than google"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by prince.john on 2008-01-23
hi,..
i am new to ubuntu.i installed ubuntu 7.10.now i have problem with browsing.i could take only google.if i made a search i will get the links but cant go to the particular site by clicking on it.

---

### Post by cdtech on 2008-01-23
Do you mean by typing it in the google search bar? Can you use the keyboard to select a link? If so, it sounds like a mouse problem. Maybe a double click?

---

### Post by prince.john on 2008-01-26
not its not the problem of mouse.i can get only a few sites.Cant ecen go to the site of ubuntu...is it problem of some kkind of settings in browser

---

### Post by Dr. C on 2008-01-27
Sounds like a DNS issue to me. Can you try System > Administration > Network Tools and then use the ping tool

Try sending a ping to 

[www.google.com](www.google.com)
[www.ubuntu.com](www.ubuntu.com)
[www.yahoo.com](www.yahoo.com)
[www.cbc.ca](www.cbc.ca) 

Can you get a result from all these sites? If you are only getting results from [www.google.com](www.google.com) then it may be cached and you do not have DNS resolution. 

By the way this does not work with all sites eg [www.cnn.com](www.cnn.com) and [www.microsoft.com](www.microsoft.com) will drop ping requests but I have tested the 4 above and they do work.

---

### Post by ghost_ryder35 on 2008-01-27
had similar problem with my comp.  There are two solutions here,
1. Change your routers IP address to 192.168.1.100

or

2. Apply a static IP address to your computer, and static DNS servers to your computer.  

For some reason when I upgraded to 7.10 I could not get on to any web pages also.  google would work periodicolly, and some times pings would work to other web sites such as yahoo.com and sometimes they would not.  It seems that soultion number 1 is the easiest and most simple, however solution number 1 also requires that you have physical access to your router and be able to change the IP address with out messing up other computers.  Hope this helped you out, and good luck.  Enjoy

---

### Post by sbenesole on 2008-01-30
I had a similar problem and I fixed it by changing the mtu setting from 1500 to 1492.

Place the following code in /etc/rc.local (it needs to be reapplied at startup). The settings below assume you're using eth0 for your internet connection, the TCP/IP parameters should be self-explanatory: 



ifconfig eth0 mtu 1492

---

### Post by prince.john on 2008-02-07
Thanks....doing
 sudo ifconfig eth0 mtu 1400
has fixed the problem.But everytime after booting we must execute command on terminal.i found a permanent solution in another post....


Code:

sudo nano /etc/init.d/rc.local

And add, as the 2nd line in the script, the command:
Code:

ifconfig eth0 mtu 1400

---

