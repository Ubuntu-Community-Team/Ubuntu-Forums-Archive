---
title: "Ubuntu 14.04 64 bit - wine 1.6 - 32bit prefix v 64 bit prefix"
date: 2014-09-02
forum: Wine
---

### Post by xigen on 2014-09-02
I think (*presume) that I installed office 12 (Office 2007 home /student edition) under a 64 bit prefix when I needed to install office 2007 under a 32 bit prefix.    

Office 2007 starts - unfortunately, Word 2007 is not working with .docx  documents.

1) How do I remove my previous installation of Office 2007?

2) how **exactly** do I set the wine prefix to be 32 bit rather than 64 bit?  


```
Location of Office 12 on my system
/home/meow/.wine/drive_c/Program Files (x86)/Microsoft Office
```


Unfortunately I found  the directions at WineHQ quite confusing. 

> 7.2. How do I create a 32 bit wineprefix on a 64 bit system?

At present there are some significant bugs that prevent many 32 bit applications from working in a 64 bit wineprefix. To work around this, you can create a new 32 bit wineprefix using the WINEARCH environment variable. In a terminal, type:

WINEARCH=win32 WINEPREFIX=/path/to/wineprefix winecfg 

(use the actual path to the wineprefix), then install your 32 bit application(s) to that wineprefix.

Do not manually create the directory before running that command; Wine must create it. WINEARCH only needs to be set when creating the wineprefix, and the architecture of an existing wineprefix cannot be changed. 


Also, I would like to avoid using Winetricks and Playon Linux...  This way I can ask follow up questions on the wineHQ site.
--

---

### Post by mastablasta on 2014-09-03
instructions are quite clear. if you can't see the path to your wineprefix (it's in your home folder) you need to turn on hiden files and folders in your file manager. in nautilus it used to be shortcut Crtl+H to see those

then you just put that path to wineprefix as is instructed above.

also avoiding tools that make life easier just so you can post follow up questions on wine forums doesn't make much sense to me. but it's your decision.
however if you plan to go hard core then be prepared to use some commands. ;)

btw install via playonlinux works great. Word/Excel and powerpoint are working oK.

edit or do it like this:
**WINEARCH=win32 WINEPREFIX=/home/meow/.office2007 winecfg**

---

### Post by xigen on 2014-09-03
OK.. I see said the blind man.

1) install wine (1.6 for me)

2) get msoffice disk - put in drive - open the setup.exe file with wine.  Install Office 2007

3) Look at .wine file.  get path.  Change Winearch from 64 bit (the default on my 14.04 64 system) to an explicit 32 bit prefix
>  WINEARCH=win32 WINEPREFIX=/home/meow/.office2007 winecfg

3.5) run word/excel/etc and see how it works.

woo!

---

### Post by mastablasta on 2014-09-04
> 1) install wine (1.6 for me)
ok
.
first create the winearch. what is not clear here?:
> 
(use the actual path to the wineprefix), then install your 32 bit application(s) to that wineprefix.

 **Do not manually create the directory before running that command**; Wine must create it.

and if you do this:
WINEARCH=win32 WINEPREFIX=/home/meow/.office2007 winecfg 

then you should install into ./office2007

if you want to follow wine instructions then this is done immediately after wine install and you then install to ./wine

>  2) get msoffice disk - put in drive - open the setup.exe file with wine.  Install Office 2007

 3) Look at .wine file.  get path.  Change Winearch from 64 bit (the default on my 14.04 64 system) to an explicit 32 bit prefix

                             WINEARCH=win32 WINEPREFIX=/home/meow/.office2007 winecfg                     


instructions on wine are quite clear: ***_Do not manually_* create the directory *_before _*running that command**

---

