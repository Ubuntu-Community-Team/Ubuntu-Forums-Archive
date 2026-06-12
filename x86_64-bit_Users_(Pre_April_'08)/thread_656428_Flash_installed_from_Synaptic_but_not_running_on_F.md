---
title: "Flash installed from Synaptic but not running on Firefox. What gives?"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by eks on 2008-01-02
Even after reseting everything (it was actually installed days ago, had to configure other things first).  The list of installed files on Synaptic is:

(package name: flashplugin-nonfree)
```

/.
/usr
/usr/lib
/usr/lib/xulrunner
/usr/lib/xulrunner/plugins
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/iceape
/usr/lib/iceape/plugins
/usr/lib/iceweasel
/usr/lib/iceweasel/plugins
/usr/lib/firefox
/usr/lib/firefox/plugins
/usr/lib/midbrowser
/usr/lib/midbrowser/plugins
/usr/lib/flashplugin-nonfree
/usr/share
/usr/share/doc
/usr/share/doc/flashplugin-nonfree
/usr/share/doc/flashplugin-nonfree/copyright
/usr/share/doc/flashplugin-nonfree/changelog.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/flashplugin-nonfree
/var
/var/lib
/var/lib/flashplugin-nonfree
/var/cache
/var/cache/flashplugin-nonfree

```

There is the installing script from Kilz (which I successfully used on 7.04) [in a 60 page long thread]("http://ubuntuforums.org/showthread.php?t=476924&page=60"), and [the downloadable plugin from Adobe]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4"), in tar, rpm and yum, but not in .deb (or a repo for Ubuntu users...).

Should I give one of this options a try? If so, should I uninstall it from Synaptic? Or install over it?


eks

---

### Post by ~LoKe on 2008-01-02
You should be able to install flash like this....all one line.

```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
```
Then follow the steps.

---

### Post by eks on 2008-01-02
Thanks!!!

It worked! :)

---

### Post by ~LoKe on 2008-01-02
> **eks said:**
> Thanks!!!

It worked! :)

You're very welcome, but you should also thank **Kliz**, who made and/or uploaded the packages for use in [this](http://ubuntuforums.org/showthread.php?t=476924) thread.

---

### Post by MangasColoradas on 2008-01-02
Cant seem to connect to the sever. Waited about 5 mins, nothing happening. :(

---

### Post by ~LoKe on 2008-01-02
> **MangasColoradas said:**
> Cant seem to connect to the sever. Waited about 5 mins, nothing happening. :(

Unfortunately I don't have a copy of the package to give you.  You'll have to watch [this](http://ubuntuforums.org/showthread.php?t=476924) thread for an update or wait for it to come back online.

---

### Post by MangasColoradas on 2008-01-02
OK, thanks. 

:)

---

### Post by ~LoKe on 2008-01-03
Alright, the server's back up so it should work now.

---

### Post by MangasColoradas on 2008-01-03
Yep, all done. :) 

Kudos to Kilz! :KS

---

### Post by helix_r on 2008-01-03
This will sound like a rant, but I need to get it off my chest...

I think it is really great that the ubuntu community is coming up with workarounds for getting flash operational on browsers, I commend those that have stepped forward.

However, what I cannot understand is why the ubuntu organization can go through the colossal effort of putting together an excellent OS distro, BUT THEN SHOOT THEMSELVES IN THE FOOT by not making this ridiculous flash problem just go away. 

How many people have silently given up on linux simply because their desktop browser + flash + java applets, and java applications and development environments failed to "JUST WORK"? 

I would understand inaction if we were talking about an obscure app, but we are talking about being able to use firefox on websites that millions of people visit everyday, and being able to view, analyze and participate in vital dialog with others on the internet.

**If it really is a matter of running a simple script, why can't there just be ONE THING that we can download via synaptic and be done with it? Why do we have to rely on the charity of others to host scripts on their home.comcast.net websites? **

---

### Post by Kilz on 2008-01-03
> **helix_r said:**
> This will sound like a rant, but I need to get it off my chest...

I think it is really great that the ubuntu community is coming up with workarounds for getting flash operational on browsers, I commend those that have stepped forward.

However, what I cannot understand is why the ubuntu organization can go through the colossal effort of putting together an excellent OS distro, BUT THEN SHOOT THEMSELVES IN THE FOOT by not making this ridiculous flash problem just go away. 

How many people have silently given up on linux simply because their desktop browser + flash + java applets, and java applications and development environments failed to "JUST WORK"? 

I would understand inaction if we were talking about an obscure app, but we are talking about being able to use firefox on websites that millions of people visit everyday, and being able to view, analyze and participate in vital dialog with others on the internet.

**If it really is a matter of running a simple script, why can't there just be ONE THING that we can download via synaptic and be done with it? Why do we have to rely on the charity of others to host scripts on their home.comcast.net websites? **

Because proprietary applications like Flash, that is owned by Adobe will not let Linux (Ubuntu and others) have access to the code and (Adobe) put out updates that break things.
In Short, its not open source, so do not put the blame on Ubuntu , but on Adobe.

---

### Post by ~LoKe on 2008-01-03
> **Kilz said:**
> Because proprietary applications like Flash, that is owned by Adobe will not let Linux (Ubuntu and others) have access to the code and (Adobe) put out updates that break things.
In Short, its not open source, so do not put the blame on Ubuntu , but on Adobe.

Yep.  Adobe creates the plugins and we, the community, find ways to "make it work".

---

### Post by helix_r on 2008-01-03
> **Kilz said:**
> Because proprietary applications like Flash, that is owned by Adobe will not let Linux (Ubuntu and others) have access to the code and (Adobe) put out updates that break things.
In Short, its not open source, so do not put the blame on Ubuntu , but on Adobe.


The core issue here is not that flash isn't open source, although it would be nice, but such is reality. Also, the update as I understand it, simply had a new md5sum which was not updated in package deployment scripts. How is that the fault of adobe?

Why can't ubuntu handle this flash issue the same way that they handle "restricted" drivers for graphics cards?  Or even better, fix it so that when you install "flash-non-free-plugin" from synaptic, it JUST WORKS as expected.

Why is that too much to ask of an organization capable of delivering a kick *** linux distribution?

---

### Post by Kilz on 2008-01-03
> **helix_r said:**
> The core issue here is not that flash isn't open source, although it would be nice, but such is reality. Also, the update as I understand it, simply had a new md5sum which was not updated in package deployment scripts. How is that the fault of adobe?

Why can't ubuntu handle this flash issue the same way that they handle "restricted" drivers for graphics cards?  Or even better, fix it so that when you install "flash-non-free-plugin" from synaptic, it JUST WORKS as expected.

Why is that too much to ask of an organization capable of delivering a kick *** linux distribution?

Wrong, the plugin has loads of issues. That is Adobe's fault. Its their proprietary application. It is in no way the fault of Ubuntu or any other Linux distro.  FOSS operating systems cant just get code for proprietary applications and fix things.
Granted there is a work around. But the new plugin is awful. I have a script that installs the older plugin that Im recommending, because it works.

---

### Post by helix_r on 2008-01-03
> **Kilz said:**
> Wrong, the plugin has loads of issues. That is Adobe's fault. Its their proprietary application. It is in no way the fault of Ubuntu or any other Linux distro.  FOSS operating systems cant just get code for proprietary applications and fix things.
Granted there is a work around. But the new plugin is awful. I have a script that installs the older plugin that Im recommending, because it works.

I don't know what these all these issues are as I've only seen the md5sum thing, but whatever they are, when someone checks "flash-nonfree-plugin" on their synaptic installer, there is no good reason why it should not install *whatever* working version of flash and whatever else is needed to make it JUST WORK.

Again, I understand that limited resources cannot allow the ubuntu folks to troubleshoot every little application, but we are talking about something that virtually _everyone_ uses. It would be worthwhile for the ubuntu organization to make it so flash can be installed consistently LIKE EVERY OTHER APP, modulo a few legal "click-throughs" that no one cares about anyway.

---

### Post by Kilz on 2008-01-03
> **helix_r said:**
> I don't know what these all these issues are as I've only seen the md5sum thing, but whatever they are, when someone checks "flash-nonfree-plugin" on their synaptic installer, there is no good reason why it should not install *whatever* working version of flash and whatever else is needed to make it JUST WORK.

Again, I understand that limited resources cannot allow the ubuntu folks to troubleshoot every little application, but we are talking about something that virtually _everyone_ uses. It would be worthwhile for the ubuntu organization to make it so flash can be installed consistently LIKE EVERY OTHER APP, modulo a few legal "click-throughs" that no one cares about anyway.

I am getting the feeling from reading your words that you dont understand that most of the FOSS developers dont take those kind of steps for good reason. The reason we all have this operating system and the freedom that comes with it is because those that went before us had the sense not to make compromises that limit freedoms.
That copyright works for us, and we must do everything on the up and up and respect the rights of others. Even when it may be a little inconvenient. 
If you dont mind people ripping people off and backstabbing users and everyone in the back, there is an operating system made in Redmond.

---

### Post by nevlis on 2008-01-03
This.. didn't work for me. I thought it did. It said it did. But, then it didn't.

---

### Post by crazyness003 on 2008-01-03
Not to be negative or a "hater" so to speak, but since you want it to "JUST WORK" so bad, get off your bum and take a step at fixing this oh-so fearsome problem that has plauged this free community for...well ubuntu has been around since '04, so...for 4 years.
Sorry, but its community developed, that fact that its free, gives us unparalleled access to so much information and on top of that, people are willing to personaly help you with these problems, for the cost of three payments of $0...i'll call that a win-win-win situation. 

Peace, and let there be gnu/linux, linux, and bsd everywhere.

---

### Post by crazyness003 on 2008-01-03
By the way, I recently upgraded my kernel from gutsy 2.6.22-14-rt to hardy dev  kernel 2.6.24-2-generic. The install works. I have flawless flash in firefox. 
This is my browser info:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

Even tho it says gutsy, this is the hardy dev kernel 2.6.24-2-generic. I did pick option 3 (Gutsy) during the install.

Just so you know

---

### Post by helix_r on 2008-01-04
> **crazyness003 said:**
> Not to be negative or a "hater" so to speak, but since you want it to "JUST WORK" so bad, get off your bum and take a step at fixing this oh-so fearsome problem that has plauged this free community for...well ubuntu has been around since '04, so...for 4 years.
Sorry, but its community developed, that fact that its free, gives us unparalleled access to so much information and on top of that, people are willing to personaly help you with these problems, for the cost of three payments of $0...i'll call that a win-win-win situation. 

Peace, and let there be gnu/linux, linux, and bsd everywhere.

Peace, 

I think its great that the community is strong and willing to help people, that's why I use ubuntu. My gripe doesn't have anything to do with free software or the community.

I simply can't understand why this problem can't be fixed by making changes in the repository!  Flash seemed to be be fine until sometime in December, then this problem started and has been causing a lot of really unnecessary grief. Why can't the change that caused this problem be "rolled back"? Am I to believe that when one installs the non-free-flash from apt-get, it just blindly downloads the latest version from adobe?

---

### Post by dustytrails on 2008-01-04
1

---

### Post by Kilz on 2008-01-04
> **helix_r said:**
> Peace, 

I think its great that the community is strong and willing to help people, that's why I use ubuntu. My gripe doesn't have anything to do with free software or the community.

I simply can't understand why this problem can't be fixed by making changes in the repository!  Flash seemed to be be fine until sometime in December, then this problem started and has been causing a lot of really unnecessary grief. Why can't the change that caused this problem be "rolled back"? Am I to believe that when one installs the non-free-flash from apt-get, it just blindly downloads the latest version from adobe?

Well, actually thats how it is. Adobe only has the latest version for Linux available (to my knowledge). I just had the previous version still on my hard drive. Because I keep a few things just in case, I have seen way to many upgrades break things and the original version that worked disappear.
Could the developers maybe go backwards? Well possibly, but I have rarely seen it happen.

---

