---
title: "Opera on AMD64"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by NullaPax on 2006-08-13
Hi all.

I want to give Opera a try as Firefox seems teribly slow on Ubuntu compared to XP.

There doesn't seem to be a version for 64 though, just Sparc/PowerPC/and i386.

Will the i386 work on a 64 system ? :confused: 

Thanks in advance.

---

### Post by hajk on 2006-08-13
Yes, Opera have a *static* deb-package for i386 that installs/runs fine on AMD64, install it with "dpkg -i --force-architecture ...". Make sure to get the binaries that are statically linked, since otherwise Opera 9 will make calls to the wrong system libraries. I'm not sure, but you may have to install the ia32-libs package as well.

---

### Post by kuja on 2006-08-15
I just did this last night :) You can use the regular i386 deb too if you want to, it'll just take a little work ... If interested in doing it this way see this thread [http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62)

---

### Post by NullaPax on 2006-08-15
Thanks guys - I'm not too good at this kind of thing but if I don't try I wont learn I suppose :-k

---

### Post by BatteryCell on 2006-08-18
Um if by your not too good with this like you need a step by step...
1.)Download the .deb file from the website
2.)In a terminal go to the directory you downloaded it to and run:
```
dpkg -i --force-architecture nameoffile.deb
``` 
where nameoffile.deb is the file that you downloaded.
3)Run opera, by typing into the terminal "opera" (no quotes)
If not than dont worry about it.

---

### Post by BatteryCell on 2006-08-18
Oh and has anyone got flash to work with their opera, mine only works some of the time...

---

### Post by The Caped Crusader on 2007-08-27
having problems too, with firefox 64 and opera (i'm using ubuntu 7'04 amd64bits).

rethorical question: why the hell are we, 64bits cpu users, being left behind when it comes to software architecture? 64bits cpus have been around for more than a while now... why the hell do i need to be fiddling around with lib32 libraries and flash and sh*t just so i can browse some websites?!

damn! :mad:

---

### Post by The Caped Crusader on 2007-08-27
ok, rant finished. carry on.

---

### Post by rickyrockrat on 2007-09-05
Well said. I don't usually like cursing, but somehow it seems appropriate.
:)

---

### Post by Crinos512 on 2007-09-06
As long as you don't mind "Alpha" software there is a 64 bit version of Opera 9.5 (AKA Kesterel) that is pretty sweet.... and [COLOR="Red"]Blazingly Fast[/COLOR].

[http://my.opera.com/desktopteam/blog/2007/09/04/go-and-get-opera-9-5-alpha-3](http://my.opera.com/desktopteam/blog/2007/09/04/go-and-get-opera-9-5-alpha-3)

---

### Post by d4bdn_one on 2007-10-28
But what should I do if i get this message

[http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:) 404 Not Found

from the repositories?

---

### Post by rickyrockrat on 2007-11-05
Do what you always do when you can't find something on a web site, Delete lower directories until you get SOMETHING.
[http://deb.opera.com/opera/dists/](http://deb.opera.com/opera/dists/)

However, I can't seem to find any 64-bit anything on their site now. Stupid company. You'd think they would WANT people to use their SW.

I can see if I can find my download and send it to you.

I googled and found this link: Better get it fast.

[http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/](http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/)

---

### Post by JAwuku on 2007-11-05
The new 9.50 64-bit beta was released last week, can be obtained from:

**_[ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)_**

---

### Post by jpkotta on 2007-11-06
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by RavanH on 2008-05-26
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64]("ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64")

for latest 64bit beta2 release

---

