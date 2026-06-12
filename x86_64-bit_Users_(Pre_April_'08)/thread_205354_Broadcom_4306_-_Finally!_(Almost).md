---
title: "Broadcom 4306 - Finally! (Almost)"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-28
I've spent the past several days trying to get the new bcm43xx driver to work. Sometimes I'd get it working, and then next time I'd boot up it would not work. Finally I decided it's just not ready for prime time, so I went back to ndiswrapper. I had installed it first in Hoary when I was brand new to Linux, then had to redo it completely after upgrading to Breezy. At that time I swore I'd save my own instructions for "next time." I saved them in the Compaq R3000 wiki:

[http://prinsig.se/weekee/index.php/Ndiswrapper64](http://prinsig.se/weekee/index.php/Ndiswrapper64)

I started by trying to install ndiswrapper 1.18 from the tarball at sourceforge. But I kept getting a lot of errors, even after fixing headers, installing gcc, and trying to fix the link as suggested under Prerequisites here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

After struggling with it for a while I discovered that ndiswrapper and ndiswrapper-utils are now listed in Synaptic. (I have the extra repositories enabled; you may have to do so to find them.) So I gave up on 1.18 and just installed the 1.8 via Synaptic. Goodby "make-install" and all that stuff!

It still wouldn't quite work, even though I still had the drivers that worked before (netbc564.inf and bcmwl564.inf). So then I went back to my own instructions at the R3000 wiki above, read through them, and what I did at the very end worked again -- that is, I uninstalled it with sudo ndiswrapper -e netbc564 and then reinstalled it with sudo ndiswrapper -i netbc564. As before, this worked. Opening System > Administration > Networking, there it is! And when I select it and click on Properties, it no longer locks up my computer. Instead it shows me the networks in the area, just as it should.

But there is one small problem left that I've never had to deal with before. For some reason System > Administration > Networking shows eth1 (the wireless) as the default gateway. This used to be called wlan0, but I don't care about that. The problem is that I am at home lots more than I am at the university or elsewhere using wifi, and at home I have cable. So I want the default gateway to be eth0. I can change it to eth0, but it doesn't "stick." Next time I open System > Administration > Networking it is right back to eth1.

This makes it really slow to do anything because I have no wifi at home, therefore the wireless is not connected to anything, and every time I go to load a web page it takes a long time as the computer tries to send it through the wireless, gives up, and then sends it through eth0.

I bet there is a setting or command I can give it somewhere to fix this. Anyone know where it is?

---

### Post by tsb on 2006-06-28
there is a package you can download so it will automatically use the available connection...... I can't remember the name of it now.  After istalling it you shouldn't have any troubles.

Nothing beats MEPIS for the 4306 IMO.  All I had to do was blacklist the 43xx driver and switch the wireless to wlan0 and it worked perfectly without messing with ndiswrapper at all.

I'll do a quick search for the package now

---

### Post by John Jason Jordan on 2006-06-28
[QUOTE=tsb]there is a package you can download so it will automatically use the available connection...... I can't remember the name of it now.  After istalling it you shouldn't have any troubles.
I'll do a quick search for the package now[/QUOTE]
Thanks.

I've discovered a different problem, that may be related. Somehow installing ndiswrapper has screwed up DHCP. Both the wireless (now wlan0) and the ethernet (now eth0) are set to DHCP in Properties (looking at the System > Administration > Networking window). They always have been. At home I have no wifi, but the wireless does see the neighbors' wifi, so I know it is working. I need to go to the university and test it to be sure, though. So at home, instead of using the wifi, the computer is plugged into an ethernet jack in the wall. This goes through a switch to the router, and through the router to the cable modem, and then out into the great world of the net. I also have a Windows 2000 desktop that I am writing this on right now, set up the same way and it works fine.

On the laptop I can ping and it works. I have one e-mail account that is set to an ip address instead of a name address, and it works fine. But anything with a name just sits there and goes nowhere. In other words, it's not finding the DNS server at the cable company. Yet the Windows computer continues to function perfectly. Therefore we know that there is nothing wrong with the cable service, the cable modem, the router, or the wiring.

It was all working fine before I installed ndiswrapper. The problem began immediately thereafter. However, right after discovering the problem I rebooted the laptop, and then it worked again. However, I noticed (going into System > Administration > Networking) that the wireless was no longer listed. That's because I had installed it but forgotten one last command -- ndiswrapper -m, in order to add it to the automatic modprobe list on bootup. 

I fixed that and then restarted the computer. This time the wireless was listed in the modprobe file, so modprobe definitely started it on boot. However, I was no longer able to go anywhere. I deactivated the wireless, but still couldn't go anywhere. Then I did sudo rmmod ndiswrapper, but still was not able to go anywhere. I opened System > Administration > Networking again and wireless was no longer listed, so I definitely turned off ndiswrapper. Nevertheless, I was unable to go anywhere. 

I opened /etc/resolv/conf and it listed the DNS server as 192.168.1.1. That is the ip address of my Windows 2000 desktop. It should have shown the ip address for Comcast. I can't figure out why it suddenly thought my Windows 2000 desktop was the DNS server. It never did that before when I used ndiswrapper under Breezy or Hoary. And can guarantee that I never typed that address into anything on the laptop. Fact is, I have to go look up what numbers I have assigned to which computer/printer/device here at home because I can't remember them all. So I know the laptop got that address all by itself.

I decided to reboot the modem and router. I turned them off for a couple minutes and then turned them back on. But still no joy. 

I used to use Firefox in 32-bit chroot under Breezy, and I always needed to link the /etc/resolv.conf file to its counterpart in chroot whenever I changed locations. I had pasted the DNS addresses of the Comcast servers into my CheatSheet text file where I save such stuff. So I copied them manually into /etc/resolv.conf and resaved the file. But still no go. (Note that I do not have a chroot environment under Dapper, and hopefully will never need that again -- I just knew that I had those addresses saved from back in the days when I used to need them.) 

It is possible that the DNS server addresses I put manually into /etc/resolv.conf were out of date. But if they were, Dapper should have figured that out and updated them automatically, as it always used to under Breezy. For some reason it is not going out and finding the DNS servers. It's got to be connected to the installation of ndiswrapper, but I'm clueless.

Does anyone have any idea of what happened and how to fix it?

Edit: 192.168.1.1 is the address of the router, not the Windows 2000 desktop. Sorry. :(

---

### Post by John Jason Jordan on 2006-06-28
OK, I found out what the problem was. Now I just need to figure out how to fix it.

The problem was that under Breezy it always listed the DNS servers of whatever network I was connected to. Thus, when I saw the router address I assumed that this was wrong, and this was the reason I couldn't get anywhere.

Since then I have discovered that the router address works just fine for the DNS listing, as long as a deactivate the wireless connection. The wireless connection is still there, and I can activate it any time I want, but if both are active it won't go anywhere, even over the the ethernet and even if the wireless is not connected to a network, and even if eth0 (the cable connection) is listed as the default.

So now I need to figure out how to make it autodetect which one is connected and use just that one.

---

