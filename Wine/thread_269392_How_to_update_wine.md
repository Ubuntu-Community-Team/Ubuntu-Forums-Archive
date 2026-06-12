---
title: "How to update wine?"
date: 2006-10-01
forum: Wine
---

### Post by haxer on 2006-10-01
Hello i wounder how to update wine to the newest?

---

### Post by Mr Frosti on 2006-10-01
This depends on the method that you used to install your existing version of WINE. If you selected this package using Synaptic, or from "Add/Remove", then updating can be done by opening Synaptic Package Manager, and right-clicking on WINE and choosing upgrade (If an upgrade is available)

If you installed WINE by custom installing, then you can download the latest version, and install this. Files from the older WINE will be overwritten with the new versions.

---

### Post by Locutux on 2007-12-19
What if there's no "upgrade" availble? I would like to update my Wine to the newest version as well.

Thanks.

---

### Post by Naegling23 on 2007-12-19
go to [www.winehq.com](www.winehq.com).  Add the requested address to your package manager.

---

### Post by Locutux on 2007-12-19
Thanks man, but you're talking with a newbie here. :) I'm not sure how do I do that.

---

### Post by Hairy_Palms on 2007-12-19
go to Applications->Accessories->Terminal and past these lines

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

---

### Post by cogadh on 2007-12-19
There is a sticky thread at the very top of this forum that explains exactly how to update Wine to the latest:
[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by ThaRabbit on 2007-12-19
To be complete, using the method linked to by cogadh: wine will automatically be updated using the winehq Ubuntu repositories.

a.k.a. you'll get a notification from the update manager if a new version is released. Each time winehq releases a new version they build a Ubuntu .deb package ready for installation.

:)

---

### Post by Locutux on 2007-12-19
Thank you. It worked.

---

### Post by mikemunsil on 2008-07-08
> **Hairy_Palms said:**
> go to Applications->Accessories->Terminal and past these lines

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

And make sure you don't have Synaptic open when you try to do the install. :lolflag:

---

### Post by kai_tea on 2008-07-11
Hi,

I'm having an issue doing this.
I can get through all the commands okay, but when I type the install command I get this:
[INDENT]Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using that unstable distribution that some required packages have not yet been created or been moved out of Incoming

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help resolve the situation:

They following packages have unmet discrepansies:
wine: Depends: windind but it is not going to be installed
E: Broken pacakges[/INDENT]

Can anyone offer any help?

---

### Post by paradoxic on 2008-12-17
I already have some programs and fonts installed into my current version of Wine. Is there any method of updating Wine I can use where I wont lose my installations? (It seems like I would lose this if I used the method where I have to uninstall Wine first).

I cant update through the package manager because I did a custom install.

---

### Post by cogadh on 2008-12-17
As long as you don't delete your .wine directory in your home directory, you won't lose anything. The .wine directory is not deleted when simply uninstalling Wine.

---

### Post by TonyFordz on 2009-09-06
I did this also & I get the following message,
wine is already the newest version.

The problem is 1.0.1 is not the current highest version but it will not let me get the current version so what do I do to fix this? I am using Ubuntu 9.04 Desktop Version

Is there a command line that I can do in the terminal to update packs, and Add/Remove lists?

---

### Post by TonyFordz on 2009-09-06
NM I figured out what was up after I went threw every folder in my Ubuntu lol trying to figure out how the hell to get WINE out of my menu which the following fixed for me...

============================================================================
Go to System, Administration, Synaptic Package Manager & Search for WINE then mark for complete removal.

After that do the following,

Places, Home Folder, Press CTRL + H to show hidden files & directories
delete the ".wine" folder

Go to & delete the ".wine" folder:
.local/share/applications
============================================================================

I been making posts on my own site to help others as well as myself for future references so this should help me in the future & anyone else needing to know how to get rid of it once & for all or to get rid of it so you can update it. What I wanted was the Beta version not the current stable version.

---

### Post by bapoumba on 2009-09-07
This thread is a little old, closing :)

---

