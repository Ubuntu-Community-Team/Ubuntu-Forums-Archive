---
title: "HOWTO: Rollercoaster Tycoon 2 + Wine in Ubuntu"
date: 2008-01-02
forum: Wine
---

### Post by Mazza558 on 2008-01-02
[IMG]http://img88.imageshack.us/img88/8374/rollercoastertycoon2sy5kh2.jpg[/IMG]

[SIZE="7"]HOWTO: Rollercoaster Tycoon 2 + Wine in Ubuntu[/SIZE]

I've seen a fair amount of questions in regards to RCT2 in Ubuntu, and luckily, now it works flawlessly.

*NB: RCT2 will install to a hidden folder in /home, so make sure you have enough space for it.

**Step 1: Wine**
[B]
NB: if you already have Wine, skip to step 2.[/B]

Firstly, you want to set up the latest version of Wine. To do this, update your system with:

```
sudo apt-get update
```

Next, let's install wine:

```
sudo aptitude install wine
```

The download will be about 34mb (as of 02/01/08).

Finally, Check that wine's installed and working by going to Applications > Wine > Programs > Accessories > Notepad. If Notepad opens flawlessly, then Wine's fully functional.


**Step 2: Installing Rollercoaster Tycoon 2 with Wine**

*Grab your Rollercoaster Tycoon 2 CD and put it in the drive.

*Ubuntu will see the disk as a data disk, so just wait for the disk folder to appear in a nautilus window.

*Find "Autorun.exe", right-click on it and choose "Open with other application".

*Scroll down the list of your applications and choose "Wine Windows Emulator".

*Choose your setup language, and click the blue disk icon on the autorun screen to start the setup.

*Keep going until you get to the setup type screen. If your sound's on, you should hear the traditional RCT merry-go-round music. Gaming is near! Choose "typical" and continue.

*Wait for the install to complete - it should only take a few minutes.

*You MIGHT get a CRC error. Don't panic, this happens in Windows too. Click ignore. A dialog box should appear telling you your version of DirectX is up-to-date. Click OK to continue.

*The setup will ask whether you want an icon on your desktop. If you choose "yes", Wine'll add a convenient shortcut here. 

*Finally, click "finish" to exit the installation.


**Step 3: taking Rollercoaster Tycoon for a test-run**

*Luckily, RCT2 works fine even with Compiz on, with basically no slowdown on a moderately fast system.

*Double-click on the desktop icon if you chose to have one. If not, go to "Applications > Wine > Programs > Infrogrames > Rollercoaster Tycoon 2".

*RCT2 will come up with a "Starting for the first time" loading window, which has the text slightly cut off. 

*RCT2 will then go fullscreen, 800x600

*If you have a different resolution to the default, choose to start a new game in any level. Go to the disk icon and then to "options". From there, you can change the resolution. Note that on some PCs, the gnome interface will get in the way when you do this. If this happens, simply close RCT2 and reopen it.

*Note that although RCT2 does work with compiz, it's best to turn it off whilst playing for the best performance.

*Now that RCT2 is running, enjoy the game! Remember that you need the disk in the drive to play.

---

### Post by K.Mandla on 2008-01-03
Moved to Wine subforum. ;)

---

### Post by bonzodog on 2008-01-03
hrm...have just installed this today. Debugger goes crazy with it, it doesn't start. What version of windows does it work with?

Any mods to winecfg?
```

Backtrace:
=>1 0x02000d00 (0x0032f1b0)
  2 0x0032fef8 (0x0032fe7c)
  3 0x0144c065 in rct2 (+0x104c065) (0x0032ff08)
  4 0x7ee4e38b in kernel32 (+0x4e38b) (0x0032ffe8)
  5 0xb7ec57b7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

---

### Post by Mazza558 on 2008-01-03
> **bonzodog said:**
> hrm...have just installed this today. Debugger goes crazy with it, it doesn't start. What version of windows does it work with?

Any mods to winecfg?
```

Backtrace:
=>1 0x02000d00 (0x0032f1b0)
  2 0x0032fef8 (0x0032fe7c)
  3 0x0144c065 in rct2 (+0x104c065) (0x0032ff08)
  4 0x7ee4e38b in kernel32 (+0x4e38b) (0x0032ffe8)
  5 0xb7ec57b7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```


That's odd. I'm using Windows 2000 here, and everything is default. I haven't tweaked anything, it just works perfectly here. What version of Wine are you using?

---

### Post by bonzodog on 2008-01-04
Yeah, this is trying 0.9.52 community built package on a Zenwalk linux box, so I will get hold of the Laptop with ubuntu on it later, and try the repo version of wine for gutsy, and see if it works. Will let you know.

---

### Post by Mazza558 on 2008-01-04
> **bonzodog said:**
> Yeah, this is trying 0.9.52 community built package on a Zenwalk linux box, so I will get hold of the Laptop with ubuntu on it later, and try the repo version of wine for gutsy, and see if it works. Will let you know.

Hmm... it seems odd that the latest Wine doesn't work but the one in the repos does. Perhaps they broke something whilst implementing a new feature?

---

### Post by bonzodog on 2008-01-06
ok, the problem is with the zenwalk build of it.

I have just followed your guide, and indeed, RCT2 works just like you said, on the 0.9.46 build of wine for ubuntu gutsy. My laptop runs RCT2 like its on windows. (COOL!!). damn, means I will have to use laptop to play RCT2......
However, SimCity3000 unlimited still does not work -- it installed, but does not start. I guess they won't put any work into this as there is a linux native version of the game out there -- it costs $50 though!

---

### Post by bonzodog on 2008-01-07
I have finally tracked down the cause of my problems with Zenwalk; There is a bug caused by building wine against gcc 4.1.2, which zenwalk uses; it breaks the copy protection.
Scott Ritchie, who builds the official ubuntu version, gets round this by building against gcc 3.4.

---

### Post by Habeouscorpus on 2011-02-01
Sweet Chicken in a basket, this works. My childhood is BACK!

(I'm going to waste the next few hours on this, I know it.)

---

