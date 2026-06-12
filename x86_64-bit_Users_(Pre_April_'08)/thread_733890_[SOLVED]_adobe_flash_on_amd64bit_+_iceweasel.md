---
title: "[SOLVED] adobe flash on amd64bit + iceweasel"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by keratos on 2008-03-24
Trying to get flash running in iceweasel under amd64bit using netscape plugin wrapper for 32bit plugins.

```

# apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 394 not upgraded.
Need to get 124kB of archives.
After this operation, 508kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ftp.uk.debian.org unstable/contrib nspluginwrapper 0.9.91.5-2 [110kB]
Get: 2 http://ftp.uk.debian.org unstable/contrib flashplugin-nonfree 1:1.4 [13.7kB]
Fetched 124kB in 0s (140kB/s)
Selecting previously deselected package nspluginwrapper.
(Reading database ... 62882 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-2_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_1%3a1.4_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-2) ...
Setting up flashplugin-nonfree (1.4) ...
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
Adobe Flash Player installed.

```

I have set the repos to point to unstable and then performed apt-get update.

Also downloaded various tarballs with libflashplayer.so in and tried nspluginwrapper -i libflashplayer.so but I get the same error:
```

*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so

```

i'm not overly bothered about the GPL issue in firefox , iceweasel was just installed as default.

any ideas good folk?

---

### Post by keratos on 2008-03-24
okay, found this...
```

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

```

looks like linux32 wasnt installed.

and now i dont get the errors when doing nspluginwrapper -i ./libflashplayer.so

(libflashplayer.so) coming from a tarball from adobe site.

but...still no flash ?

---

### Post by jhnphm on 2008-03-24
Um, it'd help if you specified that you were using Debian, since on Ubuntu installing flashplugin-nonfree would fix it by automatically generating the wrappers- why are you posting here if you're not using Ubuntu anyway?

To fix the problem, you have to run nspluginwrapper -i [absolute path to libflashplayer.so], and it should dump the wrapper plugin in your home directory (I think)- check if the wrapper plugin is in ~/.mozilla/plugins , and that you have permissions for ~/.mozilla/plugins

---

### Post by JAPrufrock on 2008-03-25
Have you ever checked out Debian's forums?  Fewer online members and help is quite often lacking or very slow in coming.  Might as well try getting help from Ubuntu members!

---

### Post by keratos on 2008-03-26
> **jhnphm said:**
> Um, it'd help if you specified that you were using Debian, since on Ubuntu installing flashplugin-nonfree would fix it by automatically generating the wrappers- why are you posting here if you're not using Ubuntu anyway?

To fix the problem, you have to run nspluginwrapper -i [absolute path to libflashplayer.so], and it should dump the wrapper plugin in your home directory (I think)- check if the wrapper plugin is in ~/.mozilla/plugins , and that you have permissions for ~/.mozilla/plugins

LoL

1. Does my avatar AND my signature not indicate Debian. You write very good English, do you read it as superbly? mmmm !
2. If you know linux, then you'll of heard of Debian. If you use Ubuntu then your based on Debian. These forums are suitable for Debian as they are for Ubuntu however, there are some "features" of ubuntu that are not available in Debian and thus I have to "translate" some posts, but usually, clever people spot that and offer the advice tailored to Debian or I can tailor it myself - either because I can !

You suggestion was ineffective. I did try this, and much more, manually and couldnt get it working, thats why I turned to packages in the hope that they would perform suitable reconfiguration perhaps.

No matter, I gave up after identifiying posts on Debian.org and mailing lists that its a bit of hit and miss on x64.

Therefore I installed i686 Debian on my AMD64 and not only does flash now work, but the system is far far more responsive ;-)

thanks anyway.

---

### Post by keratos on 2008-03-26
> **JAPrufrock said:**
> Have you ever checked out Debian's forums?  Fewer online members and help is quite often lacking or very slow in coming.  Might as well try getting help from Ubuntu members!

DITTO that one buddy.

(shhhh...I dont think he knows we all sneaked over here and are all helping with contributions to Ubuntu and vice-versa) shhhh :lolflag:

---

### Post by samwyse on 2008-03-27
Debian posts go to [http://ubuntuforums.org/forumdisplay.php?f=161](http://ubuntuforums.org/forumdisplay.php?f=161).

---

### Post by keratos on 2008-03-27
> **samwyse said:**
> Debian posts go to [http://ubuntuforums.org/forumdisplay.php?f=161](http://ubuntuforums.org/forumdisplay.php?f=161).

Oh , like I really didnt know that .

"Through history we learn that our similarities bind us together, and not our differences"

I'll let you think about that.

Closing thread.

---

### Post by jhnphm on 2008-03-27
Why were you using 64 bit in the first place w/ only 512MB of RAM ? The only reason to do so is if you do media encoding or something that could take advantage of the extra registers, or need the address space to use all your RAM.

Someone correct me if I'm wrong, but isn't software more bloated due to the increased pointer size on 64-bit? W/ only 512 MB of RAM, that would negatively impact performance wouldn't it? More than half the people using 64 bit on this forum probably don't even use their systems  in a manner where they'd derive performance boosts from 64-bit, and in fact probably suffer perfomance hits. 

Also, I gave up using nspluginwrapper awhile ago, too flaky.

And yes, I can't read :)

---

### Post by Tomatz on 2008-03-27
I found the easiest way to get all plugins working was to create a symlink to the firefox plugins folder :)

Simple and effective.

---

### Post by Tomatz on 2008-03-27
> **keratos said:**
> DITTO that one buddy.

(shhhh...I dont think he knows we all sneaked over here and are all helping with contributions to Ubuntu and vice-versa) shhhh :lolflag:

You think debian is bad try mandriva :(

---

### Post by jhnphm on 2008-03-27
Uh, you can't just symlink 32 bit plugins into a 64 bit firefox.

---

### Post by samwyse on 2008-03-27
> **keratos said:**
> I'll let you think about that.
It's confusing enough working with 64bit Ubuntu in it self. Don't add the problems of another distro in the mix. There's a Debian forum for a reason. I'll let you think about that.

---

### Post by Tomatz on 2008-03-27
> **jhnphm said:**
> Uh, you can't just symlink 32 bit plugins into a 64 bit firefox.

Duh sorry didn't read post correctly :oops:

---

### Post by keratos on 2008-03-27
> **jhnphm said:**
> ...Someone correct me if I'm wrong, but isn't software more bloated due to the increased pointer size on 64-bit? W/ only 512 MB of RAM, that would negatively impact performance wouldn't it? More than half the people using 64 bit on this forum probably don't even use their systems  in a manner where they'd derive performance boosts from 64-bit, and in fact probably suffer perfomance hits. ...

Absolutely agree with this. 

My professional capacity as Software Engineer and Systems Tester on the Eurofighter Avionics (Fast Jet) brings me into contact with assembler, C++, C, Ada, OCAM and I absolutely agree that 512MB RAM will be consumed quickly on x64.

Precsiely why I "upgraded" to a K7 kernel to get 32bit AMD optmization, which I can say now runs as a breeze ... AND I have mozilla plugins working.

---

### Post by keratos on 2008-03-27
> **samwyse said:**
> It's confusing enough working with 64bit Ubuntu in it self. Don't add the problems of another distro in the mix. There's a Debian forum for a reason. I'll let you think about that.

Sometimes, ubuntu forums are very very useful and in my personal experience receive a more speedy response in greater numbers. Dont know why, but thats fact for me.

Great thing about the UK is we are a democracy... and within the constraints of law ... I'll do what I want , but thanks for the opinion.

(if I changed the signature and kept hush about debain - you wouldnt have known would you)

---

### Post by samwyse on 2008-03-27
> **keratos said:**
> Great thing about the UK is we are a democracy... and within the constraints of law ... I'll do what I want , but thanks for the opinion.

Well, I worded my reply badly. I didn't mean to have "don't" there.

---

### Post by keratos on 2008-03-27
:lolflag:You english is far superior to my reciprocal Finnish.

---

### Post by daflame on 2008-04-25
I looks like this is turning into a Debian ostracizing to me, but I AM from Ubuntu Hardy 64 and I am having the time of my life trying to get this to work.  The command you gave does this on my system and flashplugin-nonfree doesn't fully install for the same error cause:

eremy@sigma:/usr/lib32$ nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so           nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by Kilz on 2008-04-25
> **daflame said:**
> I looks like this is turning into a Debian ostracizing to me, but I AM from Ubuntu Hardy 64 and I am having the time of my life trying to get this to work.  The command you gave does this on my system and flashplugin-nonfree doesn't fully install for the same error cause:

eremy@sigma:/usr/lib32$ nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so           nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so

While I applaud you on searching for topics on the subject, since it is about a new version a separate post may have been the way to go. [But since you have posted in more than one location]("http://ubuntuforums.org/showpost.php?p=4793192&postcount=11"), you might want to limit the posting to one thread.

---

