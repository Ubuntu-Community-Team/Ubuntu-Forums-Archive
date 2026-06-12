---
title: "Nspluginwrapper 0.9.90.3 Debian Packages"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by russianpirate on 2006-10-13
There are quite a few threads about nspluginwrapper,but none worked for me. So I decided to download the latest (0.9.90.3) version of npw (not from their site from some ftp..) and repackage it to deb for everyone to use.

_If you had problems with previous versions of nsw, this package increases your chance for getting npw to work greatly._

I run Ubuntu Edgy x86_64 2.6.17 w/ Firefox 2.0RC2 and this version of nsw and it works perfectly (at least for flash.. I use blackdown java for the plugin)

**_Download here:_**
[nspluginwrapper-0.9.90.3-deb.tar.gz]("http://rapidshare.de/files/36660964/nspluginwrapper-0.9.90.3-deb.tar.gz.html")

**_Instructions:**_
1.Download the package
2.Untar it into a folder
3.Use *dpkg -i* (nameofdeb.deb) to install **both** of the debs
4.Copy libflashplayer.so to ~/.mozilla/plugins
5.Run *sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper*
6.Run *nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so*
7.Should work!

:D

---

### Post by russianpirate on 2006-10-14
Noone tried this yet?

Well, someone please do because it is a great way to termporarily (until 9.0 comes) get flash working and not lose any perfomance by using 32-bit version of firefox :D

PS: Had no crashes as of yet and it doesnt lag.

---

### Post by Aldrik on 2006-10-14
Nice one russianpirate. Mind sharing the source? 8)

---

### Post by russianpirate on 2006-10-14
What do you mean the source?

The rpms that I turned into debs?

[ftp://fr2.rpmfind.net/linux/MandrakeCooker/2007.0/x86_64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm](ftp://fr2.rpmfind.net/linux/MandrakeCooker/2007.0/x86_64/media/main/release/nspluginwrapper-0.9.90.3-1mdv2007.0.x86_64.rpm)
[ftp://fr2.rpmfind.net/linux/MandrakeCooker/2007.0/x86_64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm](ftp://fr2.rpmfind.net/linux/MandrakeCooker/2007.0/x86_64/media/main/release/nspluginwrapper-i386-0.9.90.3-1mdv2007.0.x86_64.rpm)

---

### Post by janfsd on 2006-10-15
Thanks for it, flash is working...but it crashes sometimes.

---

### Post by russianpirate on 2006-10-15
Sorry it crashes. Doesnt crash for me.

This plugin doesnt work too well for games and also places where there may be buffer overflows which cause crashes.

---

### Post by russianpirate on 2006-10-17
Fixed link ;)

---

### Post by Exclamation on 2006-10-17
Thx, I got it working..only prob is theres no sound.
btw do you also post on the archlinux fourms?

---

### Post by russianpirate on 2006-10-17
Yes I used to use Archlinux on my old 386 system :D
No sound.. make sure no other program (esd,arts,xmms,etc.) is using your sound card cause the flash plugin is coded crappily and it needs direct access :-\

---

### Post by Riverine on 2006-10-19
2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1) Gecko/20060601 BonEcho/2.0 (Ubuntu-edgy)
Shockwave Flash 9.0 d55

npviewer crashed once and locked up firefox, but since then plugin sound and video have worked fine.

Thanks for debianizing that software.

---

### Post by russianpirate on 2006-10-19
Okay anyway, I switched to i386 because of general stability and compatibility issues with amd64-version right now. So can't update it/help you anymore. But good luck :D

---

### Post by kuja on 2006-10-19
It would have been nice if Gwenole had made it more flexible, but that was his/her decision. If it worked with other browsers I would probably use it.

---

### Post by kuja on 2006-10-19
> **russianpirate said:**
> Okay anyway, I switched to i386 because of general stability and compatibility issues with amd64-version right now. So can't update it/help you anymore. But good luck :D
Stability problems? Like what?

---

### Post by bmichel on 2006-10-19
I tried this trick as well but Firefox 2.0 hang after few html/flash pages seen so it's hardly usable.

---

### Post by bmichel on 2006-10-20
Switch to Firefox2-32bit with Flash Beta 9. See the HowTo [http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

It works like a charm and you can still keep the 64 bit version of FF if needed.

Macromedia is working on a 64 bit version of flash, we'll see in one or two years.

---

### Post by fatsheep on 2006-10-20
This didn't work for me, see the attached screenshots.  What's strange is I have both of the mentioned packages installed...

---

### Post by Kilz on 2006-10-20
> **kuja said:**
> Stability problems? Like what?

If you look at his post histry its all trying to get nspluginwrapper to work. Sadly we all learn the lesson sooner or later that beta code isnt always the easiest, regardless of the bit. Nspluginwrapper is beta. His second post in this thread said that running a 32bit browser was a loss of performance. What some people dont ralise is that there is no true 64bit browsers. They are just 32bit compiled to run on 64bit. So there is little to no performance gain.
That and trying to get Stream to run under wine

---

### Post by russianpirate on 2006-10-21
Yes I agree, that is why 32-bit is a more suitable solution for me (little perfomance loss, but stability and compatibility is much better). And yes there is not true 64-bit software for linux, except perhaps the kernel (only  partial CPU code is changed) which then allows other programs that were compiled on another 64-bit machine to run and the code itself is not changed which means it doesnt use the true 64-bit bandwidth.

---

### Post by Kilz on 2006-10-21
> **russianpirate said:**
> Yes I agree, that is why 32-bit is a more suitable solution for me (little perfomance loss, but stability and compatibility is much better). And yes there is not true 64-bit software for linux, except perhaps the kernel (only  partial CPU code is changed) which then allows other programs that were compiled on another 64-bit machine to run and the code itself is not changed which means it doesnt use the true 64-bit bandwidth.

No, there is quite a bit of 64bit software. Blender a 3d modeling program is. Most of the rippers/encoders are, and some other applications. Its just that there are no true 64bit browsers. So using a 32bit one isnt a loss of performance. If there is its so small a human couldnt tell.
By going with 32bit os you lose the performance of what is 64bit. You cant run 64bit applications. The best thing imho is to use the 64bit os, but use 32bit applications where its needed or there isnt a huge loss to get functionality.
Sadly some people think its "just easier" for a 32bit os. That isnt always the case, and you have to remember that you have learned a lot putting in the 64 bit version , so when you install the 32bit one everything **seems** easier.
If you are saying compatibility issues because you were trying to get plugins to work with nspliginwrapper. That is a streach. As the wrapper is beta software and has a lot of problems. Using the 32bit Firefox solves all the problems most of the time.

---

### Post by alek66 on 2006-10-23
This happened to me... =(
> alek@darkstar:~/Desktop/nspluginwrapper-0.9.90.3-deb$ sudo dpkg -i nspluginwrapper_0.9.90.3-2_amd64.deb nspluginwrapper-i386_0.9.90.3-2_amd64.deb
Password:
Selecting previously deselected package nspluginwrapper.
(Reading database ... 90999 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.90.3-2_amd64.deb) ...
Selecting previously deselected package nspluginwrapper-i386.
Unpacking nspluginwrapper-i386 (from nspluginwrapper-i386_0.9.90.3-2_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 nspluginwrapper depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 nspluginwrapper depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.2.2-0ubuntu1.
 nspluginwrapper depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 nspluginwrapper depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.
 nspluginwrapper depends on libpango1.0-0 (>= 1.14.5); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nspluginwrapper-i386:
 nspluginwrapper-i386 depends on libc6-i386 (>= 2.4-1); however:
  Version of libc6-i386 on system is 2.3.6-0ubuntu20.
dpkg: error processing nspluginwrapper-i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
 nspluginwrapper-i386


What can i do...¿?

---

### Post by russianpirate on 2006-10-25
Update your sources and update all the packages since they are out of date?

---

### Post by hk_2999 on 2006-10-26
Excellent job! My flash works fine now. Thank you.

---

### Post by fjordlander on 2006-10-30
Hi there,
Thanks for the tutorial. Having followed it to the letter, the plugin does not appear to load and "nspluginwrapper -l" gets the following output

Inconsistency detected by ld.so: dl-close.c: 342: _dl_close: Assertion `tmap->l_ns == ns' failed!

Any ideas?  nspluginwrapper -r gets
 nspluginwrapper -r ~/.mozilla/plugins/libflashplayer.so 
nspluginwrapper: /home/tina/.mozilla/plugins/libflashplayer.so is not a valid nspluginwrapper plugin

---

### Post by russianpirate on 2006-11-11
> **fjordlander said:**
> Hi there,
Thanks for the tutorial. Having followed it to the letter, the plugin does not appear to load and "nspluginwrapper -l" gets the following output

Inconsistency detected by ld.so: dl-close.c: 342: _dl_close: Assertion `tmap->l_ns == ns' failed!

Any ideas?  nspluginwrapper -r gets
 nspluginwrapper -r ~/.mozilla/plugins/libflashplayer.so 
nspluginwrapper: /home/tina/.mozilla/plugins/libflashplayer.so is not a valid nspluginwrapper plugin

I had some problems like that with the older versions. Try deleting  the libflashplayer.so and everything from nsw and try to reinstall everything. I don't know why that problem occurs.

**PS: Keep downloading people cause rapidshare deletes files within a short period of time and I dont know exactly where the file is**

---

### Post by H3g3m0n on 2006-11-21
I also have the problem.

None of the plugins show up in Firefox's about:plugins.

And i get:
```
root@ender:/usr/lib/mozilla/plugins# nspluginwrapper -a -u -v
Inconsistency detected by ld.so: dl-close.c: 342: _dl_close: Assertion `tmap->l_ns == ns' failed!
```
Same error with -l.

> Any ideas? nspluginwrapper -r gets
nspluginwrapper -r ~/.mozilla/plugins/libflashplayer.so
nspluginwrapper: /home/tina/.mozilla/plugins/libflashplayer.so is not a valid nspluginwrapper plugin

The -r requires the npwrapper.libflashplayer.so file not the original plugin.

I tried building 0.9.90.4 from source and got the same errors, the closes error i could find on Google was nVidia drivers causing problems with OpenOffice.org but I doubt its related, although I am using them and the nspluginwrapper compile did show some Cairo stuff which i think is hardware accelerated.

I had nspluginwrapper working under a Gentoo install, I found it to work quite well although streaming videos sometimes froze seeking would cause about a second to play then freeze again, when it happened all instances of streaming flash where effected on different tabs.

Having nspluginwrapper worked well as all the 64bit media player plugins also worked under the 64bit Firefox so i was able to play most forms of streaming media without problems.

---

### Post by xopher on 2006-11-22
Thank you. Works like a charm so far ;)

Now I can remove the stupid opera I installed before.. heh.

---

### Post by xopher on 2006-11-22
I noticed the version **0.9.90.4** of nspluginwrapper was released (18.Now), so I aliened the rpms, and installed them instead. They say this version should be more stable. And they do work fine as we speak :)

I uploaded them here:

[nspluginwrapper-i386_0.9.90.4-2_amd64.deb]("http://www.kolumbus.fi/jacce/nspluginwrapper-i386_0.9.90.4-2_amd64.deb")
[nspluginwrapper_0.9.90.4-2_amd64.deb]("http://www.kolumbus.fi/jacce/nspluginwrapper_0.9.90.4-2_amd64.deb")

Have fun!

**EDIT:** Still, the release notes say the following, so remember this when installing.

Version 0.9.90.4
.
.
Flash Player 9 Beta

Flash Player 9 beta for Linux does not work correctly yet. In particular, the plugin will crash on ButtonRelease events (in an XtDispatchEventToWidget callback) when the button represents a link to another page. Independently, Valgrind reports a very high number of use of uninitialised value, conditional jump or move depends on uninitialised value and similar errors. It&#8217;s not known yet whether this is caused by nspluginwrapper or not.

---

### Post by janfsd on 2006-12-22
There is a new version of it ... 0.9.91 (22 Dec) it seems that now it works well with flash 9 beta 2, so any chances of any debs?

---

### Post by xopher on 2006-12-22
> **janfsd said:**
> There is a new version of it ... 0.9.91 (22 Dec) it seems that now it works well with flash 9 beta 2, so any chances of any debs?

Thanks for the update, let's see what I can do from here. (Im at my parents for christmas so I have to SSH to alienate the rpms.)

**Edit** (7mins later):

Ok, that wasn't hard :) Here they are:

```


[B][nspluginwrapper_0.9.91-2_amd64.deb]("http://www.kolumbus.fi/jacce/nspluginwrapper_0.9.91-2_amd64.deb")
[nspluginwrapper-i386_0.9.91-2_amd64.deb]("http://www.kolumbus.fi/jacce/nspluginwrapper-i386_0.9.91-2_amd64.deb")[/B]
```
Have fun, haven't tried them out so report back any success / problems.

**Release notes**

Version **0.9.91**
Scripting support through NPRuntime

Scripting support through the npruntime API is now supported. You can disable npruntime with the NPW_DISABLE_NPRUNTIME environment variable. Please note that Konqueror does not currently support this API. So, this will only work with Mozilla-based browsers.
Flash Player 9

Flash Player 9 beta 1 (9.0.21.55) is not supported. Flash Player 9 beta 2 (9.0.21.78) will work correctly, including with sites using javascript to navigate through other pages. There is a check to prevent the use of FP9 beta 1.
Biarch build

Most of Linux/x86_64 distributions can&#8217;t build biarch (i.e. 32-bit and 64-bit) packages at once. Henceforth, a subset of LSB Desktop 3.1 is now included so that the 32-bit viewer can be built effortlessly. You only have to make sure that your compiler supports generation of -m32 code.
Cross-platform improvements

NSPluginWrapper now supports FreeBSD and NetBSD hosts. Please read the Platforms Support Matrix and Distribution-specific Notes sections for further details.

---

### Post by janfsd on 2006-12-22
Thanks, that was fast, i am gonna try them now

EDIT: Flash 9 seems to be working great!!

---

### Post by Beini on 2006-12-26
Using the version 0.9.91 debs above, trying to install flash plugin but i get a output like this:

```
nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /home/jussi/.mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

```

Flash plugin is version 9.0.21.78

Any ideas?

---

### Post by rajeev1204 on 2006-12-26
hmm

[http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)


this is the mozilla dev link so u wont go wrong with that . u need the plugin and viewer for this to work . no need to download the source rpm.

and all those who are getting the error ' not a valid NP4 plugin' , intall to /usr/lib/mozilla-firefox/plugins cos that is the location of 64 bit firefox

flash 9 beta 2 is also working well.

regards

rajeev

---

### Post by stlutz on 2007-01-01
Not sure if you got your problem resolved or not, Beini.  I got the same error.  The solution is to install the linux32 package.

Has anyone gotten flash to work in Konqueror using this method?  I can see the plugin listed, but it doesn't actually work.

---

### Post by janfsd on 2007-01-02
There is a new version out 0.9.91.2 (29.12.2006) any debs?

---

### Post by Dun on 2007-01-03
> **janfsd said:**
> There is a new version out 0.9.91.2 (29.12.2006) any debs?
Why not create them with alien yourself?

---

### Post by rajeev1204 on 2007-01-03
hi

the location for the plugin is /usr/lib/mozilla-firefox/plugins  and not mozilla/plugins 

This is for all those who have that invalid plugin message.

And yes , u should thank russian pirate for the debs cos its so much easier for us.

I had to use rpms for mine.

---

### Post by janfsd on 2007-01-03
> **Dun said:**
> Why not create them with alien yourself?

Maybe a bit too lazy to make them ;) never mind then, I'll try to use alien...

---

### Post by kesman on 2007-01-04
```

:/usr/lib/mozilla-firefox/plugins$ sudo nspluginwrapper -i libflashplayer.so 
*** NSPlugin Viewer  *** ERROR: libflashplayer.so: cannot open shared object file: No such file or directory
*** NSPlugin Viewer  *** ERROR: libflashplayer.so: cannot open shared object file: No such file or directory
nspluginwrapper: libflashplayer.so is not a valid NPAPI plugin

```

and there was an error in the how to, the part
sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper

should be
sudo ln -s /usr/lib/nspluginwrapper/x86_64/linux/npconfig /usr/bin/nspluginwrapper

since there is no npconfig in the x86_64 -directory.

I also had to remove nspluginwrapper from my /usr/bin, because it was already there.

---

### Post by kcallis on 2007-01-12
> **russianpirate said:**
> There are quite a few threads about nspluginwrapper,but none worked for me. So I decided to download the latest (0.9.90.3) version of npw (not from their site from some ftp..) and repackage it to deb for everyone to use.

_If you had problems with previous versions of nsw, this package increases your chance for getting npw to work greatly._

I run Ubuntu Edgy x86_64 2.6.17 w/ Firefox 2.0RC2 and this version of nsw and it works perfectly (at least for flash.. I use blackdown java for the plugin)

**_Download here:_**
[nspluginwrapper-0.9.90.3-deb.tar.gz]("http://rapidshare.de/files/36660964/nspluginwrapper-0.9.90.3-deb.tar.gz.html")

**_Instructions:**_
1.Download the package
2.Untar it into a folder
3.Use *dpkg -i* (nameofdeb.deb) to install **both** of the debs
4.Copy libflashplayer.so to ~/.mozilla/plugins
5.Run *sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper*
6.Run *nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so*
7.Should work!

:D

And what I keep getting is:

[ ~/packages/install_flash_player_7_linux ]$ nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so
nspluginwrapper: /home/kcc/.mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

---

### Post by alteo_gange on 2007-01-12
> **stlutz said:**
> Has anyone gotten flash to work in Konqueror using this method?  I can see the plugin listed, but it doesn't actually work.I have the same problem with konqueror.

---

### Post by nbayiha on 2007-01-16
nspluginwrapper: /usr/lib/mozilla-firefox/plugins/libflashplayer.so is not a valid NPAPI plugin

i have the same problem this is what i get

---

### Post by nbayiha on 2007-01-16
actually i fixed the problem :KS  , i forgot to check on the  flash version  (i had an old version the 4th one)

secondly i forget to install one 32bit lib(ia32-libs) 

and third i forgot to install nspluginwrapper-i386_0.9.91-2_amd64.deb

after doing all those i manage to watch some funnies movies in our loving youtube.:mrgreen: :mrgreen: 


but i got a problem that i still can't fixed...the sound ain't work....](*,) 
damn!!!! i was so happy for nothing

some help are needed:confused: :confused: :confused:

---

### Post by Corbelius on 2007-01-17
> **nbayiha said:**
> 

some help are needed:confused: :confused: :confused:


[http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)

---

### Post by nbayiha on 2007-01-17
i follow this link but it ain't help me at all:( :( 

I've upgrade to the latest version of flash the ninth one. but still not working.


running firefox from the  terminal show me a lot of error in common with alsa:confused: 

LoadPlugin: failed to initialize shared library /home/nbayiha/.mozilla/plugins/libflashplayer.so [/home/nbayiha/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

ALSA lib pcm.c:2109:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so

 
i guess my sound it's not working since now cause i have the latest version of alsa 1.0.14rc1.  

looking around i saw that someone (almost) had the same problem than me [http://www.ubuntuforums.org/showthread.php?p=2028127#post2028127](http://www.ubuntuforums.org/showthread.php?p=2028127#post2028127)

i followed a lot of thread looking everywhere but everything that i tried just didn't succeed to make the sound work.](*,) ](*,) ](*,) ](*,)

---

### Post by pinguin on 2007-01-18
Try installing lib32asound2
bye

---

### Post by nbayiha on 2007-01-19
It's already installed. even with it there's still no sound :confused: :confused:

---

### Post by Corbelius on 2007-01-21
Remove completely previous installation and files, and try:

Add my repository to your sources.list and install nspluginwrapper:

```
sudo apt-get install nspluginwrapper
```

Download Flash Player plugin from Adobe website: Flash Player 9
Extract and move the content of the package in the folder /usr/lib/firefox/plugins.
Now from command line execute:

```
nspluginwrapper -v -a -i
```

Nspluginwrapper will create the necessary files to work in the folder /home/user/.mozilla/plugins/, now check if plugin work correctly, visit [http://www.youtube.com/](http://www.youtube.com/).
This method works with all Gecko browser family&#8217;s (Epiphany, Firefox, Galeon, etc etc.).

[http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)

---

### Post by ndefontenay on 2007-03-28
I got this:

```
spluginwrapper -i /usr/lib/browser-plugins/libflashplayer.so
nspluginwrapper: /usr/lib/browser-plugins/libflashplayer.so is not a valid NPAPI plugin
```

argh!:confused: 

any reason why it would say that?

---

