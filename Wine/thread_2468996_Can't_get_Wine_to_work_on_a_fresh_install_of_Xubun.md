---
title: "Can't get Wine to work on a fresh install of Xubuntu"
date: 2021-11-16
forum: Wine
---

### Post by peyre on 2021-11-16
Oh my goodness, my system's given me so much trouble...I had to reinstall from scratch because it [started failing to upgrade to the latest version](https://ubuntuforums.org/showthread.php?t=2468485).  This is on my Dell Inspiron 3847 (ca. 2012?) with an old NVidia GEForce 9600 GT video card.  It now [refuses to output video through the card]("https://ubuntuforums.org/showthread.php?t=2468896") if I install the proprietary NVidia driver, so rather than use a single monitor with onboard video I'm using the video card with the nouveau driver.  I'm running Xubuntu 20.04 LTS.

I installed Wine as usual (plus all my other Linux programs), then started installing my old favorite Windows games.  The Desktop launchers simply fail to run.  They never (seem to?) open Wine.  If I run, say, [FONT=Courier New]wine Starcraft.exe[/FONT] from the terminal in the appropriate location, it brings up a Wine window showing my Desktop within Wine for a moment, then closes, and the terminal shows:

```

X Error of failed request:  GLXBadFBConfig
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  0 ()
  Serial number of failed request:  329
  Current serial number in output stream:  329

```

I've done a bunch of installing and reinstalling of Wine, trying the development version instead of stable, etc.  At one point I could run, say, Starcraft from the terminal, but the Desktop shortcuts absolutely refused to work, and of course they didn't say why by throwing up an error message.
Wine 5.0-3
Wine (development version) 5.5-3

I've installed mono:
sudo apt install mono-complete

Installed gecko:
sudo apt-get install wine-gecko\*

Installed dotNet 4.5
winetricks dotnet45

And through the Winetricks interface I've installed:
d3dx9
d3dx10
glidewrapper

Wine is an awesome application that *just works* most of the time.  I don't get why I'm having so much trouble on a fresh install of the OS, and with older Windows software that's always run well in Wine before.

---

### Post by peyre on 2021-11-17
No one, really?  I suppose I could wipe and reinstall from scratch again, but this will be the third time in a row.  It takes me two days of installation and configuration to get back up to speed.

---

