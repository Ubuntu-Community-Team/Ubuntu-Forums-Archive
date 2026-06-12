---
title: "World of warcraft folder question"
date: 2012-02-29
forum: Wine
---

### Post by naggu on 2012-02-29
Hello All,

I have WoW game copied to external hard disk. Now that my laptop is ubuntu only, how can I play WoW from this folder without downloading again through wine.

:guitar::guitar:

---

### Post by oldrocker99 on 2012-02-29
Hmmm...I've never tried this, but you could cd to the WoW directory, and run 'wine wow.exe (or whatever it's called)'.

---

### Post by cwwilson721 on 2012-03-01
> **oldrocker99 said:**
> Hmmm...I've never tried this, but you could cd to the WoW directory, and run 'wine wow.exe (or whatever it's called)'.
[SIZE="4"]***_[COLOR="Red"]NO!!!![/COLOR]_***[/SIZE]

This is where "I never tried this" will screw you over.

First, create a "fresh" wine folder by running 'winecfg'. This will create a new .wine folder including registry entries and gecko (assuming you never ran it before. If you have, rename your current .wine to something like '.wine-old', then run 'winecfg'). If you do what the previous poster said...Well, good luck unscrewing your wine install.

Next, go to that folder, then drive_c, program files. (Ex: .wine/drive_c/Program Files)

Next, create a shorcut ( or "softlink") to where ever you have WoW actually at (in my case, it's in /dev/sdb1/WoW/World of Warcraft). Using Nautilus, I go to that folder, right click on "World of Warcraft" folder, and "create shortcut". Then I copy that shortcut to the Program Files folder in .wine. (Making sure the shortcut is named "World of Warcraft")

Next, create a new launcher with the correct "address" to your "new" wine directory, with the actual lauch command being
```
env WINEPREFIX="/home/<USER>/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```

The above will launch WoW.exe in opengl mode.

Once you are sure that WoW works, you can rename the .wine folder to something like ".wine-wow", and then edit the launcher to point to the renamed folder:
```
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe"
```

[COLOR="Blue"]NOTE: Change any instance of <USER> above to your username. ALL of the above assumes tyour WoW install is NOT on a NTFS formatted partion. If it is on NTFS, performance will be HORRIBLE. OpenGL is the preferred method of running WoW in wine. If you have an Intel Graphics chip, search this forum for "wow+intel" for tips.[/COLOR]

The "env=WINEPREFIX" command allows you to run wine programs from a place other than the 'standard' .wine folder.

Let me know

---

