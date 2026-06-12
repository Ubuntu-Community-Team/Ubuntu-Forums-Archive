---
title: "Qjoypad Installation?"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2007-01-15
Hello,

 I had Qjoypad working as it was installed when I was running the 32bit version, and still worked when I switched to 64bit. I made a mistake and tried to do somnething with it and it broke  the install and I had to do a "sudo apt-get install -f" to fix the problem. Well so long Qjoypad.

 I then went and tried to follow the instructions from [[COLOR="SeaGreen"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=147918") :

```
fakeroot alien qjoypad-3.4-1.i586.rpm

I installed using dpkg:

sudo dpkg -i qjoypad_3.4-2_i386.deb

I then linked the icons so they actually worked:

cd /usr/local/share/pixmaps/qjoypad/
sudo ln -s gamepad2-24x24.png icon24.png
sudo ln -s gamepad2-64x64.png icon64.png

NOTE: try `eog /usr/local/share/pixmaps/qjoypad/ &` first if you want a choice of icons!

Finally, I hope someone fixes this stupid libqt3-mt dependency crap.

Regards,
td
```

Well when I run the fakeroot alien part I get the following:

```
Warning: Skipping conversion of scripts in package qjoypad: postinst
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
                xargs -0 -r -i cp -a {} debian/qjoypad
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path /usr/lib32/libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libqt-mt (soname 3, path /usr/lib32/libqt-mt.so.3, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: qjoypad-3.4: No such file or directory

```

So, it appears to me I need a to find a way to force the architecture or something when running alien??? 

Any help would be greatly appreciated by this no nothing Linux novice!

Chris

---

### Post by chrism66 on 2007-01-15
First sorry about the double posting my mistake trying to edit my bad spelling, too many windows open, etc....

All right I got it installed!! Did some further reserch and found that mandrake had a 64 bit version and it installed flawlessly.

---

### Post by Maybelline on 2008-07-14
> **chrism66 said:**
> All right I got it installed!! Did some further reserch and found that mandrake had a 64 bit version and it installed flawlessly.

Do you have a link to share?  I'm in dire straits!

---

