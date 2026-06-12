---
title: "Lightscribe on 64-bit Feisty"
date: 2007-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mbobak on 2007-04-09
Hi,

I'm running 64-bit Feisty Beta, and I'm trying to get Lightscribe working.

When I run alien on the .rpm I downloaded, it says:
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

So, ok, it's a 32-bit binary, and my O/S is 64-bit.

But, (with the right 32-bit libraries installed) shouldn't 32-bit programs run just fine on my 64-bit install?  And if so, is there a way to force alien to install the program?  I have a 32-bit Firefox installed, and that works just fine.  Shouldn't (theoretically) any 32-bit program work, assuming the appropriate 32-bit libraries are available?  I don't want to go through setting up a chroot environment, if I don't have to.

AdvThanksance,

-Mark

---

### Post by ronocdh on 2007-04-09
Maybe this thread will help you: [http://ubuntuforums.org/showthread.php?t=398586&highlight=force+architecture](http://ubuntuforums.org/showthread.php?t=398586&highlight=force+architecture)

---

### Post by mbobak on 2007-04-09
Problem w/ that is, "force-architecture" option is for dpkg.  I have a .rpm that I'm trying to convert to .deb using alien.  Alien does not seem to have any such option.

-Mark

---

### Post by rubberglove on 2007-06-07
Hi - I'm curious to know if you got this running without a chroot... I'm just about to do the same thing.

---

### Post by Mr_bleu on 2007-06-07
> **mbobak said:**
> Problem w/ that is, "force-architecture" option is for dpkg.  I have a .rpm that I'm trying to convert to .deb using alien.  Alien does not seem to have any such option.

-Mark
Alien will convert it to a deb file.  Then you use --force-architecture -i option to dpkg it.

---

### Post by kuja on 2007-06-07
WHat happens if you run alien with linux32?

---

### Post by pentax on 2007-06-08
I hope somebody can help me, I've been unsuccessful at building a deb using alien, here is the output from the terminal
```

kris@:~/downloads$ sudo alien lightscribe-1.6.45.1-linux-2.6-intel.rpm
Warning: Skipping conversion of scripts in package lightscribe: postinst
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/lightscribe
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: lightscribe-1.6.45.1: No such file or directory



```

---

### Post by almalaci on 2007-10-10
So in other words, there is no solution to mbobak's original question?
I have the same problem and I don't want to either chroot or install a 32bit system just for this. 
Or do I have to, is there no other way?

---

### Post by John Jason Jordan on 2007-10-10
> **almalaci said:**
> So in other words, there is no solution to mbobak's original question?
I have the same problem and I don't want to either chroot or install a 32bit system just for this. 
Or do I have to, is there no other way?
I got it running on Feisty amd64, but I don't recall off the top of my head how I did it except that I used information in another thread here on the forums. I'm not at the computer with the Lightscribe drives at the moment, so I can't help other than to tell you to search the forums for posts by me regarding Lightscribe, because that's the thread you want. I'm in a hurry at the moment or I'd do it for you.

---

### Post by John.Michael.Kane on 2007-10-10
> **almalaci said:**
> So in other words, there is no solution to mbobak's original question?
I have the same problem and I don't want to either chroot or install a 32bit system just for this. 
Or do I have to, is there no other way?

Here are the threads John Jason Jordan is referring to..
[How to Lightscribe ?]("http://ubuntuforums.org/showthread.php?t=534676&highlight=Lightscribe")
[lightscribe?]("http://ubuntuforums.org/showthread.php?t=434981&highlight=Lightscribe")
[[SOLVED] No such file or directory - Lightscribe and others]("http://ubuntuforums.org/showthread.php?t=511987&highlight=Lightscribe")

---

### Post by almalaci on 2007-10-10
Thanks a lot,
But actually my issue was with a canon printer driver. I decided to install a 32-bit Feisty but in the end I got away with just using the install cd, apt-get alien and made the debs good. (The printer is still not working though but that's a different issue :)

---

### Post by dad311 on 2007-10-10
Just thought I would mention, that I got lightscribe working with Gusty 64 bit:).  I downloaded the 386 rpm files, converted them with alien(32 bit) and install them with the dpkg -force architecture  option.  Works great:)

---

### Post by John Jason Jordan on 2007-10-10
> **dad311 said:**
> Just thought I would mention, that I got lightscribe working with Gusty 64 bit:).  I downloaded the 386 rpm files, converted them with alien(32 bit) and install them with the dpkg -force architecture  option.  Works great:)
So when the great day comes and I upgrade to Gutsy, will I be able to run 32-bit alien? As I recall, in order to get Lightscribe working I had to have a friend with 32-bit Linux run alien on the RPMs so I could install them because alien on my 64-bit Feisty machine puked them up.

---

### Post by dad311 on 2007-10-10
Sorry I forgot to mention I had a 32bit machine also.  I converted the rpms on my 32 bit machine then installed them on the 64 bit machine.  

If you dont have a 32bit PC, install VirtualBox and run 32 bit Ubuntu virtually

As I said earlier, the rpm installed and worked on x64 Ubuntu without much effort.  I should note however, you will need to run 4L-gui and root.

Good Luck.

---

