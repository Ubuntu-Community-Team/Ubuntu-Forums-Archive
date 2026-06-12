---
title: "Problems with IE"
date: 2008-03-29
forum: Wine
---

### Post by mmarif4u on 2008-03-29
Just recently i install wine and after that i tried to install IE, but  i get error stating that:
> IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install everything at: /home/arif/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXE   mfc42.cab
   0%   SCR56EN.CAB[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/arif/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IE_S*.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/VGX.CAB: No such file or directory
 An error occured when trying to cabextract some files.


I need IE for testing my pages.
I heard about crossover.but not sure how to use.I know its in automatix2.i have installed this.
If i want to install this,mean i have to uninstall wine.
Any guidance will be helpful.

---

### Post by wormser on 2008-03-29
I got it running with this [guide]("http://www.psychocats.net/ubuntu/ies4linux").

---

### Post by p_quarles on 2008-03-29
Moved to the Wine forum. 

If you don't manage to get it working, you might be interested in what I use for testing purposes:
[http://browsershots.org/](http://browsershots.org/)

---

### Post by mmarif4u on 2008-03-29
i follow the guide,and again same error:
> IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/arif/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   DCOM98.EXE   mfc42.cab
   0%   SCR56EN.CAB
  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/arif/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/IE_S*.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: No such file or directory
/home/arif/.ies4linux/downloads/ie6/EN-US/VGX.CAB: No such file or directory
 An error occured when trying to cabextract some files.



---

### Post by Twitch6000 on 2008-03-29
Ok I am sorry but, even if you are a web coder its not your fault people use ie.So if they want to use a crappy browser they will get crappy results.Although if you must take extra time to make it work for ie then you can put windows on vmware or something and test from there.

---

