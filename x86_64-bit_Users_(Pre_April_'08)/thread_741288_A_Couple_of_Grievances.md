---
title: "A Couple of Grievances"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by JudasReanimated on 2008-03-31
Hi I´m a semi-Veteran to Ubuntu (I´ve been here since Dapper), and even though I haven´t gotten to add too much to the community as of yet I do plan to do as much as I can get by with in the future. I love Ubuntu and everything about it, as well as the community that represents it!

However I do have some small problems which I can´t seem to figure out. The first of which is my internet. For the life of me I cannot seem to get Static IP wireless to work on this, but DHCP through Roaming works fine, for the first few hours or minutes, before I have to reset my Laptop. 

When I configure the network manager to use my static information,
192.168.1.1xx
255.255.255.0
192.168.1.1 for example; It does nothing, and just hangs when trying to load my homepage. Yet when I just enable roaming and enter my password, etc; It works fine for a while before as I said above it just stops and I have to restart my Laptop. I haven´t messed around with ifconfig too much, but here is the output

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:15:AF:9A:CD:6E  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe9a:cd6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1043106 (1018.6 KB)  TX bytes:211184 (206.2 KB)


However wired DHCP/Static work fine.


My second question is just as odd. My graphical settings just will not save. I have desktop plane enabled and everytime I shutdown, log out, or restart my computer I have to go in and disable and re-enable to get the effect to work again, however my water-effect has ceased to function completely. 

As for the rest of my effects, they just randomly seem to change and some reset and some stay the same. I´m at a total loss as to why that is.

Any help would be appreciated, thanks.

---

### Post by knightcoder on 2008-03-31
To get a static IP, try setting it up on you NAT box ( your wireless router) to set you a specific IP for your MAC address.
So, no matter when you connect, you'll have a fixed IP.

I hope that was what your problem was.

---

### Post by JudasReanimated on 2008-03-31
Thanks for the hasty response, but I was more looking to fix my current issue without a work-a-round. Also I don´t believe my router will allow me to set up Mac Specific IPs. Only allow me to secure access for particular MAC IDs.

---

### Post by JudasReanimated on 2008-04-01
Ok been a day, BUMP

---

### Post by wannadumpwindows on 2008-04-01
I had the exact same problem on my laptop, and it works fine on the desktop too. The only way I could get it fixed was to switch from network-manager to WICD. I've read in many places that network manager just doesn't like static ip's a lot of the time, but it still works for all my wired connections too. As soon as I did, it worked fine, and I haven't had any problems since. Although it's not in the official repos, that tends to turn a lot of people off. But I've had absolutely no problems or any issues since. I would personally recommend it, and I actually like it better, and not just because it works. LoL.

---

### Post by JudasReanimated on 2008-04-01
I installed Wicd and I can already feel a difference. My net is a lot snappier now. If it remains stable then I´ll be extremely happy, Thanks a bunch, but now onto my next issue while we wait to see is my net remains stable.



EDIT: Well about 30 seconds ago it failed, and I had to shut the Laptop down, then bring it back up to get a connection again, though the Wicd is far better than the default network manager, and allows me to use static, so thanks were awarded proper, however this leads me to believe that fault may lie in an unstable driver or similar. I have a Realtek RTL8187, if that´s any help?

---

### Post by JudasReanimated on 2008-04-02
Change that Internet is fine now after the reboot, that just leaves my other problem.

---

### Post by tubasoldier on 2008-04-02
Network-Manager does not yet support static IP addresses. So using it would be out of the question. 

You could easily use the 'if' tools. ifup ifdown ifconfig.
Wifi-Radar(gtk) or Wireless Assistant(qt) make using it bearable. However, you have to put in your admin password to change networks.


As for Destop Effects... IDK.

---

### Post by wannadumpwindows on 2008-04-02
I don't know much about drivers yet, especially those different from my own, sorry I can't be of more help in that area. But it's good to hear you got it working now, glad I could be of assistance.

---

### Post by firecat53 on 2008-04-03
If your settings aren't saving, I'd suspect a permissions issue with the settings folder perhaps. I'm not 100% sure where the settings are, but I'd guess somewhere in .config or .gconf or some such. (type 'locate compiz' and sift the through results there). Make sure the directories and/or files are writable. 

Good luck!
Scott

---

### Post by phynix on 2008-04-03
I had the same problem with compiz settings not sticking. I fixed by changing to a fixed file background. Its under the preference page.

---

### Post by JudasReanimated on 2008-04-04
I couldn´t find the fixed file background, and apparently I have to reinstall Flash everytime I restart my PC as well.

---

### Post by JudasReanimated on 2008-04-06
Bizump

---

### Post by JudasReanimated on 2008-04-10
Bumpity Bump BUMP!

---

