---
title: "migrating away from 32 bit chroot?"
date: 2007-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by HankB on 2007-04-08
Hi all,
At present I'm using a 32 bit chroot for running some programs that aren't fully functional in 64 bit. IIRC, this is Firefox with support for flash and mplayer. There are probably a few other things there that I'm not thinking about too. Oh, yeah... I had OO installed there when it would not run under dapper 64.

This is on a system that is now running edgy which was upgraded from dapper. I don't recall if I installed dapper originally or something earlier, but I have done upgrades rather than reinstall if that makes any difference at this point.

I am planing to install wine and/or a VM running WinY2K to see if I can get some Garmin S/W running under Linux.

So... I have some questions.

First, it seems that there are a couple of ways to go with Firefox. One is to force the 32 bit version (and 32 bit plugins) and the other is to install a 64 bit version and use a wrapper to allow it to run 32 bit plugins. If I don't have that correct, clarify me! What are the advantages or disadvantages to either solution? Which should I choose?

Second, Anything I need to do to remove the chroot other than delete the directory and mounts in /etc/fstab?

Third, does any of this have any implications WRT the pending upgrade to feisty? My HOME is on a separate partition, so I could reinstall from scratch if necessary. (I have my most critical files backed up elsewhere anyway.) 

What's the simplest way to do this? Should I use the simple64 script or follow the detailed directions in posts, wikis and blogs?

Are there any pitfalls lurking for me with this upgrade? Anything else I should be thinking of?

thanks,
hank

---

### Post by Medieval_Creations on 2007-04-08
I'm currently running Feisty Beta amd64 and used 2 HowTo:'s to ger Firefox up and running without a problem.

First (to install Firefox 32 & additinal plugins)
[http://www.xnowherex.net/simple64/index.php](http://www.xnowherex.net/simple64/index.php)

Second (to install Java Runtime for 32bit Firefox)
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

For your second item I don't see why after taking the stpes you mentioned you should have any problems, that's what I've done in the past on previous systems.

Third, I'm not sure.  I did a fresh install with Feisty.  Afraid I woun't be much help there.

---

### Post by Kilz on 2007-04-08
> **HankB said:**
> Hi all,
At present I'm using a 32 bit chroot for running some programs that aren't fully functional in 64 bit. IIRC, this is Firefox with support for flash and mplayer. There are probably a few other things there that I'm not thinking about too. Oh, yeah... I had OO installed there when it would not run under dapper 64.

This is on a system that is now running edgy which was upgraded from dapper. I don't recall if I installed dapper originally or something earlier, but I have done upgrades rather than reinstall if that makes any difference at this point.

I am planing to install wine and/or a VM running WinY2K to see if I can get some Garmin S/W running under Linux.

So... I have some questions.

First, it seems that there are a couple of ways to go with Firefox. One is to force the 32 bit version (and 32 bit plugins) and the other is to install a 64 bit version and use a wrapper to allow it to run 32 bit plugins. If I don't have that correct, clarify me! What are the advantages or disadvantages to either solution? Which should I choose?

Second, Anything I need to do to remove the chroot other than delete the directory and mounts in /etc/fstab?

Third, does any of this have any implications WRT the pending upgrade to feisty? My HOME is on a separate partition, so I could reinstall from scratch if necessary. (I have my most critical files backed up elsewhere anyway.) 

What's the simplest way to do this? Should I use the simple64 script or follow the detailed directions in posts, wikis and blogs?

Are there any pitfalls lurking for me with this upgrade? Anything else I should be thinking of?

thanks,
hank

You could use my install script to install 32bit firefox with flash, java, and mplayer plugin all in one shot. Its basicly answering a few yes and no questions. The link is in my signature.  It has been tested on Feisty with few issues. There are also other options.
You could also use Simple 64 as suggested above, It basicly does the same thing, but may take a few more steps to do it. 
The last option is nspluginwrapper. It is difficlult to set up, some sites may crash the browser, and it dose not have support for the java plugin if you need it.
Next, Gaming under a vm is a waste of time. The video acceleration will not be enough to play most modern games at anything but a snails pace. Wine is ok, but it requires a lot of setup of the applications themselves. Cedega is avilable for $15 and makes installing Windows games easy. Click, click, play.
There are a few ways of installing wine, I have one linked in my signature.

---

### Post by HankB on 2007-04-08
Hi Kilz,
Thanks for the advice. I did use your script to install 32 bit Firefox and plugins. It mostly worked. (Some people can't follow directions! :oops: :roll: ) But an apt-get -f install fixed the problem. I still have one question about that. Will the normal updates and upgrades upgrade these packages as they become available or will I coninue to need to run the script? If I need to run the script, do I run the same one of do I need to download an update?

I also noticed that the cool spell checker that used to work with Firefox fields (like this one) is gone. I really need that! Is that a browser function or did I install a plugin to get that at some point? Or enable some feature that I added and forgot about? (Hmmm, there's an option in preferences to check spelling as I type that is currently checked.)

OK, that's two questions. ;)

I'll have to look into Cedega. By the way, that's Garmin as in the Garmin GPS. ([http://www.garmin.com/products/sp2720/](http://www.garmin.com/products/sp2720/)) One of the best things about this device is being able to use the PC S/W to plan routes and then download them to the GPS. That's one of the few Windows programs I still use.

thanks,
hank

---

### Post by Kilz on 2007-04-09
> **HankB said:**
> Hi Kilz,
Thanks for the advice. I did use your script to install 32 bit Firefox and plugins. It mostly worked. (Some people can't follow directions! :oops: :roll: ) But an apt-get -f install fixed the problem. I still have one question about that. Will the normal updates and upgrades upgrade these packages as they become available or will I coninue to need to run the script? If I need to run the script, do I run the same one of do I need to download an update?

I also noticed that the cool spell checker that used to work with Firefox fields (like this one) is gone. I really need that! Is that a browser function or did I install a plugin to get that at some point? Or enable some feature that I added and forgot about? (Hmmm, there's an option in preferences to check spelling as I type that is currently checked.)

OK, that's two questions. ;)

I'll have to look into Cedega. By the way, that's Garmin as in the Garmin GPS. ([http://www.garmin.com/products/sp2720/](http://www.garmin.com/products/sp2720/)) One of the best things about this device is being able to use the PC S/W to plan routes and then download them to the GPS. That's one of the few Windows programs I still use.

thanks,
hank

For some reason the spell check doesn't work in Edgy-Feisty. I'm going to look into that. As far as upgrades, I post updated .deb files on the page as a new version is released. Downloading it and installing (double click on it and gdebi will install it) it will upgrade everything without the need to run the script.

---

### Post by HankB on 2007-04-09
> **Kilz said:**
> For some reason the spell check doesn't work in Edgy-Feisty. 

Seems likely a missing or not-found library then since it worked under the chroot. I wonder how to determine what libraries a running program uses since this is probably not linked in (to be revealed by 'ldd'.)

thanks,
hank

---

### Post by elanthis on 2007-04-09
You could use strace to see which libraries it attempts to load.

Something like:
 strace mozilla | grep /usr/lib
might work for you.

---

