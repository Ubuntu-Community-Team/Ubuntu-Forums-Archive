---
title: "Upgrade to AMD64 Ubuntu?"
date: 2007-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by wheelhorse2347 on 2007-02-21
I recently installed Ubuntu on my desktop and after getting the various drivers it seemed to run fine.  I just upgraded my Processor to an AMD Athelon 64.  Is there any way for me to "Upgrade" from the OS I have now to the Ubuntu for AMD 64 without losing all of the information I have on my compy now, or will I have to make a backup and do a complete reinstall?

Thanks,
Jordan

---

### Post by xopher on 2007-02-21
No there isn't, to upgrade to amd64, you need to do a complete re-install.

If you don't know what your getting yourself into though, Id still stick to x86, the performance gain is only marginal compared to it, and you won't have problems with java, flash and wine.

---

### Post by wheelhorse2347 on 2007-02-21
Thanks.  I didn't know if there would be any performance gain at all, but you say there isn't, so I'm not too worried.

---

### Post by Kilz on 2007-02-21
> **wheelhorse2347 said:**
> Thanks.  I didn't know if there would be any performance gain at all, but you say there isn't, so I'm not too worried.

The gains all depend on what applications you run. There is a small 5% overall gain. There is also a 30% performance gain on applications that crunch numbers like 3d design/rendering and ripping/encoding media.
The people that claim it isnt that much may not run 64bit, may only run their browser, or may have failed at installing it so they rationalize that it isnt worth it.


> **wheelhorse2347 said:**
> I recently installed Ubuntu on my desktop and after getting the various drivers it seemed to run fine.  I just upgraded my Processor to an AMD Athelon 64.  Is there any way for me to "Upgrade" from the OS I have now to the Ubuntu for AMD 64 without losing all of the information I have on my compy now, or will I have to make a backup and do a complete reinstall?

Thanks,
Jordan
As said above, you will have to do a 64bit install. If you have room, install it to a different partition. That way you can ease yourself into 64bit in case you have any problems.

---

### Post by wheelhorse2347 on 2007-02-21
I'm sorry, most of my questions are probably embarasingly easy to answer, but when I installed Ubuntu the first time, did it leave a partition in which I can install the 64 bit OS, or will I have to re-format the partitions to make it fit?

---

### Post by Kilz on 2007-02-21
> **wheelhorse2347 said:**
> I'm sorry, most of my questions are probably embarasingly easy to answer, but when I installed Ubuntu the first time, did it leave a partition in which I can install the 64 bit OS, or will I have to re-format the partitions to make it fit?

You can resize the partitions during install to make room if you want to.

---

### Post by wheelhorse2347 on 2007-02-21
Thank you all very much, I'm going to try it now.

---

### Post by dirtvoyles on 2007-02-25
So, my /home will be unusable with the 64-bit system? Or did you guys just mean there was no route from 32 to 64 using apt-get?

---

### Post by RAOF on 2007-02-26
Your /home will be fine (as long as you don't accidentally reformat it!).  Your data doesn't care what processor arch it's on :).

You can't use apt to get from a 32bit to a 64bit system, though.  A reinstall is necessary.

---

### Post by bsalt on 2007-10-13
oh, so is it possible to reinstall ubuntu over the same distribution without reformatting or resizing?

---

### Post by jpyanowski on 2007-10-14
**This post could be related to an Ubuntu bug filed at**:   [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **bsalt said:**
> oh, so is it possible to reinstall ubuntu over the same distribution without reformatting or resizing?

If you are going from 32 to 64 bit you will have to format and Install. If you are "reinstalling" 32 over 32 you should format. (I think the installer tells you this), It's to your benefit to format.

---

### Post by Kilz on 2007-10-14
> **jpyanowski said:**
> **This post could be related to an Ubuntu bug filed at**:   [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

If you are going from 32 to 64 bit you will have to format and Install. If you are "reinstalling" 32 over 32 you should format. (I think the installer tells you this), It's to your benefit to format.

I know you can upgrade from one version to another without formating, as long as it is the same version

---

### Post by bsalt on 2007-10-14
So has anybody had a problem with running a 32-bit application on Ubuntu AMD64? I know about the Flash epidemic, but that matters little to me. I am seriously considering upgrading to AMD64 if it really would works with 32-bit apps.


One other thing, I've tried 64-bit before, and it appears I couldn't get the machine to boot to the disc. But then I tried a 32-bit disc (they were both downloaded and burned, so it could be a bad CD) and it worked flawlessly. 

Is booting to a 64-bit disc sometimes a problem?


EDIT:
Also, is there an Nvidia driver that supports 64-bit as well?

---

### Post by rsambuca on 2007-10-15
> **bsalt said:**
> So has anybody had a problem with running a 32-bit application on Ubuntu AMD64? I know about the Flash epidemic, but that matters little to me. I am seriously considering upgrading to AMD64 if it really would works with 32-bit apps.


One other thing, I've tried 64-bit before, and it appears I couldn't get the machine to boot to the disc. But then I tried a 32-bit disc (they were both downloaded and burned, so it could be a bad CD) and it worked flawlessly. 

Is booting to a 64-bit disc sometimes a problem?


EDIT:
Also, is there an Nvidia driver that supports 64-bit as well?

There is no "Flash epidemic" - it works very well with 64bit.
Most applications have been compiled to work natively in the 64bit environment.  There is very little difference between the 32bit and 64bit repositories.
There should be no difference between booting a 64bit or 32bit disc (unless you only have a 32bit capable machine).
There is an nVidia driver for the 64bit system.

---

### Post by bsalt on 2007-10-15
Thanks, rsambuca. Some of those questions I already answered just by looking at the package repos. I actually already downloaded and burned the Gutsy RC 64-bit iso and installed it. I am now in 64-bit and it is working perfectly. Thanks man!

---

### Post by rsambuca on 2007-10-15
Good stuff.  Ya may as well use the bits if ya got 'em!

---

### Post by bsalt on 2007-10-17
Yeah, good point. And now I'm using them, and I know I'm not wasting any aspect of my machine now. It really does scream with Ubuntu 64.

---

### Post by malachias on 2007-10-27
To upgrade your system from 32-bit to 64-bit you can follow this guide:
[http://www.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html](http://www.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html)

...but I wouldn't recommend it. Neither would the guide for that matter. It has one of the most amusing disclaimers I have ever read.
Also, it is technically for Debian and not Ubuntu, but still...

---

### Post by bitumen on 2007-11-13
WOW that's a serious disclaimer ....


Ummmm I wonder if Microsoft should adopt it for their EULA

:lolflag:


I'm thinking of doing a clean install is the better way

---

### Post by cjazz on 2007-11-14
"If it eats your firstborn"? Did Mike Tyson write that disclaimer?

---

### Post by bitumen on 2007-12-02
if anyone else is looking for 32 bit and 64 bit information this post will help

[http://ubuntuforums.org/showthread.php?t=368607]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Gotit on 2007-12-02
This may sound like an odd question, but how can I tell if I have the i386 or AMD64 version installed?  I have an AMD64 processor, but the disk I was given to install with wasn't labeled i386 or AMD64.

Thanks

---

### Post by rsambuca on 2007-12-02
Open a terminal (Applications -> Accessories -> Terminal).  At the prompt, enter```
uname -a
```You can post the output here.

---

### Post by Gotit on 2007-12-03
I show:
> Linux Home-Ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by rsambuca on 2007-12-03
You have the 32bit version of Ubuntu installed.

---

### Post by Gotit on 2007-12-03
Thanks.
Just curious, what would the 64 bit version have shown, something like "...64 GNU/Linux" instead of ..."i686 GNU/Lunix" for the 32 bit?

---

### Post by rsambuca on 2007-12-03
It would show x86_64

---

### Post by olek54321 on 2008-02-02
> **malachias said:**
> To upgrade your system from 32-bit to 64-bit you can follow this guide:
[http://www.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html]("http://www.digitalkingdom.org/%7Erlpowell/hobbies/debian_arch_up/index.html")

...but I wouldn't recommend it. Neither would the guide for that matter. It has one of the most amusing disclaimers I have ever read.
Also, it is technically for Debian and not Ubuntu, but still...

Well, I **do** have rather masochistic tendencies. ;)  I don't really want to reinstall and, although this may well end up being more work, I think I'll give it a shot.  If nothing else I'll post back to this thread so noone else repeats my mistake. :-\"

I am running Ubuntu Server 7.10 on a Dell PowerEdge SC420 with an Intel EM64T processor and 4Gb of RAM.  Keep you fingers crossed!

---

### Post by olek54321 on 2008-02-02
Ok, I'll keep a running log of my progress here.

0031: **Finally** starting the upgrade!  I'm connected to my server by ssh from my laptop.  Just to be safe, I'm logged in on terminal too.  According to Aptitude the server kernel already supports both x86 and x86_64.  Very nice.  I hope that is truly the case...  Busybox is installed and working.

0314:  Ok decided to [flash my BIOS]("http://ubuntuforums.org/showpost.php?p=4253448&postcount=36") first since I've never actually done that.  Took a little longer than I'd expected...  Ok, on to the compatibility libraries.  Found those on launchpad along with dependencies:
[https://launchpad.net/ubuntu/gutsy/amd64/ia32-libs/2.1ubuntu3](https://launchpad.net/ubuntu/gutsy/amd64/ia32-libs/2.1ubuntu3)

Copied the link location for each of the debs and then used: 
```

wget [pasted link here]

```
until I had downloaded all the necessary files.  

0343:  Ok, time for dpkg, apt-get, etc.  Same process.  Note that the "Depends on" links for "apt-listchanges" point to the ***i386 ***packages!!  If you change the "i386" to an "amd64" in the URL it will take you to the correct location.  [Filed a bug report. ]("https://bugs.launchpad.net/launchpad/+bug/188291") Might be a good idea to do an "ls" once you're done downloading to make sure you got the correct files.  Also, launchpad does not list the following packages as dependencies for the four required packages:
binutils
bzip2
libbz2
coreutils
cpio
ed
libacl1
libasound2
libattr1
libgdbm3
libgpmg1
libncurses5
libreadline5
libselinux1
libsepol1
make
ncurses-bin
patch
perl-base
perl
sed
I'm not sure if they're needed or not but I downloaded them anyway, just to be safe. :)  Also, launchpad says that "python-apt" is required so I got that too.

0509:  Ok, let's take a quick break to keep this post from getting too long.

---

