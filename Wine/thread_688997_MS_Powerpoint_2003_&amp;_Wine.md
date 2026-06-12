---
title: "MS Powerpoint 2003 &amp; Wine"
date: 2008-02-06
forum: Wine
---

### Post by Epiphyte on 2008-02-06
Hi All

This is EXACTLY a problem I have found in other posts. :confused:

I get an error that says,

> Microsoft Office Powerpoint has not been installed for the current user. Please run setup to install the application.
I wish to run MSPowerpoint 2003 on a Xubuntu platform using Wine.

However, I read these posts which suggests I try repairing and/or uninstalling MS Office. I tried all of these and I now I find**[COLOR="Red"] I cannot remove MS Office [/COLOR]**

I'm running Wine 0.4.96 on Xubuntu 7.10. I'm on an old machine, but the idea was to test software compatibility, not to get hardware speed.

Help !! :shock:

---

### Post by hyperair on 2008-02-06
I must say I've never successfully managed to get Ms Office running on Wine. Either way, if you don't have anything else (or important) installed in Wine, just go to your home folder, click view->show hidden files, and delete the .wine folder. Or just rename it.

---

### Post by Whiffle on 2008-02-06
I'd try reinstalling with a newer version of wine (directly off of the winehq repository) after removing your .wine directory.  If it still gives that error, do the repair/reinstall.  It worked perfectly for me.  I'm using wine .9.53

---

### Post by hyperair on 2008-02-06
This link might help (for enabling the WineHQ repository that is): [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

