---
title: "[SOLVED] having problems with opera + flash (no firefox installed)"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by bluepowder7 on 2008-06-22
as per subject, i have opera 9.50, and i do NOT have firefox (either 32 or 64).  flash does not work.  at all.  anymore.  when i get to a page that has flash (like youtube or forums with embedded youtube vids), it temporarily freezes and when it thaws, any sort of flash content is a white box with no right-click menu on it.  actually, on the youtube page, the entire page is a single giant static image - the links to other vids don't work, scrolling of the main page doesn't work, scrolling the "related videos" doesn't even work.  it behaves as if the entire page is one giant JPEG image of the page.

i removed firefox not long ago, and i know that opera+flash still worked after that, but as of a week ago or so, it flat out does not (maybe some automatic updates borked it???).  i tried to use Kilz's script to re-install and set up the base stuff, and that had no effect (other than tell me two things - one to run "sudo apt-get autoremove" to removed three things (one of which was and always is mencoder which i NEED and then have to reinstall - pain in the butt!!!), and two that there's things i don't have like X11 Type 1 fonts folders and some stuff about java and libc6, both of which i DO have)

so, um, what happened?  how do i fix stuff?  it's getting to be such a PITA that i'm seriously contemplating reinstalling the whole bleedin' OS and having to redo ALL my setup.  all over again.  not looking forward to it, but maybe it's the only sure-fire way to clean up whatever i have too much of and not enough of.

do i actually NEED to have firefox installed again to get opera to use flash???  i don't like 'fox and i hope that i'm not up against the infamous "IE is rigidly engrained in Windows" scenario, where one cannot hope to function without the other.

help....  :confused: :confused:

---

### Post by soxs on 2008-06-22
get the latest flashplayer beta 10.
get nspluginwrapper via
```
sudo apt-get install nspluginwrapper
```
Extract the .so library to /x/y/z (any accessable directory).
```
cp /x/y/z/libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so.
```

or /usr/lib/flashplugin-nonfree/ instead of /usr/lib/mozilla/plugins/

nspluginwrapper -l will show you all plugins you've installed via nspluginwrapper

to remove ```
sudo nspluginwrapper -r /usr/lib/.../lib...so
```

---

### Post by bluepowder7 on 2008-06-22
ok, after step 2 (install nspluginwrapper), or rather DURING it, i get this:

```

The following packages have unmet dependencies:
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
                   Depends: lib32gcc1 (>= 1:4.2.1) but it is not going to be installed
                   Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed


```

what makes this all the more odd is that if for example i try to install libc6-i386 (version 2.6.1), it will not let me.  it says that there's unresolved dependencies, and 

```

libc6-i386:
  Depends: libc6 (=2.6.1-1ubuntu10) but 2.8~20080505-0ubuntu5 is to be installed

```

now, if i have libc6 installed with version 2.8, then why does it complain about needing 2.6.1 (a lower version)???  do i have to dumb things down to the lower version before it'll co-operate?  i was under the impression that having a higher version covers the needs of previous versions too.

if i have to roll stuff back to a lower version, that'll result in quite a lot of removals and re-installs.  is that what actually needs to be done?

---

### Post by pixel :-) on 2008-06-22
i think you should live the flashplayer beta 10 last.

(i never used opera)
try removing the config directory,maybe it got broken.

this is a problem with nspluginwrapper.maybe a zomby prosses is still lurking.hmm,it wasn't you with the system that gets randomly slowed down?
the wrapper is very sensible,it tends to get blocked if it get slowed down. I would say that either this problem is a result of the slowdowns,or is a zomby npviewer.bin prosses causing it.

close opera,try "killall -9 npviewer.bin".Chek if there's a npviewer.bin.

---

### Post by soxs on 2008-06-22
that's really odd
try 
```
sudo apt-get purge ia32-libs; sudo apt-get install ia32-libs; sudo apt-get purge nspluginwrapper; sudo apt-get install nspluginwrapper
```

another thing you could try is:
```
sudo apt-get install flashplugin-nonfree
```
this seems to be dumb but it may work with opera 9.50 final

EDIT: pixel :-)'s ideas sound very possible aswell.

---

### Post by bluepowder7 on 2008-06-22
yeah, that's me with the getting-slower-and-weirder-by-the-day system.  i THINK that maybe some upgrades or highest-version installs i did recently in support of vobcopy and mencoder stuff may have been TOO new, and the rest of the stuff is at too low of a version to cope with it.

i'm letting synaptic run updates to all packages to whatever is newest to hopefully sync things up again (since some of the stuff i grabbed before was version ?.8 from the intrepid repo, i've enabled intrepid as a source - this MIGHT not be the best thing to do, but we'll see).  i'm presuming that it's an OK thing to do since the previous items that i pulled from that repo and manually installed (well, ran the deb package manually at least) worked fine for what they were intended for.  in all, that looks like it'll take around 2 hours, so meanwhile i'll be picking my nose or getting some sun.

hmm, maybe i'll cancel the current upgrades and try the purge and kill commands since they're likely quicker to show results.

back in a jiffy!

---

### Post by bluepowder7 on 2008-06-22
ok, so apparently i don't have nspluginwrapper (though i do remember installing it before, so either i removed it or it got removed through some other process), and there's no npviewer bins anywhere.

---

### Post by bluepowder7 on 2008-06-22
well then, if that didn't get me some interesting results, i dunno what could!

the large "update stuff to newest rev" totally bombed.  part way through, it told me that i need to manually run "dpkg --configure -a", and when i do it aborts (core dump) saying "too many errors, stopping" and repeatedly telling me that "A depends on B, however B is not configured yet", with A and B being any two packages (that error shows up dozens of times, for various packages)

so...  what to do...  trying to reopen synaptic tells me to run "apt-get install -f", and running that tells me to run "dpkg --configure -a", which aborts with too many errors and dumps the core.

---

### Post by pixel :-) on 2008-06-22
from what i understand,you installed beta software,with some beta libraries,and now your system is a mess.

The simplest whay out is to reinstall, and don't reinstall betas.

---

### Post by bluepowder7 on 2008-06-22
> **pixel :-) said:**
> from what i understand,you installed beta software,with some beta libraries,and now your system is a mess.

The simplest whay out is to reinstall, and don't reinstall betas.

sounds like it.  i thought they (the various packages in the intrepid repos) were normal packages - new revs that would satisfy requirements of old revs without sending me into a update loop.

i think my only realistic choices here are a full ground-up install of 7.10, 7.10-64, 8.04, or 8.04-64 - which then brings me to the dilema of 32-bit or 64-bit OS, the latter being the PITA when it comes to flash & i think java.

question - will my system continue to boot up as before up until the point that i install whatever new OS i go with?  or should i fully expect this time to be the last time i'm on it (as borked as it is)?  oh, and if i'm doing an install over top of this (keeping my win2k and winxp), should i bother to back up the /boot directory and the MBR?

---

### Post by Sef on 2008-06-23
> i think my only realistic choices here are a full ground-up install of 7.10, 7.10-64, 8.04, or 8.04-64 - which then brings me to the dilema of 32-bit or 64-bit OS, the latter being the PITA when it comes to flash & i think java.


[Kliz's script]("http://ubuntuforums.org/showthread.php?t=772490") installs flash on 64-bit with no problem.   As for java, use openjdk.  Click on the Java on 64-bit systems for more information.

---

### Post by Colonel Kilkenny on 2008-06-23
Please, dear fellow ubuntuists, stop helping opera users with nspluginwrapper. It isn't a solution, it only makes things worse.
Once again, **Opera does not need nspluginwrapper**. If you use it, Flash won't work with Opera. You're only making things more complicated.

And I'm still wondering why on earth Kilz's thread has a title which is misleading people to think that to be able use Flash with amd64 one has no choice but to follow those instructions. And as if that ain't enough it is also sticky...

On topic:
Opera doesn't need Firefox but you have probably messed up your whole system (/home/ on separate partition is always a good choice).
When having problems with Opera and plugins the first thing to do is to start opera from command line with "opera --debugplugin". "opera --debughelp" is also there to assist.

---

### Post by kuja on 2008-06-23
> **bluepowder7 said:**
> ok, after step 2 (install nspluginwrapper), or rather DURING it, i get this:

```

The following packages have unmet dependencies:
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
                   Depends: lib32gcc1 (>= 1:4.2.1) but it is not going to be installed
                   Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed


```

what makes this all the more odd is that if for example i try to install libc6-i386 (version 2.6.1), it will not let me.  it says that there's unresolved dependencies, and 

```

libc6-i386:
  Depends: libc6 (=2.6.1-1ubuntu10) but 2.8~20080505-0ubuntu5 is to be installed

```

now, if i have libc6 installed with version 2.8, then why does it complain about needing 2.6.1 (a lower version)???  do i have to dumb things down to the lower version before it'll co-operate?  i was under the impression that having a higher version covers the needs of previous versions too.

if i have to roll stuff back to a lower version, that'll result in quite a lot of removals and re-installs.  is that what actually needs to be done?

Assuming you're running Hardy - 

libc6
> blackwaltz@terra:~$ apt-cache policy libc6
libc6:
  Installed: 2.7-10ubuntu3
  Candidate: 2.7-10ubuntu3
  Version table:
 *** 2.7-10ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status


ia32-libs
> blackwaltz@terra:~$ apt-cache policy ia32-libs
ia32-libs:
  Installed: 2.2ubuntu11
  Candidate: 2.2ubuntu11
  Version table:
 *** 2.2ubuntu11 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
        100 /var/lib/dpkg/status
     2.2ubuntu10 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages


lib32gcc1
> blackwaltz@terra:~$ apt-cache policy lib32gcc1
lib32gcc1:
  Installed: 1:4.2.3-2ubuntu7
  Candidate: 1:4.2.3-2ubuntu7
  Version table:
 *** 1:4.2.3-2ubuntu7 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status

libc6-i386
> blackwaltz@terra:~$ apt-cache policy libc6-i386
libc6-i386:
  Installed: 2.7-10ubuntu3
  Candidate: 2.7-10ubuntu3
  Version table:
 *** 2.7-10ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status


Those ~should~ be the correct versions of these for hardy. If you have lower versions then this then it may have been resultant of a borked upgrade. 

As for me, with the x86_64 opera 9.5(final) package. It magically just worked. I had installed flash with the multiverse repositories "flashplugin-nonfree" package. Didn't require any extra work ....

---

### Post by soxs on 2008-06-23
> **Colonel Kilkenny said:**
> Please, dear fellow ubuntuists, stop helping opera users with nspluginwrapper. It isn't a solution, it only makes things worse.
Once again, **Opera does not need nspluginwrapper**. If you use it, Flash won't work with Opera. You're only making things more complicated.

And I'm still wondering why on earth Kilz's thread has a title which is misleading people to think that to be able use Flash with amd64 one has no choice but to follow those instructions. And as if that ain't enough it is also sticky...

On topic:
Opera doesn't need Firefox but you have probably messed up your whole system (/home/ on separate partition is always a good choice).
When having problems with Opera and plugins the first thing to do is to start opera from command line with "opera --debugplugin". "opera --debughelp" is also there to assist.

In case he uses the 64bit version of ubuntu, nspluginwrapper is required, and this was implied within the first sentence of post #1

Note: Intepid is ALPHA (you should consider ALPHA== 100% EVIL)
If you require some updatet packages, comple them yourself. DO NEVER ADD ALPHA REPOS TO YOUR CURRENT SYSTEM!

---

### Post by markbuntu on 2008-06-23
I have firefox3.0 and Opera 9.50 on my amd64 and they both work fine with flash 10b and nspluginwrapper installed. If Opera is not using the wrapper then it is smart enough to ignore it when it searches for flash.

btw, Opera 9.50 works a lot better with flash 10 and so does firefox, but Opera is faster. 

You can just download the tar.gz from Adobe and unpack it and replace etc/lib/flashplugin-nonfree/libflashplugin.so with the new one you just unpacked. Do not run the installer, it will try to put it in the wrong place. Also, if you do this, future updates to flash will work, like when 10b becomes 10rc.

---

### Post by bluepowder7 on 2008-06-23
and i'm back.

i gave up on trying to fix the wonderful intrepid alpha mess i created, and took the opportunity to:

install 8.04-64 (i was running 7.10-64 up until today)
use Xfce instead of GNOME (so, xubuntu)
use aptitude in the terminal for EVERY program installation

ok, so i now have opera 9.50, and i guess firefox is on here too.  i'll leave 'fox alone, let it sit, no harm in that.  i'm using opera 99.999% of the time anyways.

so, i haven't yet pointed opera at a youtube page, but i have come across pages where it detects that i need a flash plugin and asks me if i'd like to install (to which i just say no / cancel).  i guess i'd rather find out what is the BESTEST and RIGHTESTEST way of introducing opera to flash & java and getting them to live happily together including updates.

EDIT / UPDATE:
so as far as flash, i ran the short little 3-line instruction from Kilz, and that seems to work in firefox.  i have a feeling that FF will get used for that 0.001% of web browser duty.  i suppose i could point the opera flash plugin folder to wherever FF has it, but part of me wants to disable flash plugins on opera altogether - just keep it cleaner and presumably speed up typical page loading.

---

### Post by bluepowder7 on 2008-06-23
oh, by the way - if i EVER see a package that has this type of version format:

```

2.8~20080505

```

... with the date-code at the end, i should assume it's a alpha / beta build and should stay the hell away from it, right?  i JUST clued in to this now...  those are "daily build" or "weekly build" ID's, eh?  damn.

---

### Post by soxs on 2008-06-25
> **bluepowder7 said:**
> and i'm back.

i gave up on trying to fix the wonderful intrepid alpha mess i created, and took the opportunity to:

install 8.04-64 (i was running 7.10-64 up until today)
use Xfce instead of GNOME (so, xubuntu)
use aptitude in the terminal for EVERY program installation

ok, so i now have opera 9.50, and i guess firefox is on here too.  i'll leave 'fox alone, let it sit, no harm in that.  i'm using opera 99.999% of the time anyways.

so, i haven't yet pointed opera at a youtube page, but i have come across pages where it detects that i need a flash plugin and asks me if i'd like to install (to which i just say no / cancel).  i guess i'd rather find out what is the BESTEST and RIGHTESTEST way of introducing opera to flash & java and getting them to live happily together including updates.

EDIT / UPDATE:
so as far as flash, i ran the short little 3-line instruction from Kilz, and that seems to work in firefox.  i have a feeling that FF will get used for that 0.001% of web browser duty.  i suppose i could point the opera flash plugin folder to wherever FF has it, but part of me wants to disable flash plugins on opera altogether - just keep it cleaner and presumably speed up typical page loading.

That's because flash player 10 is alpha and some pages only search for flashplayer 9.xxx. But you can install flashplugin-nonfree in parallel to 10b (as long as you did that nspluginwrapper stuff not within /usr/lib/flashplugin-nonfree/..)

---

### Post by soxs on 2008-06-26
> **bluepowder7 said:**
> oh, by the way - if i EVER see a package that has this type of version format:

```

2.8~20080505

```

... with the date-code at the end, i should assume it's a alpha / beta build and should stay the hell away from it, right?  i JUST clued in to this now...  those are "daily build" or "weekly build" ID's, eh?  damn.

this is a SVN/git version and not 100% stable,.. but it's by far better than alpha software/OS as you can simply remove that proggy with apt

---

