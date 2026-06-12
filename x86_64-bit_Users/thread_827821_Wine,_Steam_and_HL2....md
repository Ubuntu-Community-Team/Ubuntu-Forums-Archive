---
title: "Wine, Steam and HL2..."
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by Dark_Fire on 2008-06-13
Hey guys,

Ok, so after having allot of trouble with wine-doors, I decided to start from scratch. I uninstalled wine and wine-doors, and deleted ./.wine folder.

Now its time to get everything working again. Im busy downloading the MS Core fonts again and tahoma. I also installed wine gecko. I coppied my brothers steam folder to C:/Programme Files/Steam (he runs windows)

Should I install anything else? Should I set any settings? Any thing I should do/know about?

Its Wine1rc4, Ubuntu 8.04 64...

Thanks

---

### Post by wineman on 2008-06-13
dude
sup

the core things that you need for your setup should be installed now, but heres some help on what used to make Steam-related stuff work:
1) install wine (you done that already, so skip this part)
2) google something called MSTTCOREFONTS-OFFLINE. it'll save you cash later on. Install that and continue.
3) Steam and HL/HL2/CS/Source/watever else only uses like three fonts: tahoma, verdana, and arial. A shortcut here is download the fonts off a XP distro, or go googling for them.
4) Install Wine's GECKO package. This is the HTML rendering. 
(NOTE: don't look in the repositories for this; it's a waste of time. you only get libgecko-cil or some rubbish like that.. Google GRE-WIN32-INSTALL.exe. And mshtml - thats it. for Gecko.)
5) Now install your steam however you like. You should be sorted from there, provided that Gecko decides to work. 
5b) if Gecko is still giving you trouble, download it OR
download the wine_gecko.cab file by xterming this:

wget [http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab](http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab) && cabextract wine_gecko-0.1.0.cab
you then :
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/

then, do some regediting:
**HKEY_Current_User/Software/Wine/MSHTML** and create a new key labelled "0.1.0" 
In the new "0.1.0" key, create a new string value labelled "GeckoPath" and set the string value to **"c:\windows\gecko\0.1.0\wine_gecko" **

Add these registry keys too:
**HKEY_LOCAL_MACHINE\Software\Microsoft\Internet Explorer**
W2kVersion*[Useful to make application believe that you have Internet Explorer installed (if you set it manually, you might need some IE provided dlls). Set them to "6.0.2800.1106" for IE6SP1.]*
Build*[Same as above. Set it to "62800.1106" for IE6SP1.]*
---
**HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Add Paths\IXplorer.exe**
Add the STRING called "Path" with the value "C:\Program Files\Internet Explorer". *(Leave out the "")*

6) You should be sorted to run Steam from there onward. 

NOTES:
The only other thing to do is to install your graphicas drivers, and you are sorted.

any probs, shout.
l8r bro:guitar:

---

### Post by wineman on 2008-06-13
o ya and heres some other help: 
[http://gaming.gwos.org/doku.php/wine:winestuff]("http://gaming.gwos.org/doku.php/wine:winestuff")
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam")
[http://thepemberton.com/posts/archives/13]("http://thepemberton.com/posts/archives/13")

kwl l8r bro

---

### Post by Dark_Fire on 2008-06-13
> Add these registry keys too:
HKEY_LOCAL_MACHINE\Software\Microsoft\Internet Explorer
W2kVersion[Useful to make application believe that you have Internet Explorer installed (if you set it manually, you might need some IE provided dlls). Set them to "6.0.2800.1106" for IE6SP1.]
Build[Same as above. Set it to "62800.1106" for IE6SP1.]

Im not sure what you mean by that one? should I add a string value "W2kVersion" with the value "6.0.2800.1106"?

---

