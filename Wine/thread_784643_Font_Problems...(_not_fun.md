---
title: "Font Problems...:( not fun"
date: 2008-05-06
forum: Wine
---

### Post by googleadam on 2008-05-06
ok well im new to Ubuntu (about a week now) and LOVE IT!!! :popcorn: ive had my fair share of problems but have fixed them, except this one :(

I installed Wine...for use maybe in the future...and so i go to winecfg to change a few settings and boom, the text is just HUGE like HUGE HUGE....so of course i went searching around and tried god knows everything, nothing...

Here is what it looks like

(ill only give the link so as no one with dialup will suffer :) )
[http://i113.photobucket.com/albums/n211/googleadam/Screenshot-Wineconfiguration.png](http://i113.photobucket.com/albums/n211/googleadam/Screenshot-Wineconfiguration.png)

but anyways, ive tried the system.reg trick, nothing, i cant find it.  Im lost and if I cant get it fixed, im just removing perm.

But help would be great, if u can spare some time :D thnx ahead of time

---

### Post by cogadh on 2008-05-06
Did you try using your text editor's built-in search function to find the "[System\\CurrentControlSet..." entry in the system.reg file? The entry has to be there, it is part of the default Wine registry:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
Yours may not look exactly like mine, but at the very least "[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]" has to be there. If you search for that, then change the "LogPixels" line to match what I put above, it will fix your font size issue.

---

### Post by googleadam on 2008-05-06
> **cogadh said:**
> Did you try using your text editor's built-in search function to find the "[System\\CurrentControlSet..." entry in the system.reg file? The entry has to be there, it is part of the default Wine registry:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
Yours may not look exactly like mine, but at the very least "[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]" has to be there. If you search for that, then change the "LogPixels" line to match what I put above, it will fix your font size issue.

ok thnx for the help, im not sure what I am supposed to open (sorry im a nooby) but am I opening ~/.wine/system.reg?

like I do thank you and understand the code u gave me and where to change it but i dont no what file i need to open directly. Sorry for being a nag

---

### Post by cogadh on 2008-05-06
Yes, that is the correct file to open. However, the .wine directory is a hidden directory in your home folder, so you will have to show hidden files in order to find it.

---

### Post by googleadam on 2008-05-06
> **cogadh said:**
> Yes, that is the correct file to open. However, the .wine directory is a hidden directory in your home folder, so you will have to show hidden files in order to find it.

ahh yes, thats why i could never find it! but i wanna thank you, it works now!  u really are a :KS lol well thanks a ton...now to install star scraft :cool: haha

again, thanks a lot

---

