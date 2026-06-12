---
title: "Can't leave sewers in oblivion"
date: 2008-03-19
forum: Wine
---

### Post by StephanG on 2008-03-19
I've sorted out most of the bugs, and now oblivion runs fine, except I can't exit the sewers (tutorial level).  

At this post, 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506&iTestingId=13506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506&iTestingId=13506)

the developer claimed that it was bug #8715 and that he could fix it by installing the latest git.  I can only imagine that that means gitwine, which seems to be a developing tool.  At the gitwine page they give instructions on how to install if you want to build from source code, but not for if you don't.

I would appreciate it if someone could either suggest a fix for the bug or give some instructions on how to install git.  Is there some repository I could add?

Thanks guys!

---

### Post by happyhamster on 2008-03-19
- Assuming you're using 32 bit gutsy gibbon, have the wine repository loaded (see: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)), and have uninstalled any previous wine (sudo apt-get remove --purge wine). You can keep the .wine folder though.

sudo apt-get install git-core
sudo apt-get install ccache

sudo apt-get build-dep wine wine-dev

- Get git (may take a while):
git clone git://source.winehq.org/git/wine.git wine-git

- Change into the new wine-git folder:
cd wine-git

- Check if everything's up-to-date (it will say: "Current branch master is up to date."):
git fetch ; git rebase origin

- Compile (could take  30~40 minutes, so get yourself some tea):
./configure && make clean && make depend && make

- You can now use wine (without installing it) by running it from the wine-git folder like this:
./wine /path/to/program.exe
./wine winecfg

- You have to issue these commands from within the wine-git folder (precisely the opposite of how a 'normal' wine install works: then you navigate to the game's folder and run wine from there).

- Or: you can really install this version using:
sudo make install
wineprefixcreate

- Warning: you have to *install* (or uninstall) wine as root (by using 'sudo'), but never(!) run anything else wine related as root.
(To uninstall: sudo make uninstall).

Good luck, and keep us informed.

---

### Post by StephanG on 2008-03-20
Sorry, I've been quiet for so long.

I'm just compiling now, thanks for your help happyhamster.

Will keep updated.

---

### Post by StephanG on 2008-03-20
Okay, when I'm compiling using 

./configure && make clean && make depend && make

the terminal gives

checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

This looks like I need to install the C compiler.  Which package would you recommend I install?

---

### Post by happyhamster on 2008-03-20
sudo apt-get install build-essential libc6-dev g++ gcc

Although most (if not all) of those should have been installed by running "sudo apt-get build-dep wine wine-dev" already.

---

### Post by StephanG on 2008-03-21
Compiled Successsfully, when I tried to load oblivion it said "The x11 driver is missing." Is there something else I should do? Can I reinstall wine now?

---

### Post by happyhamster on 2008-03-21
Hmm, there are still packages missing? I hate compiling. My guess is:

sudo apt-get install xserver-xorg-dev

After running ./configure (nothing else), does it give a hint which package is missing?

And something to consider: wine 0.9.58 should be just around the corner :)

---

### Post by StephanG on 2008-03-21
It gives a LONG list of packages with either a yes or a no at each one.  The command

./configure && make clean && make depend && make

seems to finish correctly.  I try to run:

./wine /home/stephan/Games/Oblivion/OblivionLauncher.exe

and the full error message is:

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

Is there some sort of wine driver that I am supposed to load, or should I reinstall wine.  Would it make a difference if I installed wine again?

---

### Post by happyhamster on 2008-03-21
You were missing some packages for wine to support X. After installing those packages you'll need to recompile and install wine from the start.

To uninstall: "sudo make uninstall"

BTW, wine 0.9.58 is out now, so you could also try compiling that version (or wait until the ubuntu packages are available).

[http://www.winehq.org/](http://www.winehq.org/)

[edit: There's no need to re-install Oblivion BTW, but make sure to issue the command "wineprefixcreate" before trying to run Oblivion with a new wine version]

---

### Post by StephanG on 2008-03-23
Hi, I've tried saving Oblivion on the windows machine.  It seems to be that all outside areas are a problem,  When it exits these areas, it only states a bunch of zeros.  In wine 0.9.58, it does at least try to identify your hardware, but no luck.  It still has the same problem.  The git-wine still needs that x11 package and I have no idea which one that is.  When I reinstalled wine, it had the same problem until I uninstalled git-wine. Then it worked normally.

Any other ideas.

---

### Post by happyhamster on 2008-03-23
It's a bit late :rolleyes: but I just read the bugreport: it is referring to gitwine quite some time ago. That means whatever patch was responsible for closing that bug is already incorporated in wine. So either there was a regression, or something in your setup is causing these crashes. (Make sure Oblivion itself is patched, set the recommended entries in the wine registry, make sure your video driver is configured correctly, etc.)

If all fails, you could also try opening a topic at the wine forums: [http://forum.winehq.org/](http://forum.winehq.org/)
(Make sure you give them all relevant information: linux version, video driver, wine-version, Oblivion version, etc, etc.)

---

