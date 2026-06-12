---
title: "winecfg issue."
date: 2008-04-27
forum: Wine
---

### Post by systembreak on 2008-04-27
hi all!

I set the defaultsetting in the wine to make my games drive in an emulated desktop. And when I opened the winecfg again it showed up like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67603&stc=1&d=1209332600[/IMG]   

Do anyone know how to fix this back to normal?

-systembreak

---

### Post by schtufbox on 2008-04-27
That looks like you adjusted the dpi slider right up. 
in your .wine folder you need to open system.reg file in a text editor like gedit ( MAKE SURE YOU MAKE A COPY OF THE FILE FIRST JUST IN CASE )
find the part below either by a search within the text editor or scrolling til you find it :
```

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]

```

under that there should be a "LogPixels"  entry, edit it so it is the same as below:

```

[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]
"LogPixels"=dword:00000060

```

You want to make sure that the log pixels entry is as above, this will reset wine to use 96dpi for fonts.
Then save and run winecfg to check it worked, if it didn't, then I'm out of ideas :D

The "00000060" is actualy in hex - 0x60 = 96.

---

### Post by schtufbox on 2008-04-27
Just to be sure I went ahead and made my fonts ridiculously huge by messing with the slider too, then did the edit above and it fixed the problem. So it 'should' work for you too.
Again, make sure you backup system.reg first just to be safe.

---

### Post by systembreak on 2008-04-27
hi thanks! 

it worked, but there is something I have to sure of. Is this good or bad:

linux@linux-desktop:~$ winecfg
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file

(It opens the winecfg and I can do everything as normal)

-systembreak

---

### Post by systembreak on 2008-04-27
Well actually it caused a bug.

Every time I configure anything in winecfg and I apply the new configuration it don't save the configuration, because there's no change as there should be and when opening the winecfg again, it does not show the configuration either? 

(Happy to have made the backup =))

-systembreak

---

### Post by cogadh on 2008-04-27
What did you use to edit the registry file and how did you save it? It sounds like you didn't use a plain text editor and whatever you did use added some formatting that screwed up the registry files.

---

### Post by schtufbox on 2008-04-27
Yeah that's what I was going to suggest. Which editor did you use to edit the .reg file?
I used gedit with mine and it worked.
If not that I would probably use nano.

So glad I suggested a backup!

---

### Post by systembreak on 2008-04-27
Ups.... did a mistake. Well thanks guys! Its working properly now.

---

### Post by zap_xlib on 2011-12-25
It worked!. wow!.

Thanks for the solution!.

---

