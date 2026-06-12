---
title: "64 vs 32? i dont really know whats going on here"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by ThatGuy07 on 2008-10-08
okay so i am semi new to linux in general. I tried hardy a few months ago but due to a broadcom issue and lack or being hard wired into the internet it was a no go. so here i am again trying to get away from vista, but I have no clue what is going on. Heres the low down on what im running ,
Amd64 3700+
1.5 GiB ram
557 GiB Disk space
Ati Radeon hd2400pro

Now, when i say i am new to this, i really mean it. It took me over two hours to get my dual monitors to work. Anywho, to the point of all this, when i installed intrepid i went with the 64bit version. I didnt know the diffrence and to be honest i still really dont. But i am having alot of issues getting my graphics and wireless cards working. Plus i hear there are alot more issues with having a 64 bit system. So, would it be in my best intrest to go with the 32 bit until im a hardened ubuntu vet? or stick with the 64 and spend hours upon hours trying to get things working right? bah. excuse the lengthiness of all this, ive been at this graphics card for hours now and still no go. 

any guidance is greatly appreciated

---

### Post by xmunk on 2008-10-08
i run and have run 64 gutsy and hardy and have had little to no problems.  the problems i have had had nothing to do with 64 vs 32.  Since you are new new my suggestion would be to try hardy.  Intrepid is still in beta and thus slightly unstable.  imo try hardy it works and you can rule out a majority of the os being the problem.  as for wireless its always been a pain in my experience

---

### Post by ThatGuy07 on 2008-10-08
i just came to that decision a few mins ago. i had someone download 8.10 for me, not knowing it was still unstable. browsing through the forums i noticed a comment in someones tag saying so.

well i am headed to do that as we speak, thanks for the reply, it was the first out of my 4 posts(which were all over several months).

---

### Post by mikewhatever on 2008-10-08
Hmm... [64 versus 32.]("http://www.google.co.il/search?q=64+vs+32&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

---

### Post by Jouke74 on 2008-10-08
Other than finding a 64 bit solution for your wireless card there should be no problems using 64 bit Hardy Heron. 
Make sure you check this beforehand if this is your only way to get connected to the internet (find a linux driver, check ndiswrapper, check compatibility in the wiki's). Notice you can also use the live CD to test a few things and see how it works beforehand (that's how I started).

As is said many times (Where is Kilz??? :-) )the problem lies not in 32 bit vs 64 bit system, but more in 1. people wrongly blaming the "64 bits" for driver issues and getting hardware to work, 2. there are more people using 32 bit, and hence there are more how to's and answers to problems for 32 bit. Notice that many of these 32 bit solves work also on 64 bit. 

With any new thing you need to learn. Read the manual(s) and try, it will also take some time.

---

### Post by Sef on 2008-10-08
With graphic cards and wireless, the biggest problem is proprietary hardware and software.  Proprietary depends on when a company gets the work done versus the community getting it done.

---

### Post by Kilz on 2008-10-08
> **Jouke74 said:**
> Other than finding a 64 bit solution for your wireless card there should be no problems using 64 bit Hardy Heron. 
Make sure you check this beforehand if this is your only way to get connected to the internet (find a linux driver, check ndiswrapper, check compatibility in the wiki's). Notice you can also use the live CD to test a few things and see how it works beforehand (that's how I started).

As is said many times **(Where is Kilz??? :-) )**the problem lies not in 32 bit vs 64 bit system, but more in 1. people wrongly blaming the "64 bits" for driver issues and getting hardware to work, 2. there are more people using 32 bit, and hence there are more how to's and answers to problems for 32 bit. Notice that many of these 32 bit solves work also on 64 bit. 

With any new thing you need to learn. Read the manual(s) and try, it will also take some time.

Right here :)

Trying to resist reporting ya32v64p that should be in reoccurring discussions. But I agree with you.

---

### Post by Alpha-geek on 2008-10-08
I've running 64 bit Hardy for quite a while with no major problems. A little pre-planning to make sure your hardware is supported helps a LOT. This holds true with 32 bit version as well. Then just pay attention when you install new software for any mention of 64 bit differences. Perhaps it's just my perception, but the 64 bit version of Hardy seems to run a little faster than the 32 bit.

---

### Post by John.Michael.Kane on 2008-10-08
> **ThatGuy07 said:**
> i just came to that decision a few mins ago. i had someone download 8.10 for me, not knowing it was still unstable. browsing through the forums i noticed a comment in someones tag saying so.

well i am headed to do that as we speak, thanks for the reply, it was the first out of my 4 posts(which were all over several months).

For broadcom based wireless devices, you can try the below guide.

[broadcom guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy")

To find out what Broadcom chip you are using you can pass the below command, to list the PCI devices in your system.

```
lspci
``` 

The output should be something like below.
xxxx xx xx.x Network controller: Broadcom Corporation BCM "model" 802.11b/g Wireless LAN Controller (rev 0x)

[HardwareSupportComponentsWirelessNetworkCardsBroadcom]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")

For further troubleshooting
[WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Regarding your ati card, you can try the below method.
[Ubuntu_Hardy_ATI_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Hope this helps.

---

### Post by ThatGuy07 on 2008-10-09
Ok sorry it took so long for me to get back at yall. The issues wasnt 64 vs 32 or anything like that it was me being an idiot. lol. 

i tried to switch to hardy 64 and got this boot error, couldnt find grub or somthing like that. So i tried to install like 4 times, ( i was dual booting with vista) everytime the live cd would work but when i would reboot i would just get that grub error. 

Im sure there was an easier way to fix it than what i did, but i just went into the live cd, transfered everything from vista i wanted to keep to an external, formatted my hard drive and put in a clean install of hardy 64. Running great now. The graphics card works find, ive got my dual monitors and compiz running. Still having issues with the broadcom drivers, but i havent put much time into it

I did a google search and that is where i heard everyone complaining that 64 bit was causing all these problems. It was my fault for running intrepid as a noob i suppose, hardy is working fine. Im have a few small issues but im searching the forums before i go crying about any of those. 

Anyways, thanks all for your help.
I was close to switching back to windows outta frustration, but ya'll just saved another sould from microsoft.

---

