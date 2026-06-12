---
title: "Quesion from a noobe"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ascus4 on 2007-03-14
I installed Ubuntu 64 bit on my AMD Turion before I found this forum.  I am now seriously thinking of replacing it with 32 bit.  It's not that big of a deal because I haven't installed a lot of software yet.

If I were to do this, do I just put in the live CD and hit install?  I'm assuming that when I get to the partition section of the install it will format or something to eliminate the 64 bit install?  I want to do a clean install without disturbing my Windows partition.

Thanks,

---

### Post by mixium on 2007-03-14
> **ascus4 said:**
> I installed Ubuntu 64 bit on my AMD Turion before I found this forum.  I am now seriously thinking of replacing it with 32 bit.  It's not that big of a deal because I haven't installed a lot of software yet.

If I were to do this, do I just put in the live CD and hit install?  I'm assuming that when I get to the partition section of the install it will format or something to eliminate the 64 bit install?  I want to do a clean install without disturbing my Windows partition.

Thanks,

Yes, you should put in the LiveCD and take care to make sure that the partitions are selected to be formatted. Be mindful not to format the Windows partition (likely labeled as NTFS filesystem). It should be no different (maybe easier) than the prior installation.

You do leave me wondering why you want to replace the 64 bit version before even trying to install any new packages. Is there something that bothers you about running in 64 bit mode?

I really enjoy running in 64 bit mode.

:)

Michael

---

### Post by John.Michael.Kane on 2007-03-14
Before installing 32bit ubuntu. 

Have a read [ Advantages and Disadvantages of 64bit.]("http://ubuntuforums.org/showthread.php?t=368607")

I'm pretty sure any issues your having with 64bit can be sorted out with out you having to move to 32bit.

Also it would help if you could tell us why you want to move back to 32bit.


In any case if you feel the need move back to 32bit just use the 32bit live cd to reinstall,and wipe your current running OS.

---

### Post by ascus4 on 2007-03-14
Good question.

I'm new to Linux and a lot of it confuses me.  I barely understand installing repositories, packages and such and it usually fails when I try.  I realise that it's probably not that hard once you learn and learn it I will, but I have yet to successfully install a package from start to finish. I have tight schedules and don't have lots of time to play with it.  For now I just want it to work and then I can learn as I go with a working machine.

The main thing is that I want to run Wine and I don't think I can deal with the extra steps involved.


W-

---

### Post by John.Michael.Kane on 2007-03-14
> **ascus4 said:**
> Good question.

I'm new to Linux and a lot of it confuses me.  I barely understand installing repositories, packages and such and it usually fails when I try.  I realise that it's probably not that hard once you learn and learn it I will, but I have yet to successfully install a package from start to finish. I have tight schedules and don't have lots of time to play with it.  For now I just want it to work and then I can learn as I go with a working machine.

The main thing is that I want to run Wine and I don't think I can deal with the extra steps involved.


W-

Ok that's understandable,however.Understand that you will still need to use the guides for installing wine,and codecs under 32bit as well.

 If you want to give 64bit one more shot I can give you guides for installing wine,and codecs/ect under 64bit,however. if you really feel moving back to 32bit is best for you at this time thats fine.

---

### Post by ascus4 on 2007-03-14
I'll give it another shot.  I'd like to keep 64 if it's practical.  I think the main thing is Wine with it's hack.  I follow various guides for various things and it hasn't worked.
I have however, found some good web instruction for the use of synaptic that I havenm't had a chance to use yet.  
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
and
[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html#more-94](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html#more-94)

Anyway, long story short...if I can work it out I'd like to keep 64.  I just read so much stuff in this forum that seemed negative about it at this point in it's development......I don't have the skill with Linux yet to work out too many complicated problems.

If I can get Wine installed and working and get a better understanding in the use of synaptic, packages and repositories then...cool.
I would accept gratefully any help you care to throw my way.

I appreciate your offer.

W-

---

### Post by John.Michael.Kane on 2007-03-14
Heres ways to get wine,and other codecs.
[**Install wine to 64 bit**]("http://www.ubuntuforums.org/showthread.php?t=185557")

Script method: note also offers codec installing.
[**simple64**]("http://www.ubuntuforums.org/showthread.php?t=266290&highlight=java")

For Dvd playback manual install.
[**Gstreamer**]("http://www.ubuntuforums.org/showpost.php?p=2205606&postcount=3")

For flash ect.
[**Firefox with Flash**]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java")

---

### Post by ascus4 on 2007-03-14
Ok, thanks for the links.  It may take me a bit to get through all that, looks confusing.  If I can get on it tonight I will.

I'll let you know what happens and again, thanks.

W-

---

### Post by ascus4 on 2007-03-14
One additional note.  The guide says it's for Dapper and I'm running Edgy.

I see that in some spots it says to do such and such if running Edgy.  Is this guide really practical
for Edgy?

---

### Post by ascus4 on 2007-03-14
Wait a moment.  I was looking at the package download site and it shows Edgy as 6.10.

I have 6.06.  That means I have Dapper, not Edgy?

---

### Post by mixium on 2007-03-14
Yes, the 6.06 version is the Ubuntu 6.06 LTS (Long Term Support) and has a specific emphasis on the needs of large organizations with both desktop and server versions.

Edgy is the 6.10 version.

:)

Michael

---

### Post by Kilz on 2007-03-14
> **ascus4 said:**
> One additional note.  The guide says it's for Dapper and I'm running Edgy.

I see that in some spots it says to do such and such if running Edgy.  Is this guide really practical
for Edgy?

As far as wine goes and most other things dealing with 64bit, there is very little difference (if any at all) in the instructions for Edgy or Dapper. Most howto's will deal with both (since they are both supported) and may have extra instructions if needed for Edgy.
Dapper is a long term support(I believe 3 years of suooprt). It will still have support for a year when edgy (18 months of support)is no longer supported. It is very stable and has a ton of applications available. To me the only difference between the two is some new graphics in some places.
For me, Dapper is my choice, even though Im testing Feisty (now in Alpha testing) I spend a majority of my time using Dapper.

---

### Post by ascus4 on 2007-03-14
You sent me to
[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
and it helped me out with my Wine install on 64 bit Dapper.  You got me further than I have gotten so far but when I ran winecfg I got the following error:

thing1@thing1-laptop:~/Desktop$ winecfg
wine: creating configuration directory '/home/thing1/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/thing1/.wine'.
thing1@thing1-laptop:~/Desktop$ wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/system.reg : No such file or directory
wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/user.reg : No such file or directory


Do you have any idea what that might be?
I sure appreciate it.

W-

---

### Post by Kilz on 2007-03-14
> **ascus4 said:**
> You sent me to
[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
and it helped me out with my Wine install on 64 bit Dapper.  You got me further than I have gotten so far but when I ran winecfg I got the following error:

thing1@thing1-laptop:~/Desktop$ winecfg
wine: creating configuration directory '/home/thing1/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/thing1/.wine'.
thing1@thing1-laptop:~/Desktop$ wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/system.reg : No such file or directory
wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/user.reg : No such file or directory


Do you have any idea what that might be?
I sure appreciate it.

W-

The GLX errors indicate you do not have accelerated graphics. You may need to install the proprietary graphics driver for your card to get it. Secondly did you install the sidenet setup script?

---

### Post by John.Michael.Kane on 2007-03-14
I was unable to duplicate your errors. Test ran on a clean fully updated install of 6.06.1 with the nividia drivers installed as well.

You can restart using the steps listed here. you should not have to reinstall.

Download this version wine_0.9.32 6.06-1_i386.deb
[**6.06-1_i386.deb**]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.06-1_i386.deb")

Download the libxxf86dga1 package from the link below
[**libxxf86dga1 package**]("http://ubuntu.cs.utah.edu/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb")

Next step install these files. 

```
sudo aptitude install libartsc0 libaudio2
```

Next you can install the needed libraries.
```
cd ~/Desktop
```
Run:
```
dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
```
Next run:
```
sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
```

This command will install wine:
```
sudo dpkg --force-architecture -i wine_0.9.32~winehq0~ubuntu~6.06-1_i386.deb
```

Test it out by typing winecfg, the wine controll pannel will should start up.

This info is from Kilz guide only parts filled in where the libartsc0 libaudio2 dependances,and editing the dpkg to match the downloaded deb.

I included a screen shot of the wine panel running. hope it helps.
[[IMG]http://img174.imageshack.us/img174/8151/screenshot1tv2.th.png[/IMG]](http://img174.imageshack.us/my.php?image=screenshot1tv2.png)

---

