---
title: "ttf-mscorefonts-installer"
date: 2015-03-16
forum: Wine
---

### Post by carusoswi on 2015-03-16
Wine (and Crossover) have refused to either install or function on my machine for the past month.  I have upgraded from a perfectly functioning 14.04 to 14.10, then reinstalled 14.04, then upgraded again.  Results are always similar.  Wine almost always refuses to install.  On occassion, I have installed it from terminal (copying commands from posts offering help to others). in those cases, it installed, but still would not run.

Crossover refuses to install without errors that require me to run additional scripts.  Even then, it doesn't want to function properly.

FWIW, I am looking to install Irfanview, the lightweight image viewer that I have been using with Ubuntu/wine for years.

That application is known to run so smoothly under wine, that the author has never bothere porting it to Linux.

I lost patience again yesterday afternoon, and once again installed 14.10 onto my system.

I do this by booting the Ubuntu CD, then selecting install, then selecting the option to erase the current ubuntu system (preserving my Win7 installation) and installing the new version of Ubuntu.

I'm no Linux (or computer) whiz, but I do have years of experience with both, having worked with PC's since the DOS/MSDOS days, with Ubuntu since the 6.04 days.

For the user, (especially in Linux), everyday chores such as installing/removing software, upgrading OS's, etc. are much simpler today.  But, everyonce in a while, I experience something perplexing such as this.

My most recent attempt to install Wine resulted in a message that ttf-mscorefonts-installer could not be downloaded, that I should check my internet connection or setup or something like that.

Any help would be greatly appreciated.

I would like to get Wine and/or Crossover installed so that I can install Irfanview and move on with my photo efforts.

Thanks in advance for any advice.

Caruso

---

### Post by kc1di on 2015-03-16
I must say I've had no problem installing wine on any Ubuntu release.  sometimes some of the windows software requires a certain version of wine and I've had to downgrade the wine version to get it to work , that is where wine tricks has helped.  

sound's like your apt sources list may not have the correct repositories listed.  

Wish I could be of more help, but not at my ubuntu machine at the moment. 
hope you find a solution.

---

### Post by SeijiSensei on 2015-03-16
Have you tried installing **ubuntu-restricted-extras** which includes the MS fonts package?

---

### Post by carusoswi on 2015-03-28
Just did it now.
Wine is currently installed, but, when I right click on Irfanview, click on open with Wine (or whatever the exact menu wording is), the little circle icon spins for a while, then just stops.  Can't install the program.
Very frustrating.
Don't know what I (or my system) is doing wrong.
Thanks for the replies.
Caruso

---

### Post by SeijiSensei on 2015-03-28
Are you trying to run the irfanview installer or irfanview itself?

Try running it from the command prompt with 
```
wine /path/to/program.exe
```
using whichever program you're trying to run.  What errors do you see?

Have you considered using native Linux viewers like gwenview?

---

### Post by carusoswi on 2015-03-29
I am trying to run the installer by right clicking it and selecting "open with wine . . ." or "open with Crossover".
In the case of Crossover, I can also start that application and run through its menu to select the installer file, create a new bottle (or use an existing one), then proceed with the installation.

Yesterday, I again re-installed Ubuntu 14.10, went to the Codeweavers support site and installed Crossover from the code provided (rather than from the package offered for download).  The three lines
 of code: "sudo apt-get install gdebi" 

"sudo apt-get install python-gtk2 libasound2:i386 libasound2-plugins:i386 libfontconfig1:i386 lib32nss-mdns libxslt1.1:i386 libxcomposite1:i386 libosmesa6:i386 libopenal1:i386 libmpg123-0:i386 libldap-2.4-2:i386 libgstreamer0.10-0:i386 libgstreamer-plugins-base0.10-0:i386 libgsm1:i386 libxinerama1:i386 libxi6:i386 libv4l-0:i386 libsane:i386 libxml2:i386"

and:

"sudo gdebi crossover_14.0.0-1.deb"

allowed me to install a working copy of the program.

From there, I was able to select a version of Irfanview (4.35 with associated pluggins) that actually runs on my system.

I would prefer to just run Wine (not through Crossover) and had installed and used Irfanview (4.35 and a later version, 4.38 I believe) without a problem through version 14.04 of Ubuntu.

I had accidently set my 14.04 password with the caps lock on, and finally grew tired of having to remember to press caps lock when booting into Ubuntu, so reinstalled it to correct my password.  During the course of installing all my usual photo aps, I discovered that Irfanview would not install in Wine, and, if installed via Crossover, the installation would either not complete or Irfanview would not open.

As for error messages, there were none (might have seen something had I opened a terminal, but I didn't).

What would happen when I tried to install Irfanview with Wine is that the little circle (the hourglass used to be the typical icon) would spin briefly (15 or so seconds), then just disappear.

FWIW, I was using installation files (Irfanview and Irfanview pluggins) stored on an external drive that I have used countless times when re-setting up my system.

I'm thinking something has changed in 14.xx that caused the problems, perhaps some update in 14.04 that wasn't present when I first installed wine/irfanview in 14.04 but is there now, something in 14.10 also.

Fortunately, I now have a working copy of Irfanview, so, although I don't know the cause of the problem, I can now move on and just use this most useful program.

I've nothing against using Linux viewers and will have a look at gwenview, but, when one is used to using a certain application (especially one that works identically across platforms (and Irfavnew to my eyes runs faster on Linux/wine than it does on its native windows)) this body doesnt really spend too much time searching for something else.

Thanks for the replies and suggestions.

Caruso



> **SeijiSensei said:**
> Are you trying to run the irfanview installer or irfanview itself?

Try running it from the command prompt with 
```
wine /path/to/program.exe
```
using whichever program you're trying to run.  What errors do you see?

Have you considered using native Linux viewers like gwenview?

---

### Post by SeijiSensei on 2015-03-29
You won't see error messages unless you run wine from the command line.

---

