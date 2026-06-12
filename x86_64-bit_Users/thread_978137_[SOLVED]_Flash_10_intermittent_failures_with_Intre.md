---
title: "[SOLVED] Flash 10 intermittent failures with Intrepid 8.10 on AMD64"
date: 2008-11-10
forum: x86 64-bit Users
---

### Post by PilotJLR on 2008-11-10
Hello,
I've recently performed a clean install of Ubuntu 8.10 Intrepid Ibex on an AMD64 platform.
Most everything is working well, EXCEPT for flash.

I have tried using ubuntu-restricted-extras to provide Flash 10... I have also tried uninstalling that and manually installing Flash10 and nspluginwrapper. Same results with both methods.

So here is the issue... Flash works probably 3 out of 4 times. Occasionally, and for no reason I've yet figured out, flash will fail and a gray or white box will be displayed where the flash applet SHOULD be. I've attached 2 example screenshots of this.
When this fault occurs, I can fix it by restarting firefox. I've also tried running firefox from a console, and no errors are being posted there!

I'm out of ideas for the moment... I've seen lots of posts here regaring flash, but most people seem to have all or nothing results. My problem is quite irritating (to me, at least), since Flash works sometimes and fail at other times for no clear reason.

Any suggestions or ideas would be highly appreciated!
Thanks!

---

### Post by tuxxy on 2008-11-10
Are you sure Flash is installed, type this into the address bar you are looking for the Flash plugin to be listed.

```
about:plugins
```

If it was a fresh install of Ibex ubuntu-restricted-extras should install flashplugin-nonfree without any hassle and as its a 32-bit plugin it could be that actually at fault, however it shouldnt crash 25% of the time I personally have had 1 crash with Flash 10 in either Opera or Firefox since Ibex beta. 

```
sudo apt-get install ubuntu-restricted-extras
```

Have you tried an alternative browser such as Opera to check its also having difficulty with Flash content.

---

### Post by PilotJLR on 2008-11-10
Thanks for the quick reply! Flash is definitely installed... it does work 3/4 times. I've attached a screen grab of the version.

At the moment, I am using ubuntu-restricted-extras to provide flash 10, though I did previously also remove that and do a manual install. With a manual install, the exact same problem occurred.

I will try Opera in an attempt to isolate the problem further... I don't intend to use Opera long term, but that's a really good idea for the troubleshooting.
Thanks!

---

### Post by tuxxy on 2008-11-10
No problem, in future if your Flash/Firefox does crash open up system monitor and kill the process named **npviewer.bin** this should ungrey Firefox and allow you to refresh the page rather than restart the browser and also I started out on Opera thinking the same and here I am using it around 80% of the time now :lolflag:

---

### Post by PilotJLR on 2008-11-10
This post is coming from Opera!  :-)

Flash is up and running in Opera... I will report back here either in a couple days... or if flash fails inside opera as well! I'll have to give this a couple days of decent flash use before I can really say for sure if it is working consistently.

More info to follow!

---

### Post by Arup on 2008-11-10
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

Best way to install flash and it works nicely on both Opera and FF. However beware not to install Flash via restricted drivers as that would ruin the whole structure and lead to problems.

---

### Post by PilotJLR on 2008-11-10
Thanks for the reply... I tried that already as well. A couple days ago, I removed ubuntu-restricted-extras and flashplugin-nonfree and used this script. Exact same results as with ubuntu-restricted-extras.

---

### Post by jdong on 2008-11-10
I'm tracking this down too -- npviewer is SIGSEGV'ing in libc.so.6, unable to get a symbolic stacktrace yet. It happens with or without pulseaudio, and even when I am just sitting on one page (i.e. Pandora for an hour)

---

### Post by Kilz on 2008-11-11
> **Arup said:**
> 

Best way to install flash and it works nicely on both Opera and FF. However beware not to install Flash via restricted drivers as that would ruin the whole structure and lead to problems.

The command in that howto downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time. Im not saying this script has been. But it is unsafe and should not be trusted. Users should read and understand all scripts they install, especially from 3rd party sites. This is impossible to do if it downloads and automatically installs.

---

### Post by jdong on 2008-11-12
```

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-pl
ugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_play
er_10_linux.tar.gz
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins
/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/li
b/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/li
b/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"

```

I won't even begin to explain why this script is unsafe and entirely unsupported. I hope looking a few lines into it will answer that.

---

### Post by xebian on 2008-11-12
> **jdong said:**
> I'm tracking this down too -- npviewer is SIGSEGV'ing in libc.so.6, unable to get a symbolic stacktrace yet. It happens with or without pulseaudio, and even when I am just sitting on one page (i.e. Pandora for an hour)

Getting segfault error too

```
npviewer.bin[6148]: segfault at c ip 00000000f6690333 sp 00000000ffe6c340 error 4 in libplds4.so.0d[f668f000+2000]

```

---

### Post by kholis on 2008-11-14
@jdong
thanks it works

---

### Post by Penguin Power on 2008-11-14
Please tell us you didn't run that script...

---

### Post by jdong on 2008-11-14
Can I start crying now?

---

### Post by Arup on 2008-11-14
For those with Opera having problems with blank or grayed out screen, I have found a solution that works. In my system, installing Flahs from the rep worked fine with FF but not with Opera, only way was the through the script way and that is not really preferred. Well the workaround is to install Flash first and then install Opera, somehow this way works out fine.

---

### Post by Yellow Pasque on 2008-11-14
I solved my problems with both Flash 10/Intrepid and Flash 9/Hardy on Firefox/Swiftweasel by going to a Flash app that actually worked, right clicking and selecting "Medium Quality". Now all the Flash apps that used to be grayed out work. (BTW, I don't notice any difference in video/picture quality).

---

### Post by null_pointer_us on 2008-11-14
> **Temüjin said:**
> I solved my problems with both Flash 10/Intrepid and Flash 9/Hardy on Firefox/Swiftweasel by going to a Flash app that actually worked, right clicking and selecting "Medium Quality". Now all the Flash apps that used to be grayed out work. (BTW, I don't notice any difference in video/picture quality).

I don't get this option when right-clicking on Flash videos.

BTW, here are some Flash plugin configuration pages.
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html)

---

### Post by PilotJLR on 2008-11-14
I noticed that some flash videos do have this option... I tried going to medium quality, but the problem still persists.
Thanks for the info, though!

---

### Post by Tycho1214 on 2008-11-14
I'm having the same problem as the original poster with Flash 10 apps... I'm having a far higher failure rate than him though.  The site I've been going to as of late ([www.kongregate.com](www.kongregate.com)) revolves around Flash games and the inability to play them is irksome...

---

### Post by loomsen on 2008-11-14
As far as YouTube is concerned, totem ships with YouTube plugin, as well as BBC.

---

### Post by jdong on 2008-11-14
A 32-bit chroot three days later has yet to crash. I'm thinking the first crash was a fluke. Sheesh this is such an ugly hack, I debootstrapped a 32-bit Ubuntu base system in /root32, then set up schroot with my default user (bind-mounting /home, /tmp, /var/tmp, and /var/run). I don't recommend this ugly workaround but I blame nspluginwrapper at this point.

---

### Post by Yellow Pasque on 2008-11-14
> but I blame nspluginwrapper at this point.
nspluginwrapper shouldn't be necessary for something so common. I blame Adobe for not releasing a native 64-bit version of Flashplayer. This is the least they could do if they're not willing to provide the needed documentation or open-source their binary blob.

---

### Post by jdong on 2008-11-14
Well of course the problem would be solved if we have native 64-bit flash10 or maybe we'll just be given a flash10 that segfaults natively too!

But my blame trail was in the interest of figuring out why flash greys out in its current state -- that's something that I still feel we have control over and can fix. Sitting around and whining that Adobe Flash is a crappy FOSS citizen isn't going to get us anywhere.

---

### Post by Arup on 2008-11-14
> **Temüjin said:**
> nspluginwrapper shouldn't be necessary for something so common. I blame Adobe for not releasing a native 64-bit version of Flashplayer. This is the least they could do if they're not willing to provide the needed documentation or open-source their binary blob.

I fully agree, Adobe is x64 phobic in general, that goes for their apps as well, still resisting going x64 way, Adobe PS and Premiere need x64 more than anything due to their heavy use of RAM and yet, they keep circumventing this issue.

---

### Post by Yellow Pasque on 2008-11-15
> Sitting around and whining that Adobe Flash is a crappy FOSS citizen isn't going to get us anywhere.
In the past, I've sent Adobe a few e-mails suggesting a 64-bit version of Linux Flash Player. I've also started petitions for it in the Adobe forums. Unfortunately, few people seem to share my sentiment strongly enough to send feedback to Adobe. Fixing nspluginwrapper to support the latest version of Flash is a band-aid fix at best. If we just keep doing that, then we'll keep having the same problem. (Do you really want to go through this again when Adobe releases Flash 11, 12, 13, ...?)

---

### Post by ushimitsudoki on 2008-11-15
> **jdong said:**
> ```

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-pl
ugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_play
er_10_linux.tar.gz
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins
/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/li
b/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/li
b/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"

```

I won't even begin to explain why this script is unsafe and entirely unsupported. I hope looking a few lines into it will answer that.

Actually, I'd appreciate it if you'd point out exactly and entirely what is wrong with the script.

---

### Post by jdong on 2008-11-15
(1) Incorrect use of killall -9 to shut down Firefox. This can lead to the Firefox SQLite databases that store bookmarks and history to be irrecoverably damaged, along with other parts of your profile.

(2) Downloads using wget some deb called "getlibs" from nowhere notable. It is also done from a cleartext connection and does not perform signature validation. Basically anything and everything can arrive in that deb and you're handing it root access to your system.

(3) Usage of apt-get remove with -y override does not provide user with opportunity to review APT's decisions. If a dependency tree somehow forced 300 packages to be uninstalled, the user would not be alerted to this situation.

(4) Pointless use of --purge to remove the listed components not only risk flushing out user-modified configuration files associated with those packages, but also with core system packages.

(5) Poor use of rm -f to remove flash plugins from suspected locations. This also touches /usr directly instead of going through dpkg, which is a bad idea on Debian machines.

(6) The removals forget to target /usr/lib/xulrunner-* and /usr/lib/xulrunner-addons, which are the Hardy+ locations for such plugins.

(7) The removals can leave dangling symlinks in /etc/alternatives. No attempt is made to verify if this happens.

(8) Right after removing and purging nspluginwrapper, he installs it again. ???

(9) The use of some third party 'getlibs' script to  download three 32-bit libraries. Good luck trusting your system to that. They are also versioned against specific versions (1d, 0d) that may not be up to date.

(10) Flashplayer is downloaded to the user's home directory and removed by rm -rf executed within the home directory. Assumes nothing by the existing name already exists.

(11) Direct placement of libflashplayer.so into /usr/lib, subverting dpkg.

(12) The installation of 32-bit .so into 64-bit /usr/lib. You're lucky Firefox ignores that instead of crashing and burning.

(13) Then, symlinking these plugins into various /usr/lib locations again.

(14) The end effect is not only a dangerous script using unsupported methods to affect your system, but also it leaves stuff scattered around with no undo instructions. Good luck reading through the script to figure out how to remove what it did later on.

(15) If you later install flashplugin-nonfree, you will end up with two installations of the flash plugin. Which one is used? When will you figure out this happens?

---

### Post by Arup on 2008-11-15
I have had absolutely no problems flash on FF by installing it via the repos, the problem came with Opera but its solved easily by installing flash first and then installing Opera, same with Java, for Opera, I reccomend Sun Java as its picked up by Opera easily.Thanks for the detailed explanation jdong, that script is indeed a bad idea.

---

### Post by Yellow Pasque on 2008-11-15
> (9) The use of some third party 'getlibs' script to download three 32-bit libraries. Good luck trusting your system to that.
getlibs is a very useful script made by an Ubuntu Forums member (Cappy) to help 64-bit users install 32-bit libraries correctly. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by jdong on 2008-11-15
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)

The safety of that script isn't too great either.

---

### Post by ushimitsudoki on 2008-11-15
Thank you for the details. I'll point to it from my blog.

---

### Post by Kilz on 2008-11-15
> **jdong said:**
> [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs)

The safety of that script isn't too great either.

Maybe, but I think it, or a modified version, should be included by default on all 64bit installs. It installs 32bit libraries from the repositories into the correct locations on 64bit systems.

---

### Post by Yellow Pasque on 2008-11-15
Definitely. The getlibs scripts addresses a critical need for 64-bit users (i.e. the need to run 32-bit programs without resorting to a chroot).

---

### Post by jdong on 2008-11-15
It would be nice for dpkg to gain that ability without the need to use external scripts to cut out the libraries desired.

---

### Post by Kilz on 2008-11-15
> **jdong said:**
> It would be nice for dpkg to gain that ability without the need to use external scripts to cut out the libraries desired.

Over a year ago I found out that holding your breath waiting for that could make you turn blue. It truly would be awesome, but getlibs is a great script that fills a need right now. It should be a default 64bit package.

---

### Post by jdong on 2008-11-15
> **Kilz said:**
> Over a year ago I found out that holding your breath waiting for that could make you turn blue. It truly would be awesome, but getlibs is a great script that fills a need right now. It should be a default 64bit package.

Well it's a shame people decide to use their time writing unsupported and unmaintainable scripts to kind of get the job done rather than invest their efforts towards something that is a properly done solution. I didn't say to hold your breath.

---

### Post by kholis on 2008-11-16
@Penguin Power
yes. i just run that script. and it works.

---

### Post by petersaints on 2008-11-16
By default (with flashplugin-nonfree package) on Ubuntu 8.10 RC x86-64 I also had intermittent failures. I mean... most common sites worked without major problems (just a few slowdowns) but there were certains sites, most of them were hi5 profiles, a Social Network very popular here in Porugal, in which certain flash animations that many use get really really slow and evntually crash NSPLUGINWRAPPER... The poor flash support on 64-bit Linux is currently the main reason why I don't use 64-bit... that allied to the fact that I only have 2GB RAM make me stay on 32-bit.

---

### Post by Kilz on 2008-11-16
> **jdong said:**
> Well it's a shame people decide to use their time writing unsupported and unmaintainable scripts to kind of get the job done rather than invest their efforts towards something that is a properly done solution. I didn't say to hold your breath.

No, its open source. Some people may not have the ability to properly code applications. But see a need. When they ask if those that can code to fill that need and are told no, they do what they can.
Prior to Dapper Drakes release I asked the developers mail list a few questions. I asked about multiarch and firefox/flash. The reply from the top is that they are waiting on Debian to do implement multiarch. Debain has not done it so we wait some more. I was told that they maybe could get the wrapper in for flash, but that it would take some time and I was free to do what I wanted because this was "open source" and so I did. It wasn't until Gutsy we has so/so wrapper support, but my 32bit firefox worked just fine with Dapper.
Cappy saw a need and filled it. The need was 32bit applications could be installed without a chroot, but adding the 32bit libraries by hand was a pain. Getlibs filled the need perfectly. It now is easy to make most 32bit applications run (if you really need them). Why shouldn't Ubuntu use what Cappy wrote and fix any minor issues, if not implement something that works the same. I have my guesses why they wont, starting with the amount of eye candy and development added each version to a 32bit os for which hardware is no longer made.

---

### Post by H4rold on 2008-11-17
Adobe released a 64 bit alpha version. No gray box anymore :

[http://ubuntuforums.org/showthread.php?p=6196594#post6196594](http://ubuntuforums.org/showthread.php?p=6196594#post6196594)

---

### Post by PilotJLR on 2008-11-17
I just came here to post that, but you beat me by 15 minutes.  :-)

I'm trying the 64 bit alpha version now.

---

### Post by H4rold on 2008-11-17
> **PilotJLR said:**
> I just came here to post that, but you beat me by 15 minutes.  :-)

I'm trying the 64 bit alpha version now.

Been trying it : youtube / bbc iplayer / Daily show / deezer / a few games.

No gray box :biggrin:

---

### Post by PilotJLR on 2008-11-17
I've only used this 64 bit plugin for a few minutes, but so far everything works perfectly.
I'll have to give it a couple days to make sure it doesn't segfault, but I think this one may be the resolution!

---

### Post by Arup on 2008-11-17
Watched an entire movie on youtube for one and a half hour, no issues. Mind you those using online web based messengers like Meebo Tokem etc. the mic and cam doesn't work with this plugin.

---

### Post by jdong on 2008-11-17
As another aside, I was notified that nspluginwrapper 1.1.4 should fix the grey-box crashes in nspluginwrapper 1.1.2. I'm building some packages to verify this claim.

---

### Post by jdong on 2008-11-17
Another hint I was given by our resident Mozilla guru, disable Windowsless mode in Flash.

Make an /etc/adobe/mmm.cfg file with the contents
```

WindowlessDisable=true

```

---

### Post by seamuso on 2008-11-18
throwing in my $.02 .. ripped out the wrapper + 32 bit flashplayer .. dropped in the 64bit version and everything is great.

---

