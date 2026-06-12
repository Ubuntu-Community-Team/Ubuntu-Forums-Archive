---
title: "network-manager icon missing on toolbar"
date: 2009-10-21
forum: x86 64-bit Users
---

### Post by kartook on 2009-10-21
Hi 

ny network manager icon was not showing on my toolbar 


```

K@Kuzar:~$ sudo apt-get install network-manager network-manager-gnome

```

---

### Post by MelDJ on 2009-10-21
right click the panel, press add to panel and add the notification area

---

### Post by kartook on 2009-10-21
Dude i did like this way on the 

system--> prefer -- network connection 

right click added 

thanks for your answer 

thanks you very much 

K

---

### Post by MelDJ on 2009-10-21
if you want to see the network connection menu, just left click the connection icon and press vpn connections and then configure vpn

---

### Post by wjamoore on 2009-11-02
My N-M icon is missing too.  I think it happened at the last upgrade

Anyway,  I tried all the above.

Add to panel. Network is not available

In network manager it was not possible to right click and add to panel.  Although I am connected (as you can read this)

Any ideas?

thanks

Aaron

---

### Post by wjamoore on 2009-11-02
Actually it's an interesting issue and I just figured out  what is going on. (at least in my case)

The NM manager icon is only displayed on the screen of the user who first logs on and therefore connects the PC to the network.  My wife logged on first this morning and on her sessions the nm icon is always visible

However I am the system administrator and i'd have thought I would at least be able to control my network connection.  But I have to re-boot to make the log-on again.

Not so much a bug as an implementation oversight I think.

Aaron

---

### Post by juliobahar on 2009-11-02
> **kartook said:**
> Hi 

ny network manager icon was not showing on my toolbar 


I have the same issue with the network-manager icon on my upgraded karmic (Desktop). I'm able to connect to my eth0 though. And the same thing goes with my wireless adapter after plugging it in.

I've noticed some bugs with the notification area as sometimes the icons get duplicated in a very weird way life half icons and stuff.Also there is an empty area within the notification where I suppose is must be the network-manager's icon allocated place.

I can still access network by system --> preferences --> network connections

Btw I have a new install of ubuntu Karmic on my laptop so far it seems fine. But I have experience ONE only notification area bug. For that restart solve the problem.

---

### Post by footprint on 2009-11-10
I have the same problem. The network icon is missing. If I remove the Notification Area from the panel and then add it again the icon is back. However, after a reboot it is missing again. Network Manager is running as shown by the fact that eth0, wlan0 and my mobile broadband dongle all work!

---

### Post by sipik on 2009-11-11
> **footprint said:**
> I have the same problem. The network icon is missing. If I remove the Notification Area from the panel and then add it again the icon is back. However, after a reboot it is missing again. Network Manager is running as shown by the fact that eth0, wlan0 and my mobile broadband dongle all work!

I have the exact same problem

---

### Post by footprint on 2009-11-12
Transferred to a new thread at [http://ubuntuforums.org/showthread.php?p=8301800#post8301800](http://ubuntuforums.org/showthread.php?p=8301800#post8301800)

---

### Post by Yellow Pasque on 2009-11-12
> **footprint said:**
> If I remove the Notification Area from the panel and then add it again the icon is back. However, after a reboot it is missing again.

Look in System -> Preferences -> Startup Apps. The n-m applet is usually there by default, but maybe yours got removed along the way.

---

