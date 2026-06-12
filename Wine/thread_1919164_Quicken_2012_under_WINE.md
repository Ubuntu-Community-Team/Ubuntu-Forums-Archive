---
title: "Quicken 2012 under WINE"
date: 2012-02-02
forum: Wine
---

### Post by TheFu on 2012-02-02
I'm attempting to get **Quicken 2012 Home & Business **installed under **WINE** in **Ubuntu 10.04**.

I've had Quicken 2008 running almost perfectly for years and have installed Quicken 2011 Premium under WINE successfully elsewhere.  The dependencies for 2012 appeared to be the same, but following the 2011 installation instructions does not work.

Attempted to follow the instructions here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25204](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25204) . The app installs fine after the multiple winetricks are handled, but crashes during startup due to a TBD error.  I've worked through a number of the errors by manually copying newer DLLs into the Wine area from a WinXP x32 installation.

I'm running LXDE on Ubuntu Server 10.04 LTS x32 still.

[LIST]
[*]**wine-1.1.42** – `wine —version`
[*]2.6.32-37-generic #81-Ubuntu SMP i686 – `uname -a`
[*]Ubuntu 10.04.1 LTS – `more /etc/lsb-release`
[/LIST]
Can someone post their working configuration and the winetricks they've used to get there?  I'm in the **process of loading a new 11.10 server with LXDE to get a newer wine version** and more current other libraries. Normally I'd wait until 12.04 LTS before attempting this, but I can't wait any longer.   I believe the WINE version that **will be installed is WINE 1.3.37.**

I know the WINE version is old, but that's the version in the repos.

For a little more background see [http://blog.jdpfu.com/2012/02/01/failure-quicken-2012-not-working-on-ubuntu-10-04](http://blog.jdpfu.com/2012/02/01/failure-quicken-2012-not-working-on-ubuntu-10-04)

Thanks for any help you can provide.

---

### Post by TheFu on 2012-02-13
bump?

I did install 11.10 plus a newer WINE. Then attempted to get Quicken 2012 working.  It fails when trying to open any prior QDF files - locked up WINE completely.

---

