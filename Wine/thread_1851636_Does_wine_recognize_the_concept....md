---
title: "Does wine recognize the concept..."
date: 2011-09-28
forum: Wine
---

### Post by Ubunski on 2011-09-28
[FONT=Calibri][SIZE=3]How do I ensure wine is recognizing my 512mbs of video graphics?  (Yes I know only 512) :D If it does not recognize how do I rectify the configuration to do so?[/SIZE][/FONT]

---

### Post by Veikk0 on 2011-09-28
You can define the amount of video memory (and many other things) in the Wine registry.

In short, open up a terminal or press ALT+F2 and run regedit. In regedit go to HKEY_CURRENT_USER -> Software -> Wine -> Direct3D. Look for a value named "VideoMemorySize", if it's not there then create it (right click -> New -> String value -> name it VideoMemorySize). The value of the string will define the amount of video memory that Wine will see in megabytes (so it' 512 if you have 512MB of video memory).

If you want to know more about registry keys you can check out the "Useful Registry Keys" page from the Wine wiki: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

My explanation might have not been correct to the letter because I'm not using Ubuntu at the very moment. So I'll just leave this here too: [http://www.winehq.org/docs/wineusr-guide/using-regedit](http://www.winehq.org/docs/wineusr-guide/using-regedit)

I hope this helped :p

---

### Post by Perfect Storm on 2011-09-28
Moved to wine section.

---

