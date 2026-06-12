---
title: "Digikam 0.9 packages anyone?"
date: 2006-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2006-12-20
Is there any good boy here that he is able to compile and provide us with digikam and digikamimageplugins 0.9 packages for kubuntu edgy amd64?  ;) 

I tried to compile the source but I have too many compilation problems/errors :( :(

---

### Post by xopher on 2006-12-21
Please post your errors and we'll guide you through it ;) This way YOU could make the packages for US, and contribute to the community.

---

### Post by kleeman on 2006-12-21
This one looks hard. I suggest you wait until it gets into feisty and then try 
dpkg-buildpackage -rfakeroot
rc1 is there already.

Edit: Looks like libexiv2 is the main problem. digikam 0.9 needs version 0.12 but only 0.10 is in edgy

---

### Post by CyberAngel on 2006-12-21
> **kleeman said:**
> This one looks hard. I suggest you wait until it gets into feisty and then try 
dpkg-buildpackage -rfakeroot
rc1 is there already.

Edit: Looks like libexiv2 is the main problem. digikam 0.9 needs version 0.12 but only 0.10 is in edgy


Libexiv2 0.12 is the easiest one to compile :P
It compiled with no errors....

I am installing now a clean kubuntu 64bit vmware machine to try the compilation again because my main system has so many extra repositories that I have some conflicts (A package x is needed but it is not going to be installed etc) when I try to install a few packages.

I Will post my problems after I start the digikam 0.9 compilation :)

Wish me luck :KS


....And by the way where did you found the rc1 packages?

---

### Post by kleeman on 2006-12-21
Actually it is rc2:

[http://packages.ubuntu.com/feisty/graphics/digikam](http://packages.ubuntu.com/feisty/graphics/digikam)

---

### Post by beefcurry on 2006-12-21
is there a difference between that 0.9 rc2 and the new 0.9 version? Being release candidate I assume it has the same things.

---

### Post by kleeman on 2006-12-21
Sometimes there is no difference sometimes there is. You need to look at the changelog.

---

### Post by xopher on 2006-12-21
Or, you could use prevu to backport the package yourself. Search the forums for prevu and you'll see what I mean. :)

```
sudo prevu packagename
``` ;)

---

### Post by Aldrik on 2006-12-22
I posted [instructions on how I compiled it over on the kubuntu forums]("http://kubuntuforums.net/forums/index.php?topic=12047.0"). ;)

---

### Post by kleeman on 2006-12-22
> **Aldrik said:**
> I posted [instructions on how I compiled it over on the kubuntu forums]("http://kubuntuforums.net/forums/index.php?topic=12047.0"). ;)
Thanks that worked I built some debs for amd64. Checkinstall I'm afraid but better than nothing ;-)
 [http://www.yourfilelink.com/get.php?fid=244604](http://www.yourfilelink.com/get.php?fid=244604)
[http://www.yourfilelink.com/get.php?fid=244606](http://www.yourfilelink.com/get.php?fid=244606)

install with 

sudo dpkg -i digikamimageplugins_1:0.9.0-1_amd64.deb digikam_1:0.9.0-1_amd64.deb

---

### Post by ariel on 2006-12-23
Deleted

---

### Post by CyberAngel on 2006-12-31
> **kleeman said:**
> Thanks that worked I built some debs for amd64. Checkinstall I'm afraid but better than nothing ;-)
 [http://www.yourfilelink.com/get.php?fid=244604](http://www.yourfilelink.com/get.php?fid=244604)
[http://www.yourfilelink.com/get.php?fid=244606](http://www.yourfilelink.com/get.php?fid=244606)

install with 

sudo dpkg -i digikamimageplugins_1:0.9.0-1_amd64.deb digikam_1:0.9.0-1_amd64.deb

Works for me ;)
Very nice :)

Thank you!

---

### Post by Didjit on 2006-12-31
Is there a deb package for the latest Exiv2 somewhere?

Didjit

---

### Post by kleeman on 2006-12-31
Here you go (there are two debs):

[http://www.yourfilelink.com/get.php?fid=250261](http://www.yourfilelink.com/get.php?fid=250261)
[http://www.yourfilelink.com/get.php?fid=250262](http://www.yourfilelink.com/get.php?fid=250262)

---

### Post by beefcurry on 2007-01-02
Anyone have them for 32bit?

---

### Post by Didjit on 2007-01-21
So, I've really been liking digiKam. Finaly something with Picasa features and more.

Anway, question; After I load pics from my camera, Gthumb comes up as the default displayer of pics. Anyone know how I can change this to digiKam?

Tx

Didjit

---

### Post by kleeman on 2007-01-21
System---->Preferences------>Removable Drives and Media

There is a tab for cameras that allows you to change this

---

### Post by Didjit on 2007-01-21
Perfect. Thanks!
Didjit

---

### Post by jkroto on 2007-02-13
> **kleeman said:**
> Thanks that worked I built some debs for amd64. Checkinstall I'm afraid but better than nothing ;-)
 [http://www.yourfilelink.com/get.php?fid=244604](http://www.yourfilelink.com/get.php?fid=244604)
[http://www.yourfilelink.com/get.php?fid=244606](http://www.yourfilelink.com/get.php?fid=244606)

install with 

sudo dpkg -i digikamimageplugins_1:0.9.0-1_amd64.deb digikam_1:0.9.0-1_amd64.deb

The digikam package worked great, thanks.  Can't download the plugins however, any chance of putting it up again? (link for file 244606 says "can't find file")

Thanks again.

---

### Post by CyberAngel on 2007-03-10
I have compiled and created using checkinstall the digikam and digikamimageplugins 0.9.1 packages ;)
Also I have compiled kipi-plugins 0.1.3.

I hope that someone else would be interested too so I have uploaded the files :)

Use the links below to download:

[digikam 0.9.1]("http://www.yourfilelink.com/get.php?fid=296372")
[digikamimageplugins 0.9.1]("http://www.yourfilelink.com/get.php?fid=296367")
[libkexiv2 0.1.1]("http://www.yourfilelink.com/get.php?fid=296369")
[libkexif1 0.2.5]("http://www.yourfilelink.com/get.php?fid=296378")
[exiv2 0.12]("http://www.yourfilelink.com/get.php?fid=296382")
[libexiv2 0.12]("http://www.yourfilelink.com/get.php?fid=296375")
[libexiv2-dev 0.12]("http://www.yourfilelink.com/get.php?fid=296376")
[kipi-plugins 0.1.3]("http://www.yourfilelink.com/get.php?fid=296374")
[libkipi 0.1.5]("http://www.yourfilelink.com/get.php?fid=296370")

---

### Post by beefcurry on 2007-03-10
nice :D

---

### Post by kleeman on 2007-03-10
Here are some amd64 debs with all dependencies flagged.

[http://www.math.nyu.edu/faculty/kleeman/amd64/digikam/](http://www.math.nyu.edu/faculty/kleeman/amd64/digikam/)

---

