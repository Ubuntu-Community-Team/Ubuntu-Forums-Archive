---
title: "HOWTO: Making 32bit compatibility packages"
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nuke Skyjumper on 2008-01-12
With a 64bit distro, you run into things like Adobe Flash and Adobe Acrobat that still depend on 32bit libs. You can't install the packages for these 32bit libs because your 64bit libs will be overwritten. There are a lot of solutions on the forum for problems like this, and a lot of them leave libs and files laying around where the package system can't find them - causing problems in the future.

Rebuilding a 32bit library package for your 64bit system is actually pretty easy, though there are a lot of steps. Once you know which library you need, search for it on [http://packages.ubuntu.com](http://packages.ubuntu.com) and download the i386 (NOT the AMD64) version.

I'm going to use libpulse0_0.9.6-1ubuntu2_i386.deb as an example since it was the key to getting Adobe Flash to play sound via PulseAudio on 64bit. Extract the .deb package:
```
dpkg -x libpulse0_0.9.6-1ubuntu2_i386.deb libpulse
dpkg -e libpulse0_0.9.6-1ubuntu2_i386.deb libpulse/DEBIAN
```
Now go into the **libpulse** directory and rename **usr/lib** to **usr/lib32**:
```
cd libpulse
mv usr/lib usr/lib32
```
And remove all of the other directories under libpulse, otherwise they would conflict with the 64bit version of libpulse that you already have installed:
```
rm -r etc/ usr/share/
```
Now to modify the package's control files which are in the DEBIAN directory. Remove the **conffiles** file which is supposed to tell the package manager which config files are in your package. You are only packaging the libs, not the config files, which you already removed up above.

```
rm DEBIAN/conffiles
```
Go into the DEBIAN directory and edit the **md5sums** file. Change everywhere that it says **usr/lib/** to say **usr/lib32/**. Then remove every line EXCEPT the usr/lib32 lines. Again this is because you are packaging only the libs, and not manual pages, config files, or anything else that might conflict with your already-installed 64bit version.

Now edit the **control** file. Add "32" after the word "lib" in the package name, so where it says ```
Package: libpulse0
``` and change to ```
Package: lib32pulse0
``` Change Architecture from **i386** to **amd64**. Save the control file and head back to your command line.

Make sure you're in the directory where you downloaded and extracted the original .deb package. Then go ahead and build your shiny new 32bit compatibility package:
```
dpkg --build libpulse
```

You can ignore any warnings about user-defined fields. If everything worked, you should now have a **libpulse.deb** sitting there waiting to be installed. Of course it might be a good idea to rename that lib32pulse_compatibility.deb or something similar and keep it around just in case.

This procedure should work for most library packages. Larger, more complex packages might have postinst / postrm scripts in the DEBIAN directory that you would need to trim down, and possibly other fields in the control file that might need removed or modified.

Hope this is useful. Good luck.

---

### Post by Kilz on 2008-01-12
Nice manual howto. I have been using a  similar method since Dapper Drake to install the few 32bit applications I need. But I just extract and copy the files into place. 
But then Cappy wrote [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") it will do all that automatically.  Its main advantage is when you have multiple libs to install. I remember having to extract 10 debs in the past.

---

### Post by Cappy on 2008-01-12
> **Nuke Skyjumper said:**
> There are a lot of solutions on the forum for problems like this, and a lot of them leave libs and files laying around where the package system can't find them - causing problems in the future.

Getlibs will implement this kind of method very shortly (in the next week maybe? Probably January 17th since I usually do biweekly releases). I was thinking of making a log file and uninstallation method earlier but I decided to do something like this instead to hopefully combat disappearing libraries from apt-get upgrading. I haven't decided if I will make it the default option or just an option yet.

This is a good guide for doing it by hand or in cases where getlibs may have a problem! It's also a good guide for someone who wants to distribute a 64-bit package with 32-bit libs in it.

---

