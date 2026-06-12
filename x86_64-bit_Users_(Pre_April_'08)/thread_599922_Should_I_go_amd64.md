---
title: "Should I go amd64?"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdean on 2007-11-01
My situation is this:

I have an entirely new computer: Athlon 6000+, Foxconn C51XEM2AA nForce 590 mobo, 4 GB of RAM, lots of hard drive space, GeForce 8800 GTX, Plextor 716SA burner.

I'm going to dual boot Windows XP and Ubuntu. The boot time for Windows is less than a minute, so I can switch to it for games and Windows-only tasks (silly classes requiring Visual Studio). However, I've used Ubuntu exclusively as my desktop on another computer for about two weeks, and really don't want to go back to Windows for everyday, regular tasks.

Before I installed Windows, I slapped on Ubuntu i386 to see how the machine ran. It boots in less than 20 seconds, shuts down in ~5. However, a mere 3.12 GB of RAM is recognized, like Windows. This is acceptable for Windows because I'm pretty sure that's all Windows 32-bit can recognize. However, I know that Ubuntu can eke out some more of the RAM. IIRC, the BIGMEM kernel config will enable more than 4 GB, but I don't know the drawbacks of doing this on i386.

The dilemma is this: I want to be able to use all 4 GB of RAM. I need 3D video to work, too, because I do hop into Nexuiz or UT2004 on Linux every now and then to take out some frustration.

**Should I use i386 or amd64?**

In my preliminary tests, I can get the amd64 live cd to boot, but after the bootscreen, the screen goes black and never shows the loading screen. The drive spins like its loading, and the screen doesn't turn off/go into power save mode, but I can't figure out what's wrong past that.

Additionally, I know there were some issues with Flash in the past, but a general survey of the forums seems to show that people do have it working, at least in a 32-bit Firefox. What about 64-bit?

---

### Post by Yellow Pasque on 2007-11-01
Did you try the livecd with safe video settings?

I've got Flash working just fine with 64-bit Firefox and/or Swiftweasel. It's very easy with nspluginwrapper now having an available package in synaptic. From my understanding, some java sites work with 64-bit browsers with a package called icedtea. Some sites don't work though, and if you encounter one of those that you need, you'll have to go with a 32-bit browser (at least for that site).

---

### Post by cdean on 2007-12-10
I did finally get it to boot just now. 

I removed the **quiet splash** options from the safe video kernel command line and it booted right up. When it installed, however, it left those options in menu.lst, so I had to remove them in order to actually let the system keep loading. 

Perhaps framebuffer doesn't like my 8800 GTX?

---

### Post by Melcar on 2007-12-11
The only thing that pisses me off about x86_64 is the lack of java, but I have my laptop for that.  You won't notice much of a difference between on or the other, aside from a few programs not having 64bit versions.

---

### Post by rsambuca on 2007-12-11
For the 8800, you definitely should be using the new beta drivers from nvidia.  Also, if you are doing 3D Rendering, then you shouldn't be wasting your time on a 32 bit system.  Flash works with Gutsy just by going to a website that requires Flash.   You are then prompted to install it with one click.

If you need Java plugin for your browser, then there is Kilz's script to install the 32bit browser with Flash and Java.

Don't bother with 32bit.  Thanks to the hard work of the developers and many members of the community, 64bit is pretty smooth sailing.

---

### Post by Jouke74 on 2007-12-11
Of course you should use AMD64....

For the 8800 black screen bug there are many posts all over the forum already with answers for the work-around (e.g. nosplash, use safe mode to switch drivers). There should also be a bug report and I think it is mentioned in the wiki (hopefully with solve).

---

### Post by sirdilznik on 2007-12-11
Flash in 64-bit pretty much works out of the box now.

---

### Post by sings64 on 2007-12-11
I have an HP machine with an athlon 6000+ and 4Gb of ram, and I'm running Gusty AMD64 on it.  It works very well and recognized the 4Gb of ram right away.  The cpu scaling works perfectly also.  I haven't had problems except that you can't manually control fan speeds due to the lack of i8k for AMD64 (search the forums for a more detailed description of this...)

---

