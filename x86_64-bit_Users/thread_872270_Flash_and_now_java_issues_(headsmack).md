---
title: "Flash and now java issues (headsmack)"
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by opr8ive on 2008-07-27
Hello, Hello..  First post here in the ubuntu forums (woo-hoo!)

Played with various linux flavors off and on since about redhat 7 or so.. Always ended up going back to windows eventually for various reasons, usually out of a need for windows apps, not a dislike of *nix.

Finally had the means to pick up some dedicated hardware (Bought a new HP widescreen notebook) and yanked vista out before even signing the EULA :)

So far, got most everything going well (HH 8.04) with even limited java, and flash ..

But, Im running into troubles installing both the sun java, and the nonfree flash.. Ive read the tutorials, and I think im real close to getting it, but a little knowledge is dangerous, and I fear that in my tinkering Ive broken something (moved a file, changed a link, or something) and now cant get either to install..

First off, lemme give you some term output:

This is what I get with apt-get install flashplugin-nonfree:

```
Download done.
Flash Plugin installed.
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ia32-sun-java6-bin
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@sisyphus:~$
``` 


Heres the error I get trying to install the sun-java6:

```
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ia32-sun-java6-bin (6-06-0ubuntu1) ...
/var/lib/dpkg/info/ia32-sun-java6-bin.postinst: 99: /usr/lib/jvm/ia32-java-6-sun-1.6.0.06/bin/java: not found
dpkg: error processing ia32-sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 flashplugin-nonfree
 ia32-sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@sisyphus:~$
``` 

Ive tried removing, purging and cleaning, and re-installing both, but I still get these errors.

limited flash support in firefox right now with swfdec, but Id really like to get the adobe flash working.

Ive been searching, and trying all the tutorials I can find (even the two stickys at the top of this forum) still no go..

Any help would be great, and I thank you all in advance :)

-Jason

---

### Post by tuxxy on 2008-07-27
You dont need to install the new java, I use the gcj and the webplugin just fine from the buuntu-restricted package..

As for the flash did you not install the **ubuntu-restricted-extras** package from the repository.  THis will install flash among other things like unrar, java etc

```
sudo apt get install ubuntu-restricted-extras
```

If you installed flash mayeb you just need to make a link to it in your firefox plugins folder?

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by opr8ive on 2008-07-27
unfortunately, I did install the whole restricted packages package, and I believe flash was working..

(here comes the headsmack) I had later removed flash, as I was running into problems, and thought I had multiple installs of it.. Then I tried to install flash 10 (IIRC) and started getting this error..

I have tried from synaptics to uninstall/reinstall the whole restricted packages package to try and fix this, but got the same errors Im getting now.

Lemme try to take out the sun java6, to get that error to go away, and go to sun, and test my java ver.. Will report back in a sec..


(edit) Just removed it(ia32-sun-java6-bin), got the errors to go away for java, and re-started firefox, and it appears java6 is working just fine.. Heh.. Still having a beast of a time with the flash... (/edit)

-Jason

---

### Post by Sef on 2008-07-27
To install Flash on 64-bit, read [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490").

To install Java on 64-bit, read [Java on 64-bit]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by Nepherte on 2008-07-28
Hardy now automatically wraps the flashplugin with ndiswrapper if you just install the flashplugin-nonfree. Just type in a terminal
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by opr8ive on 2008-07-28
Tried Kilz's tutorial (again) When I get to the sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns I still get the same error..

```
 Download done.
Flash Plugin installed.
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@sisyphus:~$ 
```

Any thoughts?

Thanks again!

-Jason

---

### Post by opr8ive on 2008-07-30
(bump)

sorry, I know this is probably some kind of easy fix, but whatever it is, it eludes me,,,


-Jason

---

### Post by paolol61 on 2008-07-30
Hi I follow this guide and all is working good :)
Running the script and choosing type 3 and all is working fine ;)

> **Sef said:**
> To install Flash on 64-bit, read [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490")

---

### Post by opr8ive on 2008-07-30
Tried Kilz's tutorial a couple times (see post #6)

It errors out when configuring flashplugin-nonfree after install, and the tutorial says specifically to *not* continue if theres any errors installing the packages.

/me smacks head on wall, Heh

thanks tho.. 

-Jason

---

### Post by conorsulli on 2008-08-06
Um why just not completley uninstall the restricted extras and them re-install them through synaptic??
P.S with flash you should reboot after uninstalling and after re-installing. This should fix anything if you haven't messed up any configs.

Good luck! -remember to reboot!! and that flash 10 you installed separately is removed - but it probably will remove that anyway. I had the exact problem you had and this fixed it (the second time when I rebooted at each step).

:)

---

### Post by opr8ive on 2008-08-06
I had un-installed, then re-installed the whole restricted extras a couple times.

Still errored out..

Got it working now tho.

Some missing files in the lib32 dir.

Thanks anyways.

-Jason

---

### Post by kob0724 on 2008-08-15
opr8ive, what files were you missing in the lib32 directory? I'm having the exact same problem as you.

---

### Post by opr8ive on 2008-08-15
I dont know exactly, But what I did was removed, amd re-installed pretty much all the 32 bit lib packages I could find. (ia32-libs, libc6-i386, pretty much anything that looked like it was having to do with 32bit compatability)

Im sorry i dont remember exactly which package fixed it.. I kinda marked all of them for re-installation

Sorry i cant help more, I should have written it down somewhere :( .. I guess hindsight is 20/20

-Jason

---

### Post by Chibone on 2008-08-16
Hmm, I had a similar situation where I wanted to watch Big Brother on CBS and flash wouldn't work properly.

I got my flash working 100% by installing firefox32 on my 64 bit system using the script [here]("http://ubuntuforums.org/showthread.php?t=202537") and then removing it.  Seems like flash works better when having 32 bit libs.

From looking at the script it seems that these packages were installed:

```
ia32-libs ia32-libs-gtk lib32asound2 lib32ncurses5 ia32-libs-sdl
```

Maybe that'll help narrow it down some.

---

