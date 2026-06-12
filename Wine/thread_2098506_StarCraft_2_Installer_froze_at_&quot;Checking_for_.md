---
title: "StarCraft 2 Installer froze at &quot;Checking for updates&quot; ... :("
date: 2012-12-26
forum: Wine
---

### Post by mind_exploit on 2012-12-26
Hey, huys :)

I'm trying to install StarCraft 2 and World of Warcraft, and so I downloaded both installers, installed wine - it's 1.4.1 now. I made both installers executable ... 

BUT ... for both of them - when I launch them - they start with "Checking for updates..." - and no progress at all.

Tried with starting the launchers directly and running them from the terminal. Also - installed a few things from winetricks, cause I read that they are prerequisites for StarCraft 2.
Also - tried with my laptop conneted to internet via cable and not wiresell. Nothing helped so far.

So ... do you have any idea? ... I'll be very gratefull ... :) ...

---

### Post by overdrank on 2012-12-26
Moved to Gaming & Leisure :)

---

### Post by mind_exploit on 2012-12-27
I forgot to mention that I'm on Kubuntu 12.10 64 bit. I also installed ia32-libs-multiarch:i386 ... no result.

Also - when I run the installers - nevermind which one - in the Konsole - I see many lines ending with "... already in cache - don't know what to do!"
And on every minute it starts again and again, and then stops, and wait for a while again. The last lines before stopping are kind of "Deferred delete of 'xxxx' resource completed"

Any ideas? ...

---

### Post by jonobeen on 2012-12-27
Getting same issue with Ubuntu 12.10 and WINE 1.4.1.

*[Edit] More Info*

I've been trying to get this to work for a couple hours now. It seems to be an issue with the Blizzard Tools updater not being able to update the launcher, Ive had various issues from being stuck on 'Updating Blizzard Update Agent' to 'Checking for Updates'. 

It seems to be a problem on Windows too, some of the causes in Windows are the Secondary Logon Service not working, Firewall blocking traffic etc. I have no idea if these could be problems with WINE.

I am new to Linux, I've played around with it a couple of times over the years but this is the first time I've installed it and kept it without a dual-boot.

I've had a rant at Blizzard over on their forums... anyway naturally the blues just ignored me because I'm running Ubuntu regardless that this seems to be a Blizzard problem.

---

### Post by jonobeen on 2012-12-27
Okay, I think I've figured this out. Uninstall Wine 1.4 and redownload the experimental version WINE 1.5. Then try and I think it's working. 

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by mind_exploit on 2012-12-27
> **jonobeen said:**
> Okay, I think I've figured this out. Uninstall Wine 1.4 and redownload the experimental version WINE 1.5. Then try and I think it's working. 

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

Yes, my friend :) ... that helped ;) ... 

I removed 1.4 of Wine, then I did autoremove, then I added the repository and installed wine 1.5. Then the launcher ontinued :) ... 

(It gave me an error with error code BLZPTS00008, I downloaded the installer again, and so - now I'm installing the game :) ...)

Thank you so much :) ... :guitar: ...

---

### Post by jonobeen on 2012-12-28
Awesome, glad it worked for you too :cool:

---

### Post by sir.sargento on 2013-01-21
Sorry for resurrecting the dead. But I have the same problem. Installed the beta 1.5 wine and am still getting this problem. Should I start a new thread? Any ideas?

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Which distro are you running? Bit type? What else have you tried? Make sure you deleted all the old remnants of previous .wine folders before you installed 1.5.

---

### Post by sir.sargento on 2013-01-21
Hey mate. Yes. I deleted all of my old wine folders as they said in this thread. I am using ubuntu 12.04 32bit. Was using wine 1.4 something now using 1.5

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Did you autoremove with the terminal and then run an update before you or after you installed the later wine? Make sure you don't have Firewalls blocking it, also, try this fix;

> 
typing

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

before running starcraft 2 avoids the issue for me

Given the workaround, it could be related to this bug
[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206)
or this one
[http://bugs.winehq.org/show_bug.cgi?id=24193](http://bugs.winehq.org/show_bug.cgi?id=24193)
Thanks to Shadows_Friend for pointing these out here
[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/978678](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/978678)


If that fails, I would suggest something that nearly works everytime I or another suggests it; downgrading to 1.3. wine. But I will continue to offer my assistance for your current version as long as you are willing to still use it. :)

You may also try; [http://www.elidust.com/how-to-install-starcraft-ii-on-linux/](http://www.elidust.com/how-to-install-starcraft-ii-on-linux/)

---

### Post by j0lliyo on 2013-04-13
Thanks, using 1.5 worked for me aswell =)

---

