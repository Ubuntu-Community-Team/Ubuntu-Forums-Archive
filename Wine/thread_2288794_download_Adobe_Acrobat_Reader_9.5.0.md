---
title: "download Adobe Acrobat Reader 9.5.0"
date: 2015-07-29
forum: Wine
---

### Post by dreamquartz on 2015-07-29
Looking for the windows version to run under Wine.
Does anyone know where to find it?

Thanks in advance,

DQ

---

### Post by Toz on 2015-07-30
[ftp://ftp.adobe.com/pub/adobe/reader/win/9.x/9.5.0/en_US/]("ftp://ftp.adobe.com/pub/adobe/reader/win/9.x/9.5.0/en_US/")

Note: Looks like you need [Wine 1.7]("https://www.winehq.org/download/ubuntu") for it to work. Here are the instructions that I used on a 64-bit 15.04 xubuntu install:

[LIST=1]
[*]Install wine 1.7 from the PPA
[*]Create and use a new wine prefix, specify a 32-bit wine install and install acrobat reader:
```
WINEPREFIX=~/.wineAD WINEARCH=win32 wine ~/Downloads/AdbeRdr950_en_US.exe
```
[*]Start it via the icon on the desktop or manually via:
```
WINEPREFIX=~/.wineAD WINEARCH=win32 wine ~/.wineAD/drive_c/Program\ Files/Adobe/Reader\ 9.0/Reader/AcroRd32.exe
```
[/LIST]

---

