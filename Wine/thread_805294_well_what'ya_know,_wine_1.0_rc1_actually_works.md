---
title: "well what'ya know, wine 1.0 rc1 actually works"
date: 2008-05-23
forum: Wine
---

### Post by logos34 on 2008-05-23
After I upgraded to Hardy I was forced to rollback to an earlier wine (gutsy .47) to get it to recognize my cdrom drive (gotta have my Exact Audio Copy).  Well, I haven't used wine/windows programs for a few days and I got a nasty shock just now: one of the many recent updates appears to have thrown wine for a loop such that it refuses to launch.

But luckily the 1.0 rc1 appears to have fixed whatever Hardy-related bugs were in the .59 and .60 versions.  

Please let that be the last of my wine issues!

---

### Post by YokoZar on 2008-05-24
This is the whole reason to have a stable release, really.  If Wine 1.0 works for you, then you should avoid upgrading unless you find a new application that doesn't work or you're upgrading to another stable release.

I tried to make the Wine version that ended up in Hardy as stable as possible myself, manually patching the regressions I could find, but ultimately the month+ of stabilization work that's going into Wine 1.0 will inevitably be better.

---

### Post by logos34 on 2008-05-24
> **YokoZar said:**
> This is the whole reason to have a stable release, really.  If Wine 1.0 works for you, then you should avoid upgrading unless you find a new application that doesn't work or you're upgrading to another stable release.

I tried to make the Wine version that ended up in Hardy as stable as possible myself, manually patching the regressions I could find, but ultimately the month+ of stabilization work that's going into Wine 1.0 will inevitably be better.

yeah, I've locked it down in synaptic so it won't upgrade automatically.

That said I will consider trying 1.0 stable when it comes out, being prepared, of course, to beat a hasty retreat back to the version I'm using now at the first sign of trouble.

kudos to you guys...I'm sure you're doing your best to fix the bugs.  Wine is a great program; makes life a lot easier in linux.

---

### Post by MaindotC on 2008-05-24
I am pleased w/ Wine as well.  For a long time I've wanted to run Starcraft on my T60 but have always had trouble and crashes as well as applications remaining in the menu even after I uninstall them.  I did a nice, fresh, clean install of Gutsy recently (Hardy was a disaster) and installed Wine from source.  The fonts in Starcraft are still messed up but I can play on-line with my friends and I don't have any crashes.  Praise to the developers for making my day!

---

### Post by cogadh on 2008-05-24
RC2 is even better. I just got Vampire: Bloodlines to run practically flawlessly, which is really impressive, considering the game barely works on Windows to begin with.

---

### Post by MaindotC on 2008-05-24
When a new candidate is released and you install it, does it overwrite the previous wine installation, or does it just write into additional directories and clog up your file system?  I'd like to install rc2 from source but I don't wanna just keep bloating up my drive and I don't know the procedure for uninstalling wine other than finding each directory with "wine" in it and deleting it.

---

### Post by cogadh on 2008-05-24
If you compiled it from source, then all you should need to do is open a terminal, cd to the directory where you have the source code, then run "sudo make uninstall". 

If you want to avoid having to do that, use [checkinstall](https://help.ubuntu.com/community/CheckInstall) instead of the usual "make install". Checkinstall can make a rough .deb package that can be installed, uninstalled or upgraded just like packages you get from the repositories.

---

### Post by MaindotC on 2008-05-24
Cool I'll do that.  As I said earlier Broodwar finally works for me, but it would be nice if the font issue was resolved.

---

### Post by MaindotC on 2008-05-25
I'm sorry cogadh - one other question.  If I have rc1 installed from source, would you forsee installing rc2 from source interfering or causing problems?  I figured this would keep the games that I currently have installed.  If you don't know it's cool - just wanted to ask before doing it.  Thanks!

---

### Post by cogadh on 2008-05-25
It shouldn't cause a problem, as long as you run "wineboot -u" after installing to update your existing .wine directory with any changes made in the new version.

---

### Post by MaindotC on 2008-05-25
Cool I didn't know about the wineboot function.  I'll get right on it.

---

### Post by MaindotC on 2008-05-25
I installed rc2 - no changes, Broodwar is still buggy but hey, at least I have rc2 :)  Thanks for the help cogadh!

---

### Post by YokoZar on 2008-05-25
> **strAlan said:**
> When a new candidate is released and you install it, does it overwrite the previous wine installation, or does it just write into additional directories and clog up your file system?  I'd like to install rc2 from source but I don't wanna just keep bloating up my drive and I don't know the procedure for uninstalling wine other than finding each directory with "wine" in it and deleting it.Why not just use the packages?

---

### Post by flapane on 2008-05-25
> **strAlan said:**
> I installed rc2 - no changes, Broodwar is still buggy but hey, at least I have rc2 :)  Thanks for the help cogadh!

if you used checkinstall, please can you share us your package?

---

### Post by cogadh on 2008-05-25
Why not just compile it yourself? Its really not that hard, it just requires the use of the terminal for most of it:[LIST=1]
[*]Download and extract the Wine sources from WineHQ. 
[*]Open a terminal and change directories to the directory where you extracted the Wine sources
[*]Install the build essentials and checkinstall packages ```
sudo apt-get install build-essential checkinstall
```
[*]Get all the Wine build dependencies ```
sudo apt-get build-dep wine
```
[*]Run this to configure the compile:```
CC="gcc-4.2" ./configure --verbose
```Check the end of it for any missing dependencies. If there are none, move on to step 6. If you do have any missing dependencies, do the following: [LIST=a]
[*]Search Synaptic for the appropriate dev package and install it
[*]After installing any missing dependencies, run this ```
make distclean
```
[*]Return to step 5
[/LIST]
NOTE - You can completely avoid these steps by using Dan Kegel's simple script that will install everything you could possibly need to compile Wine. I choose not to use it because it seems to install more than what is actually needed, but it doesn't do anything harmful, I'm just a drive space Nazi. There are versions of the script available for [Feisty](http://www.kegel.com/wine/feisty.sh), [Gutsy](http://www.kegel.com/wine/gutsy.sh) and [Hardy](http://www.kegel.com/wine/hardy.sh).
[*]Run this to start the compile:```
make
```Go take a nap, this will take a while
[*]Once the "make" step is complete, run this to buld the rough package:```
checkinstall --install=no
```Enter a description for the package (whatever you want) and then accept the default options.
[/LIST]
The package will be in the directory where you extracted the Wine sources. You can install it by simply double-clicking on it. Please note that this will be an extremely basic package that doesn't require the binfmt-support package like the regular Wine packages do and still installs everything in Wine's default locations.

---

### Post by flapane on 2008-05-25
Hi,
thank you for yout tips, I already compile amsn and other stuff from svn on my box, but in this case I would need the gutsy i386 (that runs on an old box) package, so the only way is to compile it directly on that system, and this is impossible atm, I'll wait then ;)

---

### Post by MaindotC on 2008-05-25
I've had problems w/ Wine in the past.  I've only tried two games - the two that keep me attached to windoze - Broodwar and Counterstrike.  Always something like the menus have no letters or something totally crippling that keeps the game from working (yes I've installed mstcorefonts).  I've heard people say that installing from source provides a better installation configuration to your operating system.  However, I don't know how to prove installing from source is in any way advantageous to installing from repos.

---

### Post by logos34 on 2008-05-26
I just upgraded to wine-1.0-rc2 and all my windows apps including CDex work fine.  (yeah, I know I said I'd lock down rc1 but i couldn't resist.) But now Exact Audio Copy refuses to launch.  It's really breakin my bolls.  I'm getting this error:

[ATTACH]71700[/ATTACH]

I've tried every conceivable setting in winecfg

EAC forums aren't much help

I'm pretty sure it's something in wine and not eac that's causing the problem.  It can't be the drive settings because Cdex works fine.

Ideas anyone?

(I've even tried going back to rc1 but now THAT doesn't work with eac!)

---

