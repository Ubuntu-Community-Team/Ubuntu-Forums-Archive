---
title: "wmv problem"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thomas,Bakker on 2006-06-06
I just installed some codecs whit easy ubuntu ([http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html))
and it works perfectly.
Only i noticed one strange thing while playing wmv files.
some wmv files work whitch is great but other's i only hear the
sound and i dont see the movie itself.
Anyone has an idea why this is happening and what to do about it?

my system:
Acer Aspire 5020
AMD Turion 64 ML-34 processor
Ati Mobility Radeon X700 PCI Express 128MB VRAM
512MB DDR Ram

installed dapper drake 64bits, if you need more info plz ask

---

### Post by localzuk on 2006-06-06
It is due to the nature of wmv files. There are currently no 64 bit codecs for wmv9 so these ones will not play correctly.

For more information, take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Thomas,Bakker on 2006-06-06
[QUOTE=localzuk]It is due to the nature of wmv files. There are currently no 64 bit codecs for wmv9 so these ones will not play correctly.

For more information, take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]

Thanx for the quick reply mate ill take a look at the link.

[EDIT]
Is it an idea to convert the "bad" wmv files to let say mpeg or avi? if so how could i do that?
[EDIT]

---

### Post by Schapie123 on 2006-06-06
you can play them by installing the mplayer32. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=188974](http://www.ubuntuforums.org/showthread.php?t=188974)

---

### Post by RAOF on 2006-06-06
[QUOTE=Thomas,Bakker]...
Is it an idea to convert the "bad" wmv files to let say mpeg or avi? if so how could i do that?
...[/QUOTE]
To do that you would need to decode the existing wmv, then encode to mpeg/whatever.  But since there's no 64bit wmv decoder...

---

