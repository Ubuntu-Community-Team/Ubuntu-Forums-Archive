---
title: "Diablo II won't Install through WINE because of d2sfx.mpq"
date: 2007-12-19
forum: Wine
---

### Post by Sugi on 2007-12-19
I can't install Diablo II through WINE because of some file it hangs at.  d2sfx.mpq stops the installation process.  My Wine is 0.9.51.

How can I get Wine to install Diablo II?

---

### Post by cogadh on 2007-12-19
There is a Wine subforum now for posting any questions related to Wine:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

As for your problem, it would help to know what errors, if any, are produced in the terminal when you try to install the game. You might also try following the how-to on Wine's AppDB page for the game:
[http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49)

---

### Post by loudnlownoma on 2007-12-19
Are you installing from the Diablo II CD's, or from .ISO images?

---

### Post by Sugi on 2007-12-19
I payed for my copy of diablo II.  So, I am using cds.  How Do I run Diablo II from the terminal
> wine /INSTALL/setup.exe

---

### Post by loudnlownoma on 2007-12-19
> **Sugi said:**
> I payed for my copy of diablo II.  So, I am using cds.  How Do I run Diablo II from the terminal'

Not necessarily saying you didn't pay for it, if it was implied, I apologize.  I bought mine as well, but prefer to use ISO's in most cases, so that I don't have to worry about over-use of the CD's and with them getting scratched and all.  No biggie.

To install from the CD, you will use something like:

```
wine /media/cdrom0/(filename).exe
```

depending on what your CD-Rom drive is labeled and mounted as, and filename would be the install file on the CD.

If you are referring to running it after installed, I have found it easiest to move to the folder the game is installed in, then just run the wine command from there, such as:
```

user@desktop:/.wine/drive_c/Program\ Files/Diablo$ wine Diablo\ II.exe

```

The reason I ask about this is because it likely "hangs" in the installation where it is asking you to switch the CD to a different disk.  I have seen a number of people on here (though I have never had the problem myself) note similar problems where the window asking for the new CD is hidden behind the installer window.  That would make it appear the installation has hung up and locked out, but is simply waiting for the CD to be switched.

---

### Post by loudnlownoma on 2007-12-19
I was also very thankful to find [this guide](http://ubuntuforums.org/showthread.php?t=443821) when installing for myself, which has a great walkthrough on installing Diablo II that worked flawlessly for me on a couple different PC's now.

---

### Post by Sugi on 2007-12-20
loudnlownoma, Ew, Im sorry if I came off as an ahole.  I actually have ISO of my Diablo 2 game as well, but I just made a copy of them so I can carry them around and I as well, don't have to worry about them getting scratched.

I ended up just booted into windows and install the files on that partition.  Then I went back to ubuntu and copy the files over.

My next question is, has anyone tried "Playing Multiple instances of Diablo II" or any other game?  I use to run multiple wines and always had this problem of wine minimizing the window.  After it minimized I couldn't get it to unminimize.

EDITED:  I may have found some stuff to aid me in my multiple instances of Diablo II and other games.  I'll give these links a try later and report back to everyone on ubuntu forum.

[http://ubuntuforums.org/showthread.php?t=443821]("http://ubuntuforums.org/showthread.php?t=443821")
> I typed: env WINEPREFIX="/home/erin/.wine2" wine "C:\Program Files\Diablo II\Diablo II.exe" -d3d9 -mpq cdkey_erin.mpq
[http://ubuntuforums.org/showthread.php?t=438724]("http://ubuntuforums.org/showthread.php?t=438724")
> I'm sure I'm not the only one that experiences Diablo II shrinking to the minimum possible window size when a second client is opened. There is a solution for this, and it is quite simple although it will take up a large amount of Harddrive space because essentially the only way I've found to do this is to copy the .wine folder and rename it. Here are the steps:

---

### Post by Sugi on 2007-12-20
How do I stop wine from minimizing when I click the Desktop or something not in wine.  It always minimize and never restore to it's normal size.  How can I stop this from happening?

---

### Post by loudnlownoma on 2007-12-21
Sorry for the delay in response.  Had a day off from work and things of course went crazy, as they have a way of doing...lol.  That's cool, I wasn't offended or anything, just wanted to make sure I wasn't making that impression.  :)

I honestly haven't tried to mess with running multiple instances, so I may not be much help there.  I know a blurb is mentioned in that walkthrough I linked earlier, but didn't pay it much mind as I only play it with one character at a time.  And the minimizing I'm not sure.  I usually run mine windowed so I can do other things in the background or use IM or whatever, but have never had any problem like that.  The window normally stays up and open.  Are you trying to run the game windowed, or are you running full-screen and switching to another desktop or alt-tabbing to a different window when that happens?

---

### Post by Sugi on 2007-12-25
I have been a little busy myself as well, So sorry about that.  Well, when I click the Desktop (the wallpaper), menu button, change workspaces, or anything but the game it will minimizes it.  And then I try to get it to come back to it's normal spot and nothing.  And yes, I am playing Diablo II in windows mode.

---

### Post by loudnlownoma on 2007-12-25
Strange....

If you open winecfg, then click the Graphics tab...  What options are checked?  If the "Allow Window Manager to control the windows" option is selected, try removing that, hitting OK, then run the game again.  Also, what version of Wine are you running?

---

