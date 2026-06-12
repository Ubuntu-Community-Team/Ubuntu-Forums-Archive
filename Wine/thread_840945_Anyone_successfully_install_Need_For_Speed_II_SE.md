---
title: "Anyone successfully install Need For Speed II SE?"
date: 2008-06-25
forum: Wine
---

### Post by reponzo01 on 2008-06-25
Hi all,

I've tried for days to get my Need For Speed II SE installed in Wine, but to no avail. I've tried setting Wine to Windows 95 which works to get the game installed. 

When running nfs2sen.exe, I get this error:

```
The instruction at 0x00493062 referenced memory at 0x00000004.
The memory could not be written.
```

So I installed a glide wrapper and copied over nfs2sea.exe from the CD and tried to run it...at which point, I get this error as a popup error message:

```
initgraphics - INITMEMMAN REQUIRED BEFORE INITGRAPHICS FILE c:\nfs2se\game\3rash\initgrf.c LINE 44
```

I've tried Windows XP sdb patches (which Wine won't let me install). I've tried a hundred different things! The main reason I still dual boot with XP is to play this game :( If I got this working, it would make my day!

Has anyone had success installing this game (this is the retail NFS2SE)? If so, how did you do it? Cuz I would totally buy you a beer!

---

### Post by sj_ on 2009-04-19
Hi, there. Just trying to run NFS2:SE under Wine 1.0.1 and have no luck. Game menu loads fine  but when i press RACE button game is closed.

---

### Post by NightMKoder on 2009-04-19
Aw that was a fun game.

First, try the latest wine (1.1.19), and check AppDB: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902) , which says you need to run some patch on the executable.

If that doesn't help, post a full log.

---

### Post by asdfoo on 2009-04-19
> **NightMKoder said:**
> Aw that was a fun game.

First, try the latest wine (1.1.19), and check AppDB: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902) , which says you need to run some patch on the executable.

If that doesn't help, post a full log.

yep.. the appdb now has instructions for working around the crash/freeze after clicking Race

---

### Post by divan0 on 2009-05-12
I have Jaunty on laptop Acer Aspire 5100 and on my desktop Dell Optiplex 745(with Nvidia 9600 and 24-inch monitor). 
On the laptop NFS2 runs like a charm.
On the desktop it fails with the same error as in the first post of this thread and was fixed with schedtool:

```
sudo apt-get install schedtool
schedtool -a 0x1 -e wine NFS2SEN.EXE
```

---

### Post by asdfoo on 2009-05-12
> **divan0 said:**
> I have Jaunty on laptop Acer Aspire 5100 and on my desktop Dell Optiplex 745(with Nvidia 9600 and 24-inch monitor). 
On the laptop NFS2 runs like a charm.
On the desktop it fails with the same error as in the first post of this thread and was fixed with schedtool:

```
sudo apt-get install schedtool
schedtool -a 0x1 -e wine NFS2SEN.EXE
```

I think you need to use this patch:

[http://bugs.winehq.org/attachment.cgi?id=10524](http://bugs.winehq.org/attachment.cgi?id=10524)

[http://wiki.winehq.org/Patching](http://wiki.winehq.org/Patching)

---

### Post by reponzo01 on 2009-06-29
Thanks to NightMKoder for the WineHQ link [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10902) . The game installs and runs ok now. One small quirk though...plugging in a USB gamepad before launching the game causes the menu in the game to appear as if you are constantly pressing the "Up" key every half-second. Just be patient and hit "Enter" when it goes to "Options", "Controls", then "Setup". Then be patient again and setup your controls for using the gamepad. After you've set up your "Steer Left, Steer Right, Brake and Accelerate", press up or down on the keyboard and the menu should stop moving up on its own. 

If you are not using a USB gamepad, the problem does not happen. I am still trying to get the Glide wrapper portion working right but that's just icing on the cake. At least the regular game runs perfectly! Thanks! :-D

---

### Post by Cjvrt on 2012-02-13
Hi there every1... Just signed up..

Well I too have a problem for nfs2se installation...
I tried doing it myself after reading here and a couple of other websites...

I have crossover version 10.2.0. and OSX latest, and iso of need for speed II se.
Can anyone plz tell me how to go about it from the start !

Cheers!

---

