---
title: "Working KDE Themes in 32-bit GTK Applications!"
date: 2007-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by cypher35 on 2007-05-17
So using the following thread, I just recently ran Kilz's automated install script to set up 32-bit firefox on my AMD64 Kubuntu Feisty setup:
_[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)_

Upon startup I noticed that the newly-installed browser, while fully functional, looked like crap with the blocky GTK default theme, even though the *64-bit* firefox had integrated flawlessly with my KDE appearance settings.  I searched the forums for a fix, but found only a handfull of complaints and a response from Kilz saying that he [_didn't have a solution_](http://ubuntuforums.org/showpost.php?p=2463694&postcount=667).

So I set out on my own to understand why my KDE themes would not (or could not) be applied to a 32-bit GTK app such as this version of firefox when they could easily be applied to the 64-bit version I was using earlier.


First, I ran firefox in a terminal and discovered it was complaining about a missing file.  This was fixed with the following package:
```
sudo apt-get install ia32-libs-kde
```

I opened up the 32-bit firefox again and it looked a little better (not as blocky as before), but it still wasn't using my KDE theme.  I decided to take a look at my particular KDE theme's package (kde-style-polyester) to find out what files it installed and where.  Then I noticed that there were files being installed in **/usr/lib/**, and thought that logically since 32-bit applications use **/usr/lib32/*** instead of **/usr/lib/***, it might work if I were to grab the 32-bit package and extract it into my 32-bit lib folder.  So I downloaded the i386 package from [_packages.ubuntu.com_](http://packages.ubuntu.com/feisty/kde/kde-style-polyester) and ran the following commands to copy the appropriate files to the appropriate location.

```
cd ~/Desktop
sudo dpkg -x kde-style-polyester_1.0-1ubuntu2_i386.deb ~/Desktop
sudo cp ~/Desktop/usr/lib/kde3/* /usr/lib32/kde3
```

However, this didn't solve the problem.  I decided that it must still be looking in the wrong location for these files, so I searched around for some sort of config file that might point to these locations.  My search led me to the file "**qtrc**" located at both **/etc/qt3/qtrc** and **~/.qt/qtrc**.  Opening up **~/.qt/qtrc**, the following two lines appear to be relevant:
```
[3.3]
libraryPath=/home/mike/.kde/lib/kde3/plugins/:/usr/lib/kde3/plugins/

[KDE]
kdeAddedLibraryPaths=/home/mike/.kde/lib/kde3/plugins/^e/usr/lib/kde3/plugins/^e
```

I added an entry to both of these lines so they looked like the following:
```
[3.3]
libraryPath=/home/mike/.kde/lib/kde3/plugins/:/usr/lib/kde3/plugins/:/usr/lib32/kde3/plugins/

[KDE]
kdeAddedLibraryPaths=/home/mike/.kde/lib/kde3/plugins/^e/usr/lib/kde3/plugins/^e/usr/lib32/kde3/plugins/^e
```

I restarted firefox again and **Voila!**, my theme showed up just as it had in the 64-bit firefox.  However, this solution had a couple of problems.  The relevant entries in **~/.qt/qtrc** are reverted whenever a user re-logs in or changes their appearance settings.

The only way I have found to fix this is an ugly hack, but it works.  Since qt apparently looks in both **~/.kde/lib/kde3/plugins/** *AND* **/usr/lib/kde3/plugins/**, I decided to leave the config file as it was and copy the 32-bit theme into the (currently empty) **~/.kde/lib/kde3/plugins/** with the following command:
```
sudo cp -r /usr/lib32/kde3/plugins ~/.kde/lib/kde3/
```

This is probably horrible practice, but it works just the same... If anyone has a better solution, please let me know.


Theoretically, this should work with other 32-bit GTK apps and other Qt themes, but I have only tried it with the one in this example. Also if anyone is following along and finds that I've missed a step or forgotten to mention something, let me know and I'll add it in.

---

### Post by kuja on 2007-05-17
What about /etc/qt3-32/qtrc - have you experimented with it any?

---

### Post by cypher35 on 2007-05-17
> **kuja said:**
> What about /etc/qt3-32/qtrc - have you experimented with it any?

Hmm, I didn't know that file existed on my system.  I must have used the *locate* command without running *updatedb* after installing that last package.

I'll take a look at it.


**Edit:**
Unfortunately, it appears that editing this file doesn't do much.  The settings must get overwritten by the qtrc file on the home directory.  Any ideas?

Would it be trivial to recompile the 32-bit qt binary with a different filename or path for the user config, like "~/.qt-32/qtrc"?

---

### Post by kuja on 2007-05-17
Hmm, try creating that file, perhaps it will read it? I don't know that it'd be trivial to recompile that package, in fact, it might be a royal pain in the you know what. Give it a try though if you need to, and if you  hit stumbling blocks report back; maybe me or someone else will have an idea on how to get around it.

---

### Post by Kilz on 2007-05-17
> **cypher35 said:**
> So using the following thread, I just recently ran Kilz's automated install script to set up 32-bit firefox on my AMD64 Kubuntu Feisty setup:
_[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)_

Upon startup I noticed that the newly-installed browser, while fully functional, looked like crap with the blocky GTK default theme, even though the *64-bit* firefox had integrated flawlessly with my KDE appearance settings.  I searched the forums for a fix, but found only a handfull of complaints and a response from Kilz saying that he [_didn't have a solution_](http://ubuntuforums.org/showpost.php?p=2463694&postcount=667).

So I set out on my own to understand why my KDE themes would not (or could not) be applied to a 32-bit GTK app such as this version of firefox when they could easily be applied to the 64-bit version I was using earlier.


First, I ran firefox in a terminal and discovered it was complaining about a missing file.  This was fixed with the following package:
```
sudo apt-get install ia32-libs-kde
```

I opened up the 32-bit firefox again and it looked a little better (not as blocky as before), but it still wasn't using my KDE theme.  I decided to take a look at my particular KDE theme's package (kde-style-polyester) to find out what files it installed and where.  Then I noticed that there were files being installed in **/usr/lib/**, and thought that logically since 32-bit applications use **/usr/lib32/*** instead of **/usr/lib/***, it might work if I were to grab the 32-bit package and extract it into my 32-bit lib folder.  So I downloaded the i386 package from [_packages.ubuntu.com_](http://packages.ubuntu.com/feisty/kde/kde-style-polyester) and ran the following commands to copy the appropriate files to the appropriate location.

```
cd ~/Desktop
sudo dpkg -x kde-style-polyester_1.0-1ubuntu2_i386.deb ~/Desktop
sudo cp ~/Desktop/usr/lib/kde3/* /usr/lib32/kde3
```


Its simply amazing that after I gave you [the method to accomplish this ]("http://ubuntuforums.org/showthread.php?t=159810"). I see a post that explains how to do it.

---

### Post by cypher35 on 2007-05-18
> **Kilz said:**
> Its simply amazing that after I gave you [the method to accomplish this ]("http://ubuntuforums.org/showthread.php?t=159810"). I see a post that explains how to do it.
Does that offend you or something?  I'm not trying to take credit for your work or anything, I actually didn't read your post until after I had started this thread...  I wish I had noticed it earlier as it would have saved me some time.

Anyway, I'm still trying to figure out this problem of getting the lib32 qt libs to use a different per-user config file than the usual ~/.qt/qtrc

I looked into it a bit more and discovered that this ~/.qt-32/ home directory did exist at one point in time.  According to the changelog:
```
qt-x11-free (3:3.3.6-1ubuntu6) dapper-updates; urgency=low

  * Leave out (-1ubuntu5), rejected upload.
  * Use **~/.qt-32** as user config directory, when running the i386
    binaries on amd64, adds kubuntu_03_qt_private_confdir_ia32.dpatch.
  * Check for lib32 paths, when running the i386 binaries on x86_64 or ia64,
    adds kubuntu_02_qt_modules_ia32.dpatch

 -- Matthias Klose <doko@ubuntu.com>  Mon, 12 Jun 2006 17:24:02 +0200
```

But unfortunately both of these patches were removed a few months later (something to do with openoffice no longer needing it).

I am considering just recompiling ia32-libs-kde with this patch added back in, but I can't figure out how the heck to compile a 32-bit binary from my 64-bit system.  Could anyone help me out?

---

### Post by shame on 2007-05-18
Personally I install qtcurve in both the 64-bit install and the chroot and everything matches nicely.
I tend to use a wide mix of kde/gtk stuff though.

---

