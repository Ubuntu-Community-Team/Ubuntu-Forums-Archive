---
title: "Error due to CrossOver. . ."
date: 2013-02-12
forum: Wine
---

### Post by ulynemesis on 2013-02-12
Hi, I have installed [COLOR=Blue]**Ubuntu 12.10**[/COLOR] and updated it as well as downloaded Wine and [COLOR=Blue]**CrossOver Demo**[/COLOR] (latest version available on the codeweaver site).

However, after I installed Crossover, an error is persistently showing on my screen whenever I login or when I use [COLOR=Blue]Ubuntu Software Center[/COLOR] or [COLOR=Blue]Software Updater[/COLOR]. The error says:

[INDENT][COLOR=Red]**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:The package crossover needs to be reinstalled, but I can't find an archive for it.

[/COLOR][/INDENT]And now, I can't even use my Ubuntu Software Updater because it keeps on crashing and the error above always shows when I try my Software Updater.

I tried uninstalling it using the uninstaller that comes with the installation but nothing happens or nothing appears after I click it. I also tried removing it from the Terminal using:  [COLOR=Blue]*sudo /opt/cxoffice/bin/cxuninstall*[/COLOR] and dialog box would appear with options for uninstalling the software, however, another error would pop up saying that [COLOR=Red]*An error occured while uninstalling Crossover for Linux. *[/COLOR]

Please, I really need help on how to fix this problem, either removing/uninstalling the CrossOver or successfully install it on my Ubuntu. Thanks!

---

### Post by varunendra on 2013-02-12
*Thread moved to **Wine**.*

---

### Post by varunendra on 2013-02-14
> **ulynemesis said:**
> The error says:

[INDENT][COLOR=Red]**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:The package crossover needs to be reinstalled, but I can't find an archive for it.

[/COLOR][/INDENT]And now, I can't even use my Ubuntu Software Updater because it keeps on crashing and the error above always shows when I try my Software Updater.

Well.. since no one else responded I guess I'll try.

If you are still getting the error and looking for a solution, you may try the "dpkg" option in "Recovery Mode" in Grub menu as a first shot.

To get the Grub menu *(it won't appear by default if Ubuntu is the only OS installed)*, when the system is booting, press and hold 'Shift' key.

Then in the menu, choose the second option that says "Recovery mode".

In the recovery menu, choose "dpkg" (fix broken packages) option, let it do whatever it wants, then choose again to boot normally. If that doesn't help, we may have to dig deeper.

.. and, please post back with the exact version of crossover you are using (I've installed version 10 with no issues).

---

