---
title: "Wine Language"
date: 2007-11-28
forum: Wine
---

### Post by jontybuntu on 2007-11-28
I am new to Linux and I have a problem I can't figure out.  I installed [Interlinear Scripture Analyzer]("http://http://www.scripture4all.org/") in Wine and afterwards, my wine interface is in Greek:

[IMG]http://i2.photobucket.com/albums/y15/jrsmith/winegreek.jpg[/IMG]

ISA would not run in Wine, so I uninstalled it, but Wine is still in Greek.  I tried uninstalling and reinstalling Wine, but that did not help.  I found [another thread]("http://ubuntuforums.org/showthread.php?t=516492") that seemed to address my problem.  I tried to follow the instructions and run the following command:
```

sudo apt-get --purge wine
```

but when I do so, this happens:
```

E: Invalid operation wine
```

Does anyone have any idea how I can get Wine set back to English?

Thanks in advance!

---

### Post by cogadh on 2007-11-28
The command you should have used is this:
```
sudo apt-get remove --purge wine
```
You missed the "remove" part.

However, doing that and reinstalling Wine won't work, since the language setting is stored in your "fake Windows" directory and uninstalling Wine does not remove that. If that application was the only thing you installed in Wine, then all you have to do to reset the language is delete the .wine directory in your home folder, then run "winecfg" to create a new one.

I believe there may also be a way to change the language through a registry edit, but I do not know for certain what that key may be. There is a "Locale" setting in the registry, found in "HKEY_LOCAL_MACHINE/System/CurrentControlSet/Control/ContentIndex/Language/Neutral", but any changes I make to it don't seem to affect anything. It could be that I am not using the correct setting to see any difference (I just plugged in random numbers to see what would happen). On my system, that "Locale" DWORD is normally set to 0, so if yours is something different, you might try changing it to 0 to see if it fixes your issue. After making the change and exiting regedit, you might need to run "wineprefixcreate" to update the change and see any difference.

---

### Post by jontybuntu on 2007-11-28
Thanks for the advice.  I opened the registry and guess what?  It was in Greek, also!  I tried to feel my way through the registry and I think I found the key you mentioned, but the value was already 0.  I only have a couple of other programs running in wine and I can reinistall them with no trouble.  I think my best option is probably to delete the .wine directory like you said and start from scratch.

---

### Post by jontybuntu on 2007-11-28
That worked.  Thanks again!

---

### Post by Sammi on 2007-11-28
> **jontybuntu said:**
> I opened the registry and guess what?  It was in Greek, also!:lolflag:

---

### Post by cogadh on 2007-11-28
Just a little unsolicited advice; if you have a functional .wine directory with programs already installed and running fine, you might want to create a separate "test" Wine directory to run initial installs on, so that anything you do doesn't screw up the stuff that already works. After you work the bugs out, you can then install the app in your normal Wine directory and wipe out the test directory to clean it up for your next install. To create a test .wine directory:
```
winprefixcreate --prefix .winetest
```
You can actually make it any name you like, I just used .winetest as an example. To use the new .winetest directory:
```
env WINEPREFIX=~/.winetest wine executable.exe
```

---

### Post by jontybuntu on 2007-11-28
Great advice, thanks!

---

