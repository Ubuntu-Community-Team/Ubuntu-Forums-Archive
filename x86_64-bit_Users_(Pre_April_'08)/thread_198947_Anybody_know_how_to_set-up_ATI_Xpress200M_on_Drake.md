---
title: "Anybody know how to set-up ATI Xpress200M on Drake (64-bit)?"
date: 2006-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by grittyg on 2006-06-18
Well first and foremost my problem is that i simply want to change the resolution of Ubuntu from the really large 640x480 to something tolerable such as 1024x768. I have installed Dapper v6.06 on one of my boxes and it has for a vid card the ATI Xpress 200M (probably the source of all of my problems even for 5.10), and installing the ATI 64-bit drivers did diddly squat, I think it doesn't support the Xpress 200M at 64bit. So now i just want to set it to vesa mode, unfortunately it is detected in the X config as a Xpress 200M although it doesn't work properly. I hope that setting it up to vesa might at least make the desktop to 1024x768, can anybody help me in setting this up to vesa? 

I could just firmly say that I have a lot of experience and know a lot on wintel machines, but I'm pretty much screwed at Linux, so I just became a complete noob. I'm nearly going insane with this problem.


Thought to self: Would it be easier for me to try dapper drake (32 bit version) and get the official ATI drivers? hmmm.... Or simply a change in distro is needed. Although, Ubuntu is still a good distro, my ******g vid card may be the source of all me Linux probs.

---

### Post by Kilz on 2006-06-18
[QUOTE=grittyg]Well first and foremost my problem is that i simply want to change the resolution of Ubuntu from the really large 640x480 to something tolerable such as 1024x768. I have installed Dapper v6.06 on one of my boxes and it has for a vid card the ATI Xpress 200M (probably the source of all of my problems even for 5.10), and installing the ATI 64-bit drivers did diddly squat, I think it doesn't support the Xpress 200M at 64bit. So now i just want to set it to vesa mode, unfortunately it is detected in the X config as a Xpress 200M although it doesn't work properly. I hope that setting it up to vesa might at least make the desktop to 1024x768, can anybody help me in setting this up to vesa? 

I could just firmly say that I have a lot of experience and know a lot on wintel machines, but I'm pretty much screwed at Linux, so I just became a complete noob. I'm nearly going insane with this problem.


Thought to self: Would it be easier for me to try dapper drake (32 bit version) and get the official ATI drivers? hmmm.... Or simply a change in distro is needed. Although, Ubuntu is still a good distro, my ******g vid card may be the source of all me Linux probs.[/QUOTE]

You can have the official drivers in 64 bit. I dont know where you got the information that you cant, but its wrong [ ATI has a 64 bit driver installer. ]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") Download the driver installer for your product. I think its a notebook since its an M. [Then use these instructions.]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") One thing those intructions dont mention is you may need the headers. ```
sudo apt-get install linux-headers-`uname -r`
``` At least I did to install a x200 express. It cant hurt to get them.

---

### Post by flip314 on 2006-06-18
my native LCD resolution (1280x800) was supported out of the box on both 32 and 64 bit dappers, so I'm not sure where your problem is originating.

I'd use the non-free ATI drivers from the repositories, I had more luck with those than the ones straight from the ATI website.

---

### Post by grittyg on 2006-06-18
Oh sorry about the post. I've found the solution in the How to's section, the  HOW TO: ATI Drivers v0.2 (Revised) ([http://www.ubuntuforums.org/showthread.php?t=24557&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&pp=10)) thread . Sorry that I didn't look more throughly. Seems that the problem was the settings in my XServer, it's using the ATI driver when it should use the fglrx one instead, thus causing me not to be able to change resolutions (Although for others reading the thread is important, if you got such a problem as mine). 

Well my vid card, the ATI Xpress200M is on my Asus P5RD1-VM mobo, and since breezy it's been giving me problems. During breezy it hangs at the "Starting hotplug subsytem" thingy. So I simply gave up and when I saw the new dapper i tried it and it works much better. Although when I first loaded it, it took a hell of a long time and it was experiencing the "Buffer I/O error cannot read, hdc"(something of the sort) error, waited for 10 mins and it started. Now in dapper i think the problem is my combo drive which reads the thing but slowly. If you want ubuntu DON'T get one of these boards, it will cause a lot of frustration and heartache for those not the strong of will.


Thanks for the great support anyway!

---

