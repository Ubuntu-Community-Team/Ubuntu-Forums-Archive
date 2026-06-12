---
title: "Broadcom b/g WLAN for AM64"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Origin on 2006-08-15
I am on a compaq presario 2565us I think equipped with an AMD 64 (Turion) processor. I recently installed Ubuntu x64 as a dual-boot.

I don't know where to get the driver for the broadcom b/g WLAN, and when I get something, I don't know how I can install it. I've looked around here but it's very confusing. This is my first time on linux.

Can anybody help me?

---

### Post by John Jason Jordan on 2006-08-15
> **Origin said:**
> I am on a compaq presario 2565us I think equipped with an AMD 64 (Turion) processor. I recently installed Ubuntu x64 as a dual-boot.

I don't know where to get the driver for the broadcom b/g WLAN, and when I get something, I don't know how I can install it. I've looked around here but it's very confusing. This is my first time on linux.
The first thing to do is to determine which Broadcom chip you have. If it's a Compaq I'm going to make a wild guess that it's a 4306. One easy way to tell is during the boot process you may get a couple error messages about "Broadcom xxx driver not found" or something similar. The "xxx" is what you are looking for. There are also command line probes to find out.

Once you know what chip you have you can proceed to get it working. There are now two ways to do that -- the new Broadcom wireless driver that Dapper comes with, and the traditional ndiswrapper. Ndiswrapper uses the Windows 64-bit driver and "wraps" it so that Linux thinks it is a Linux driver. If you need the 64-bit Windows driver you may be able to find it (free) on linuxant.com. The new Broadcom  driver that Dapper comes with has occasional problems. 

A TON has been written on these forums about getting wireless working in Linux. Search the forums for "broadcom" and you should get reams of comments, how-tos and wikis.

---

### Post by Origin on 2006-08-15
I think it says 4318, according to device manager. (Driver version 3.100.64.0)

I have 6.06 LTS. I also have the 64 bit windows driver. I can use ndiswrapper to make my 64 bit windows driver work on Ubuntu?

Sorry, I did search but whatever I came across were a bit too technical for me :(

---

### Post by Origin on 2006-08-15
I tried the How-Tos out there, but they don't work. I tried installing ndiswrapper according to its installation file but it doesn't work. ("make is not a valid command" or something of the sort)

How do I reconcile this problem?

Why does Linux have to be so hard? Why can't it be intuitive like Windows? :(

---

### Post by John Jason Jordan on 2006-08-15
> **Origin said:**
> I tried the How-Tos out there, but they don't work. I tried installing ndiswrapper according to its installation file but it doesn't work. ("make is not a valid command" or something of the sort)
It used to be that you had to use "make" and a bunch of other commands to install ndiswrapper, but now you can install it with Synaptic. (System > Administration > Synaptic Package Manager.) 

Once you install it you must configure it to see your Broadcom 4318. It's just a couple of commands, but it's been several months since I did it and I forget what they are.

> **Origin said:**
> Why does Linux have to be so hard? Why can't it be intuitive like Windows? :(
But then it wouldn't be so much fun! :)

Seriously, Windows is truly easier to use. That's because it has the majority of the market so manufacturers all make sure their products have Windows drivers. Some (like Broadcom) won't even release the specifications for their products so the open source community can write the drivers. It makes it a lot harder to make an OS which is completely plug and play when things have to be reverse engineered.

On the other hand, Linux is way ahead of Windows in lots of other ways. It's more secure, usually runs faster, and you feel as though you are in control. To me that makes it worth it to put up with the other problems.

---

### Post by Origin on 2006-08-15
I don't mind searching for stuff, but I've been doing this for a while and nothing has worked. I find something that I think might work, turn off my Windows, sign onto Ubuntu, try the things, see it doesn't work, try alternatives and stuff, see them fail too, sign off Ubuntu, then get back on Windows to complain.

I hate this cycle because I get nothing done, and it takes a bit of time to turn off and turn on. I wish there was one CORRECT set of instructions to install the WLAN so I can actually complain about other stuff while logged on Ubuntu.

Yeah I know Linux has its advantages, but I can't take advantage of them if I can't connect!


*sigh* I'll try what you said. I'll log onto Ubuntu again, try installing ndiswrapper via Synaptics Package, and come back here to complain it doesn't work :P Seriously though, if the instructions are wrong, shouldn't ndiswrapper's website update the instructions?

I thank you profusely for your help :)

---

### Post by greenfrog on 2006-08-16
You need to download the BCMWL564.SYS driver which is 64 bit along with the 
netbc564.inf file.

Then the 64 bit ndiswrapper will work.

---

### Post by finite9 on 2006-08-16
See my HOWTO at [http://www.ubuntuforums.org/showthread.php?t=237537](http://www.ubuntuforums.org/showthread.php?t=237537)

Hope it's useful to you.

---

### Post by clevershark on 2006-08-16
Actually for the 4318 chips what you have to do is configure ndiswrapper and blacklist the bcm43xx driver. This is because the chipset is the Broadcom Air Force One rev 02, which (in typical Broadcom fashion) is not compatible with the drivers for the revision 1 drivers.

There is a howto somewhere on this site about it.

---

### Post by Origin on 2006-08-16
I don't get it. What's wrong with the native 43xx drivers in Linux? How do I use that?

---

### Post by clevershark on 2006-08-16
The native bcm43xx driver doesn't work with the BCM4318 chipset. That's why you have to use ndiswrapper.

---

### Post by Origin on 2006-08-16
Oh.

That's a bummer. Thanks for the info.

So to sum it up, install ndiswrapper, and use my WinXP drivers for Ubuntu?

---

### Post by clevershark on 2006-08-16
Correct, except that you then have to make sure that the bcm43xx driver doesn't load by blacklisting it.

Instructions for the whole procedure are also shown here:
[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)

Also make sure that ndiswrapper is using the 64-bit driver.

---

### Post by Origin on 2006-08-17
It kinda worked... but now I don't have the WLAN b/g option in Network Settings/Networkings page under Admin.

I checked with ndiswrapper and stuff, and it says BCMWL5 was installed (Broadcom WLAN b/g BCM4318  [AirForce One].. something). But it's useless if I can't see it on Network Settings/Networkings page, as I can't configure it :(

Basically here's what I did:
installed ndiswrapper from CD
used terminal and ndiswrapper commands to install the acer driver ( BCM4318 ) by using sudo ndiswrapper -i Desktop/bcmwl5.inf
Then I did the -l command and saw it working. Then -m to supposedly put it on Network Settings

But it's not there. What's up?

---

### Post by Dun on 2006-08-17
> **clevershark said:**
> The native bcm43xx driver doesn't work with the BCM4318 chipset. That's why you have to use ndiswrapper.
What's all this about? I have bcm4318 and it's working just fine with the native driver.

---

### Post by cemptor on 2006-08-17
Considering buying a US Robotics USR5417 PCI wireless card for my desktop, just to be able to use 64 bit dapper (my current Trendnet USB card not supported by 64 bit ndiswrapper or native).

Its supposed to be based on the BCM4318 (rev 02) chipset. Ideally I want to buy it only if I can get it to work natively. Should I?

If there are issues with the native drivers, are they likely to get fixed soon? Have had a 64 bit capable desktop for months, but have'nt been able to move to 64 bit linux principally because of this.

What are the issues? Is ndiswrapper my only choice?

---

### Post by Origin on 2006-08-17
> **Origin said:**
> It kinda worked... but now I don't have the WLAN b/g option in Network Settings/Networkings page under Admin.

I checked with ndiswrapper and stuff, and it says BCMWL5 was installed (Broadcom WLAN b/g BCM4318  [AirForce One].. something). But it's useless if I can't see it on Network Settings/Networkings page, as I can't configure it :(

Basically here's what I did:
installed ndiswrapper from CD
used terminal and ndiswrapper commands to install the acer driver ( BCM4318 ) by using sudo ndiswrapper -i Desktop/bcmwl5.inf
Then I did the -l command and saw it working. Then -m to supposedly put it on Network Settings

But it's not there. What's up?

Can anyone help me?

> **Dun said:**
> What's all this about? I have bcm4318 and it's working just fine with the native driver.

How did you do that???

> **cemptor said:**
> Considering buying a US Robotics USR5417 PCI wireless card for my desktop, just to be able to use 64 bit dapper (my current Trendnet USB card not supported by 64 bit ndiswrapper or native).

Its supposed to be based on the BCM4318 (rev 02) chipset. Ideally I want to buy it only if I can get it to work natively. Should I?

If there are issues with the native drivers, are they likely to get fixed soon? Have had a 64 bit capable desktop for months, but have'nt been able to move to 64 bit linux principally because of this.

What are the issues? Is ndiswrapper my only choice?

Um, can you start a new topic?

---

### Post by finite9 on 2006-08-18
> **Dun said:**
> What's all this about? I have bcm4318 and it's working just fine with the native driver.

Yeah Dun, I have a bcm4318 too which is why I posted a link to my HOWTO, but apparently there is a difference with revisions of the adapter from Broadcom which I knew nothing about, so I cant really comment on it, but as the guy who posted that doesn't know what revision the parent post has, id say hes a bit premature in recommending ndiswrapper over bcm43xx.

---

### Post by clevershark on 2006-08-18
That seems like a bit of a non-issue. If you don't have a 4318 rev. 02, your chipset works out of the box with the native driver without requiring further configuration. If you have a 4318 and can't get it to work with ubuntu, it's because it's a rev. 02 chipset and you need to use ndiswrapper.

---

### Post by Dun on 2006-08-19
> **clevershark said:**
> That seems like a bit of a non-issue. If you don't have a 4318 rev. 02, your chipset works out of the box with the native driver without requiring further configuration. If you have a 4318 and can't get it to work with ubuntu, it's because it's a rev. 02 chipset and you need to use ndiswrapper.
Well, don't know about that:

dun@mars:~$ lspci | grep -i bc
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

And I am writing this text via wireless connection :)

---

### Post by greenfrog on 2006-08-19
If yu are using the 64 bit version of Ubuntu then you must use the 64 bit drivers.  See my post above for the correct drivers.

They work with all the versions of Bcom 43xx chips.

---

### Post by finite9 on 2006-08-19
Well I can second Duns comment...here is my output:

andrew@redwood:~$ lspci | grep -i bc
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


So, Greenfrog and clevershark...don't want to offend you but what you are posting is not correct.  I am using Ubuntu 6.06 amd64 with bcm43xx driver and rev 02 Broadcom and it's all working fine for me, as my HOWTO explains.

You *do not* need the Windows driver or ndiswrapper!

---

### Post by greenfrog on 2006-08-20
I am glad you got the native to work, however, they would not work on my
HP ZV5340U util I used the bcom564 driver and inf file.

---

### Post by Origin on 2006-08-20
Now I am confused as to what would be the best option for me :( I have a Turion-64 (not x2) on a compaq presario 2565us laptop equipped with a broadcom 4318 wireless card.

Ok, so which is the right option for me? I'm sorry for the confusion, but I'm terribly confused myself

---

### Post by lupine_nickt on 2006-08-20
Either will work ;). They'll both be a total PITA to set up, though. 

If you're not sure which to try, then I'd suggest you go for the native one first. If it works, it's a cleaner solution - and less hassle. 

You can get the firmware [here](http://www.lupine.me.uk/bcm43xx) (you'll need to install them whether you use ndiswrapper or the native driver)- for the next few days, anyway. Just save the .tar.gz file into a directory of it's own, run 'tar -xzvf *', 'rm *.gz', 'cp * /lib/firmware', 'cp * /lib/firmware/`uname -r`'

A bit less hassle than using fw-cutter, but probably in breach of a host of license agreements... meh ;)

xF,

...Nick

---

### Post by Origin on 2006-08-20
"Connection closed by remote server"

o_O

---

### Post by Origin on 2006-08-26
The download doesn't work...

---

### Post by compwiz18 on 2006-09-01
try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) for bcm4318 cards

the howto works best on fresh installs, but that isn't to say it won't work on not-so-fresh installs

this works for rev 2 cards like yours at 54mbps.  native (if you can get it to work) will probably only run at wireless b speeds, which are slower then 54mpbs (wireless g speed)

---

### Post by ntufar on 2006-09-02
Origin,

now if *ndiswrapper -l* reports:
```

Installed ndis drivers:
bcmwl5          driver present, hardware present

```

You need to load the kenel module itself:
```
$ modprobe ndiswrapper
```

Then go to *NetworkConfiguration* and see if it appears.

To make *ndiswrapper* start on reboot add *ndiswrapper *to */etc/modules*. And dont forget to remove or comment out *bcm43xx *from */etc/modules*

For reference, mu */etc/modules* looks like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#sisfb
#lp
psmouse
rtc
ndiswrapper
#bcm43xx

```

Hope it helps.

---

