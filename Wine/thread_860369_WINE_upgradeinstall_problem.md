---
title: "WINE upgrade/install problem"
date: 2008-07-15
forum: Wine
---

### Post by Techrocket9 on 2008-07-15
[FONT=Times New Roman][SIZE=2]I wanted to upgrade to the latest version of WINE (1.1). I was on RC4 or so. The upgrade manager could not do it due to some kind of error. So I uninstalled WINE and now I cannot reinstall it. In synaptic I get: ```
wine:
 Depends: winbind but it is not going to be installed

``` If I go to install winbind, I get:```
 winbind:
  Depends: samba-common (=3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.3 is to be installed
```If I go to install samba, I get the same message (with samba in the place of winbind). If I want to uninstall samba-common with the intent to reinstall it, I am told that Ubuntu-Desktop depends upon it. I believe that uninstalling that is a bad idea. Any and all help is appreciated.

Edit: When I select force version, it says that it needs to uninstall Ubuntu-desktop and smb client.
[/SIZE][/FONT]

---

### Post by YokoZar on 2008-07-15
> **Techrocket9 said:**
> [FONT=Times New Roman][SIZE=2]I wanted to upgrade to the latest version of WINE (1.1). I was on RC4 or so. The upgrade manager could not do it due to some kind of error. So I uninstalled WINE and now I cannot reinstall it. In synaptic I get: ```
wine:
 Depends: winbind but it is not going to be installed

``` If I go to install winbind, I get:```
 winbind:
  Depends: samba-common (=3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.3 is to be installed
```If I go to install samba, I get the same message (with samba in the place of winbind). If I want to uninstall samba-common with the intent to reinstall it, I am told that Ubuntu-Desktop depends upon it. I believe that uninstalling that is a bad idea. Any and all help is appreciated.

Edit: When I select force version, it says that it needs to uninstall Ubuntu-desktop and smb client.
[/SIZE][/FONT]Latest Hardy winbind is Version: 3.0.28a-1ubuntu4.4, and should be matched with samba... are you sure you have all the repositories enabled?  (main, -security, and -updates)?

---

### Post by Techrocket9 on 2008-07-16
Thanks. YokoZar.I had those enabled, but, when I checked, they had been unchecked. I suspect the culprit was easyubuntu, which destroyed my 3rd party sources setting. I assume it did the same thing to that tab. Anyway, now WINE is installed and running perfectly. (for WINE) Thanks!
[IMG]http://smileys.smileycentral.com/cat/11/11_9_10.gif[/IMG]

---

### Post by alecz20 on 2008-08-04
I have an issue with WINE being version 0.9.57 for a very long time.

Even if last time it updated automatically from .56 to .57, now even if I install the .deb for 1.0 it says "Same version installed" and 

```

wine --version

```

shows as 0.9.57

What am I doing wrong?

---

### Post by Vorian Grey on 2008-08-04
I believe Wine has been updated in Ubuntu to 1.0. Just run reload in Synaptic and then wine should be available to upgrade. If you still don't see it, go into Synaptic and check more options in your repositories. 

You could also try adding the Wine repository to your sources list.

---

### Post by alecz20 on 2008-08-04
Synaptic says 

"Version: 1.0.0~winehq0~ubuntu~7.10-2"

I tried Updating, Upgrading from .deb, remove and install from deb and from synaptic.

Wine still says it's 0.9.57
Is this a bug in WINE maybe?

---

