---
title: "wine on gutsy amd64 does not work!"
date: 2007-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by gangstarr805 on 2007-11-03
I am giving up on wine for amd64 on gutsy.
I have tried compiling it from source (i followed winehq directions, CC command not found.)
I have all the make, build-essential, ia32libs, gcc, libc6 libraries that I need.
I have tried dpkg -i --force-architecture on 32 bit deb.
I have tried older versions of wine from winehq.
The program will install but I cannot run winecfg. I keep getting seg faults. 

This is what i get when I run winecfg:

wine: creating configuration directory '/home/gangstarr/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/gangstarr/.wine'.
gangstarr@seabass:~$ wineserver: could not save registry branch to /home/gangstarr/.wine-GFkXpd/system.reg : No such file or directory
wineserver: could not save registry branch to /home/gangstarr/.wine-GFkXpd/user.reg : No such file or directory

I manually created the directory.
mkdir .wine

Then I get:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/gangstarr', starting in the Windows directory.
Segmentation fault (core dumped)

This is a fresh install of 7.10 and have not upgraded kernel.
The only thing I can possibly think of is that i removed restricted modules so that I could install nvidia drivers.

Any ideas? I think i will switch to 32 bit Debian and save myself some time and energy.

---

### Post by FG123 on 2007-11-03
Goodness that's a lot of work, particularly trying to compile the source code.

Wine in 64-bit Gutsy works fine for me. Did you follow the instructions here:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by gangstarr805 on 2007-11-03
yes to the T

---

### Post by avik on 2007-11-03
Wait, it's not in the repos?  It is for me.  I just did an apt-get install wine.  I'm running amd64, gutsy.

Make sure you have universe and multiverse enabled.

---

### Post by homerhomer on 2007-11-03
Hmmm,


Mine works perfectly fine.  I would suggest removing wine and then apt-get the one that one that comes with gutsy. I noticed that when it installs it installs some lib32 files.

---

### Post by FG123 on 2007-11-03
> **avik said:**
> Wait, it's not in the repos?  It is for me.  I just did an apt-get install wine.  I'm running amd64, gutsy.

Make sure you have universe and multiverse enabled.
Strongly recommend against using the WINE from the Gutsy repos, unless you don't mind staying with an older version that never gets upgraded.

---

### Post by utUtu on 2007-11-04
> **gangstarr805 said:**
> yes to the T

Obviously not!

If you follow the instructions, there is no need to do all that compiling.  You just need to add the Wine repos, and just apt-get install wine.  And you get the latest all the time

:guitar:

---

### Post by chrishere01 on 2007-11-04
i have wine running

the thing is

you cant run anything but .exe files

i had this problem with steam cause it was an msi

look up the walk through for 64 bit steam if you want

---

### Post by mkoyle on 2007-11-18
The best source for WINE is probably the one described at winehq.org: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

This will give you the most recent stable release (which is usually the best).

To run MSI installer files,  use "msiexec" the command is:

```
msiexec /i fileinstaller.msi
```

---

### Post by Toadmund on 2007-11-18
> **chrishere01 said:**
> i have wine running

the thing is

you cant run anything but .exe files


I can't run most .exe files, At one time I could at least open Project64, now I can't, the exe files just sit there and don't open, I even have the options set to open with wine.

What am I missing that my .exe's don't work?

---

### Post by aphirst on 2007-11-23
Well you seem to have shited up somewhere; and I think I know where.

You mentioned in your initial post that you "manually created the .wine directory", and that it flagged up errors in winecfg like "c:\\windows inaccessible"?
Well, you MUST run winecfg without manually creating .wine; because winecfg won't setup wine if it sees a .wine folder, even if it's empty! And, l you know what that means... IT MEANS YOU CAN'T RUN APPS.

So, the solution is to manually delete your failed .wine folder; then run winecfg. a "sudo apt-get remove wine --purge" wouldn't harm your chances either.

That should work :D .

---

### Post by paradoxni on 2007-11-23
I installed Wine 0.9.49 amd64 from [here](http://wine.budgetdedicated.com/archive/index.html) and it works fine for me.

---

### Post by Ehtetur on 2007-11-23
Some win32 apps need ODBC, mfc4x or dcom runtime libs installed to get them to work..
These runtimes are not part of a wine install and need to be manually installed - preferably after running winecfg..

There's a script from winehq called winetricks that automates the install of win32 runtime libraries: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks).
You'll have to chmod 755 winetricks to make it executable.. Then run ./winetricks to see all of the runtimes available to  install.

---

### Post by paradoxni on 2007-11-23
sounds familiar..i  must have ran that too :)

---

### Post by wikiguy on 2007-12-11
actually downloading from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) did work for me.You should try it too.:)

---

### Post by stchman on 2007-12-11
According to WINE website there are 64 bit versions available.

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Just add the repos and then do the following:

```

sudo apt-get update
sudo apt-get -y install wine
```

If you have older than Feisty you will need a hack.

---

### Post by Nythain on 2008-03-27
omg, either no one knows how to read anymore these days, or they just dont have brains or something...

no one even attempted to help the original poster...
im currently having the same problem...

A. im sure the poster has tried installing the repo version, then resorted to tryign to compile from source, encountering problems with both...

B. i DID follow those oh so great perfect flawless instructions on winehq's site, and yeah, still same problem...

C. from what i've gatherd with a days worth of google, its more than likely either a lack of certain 32bit libraries, or your nvidia driver...

did you install nvidia's driver, or the one from the repos??? do you have all the 32bit libraries, or just a couple, or any at all...

if you did install nvidia's driver (from thier site) did you install the 32bit libraries for it when it asked you to???

the only valid suggestion i've found on the net that seems to have oddly fixed it for many users, is to install wine, then uninstall your nvidia drivers, and re-install them... thats about all i've got so far, anyone else have any CONSTRUCTIVE ideas besides "install the repo version" or "follow winehq's instructions" because well, we did, and its still a no go

EDIT: upon re-reading i notice you too removed restricted modules and manually installed current nvidia drivers, so we are in exactly the same boat... here's hoping it works

and oh yeah, make sure you do delete your manually created .wine folder... you got those new errors because winecfg was very consused, assuming files it put there were there, when in fact they werent because you created the folder and not winecfg

SECOND EDIT: I finally made it home, and had a chance to test the "re-install nvidia drivers" method to fix this problem... and it worked... the only thing i can think of is, i had no 32bit apps installed, thus no 32bit libraries or need for them when i manually installed the nvidia driver the first time... when confronted with the "build lib32 compat libraries" or whatever option in nvidia installer the first time, it complained that it couldnt find a certain .so file... the second time around there was no complaint, so im assuming the first time it just couldnt or didnt want to install all the required libraries, but with the addition of 32bit apps, and teh ia32-libs it had what it needed to seal the deal the second time

---

