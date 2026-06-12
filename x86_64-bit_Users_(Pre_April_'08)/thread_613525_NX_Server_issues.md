---
title: "NX Server issues"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Inxsible on 2007-11-15
I installed NX server using the following two guides.

[http://ubuntuforums.org/showthread.p...free+nx+server]("http://ubuntuforums.org/showthread.php?t=493983&highlight=free+nx+server")

[http://stuffem.wordpress.com/2007/03...ver-on-ubuntu/]("http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/")

Now, this is the scenario:

1) I use my work XP laptop to connect to my work ISP.
2) My Ubuntu box is connected to my home ISP
3) I use a router

[COLOR=Red] When I use the local address(192.168.x.x) to connect[/COLOR] to my ubuntu box from my XP machine (connected to the work ISP so the IP address is different), I can see my Ubuntu box with these problems
a) My Ubuntu box is 1440x900 and is configured as twinview with another 17 inch monitor, but my XP laptop only has 1280x1024 res. When it connects, everything from my ubuntu box is squished to fit, and I can hardly read anything. 

b) Also, I do NOT get scroll bars so that I can scroll and do something else. Because my top panel and my AWN also do not show in that small resolution :sad:

c) I cannot even maximize the screen any further :sad:

d) If I connect in Shadow mode, and I open a menu or do anything, I can see that it affects the ubuntu box, but I cannot see it on my XP machine. for eg. if i open a terminal window (from the XP machine), it will open in ubuntu, but it won't show in my XP machine. (This makes is useless, since I never know if an app was opened unless I am sitting right in front of my ubuntu box)
It seems that I only get the "print-screen" (for lack of a better word) of the ubuntu box when I first connect.

[COLOR=Red] If I use the host-name that i created @ no-ip.com, it simply doesn't connect[/COLOR]. It gives me the following error: 	```

 	NX> 203 NXSSH running with pid: 5740
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host mybox.no-ip.biz port 555: Connection timed out
``` 
I hope I am making sense. Can someone please help me out ?

---

### Post by Inxsible on 2007-11-15
bump

---

