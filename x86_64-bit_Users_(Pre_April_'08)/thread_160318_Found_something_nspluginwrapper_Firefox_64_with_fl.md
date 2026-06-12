---
title: "Found something: nspluginwrapper Firefox 64 with flash, java etc and no Chroot!"
date: 2006-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmb on 2006-04-14
Hey, while playing around with some old macintosh emulators, I came across a developers website who is developing a program/plugin that lets your run 32 bit plugins on a 64 bit compiled firefox. This is looking quite interestg.

Anyone want to say if this works or not? 

Its called nspluginwrapper, and homepage for it is here: [http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper](http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper)

---

### Post by CDN MILLWRIGHT32 on 2006-04-15
Dead link!

---

### Post by mikeyrb on 2006-04-15
[http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper]("http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper")

I tried getting it to work, but I had no luck.  As far as I could tell, I had no executable called "nspluginwrapper."  I used Alien to convert the rpm's to debs.  Whatever the source file is for, it wouldn't "make install."

---

### Post by mikeyrb on 2006-04-16
It actually works now, for some plugins!  Before I was only trying to get the rhapsody plugin to work, but this time I tried the flash plugin, which worked.

Instructions to install:

1) Download the Plugin and the Viewer from [http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper]("http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper")
2) Install Alien, if not already installed.
3) Convert the downloaded rpm's to deb's (sudo alien -d *.rpm)
4) Install the newly created debs (Install in this order: sudo dpkg -i nspluginwrapper-i386_0.9.90-2_amd64.deb, sudo dpkg -i nspluginwrapper_0.9.90-2_amd64.deb) -- If I got the order wrong, you'll know because it won't install.
5) Download the plugin you want to install, and extract the .so file.  For example, to install flash, grab the tar.gz file from Macromedia's website, and extract libflashplayer.so.
6) Move the plugin (example, libflashplayer.so) to /usr/lib/mozilla/plugins.  This is where nspluginwrapper stores the main plugin, so it's probably a nice folder to keep them.
7) Now we need nsplugwrapper to make the new plugin, so call: /usr/lib/nspluginwrapper/x86_64/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so (if wanting the flash plugin, of course).  Depending on whether or not you run that command with sudo, it will either end up in /usr/lib/mozilla/plugins, or ~/.mozilla/plugins.  If you ran it as sudo, you'll need to link it to either your profile's plugins or the main plugins (/usr/lib/mozilla-firefox/plugins).  Or copy, doesn't matter.  The old plugin must not move, as it's path seems to become hard coded in the new plugin created (which has "npwrapper-" prepended to the old name).

I had one issue where the npviewer.bin executable did not quit with firefox, so firefox couldn't load my profile again until I killed npviewer, but I'm not sure how I caused that.  It happened another time, but I didn't see npviewer as active, so I had to logout.  Macromedia flash worked, but the menu text didn't exactly show up for Google Videos, or the flash settings, though the main flash menu worked.

Oh, and if anyone gets the rhapsody plugin working for x64, let me know!

---

### Post by mikeyrb on 2006-04-16
I was able to fix fonts with the help of this page: [FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")

apt-get install gsfonts
apt-get install gsfonts-x11

Also, I discovered it's probably better to not include "-c" with alien, as it then doesn't complete install and keeps coming up during use of synaptic.  That change has been updated above.

---

### Post by Rkey on 2006-05-25
Sorry, my message is not relevant anymore...

---

### Post by ravpaul on 2006-05-28
Nothing short of genius!!! No need to go to 32bit applications again!!!

---

### Post by lnxconvrt on 2006-05-29
Excellent!

Nice how-to, mikeyrb.  Thanks!

---

### Post by jairo.serrano on 2006-06-12
[QUOTE=mikeyrb]It actually works now, for some plugins!  Before I was only trying to get the rhapsody plugin to work, but this time I tried the flash plugin, which worked.[/QUOTE]

WOW men!

flash work on my native firefox!!! 

WOW! =D> =D> \\:D/ \\:D/

[-o< y prey to have 100% stability... ;) ;)

---

### Post by superm1 on 2006-06-15
I used to have this working, and tried to reinstall using the version from 6/11/06.  It seems to have stopped actually working right however, and doesn't even show the plugins in about:plugins.

---

### Post by superm1 on 2006-06-15
solved my own problem

```
sudo apt-get install linux32
```

---

### Post by cneil on 2006-06-22
I tried this method and it didn't seem to work.  
I don't even think that firefox or mozilla realizes that I have installed this plugin.  Am I missing a step.  How do I make sure that this plugin is working in my profile.

---

### Post by superm1 on 2006-06-22
Have you run

```
/usr/lib/nspluginwrapper/x86_64/npconfig -v -a -i
```

As the user you want the plugins enabled for yet?

---

### Post by squid on 2006-06-23
Well i want to know if this thing really works.
when i make alien system ask me to include the --scripts switch. so i made it and i got the debs. but when i install the second package look this error:

----------------------
xtreme@xtreme-desktop:~/Desktop$ sudo dpkg -i nspluginwrapper_0.9.90.1-2_amd64.deb
(Reading database ... 72317 files and directories currently installed.)
Preparing to replace nspluginwrapper 0.9.90.1-2 (using nspluginwrapper_0.9.90.1-2_amd64.deb) ...
Unpacking replacement nspluginwrapper ...
Setting up nspluginwrapper (0.9.90.1-2) ...
/var/lib/dpkg/info/nspluginwrapper.postinst: line 6: /usr/bin/nspluginwrapper: No such file or directory
dpkg: error processing nspluginwrapper (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 nspluginwrapper
----------------------------

Can anyone help me out with this? Thanks a lot.

---

### Post by squid on 2006-06-23
GOD....

take look at this

root@xtreme-desktop:/home/xtreme/Desktop# apt-cache search nspluginwrapper
nspluginwrapper-i386 - A viewer for i386 compiled Netscape 4 plugins
nspluginwrapper - A compatibility layer for Netscape 4 plugins

hey guys those packages are already on the repos... :)
i suppose that those are on the repos are for 32bit or 64bit ?

i am confused :( any idea for my post above ?

---

### Post by superm1 on 2006-06-23
[QUOTE=squid]Well i want to know if this thing really works.
when i make alien system ask me to include the --scripts switch. so i made it and i got the debs. but when i install the second package look this error:

----------------------
xtreme@xtreme-desktop:~/Desktop$ sudo dpkg -i nspluginwrapper_0.9.90.1-2_amd64.deb
(Reading database ... 72317 files and directories currently installed.)
Preparing to replace nspluginwrapper 0.9.90.1-2 (using nspluginwrapper_0.9.90.1-2_amd64.deb) ...
Unpacking replacement nspluginwrapper ...
Setting up nspluginwrapper (0.9.90.1-2) ...
/var/lib/dpkg/info/nspluginwrapper.postinst: line 6: /usr/bin/nspluginwrapper: No such file or directory
dpkg: error processing nspluginwrapper (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 nspluginwrapper
----------------------------

Can anyone help me out with this? Thanks a lot.[/QUOTE]

I did it without the --scripts switch.  I think that those postinstall scripts are broken since there is a symlink not made.  If you want to use the packages with the post install scripts, you will need to make a symlink 
```
/usr/bin/nspluginwrapper to /usr/lib/nspluginwrapper/x86_64/npconfig
```

---

### Post by superm1 on 2006-06-23
[QUOTE=squid]GOD....

take look at this

root@xtreme-desktop:/home/xtreme/Desktop# apt-cache search nspluginwrapper
nspluginwrapper-i386 - A viewer for i386 compiled Netscape 4 plugins
nspluginwrapper - A compatibility layer for Netscape 4 plugins

hey guys those packages are already on the repos... :)
i suppose that those are on the repos are for 32bit or 64bit ?

i am confused :( any idea for my post above ?[/QUOTE]

In short, this is because you were installing from a deb.  This will enter it into the local apt database as a package that it has seen.  These packages aren't in the repos.  Ifyou try to install them without having the deb handy, it might tell you that another package refers to this package, but no repository holds it.

---

### Post by squid on 2006-06-24
[QUOTE=superm1]In short, this is because you were installing from a deb.  This will enter it into the local apt database as a package that it has seen.  These packages aren't in the repos.  Ifyou try to install them without having the deb handy, it might tell you that another package refers to this package, but no repository holds it.[/QUOTE]

Well thanks mate for your info. I make a clean install of ubuntu and i install everything that this guide says.

Still GOT NO FLASH :evil: 
I think i am gonna switch this box to windows again... its useless trying 3 days to make my box play flash and java. :(

Any ideas? Or can you be more specific on the installation steps? Thanks for your time.

---

### Post by vwj on 2006-06-24
hey,

i have done a fresh install to and it woudn't work
even after installing linux32.

I had experienced trouble with firefox before.
So I closed firefox and chekd with ps if any other
instance was running and yes it was, so I killed it
and the problem was solved.

---

### Post by superm1 on 2006-06-24
[quote=squid]Well thanks mate for your info. I make a clean install of ubuntu and i install everything that this guide says.

Still GOT NO FLASH :evil: 
I think i am gonna switch this box to windows again... its useless trying 3 days to make my box play flash and java. :(

Any ideas? Or can you be more specific on the installation steps? Thanks for your time.[/quote] 
Well lets see here, a pretty basic guide is:
1) Convert to deb's using alien
2) sudo apt-get install linux32
3) Put the plugins you desire to use in ~/.mozilla/plugins or your global plugins path
4) npconfig -v -a -i (As a user)
5) Verify that they are there under ~/.mozilla/plugins
6) Close all FF instances and anything like npviewer.bin that is running
7) Start FF and go to about:plugins
See if they are listed there.  If so, your golden.

I'm not on my box right now, so I don't have exact commands.  But thta should be the process

---

### Post by bluppfisk on 2006-07-11
piss.
yesterday, all worked like a charm. today, not a single flash movie is visible.

firefox says plugin is installed though:
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

any ideas what might've happened? All I did was reboot and praps installed EasyUbuntu.

---

### Post by bluppfisk on 2006-07-11
I guess I found the problem. If your flash player with nspluginwrapper worked in firefox before, but suddenly stops working, try the following (it worked for me):

1- exit any firefox browser window
2- sudo gedit ~/.mozilla/firefox/pluginreg.dat
3- find occurrences of the flash player plugin
4- delete anything that's redundant (I had three instances), and definitely remove those that refer to another plugin than nspluginwrapper.libflashplayer.so (the first time, one of those instances referred to libflashplayer.so ; the second time* both instances were correct but just redundant).
5- save the file, start firefox and if that was the problem, it should work now


[*] I don't know why, but it appears that this happens on every reboot. Firefox seems to be creating those redundant instances automatically for me. Perhaps it's because I have this nspluginwrapper.libflashplayer.so on different locations, I still have to find out.

update: yessir. the nswrapper.libflashplayer.so plugin should only exist in one location (for me this is now ~/.mozilla/plugins/) - now firefox does no longer create extra entries in pluginreg.dat for the different instances of the plugin. Unlike what was suggested in the tutorial on page 1, copying the plugin is not a good idea, symbolic linking might do the trick but I cba to figure that out. Besides, it's easier to have the plugin in only one location.

---

### Post by shadwstalkr on 2006-08-03
Has anyone figured out how to make Java work with this?  I got the 32-bit Java plugin from Sun, but npconfig exits with an error saying that it's not a NS4 plugin.

---

### Post by gokhanmansur on 2006-08-21
Hi,

When I tried to install flash i got this error message :
-> /usr/lib/nspluginwrapper/x86_64/npconfig -i usr/lib/mozilla/plugins/libflashplayer.so
-> nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NS4 plugin for i386

What can I do ?

Thanks...

---

### Post by FedeXX on 2006-09-28
Not working... I followed the guide step by step, firefox seems to recognize tha plugin, but when i load a page with flash contents (this is the plugin i want), it freezes while loading it, and must be terminated...

Linux32 must be only installed or there's something to do with it?

---

### Post by a-musing amazon on 2006-09-30
The security upgrade to Firefox 1.5.0.7 has broken nspluginwrapper 0.9.90.1 - the version publically available :(. 

There has been a recent upgrade to 0.9.90.3, released on 19-Aug-06, that is supposed to fix this, however it is currently only available as a Mandrake src deb and a i586 binary deb, not on the nspluginwrapper website as of now.

Unfortunately the src package need to be compiled on a 32-bit distro or in a chroot. I've had a look at what's involved and it seems to need a complete development library set for of X, Gtk, cairo, pango etc. Which, for me, seems a heavy download and learning curve for such a small app (I do do compilations but so far only 64-bit ones).

I've tried to convert the i586 .rpm to a .deb using alien but it seems not to be picking up my i386 shared libraries properly (because its i586?) even though the named libs are there, so I suspect that a hand-install wouldn't work either.

I'm aware that you can avoid this hassle by using a 32-bit Firefox but I run Epiphany and Liferea on top of Firefox, and my other 32-but 'wrapped' nsplugins work OK, so don't really want to go that route.

Anyone up for getting nspluginwrapper working on Dapper?

---

### Post by kingcharles1666 on 2006-10-03
I had the same problem and decided to go for 32bit browsing.
used the scripts from kilz and they work fine. suggest you give it a go
[http://ubuntuforums.org/showthread.php?t=202537&highlight=flash+amd64](http://ubuntuforums.org/showthread.php?t=202537&highlight=flash+amd64)

---

### Post by Paulo Wageck on 2006-10-06
avatar@avatar-desktop:~/Desktop$ sudo alien -d *.rpm
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
nspluginwrapper_0.9.90.1-2_amd64.deb generated
sh: Syntax error: "(" unexpected
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} nspluginwrapper-i386-0.9.90.1-1.x86_64(2).rpm":  at /usr/share/perl5/Alien/Package.pm line 466, <GETPERMS> line 12.


what can it be?](*,)

---

### Post by a-musing amazon on 2006-10-06
> **Paulo Wageck said:**
> avatar@avatar-desktop:~/Desktop$ sudo alien -d *.rpm
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
nspluginwrapper_0.9.90.1-2_amd64.deb generated
sh: Syntax error: "(" unexpected
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} nspluginwrapper-i386-0.9.90.1-1.x86_64(2).rpm":  at /usr/share/perl5/Alien/Package.pm line 466, <GETPERMS> line 12.


what can it be?](*,)

Not sure about your precise error but the version of nspluginwrapper you are trying to install no longer works since the release of Firefox 1.5.0.7

To get it working you now need the newer nspluginwrapper 0.9.90.3 rpms which can be found at:

[http://mirror.linux.org.mt/mirror/ma...7.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/ma...7.0.x86_64.rpm)
[http://mirror.linux.org.mt/mirror/ma...7.0.x86_64.rpm](http://mirror.linux.org.mt/mirror/ma...7.0.x86_64.rpm)

There has been some discussion of this in the thread:
[http://ubuntuforums.org/showthread.php?t=269170&goto=newpost](http://ubuntuforums.org/showthread.php?t=269170&goto=newpost)

This version allowed me, at least, to get flash 7 working again in 64-bit Firefox.

---

### Post by lotacus on 2007-01-16
hey. this nspluginwrapper doesn't work for me whatsoever. when I run npconfig I get a return saying "command not found". when I browse to where npconfig is, I can see that it DOES indeed exist. I get the same error even when I give it execute permissions.

I then tried it on that guys website that develops it. His options said to use nspluginwrapper command. So I tried that and it told me that permission was denied. So I ran it under sudo and it returned "command not found". 

this flash is really pissin me off. I wish devs would either drop 32bit all together or drop 64bit all together, because it just seems they don't know where priority lies or they just don't have the resources to work with both platforms. The same can be said with Microsoft, so I'm not just attacking linux. If there was more focus on 64bit, then other companies which produce drivers, will have no choice but to follow suit.

---

### Post by schreddi on 2007-01-17
With flash 9, every thing works fine)

---

### Post by superm1 on 2007-01-17
> **schreddi said:**
> With flash 9, every thing works fine)
How extensively have you been testing flash9?  Is it working out much more stable than 7 was (where it would take the browser down with it when things went south)

---

### Post by kingcharles1666 on 2007-01-22
@ lotacus

Move or copy the plugin (libflashplayer.so) to: /usr/lib/mozilla/plugins

then:

sudo /usr/lib/nspluginwrapper/x86_64/linux/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so

works for me every time a new version of flash / or the pluginwrapper is released.

give it another go
cheers,

Charles

---

### Post by MikeeAMD64 on 2007-01-23
Hi everyone, I have recently re-installed Ubuntu, and I am now having problems installing Flash.

I have tried everything, but I am receiving this error:

```
sudo /usr/lib/nspluginwrapper/x86_64/linux/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
Cannot execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

```

I never had this problem before.

EDIT:  I figured it out.  You need to do:
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
```

---

### Post by josno on 2007-03-09
I've done this, and flash 9 mostly works fine, except buttons: I can click on something in a flash application once, and then can click on no more buttons until I switch tabs and then switch back. Also, it seems to stop working after a while, so I have to restart Firefox. Anyone else have a similar problem? (Using edgy with firefox64 and flash player 9)

---

### Post by boogachamp on 2007-05-31
Anyone one in feisty using this?

---

### Post by EatenByGrues on 2007-05-31
I'm using this plugin in feisty and it works fairly well except for the error mentioned above about the 'clicking'. it would be great if I could get that resolved.

---

