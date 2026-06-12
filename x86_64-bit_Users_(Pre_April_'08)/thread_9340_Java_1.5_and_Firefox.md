---
title: "Java 1.5 and Firefox"
date: 2004-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ahyden on 2004-12-27
Hi

Does anyone know how to get java 1.5 working in firefox on amd64?

I got java installed, and it's working (can compile and run java programs), but there is no plugin to link to Firefox, not even a plugin directory in the java directory. Must I get java 1.4.2 for this to work or am I missing something?

---

### Post by Buffalo Soldier on 2004-12-27
You can refer to the "How to install J2SE Runtime Environment (JRE) Plug-in for Mozilla Firefox?" section of Unofficial Ubuntu 4.10 Starter Guide at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by shimon on 2004-12-27
i don't think there is a 64bit plugin only a i386

---

### Post by ahyden on 2004-12-27
Ok thanks for the replies.
Guess I have to install Firefox in my 32bit chroot environment.

---

### Post by Kareema on 2004-12-28
It's true: even in the newly updated Sun J2SE 1.5, there's no browser plugin for AMD64 architecture available. As a work-around I installed Blackdown Java 1.4, which has a plugin for Netscape/Mozilla/Firefox under the AMD64 architecture.

---

### Post by ahyden on 2004-12-28
[QUOTE=Kareema]It's true: even in the newly updated Sun J2SE 1.5, there's no browser plugin for AMD64 architecture available. As a work-around I installed Blackdown Java 1.4, which has a plugin for Netscape/Mozilla/Firefox under the AMD64 architecture.[/QUOTE]

How did you install Blackdown java? I tried apt-get, but got a message saying it's not installable. What is Blackdown java anyway? :)

Right now I have installed firefox and java in my 32bit environment and that works, but it would be nicer if I could run it from my normal 64bit env.

---

### Post by Psy on 2005-01-03
I got java running with firefox using Blackdown java.

Just download the amd64 binaries from [www.blackdown.org](www.blackdown.org) (latest is 1.4.2), extract the files somewhere and make a symlink  from BLACKDOWN_ROOT/plugin/amd64/mozilla/libjavaplugin_oji.so to /usr/lib64/mozilla-firefox/plugins and java should be working perfectly. At least it did for me.  :D 

For flash its possible to use gplflash.sourceforge.net availiable with apt-get as libflash0 and swf-player (I think). It doesnt work that well tho.

---

### Post by ahyden on 2005-01-04
[QUOTE=Psy]I got java running with firefox using Blackdown java.

Just download the amd64 binaries from [www.blackdown.org](www.blackdown.org) (latest is 1.4.2), extract the files somewhere and make a symlink  from BLACKDOWN_ROOT/plugin/amd64/mozilla/libjavaplugin_oji.so to /usr/lib64/mozilla-firefox/plugins and java should be working perfectly. At least it did for me.  :D 

For flash its possible to use gplflash.sourceforge.net availiable with apt-get as libflash0 and swf-player (I think). It doesnt work that well tho.[/QUOTE]

Thanks!

---

### Post by cmsj on 2005-01-18
blackdown.org now actually provides an apt source and debian packages for their java stuff. Historically they're not updated very often, but right now it is in sync with the tarball release. The line for your apt sources.list file is:

deb [ftp://ftp.tux.org/pub/java/debian/](ftp://ftp.tux.org/pub/java/debian/) unstable non-free

do an apt-get update and then install j2re1.4 - this should give you a working java install and a working firefox plugin.

HOWEVER, every time I have installed this I have had to make a small change to the firefox startup script to make it work. It does a little test for old java versions that seems to break wildly on amd64, so you need to edit /usr/bin/firefox and comment out line 162 (put a # at the beginning of the line).

---

### Post by wellington on 2005-01-18
I think Sun don't realise there's folk that aren't using their 64bit linux java on beefy opteron servers. Its not just the lack of a plugin, there's no javaws (java web start) either, and both the vms, even the jre vm, seem to be server vms - no client vms. No javaw either. Probably have to wait for blackdown to package their version of 1.5 to get these facilities.

---

### Post by blinksilver on 2005-02-21
okay, so i add the blackdown into apt, got the the j2re 1.4 and the java-common, as well as commented out the line mentioned above, but still nada, the link to the plugin is in my /usr/lib64/mozilla-firefox/plugins

i ran a mozilla-firefox -verbose and it crashes on a seg fault

---

### Post by subterrific on 2005-02-21
[QUOTE=wellington]I think Sun don't realise there's folk that aren't using their 64bit linux java on beefy opteron servers. Its not just the lack of a plugin, there's no javaws (java web start) either, and both the vms, even the jre vm, seem to be server vms - no client vms. No javaw either. Probably have to wait for blackdown to package their version of 1.5 to get these facilities.[/QUOTE]

There is a bug in Sun's Java bug track open with lots of people yelling at Sun about this, and a few developer responses, so Sun is well aware.

I've been thinking about packaging a 32bit firefox that will run without the need of a chroot. This would allow us to use all these 32bit plugins like flash, java, readaudio, etc. Is there any interest in this?

---

### Post by blinksilver on 2005-02-22
yes,

---

### Post by Bubbling Zombie on 2005-02-22
definitly

---

### Post by arx-lupus on 2005-02-22
Yes!!

---

### Post by dreadnought on 2005-02-23
Count me in  \\:D/

---

### Post by cgdef on 2005-02-23
that would be great. I'll deffinitelly install that pkg  :-P

---

### Post by blinksilver on 2005-02-26
I know this not something anyone really wants to do, but if you guys want Java 1.5 AMD64, install Konquerer, konq does not use a plugin, so as long as there is a symbolic link to java in your /usr/bin/ it should run

---

### Post by lean on 2005-02-27
[QUOTE=cmsj]HOWEVER, every time I have installed this I have had to make a small change to the firefox startup script to make it work. It does a little test for old java versions that seems to break wildly on amd64, so you need to edit /usr/bin/firefox and comment out line 162 (put a # at the beginning of the line).[/QUOTE]
What exactly is the line you mark out? The line 162 of my firefox script is a blank line, and I can't find anything that denies loading - only ld_assume things.

---

### Post by cmsj on 2005-03-01
[QUOTE=lean]What exactly is the line you mark out? The line 162 of my firefox script is a blank line, and I can't find anything that denies loading - only ld_assume things.[/QUOTE]

You probably don't need to worry anymore, I submitted a bug about it and it was fixed. Unless firefox is failing to start you don't need to edit the script :)

For reference, line 162 in the old script was:

    ```
export LD_ASSUME_KERNEL=2.2.5
```

---

### Post by blinksilver on 2005-03-01
I still am getting a segfault, I have tried everything, I don't like konq, it takes over 150MB just to start, there has got be something I am doing wrong, please,  for the love of god have some ubuntu ](*,) 

in case it matters I am running hoary

---

### Post by blinksilver on 2005-03-01
there is no fix, if you actually got it running you are amazing, happens here fedora suse you name it it crashs just error message is different

---

### Post by Irishman5381 on 2007-05-15
> **ahyden said:**
> Ok thanks for the replies.
Guess I have to install Firefox in my 32bit chroot environment.


[Google Loans Bankruptcy Tsunami solar](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

