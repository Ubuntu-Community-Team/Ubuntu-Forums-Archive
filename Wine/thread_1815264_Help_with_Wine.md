---
title: "Help with Wine"
date: 2011-07-31
forum: Wine
---

### Post by mikro 402 on 2011-07-31
I am able to run the Win7 program with wine. When I make changes to the data and save the changes, the changes don't show up when I run the program from Win 7.

Maybe I dont understand  how Wine works...Is it saving the Wine changes to a different area on the drive?

Thanks,

Mikro

---

### Post by Perfect Storm on 2011-07-31
Moved to Wine forum.

---

### Post by stephenhau on 2011-07-31
> **mikro 402 said:**
> I am able to run the Win7 program with wine. When I make changes to the data and save the changes, the changes don't show up when I run the program from Win 7.

Maybe I dont understand  how Wine works...Is it saving the Wine changes to a different area on the drive?

Thanks,

Mikro

Are you dual booting Ubuntu and Win7?
If so, the program in Wine is installed completely separately from the program in Win7. IF the program uses a config or prefs file to store its settings, you should be able to use symlinks to point to the same file. If the program stores its settings in the registry, you're probably out of luck.
That said, I'm quite new to Ubuntu/Wine, so someone with more experience may want to speak up!
It would help if you told us what the Win7 program is.

---

### Post by mikro 402 on 2011-07-31
Yes I am dual booting Win 7.
This is the program :[http://joejaworski.com/aqualog/](http://joejaworski.com/aqualog/)

---

### Post by brian70809 on 2011-07-31
wine has a .wine directory in your home directory..  hit Ctrl-H if you don't see it.. it's a hidden folder..

inside that folder is a drive_c.. this is what your wine/win7 program is storing information unless you point it to your windows7 drive or partition.

---

### Post by mikro 402 on 2011-07-31
> **brian70809 said:**
> wine has a .wine directory in your home directory..  hit Ctrl-H if you don't see it.. it's a hidden folder..

inside that folder is a drive_c.. this is what your wine/win7 program is storing information unless you point it to your windows7 drive or partition.


So how do I point wine to my win7 c drive? I looked at the Configure Wine but didn't really see anything

---

### Post by stephenhau on 2011-08-02
> **mikro 402 said:**
> So how do I point wine to my win7 c drive? I looked at the Configure Wine but didn't really see anything

[Here's a good explanation]("http://ubuntuforums.org/showpost.php?p=2000880&postcount=2"). 
If you want your program's config and data to stay on the Win7 drive:
Using Ubuntu, browse to where the program stores its config and data files. That's usually within the program folder, or in users/(your username)/Application Data/(program name)/…
Identify the config or data files, then right click and choose Make Link.
Move that link to the equivalent  place in Wine, usually /home/(your username)/.wine/drive_c/users/(your username)/Appplication Data/(program name)/

You might have to use your brains to locate where the program stores its config and data, but the principle is the same: create a symlink to make Wine read/write a file that's actually somewhere else.

---

