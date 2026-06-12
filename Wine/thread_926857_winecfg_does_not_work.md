---
title: "winecfg does not work"
date: 2008-09-22
forum: Wine
---

### Post by girishven on 2008-09-22
I installed the latest wine version 1.1.4.

After installing Office 2003 to run under wine, I am unable to launch winecfg.

everytime I type winecfg i get

wine: chdir to /home/~/.wine" wine POWERPNT.exe
: No such file or directory

I tried doing a complete removal from the synaptic manager and did a reinstall. Still get the same error.

Looks like I have no way for making a clean wine install and something is screwed up.

Can someone please help me to find out what's going on ?

thanks.
Girishven

---

### Post by Sugi on 2008-09-22
I was getting this same message with my self compiled wine.  I can't really tell you how I fixed it.  But I guess it was typo on my half.

Try:
env WINEPREFIX="/home/USR/.wine/ winecfg

NOTE:
USR = is your user name
.wine = is default location of .wine

It may help or it may not.

Have you happen to use a command lately "env WINEDEBUG=+all"?  I have noticed I have had some problems after using that command, but I can't say for sure.

Sugi

---

### Post by binbash on 2008-09-22
I was getting same error at 1.1.3 1.1.4 and after upgrading 1.1.5 it just gone

---

### Post by girishven on 2008-09-23
> **Sugi said:**
> I was getting this same message with my self compiled wine.  I can't really tell you how I fixed it.  But I guess it was typo on my half.

Try:
env WINEPREFIX="/home/USR/.wine/ winecfg

NOTE:
USR = is your user name
.wine = is default location of .wine

It may help or it may not.

Have you happen to use a command lately "env WINEDEBUG=+all"?  I have noticed I have had some problems after using that command, but I can't say for sure.

Sugi

I must thank you for pointing me in the right direction. Tried WINEDEBUG and found that my WINEPREFIX was screwed up. I set the WINEPREFIX right and winecfg works !.

---

