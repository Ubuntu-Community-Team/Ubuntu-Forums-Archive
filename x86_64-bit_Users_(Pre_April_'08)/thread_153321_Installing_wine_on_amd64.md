---
title: "Installing wine on amd64"
date: 2006-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by shibasu on 2006-03-31
Here is the output I got. Anyone with any info on how to make Wine work? I'll be out for a few hours so I won't be able to check up on this thread. Any Wiki links, helpful f.a.q's or anything else you can offer me would be most appreciated.

Or just a nice walkthrough ;)  - Thanks for any help you can give me


root@0-0:/home/diux# apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Need to get 13.5MB of source archives.
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.10~winehq1-2 (dsc) [1209B]
Get:2 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.10~winehq1-2 (tar) [13.5MB]
Get:3 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.10~winehq1-2 (diff) [47.0kB]
Fetched 3B in 1s (2B/s)
Skipping unpack of already unpacked source in wine-0.9.10~winehq1
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.10~winehq1-2
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/diux/wine-0.9.10~winehq1'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/diux/wine-0.9.10~winehq1'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.10~winehq1 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

---

### Post by hollywoodb on 2006-04-01
there are ways to get wine to install from the packages provided @ winehq's repositories....

[http://ubuntuforums.org/showthread.php?t=128739](http://ubuntuforums.org/showthread.php?t=128739)

however I recommend just setting up a 32-bit chroot. works great and there are a handful of 32-bit apps that aren't worth the hassle in a 64-bit environment. I run wine, cedega, firefox+java/flash/multimedia, mplayer, giFT with all plugins, opera, and a few others from a 32-bit chroot.

---

### Post by evilpig on 2006-04-01
I would also like to get this done. I am somewhat a noob to linux, but I have spent the last 3 hours working on anything I could find to get this done. 

I also have the AMD64 version of Ubuntu and it seems too hard.

EDIT: I was also getting the same compile error when I tried that method. :|

---

### Post by Seaman on 2006-04-01
[QUOTE=hollywoodb]there are ways to get wine to install from the packages provided @ winehq's repositories....

[http://ubuntuforums.org/showthread.php?t=128739](http://ubuntuforums.org/showthread.php?t=128739)

however I recommend just setting up a 32-bit chroot. works great and there are a handful of 32-bit apps that aren't worth the hassle in a 64-bit environment. I run wine, cedega, firefox+java/flash/multimedia, mplayer, giFT with all plugins, opera, and a few others from a 32-bit chroot.[/QUOTE]
So how do I do that? Reinstall Ubuntu with 32bit kernel?

---

### Post by ehsan on 2006-04-02
[QUOTE=Seaman]So how do I do that? Reinstall Ubuntu with 32bit kernel?[/QUOTE]

Nope.  Use [this howto](https://wiki.ubuntu.com/DebootstrapChroot).  This way you can install a 32-bit Ubuntu system on top of your 64-bit kernel, which you can switch to when you want to run 32-bit apps.

Ehsan

---

### Post by hollywoodb on 2006-04-02
[QUOTE=ehsan]Nope.  Use [this howto](https://wiki.ubuntu.com/DebootstrapChroot).  This way you can install a 32-bit Ubuntu system on top of your 64-bit kernel, which you can switch to when you want to run 32-bit apps.

Ehsan[/QUOTE]

In addition to that howto, to run an app from the chroot you don't necessarily have to use a terminal to enter and exit the 32-bit chroot environment. you can use
```
dchroot -d <appname>
```
for most apps, and you can create launchers for your menus using that syntax as the command. like the howto says, you can skip the "-c mychroot" part if you only have one chroot, which will probably be the case

---

### Post by evilpig on 2006-04-02
Err. This is starting to be too hard. I've tried everything and it just wont work. Is it possible for someone else to compile it so then I can get somewhere?

---

