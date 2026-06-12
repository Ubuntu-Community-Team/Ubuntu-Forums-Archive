---
title: "AMD Turion 64 + ATI Radeon Xpress 1100 + ubuntu 64-bit"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by techdude26@gmail.com on 2008-09-03
Hi All!!!

This is my first post on ubuntu forums. I have Ubuntu 7.10 - the Gutsy Gibbon installed on my AMD 64 laptop. Iam looking for ATI Radeon Xpress 1100 driver. I searched for the proprietary driver but I think there is no proprietary driver available. ATI provides driver for "ATI Radeon Xpress 1250", you can search for this on - [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")

I want to ask whether this driver will work for me or not, as it belongs to same series "Xpress" and it is next to 1100. If not, where can I find any open source driver.

The machine is currently working on generic driver (I suppose). I have a doubt whether this impact the boot speed of OS ? Because it takes 2.5 - 3.5 min for login window to appear. With Windows XP the boot time comes to 20-25 secs.

Its very painful that although I have the latest hardware but could not experience the visual effects and performance of Ubuntu.

Vivek

---

### Post by Bucky Ball on 2008-09-03
You have the ATI video card? ATI a bit problematic with Ubuntu but that may change with Intrepid Ibis. :)

Having said this, there are ways of making it happen I believe. You may have better luck with Hardy 8.04 and that card.

[http://www2.ati.com/drivers/linux/catalyst_84_linux.html](http://www2.ati.com/drivers/linux/catalyst_84_linux.html)

The user on this thread seemed to have some success also:

[http://ubuntuforums.org/showthread.php?p=3663742](http://ubuntuforums.org/showthread.php?p=3663742)

Good luck and welcome to the forums. :)

---

### Post by bpl07 on 2008-09-03
The proprietary driver works with the 1100 series, it's just not in that 3 frame search thing you were talking about.  The release notes list it, as posted above.  This may or may not work in gutsy, but it describes the manual and automatic ways of installing the proprietary driver:

[Ubuntu Hardy ATI Install Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by Bucky Ball on 2008-09-03
Hey, bpl07, I am clicking on your link but it doesn't seem to be working. Am keen to have a look. :)

---

### Post by techdude26@gmail.com on 2008-09-08
Now something wrong happend, I don't know what but the screen resolution is now set to 640x480. This is the only resolution available in "Screen and Graphics". 

I don't know how to resolve this !!!. 

If ATI is such a problematic with Ubuntu why don't we have some step wise article or document that walk through the procedure to install ATI driver on Ubuntu? Why these guys are not writing any driver for ATI? This is so irritating.

---

### Post by cjazz on 2008-09-08
I have a laptop with hardware you described, and the proprietary 3D driver installed at System>Administration>Hardware Drivers has always worked well for me.

---

### Post by Bucky Ball on 2008-09-08
[QUOTE=techdude26@gmail.com]Why these guys are not writing any driver for ATI? This is so irritating.[/QUOTE]

Totally agreed, if you mean the guys at ATI! I suggest you email your hardware manufacturer and ask them that question. Have you been here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Lonthong on 2008-09-09
I also have a similar laptop (Turion X2 + X1100) and never have any problem at all (from Dapper upto Hardy - always 64bit version).
Before I just followed the [link given above]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

With Hardy, I just did like cjazz & everything works well including compiz fusion.

---

### Post by techdude26@gmail.com on 2008-09-11
Ok now..... since I was not getting any proper solution for the resolution issue and Iam not able to find any article/post for same.... So I reinstalled the OS. 

Iam posting here what happened from initial installation till this installation.

[LIST=1]
[*]Installed Ubuntu 7.10-64 bit.
[*]Installed security updates from [http://security.ubuntu.com](http://security.ubuntu.com) by uncommenting enteries related to security in /etc/apt/sources.lst...it took painful 8 hrs to download these
[*]Messed with graphic driver setting in "Screen and Graphics", changed it to ATI Radeon (something like that). 
[*]Lost the 1280x800 resolution when restarted and the only resolution now available is 640x400.
[*]Posted this thread but couldn't get any solution. :mad:
[*]Finally resinstalled the ubuntu.... the updates that downloaded previously are all lost and now I have to again download it ](*,)

[*]Instead of installing security updates, enabled the restricted drivers. Ubuntu install them.
[*]Tried enabling desktop effects... got error message "Composite extension not available". :(
[*]Changed /etc/X11/xorg.conf for "composite" "0" to "composite" "1"... restarted the X system...
[*]Still not able to enable the desktop effects... got error message "Desktop effects could not be enabled" :( .
[*]Then installed xserver-xgl..... restarted the machine and ........finally got the desktop effect enabled.
[/LIST]

If it was Windows ... it would be a matter of few clicks. Got the answer why windows is so popular and widely used OS.

---

### Post by RavanH on 2008-09-30
> **techdude26@gmail.com said:**
> Ok now..... since I was not getting any proper solution for the resolution issue and Iam not able to find any article/post for same....

I have got Desktop Effects working with AIGLX (so without XGL, remove it or look in these forums on how to make it NOT run on login) following these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29)

I use a Radeon Xpress 200M. (See my sig to compare other system specs)

Hope this helps you out :)

---

### Post by cleopete on 2008-11-13
> **techdude26@gmail.com said:**
> Ok now..... since I was not getting any proper solution for the resolution issue and Iam not able to find any article/post for same.... So I reinstalled the OS. 

Iam posting here what happened from initial installation till this installation.

[LIST=1]
[*]Installed Ubuntu 7.10-64 bit.
[*]Installed security updates from [http://security.ubuntu.com](http://security.ubuntu.com) by uncommenting enteries related to security in /etc/apt/sources.lst...it took painful 8 hrs to download these
[*]Messed with graphic driver setting in "Screen and Graphics", changed it to ATI Radeon (something like that). 
[*]Lost the 1280x800 resolution when restarted and the only resolution now available is 640x400.
[*]Posted this thread but couldn't get any solution. :mad:
[*]Finally resinstalled the ubuntu.... the updates that downloaded previously are all lost and now I have to again download it ](*,)

[*]Instead of installing security updates, enabled the restricted drivers. Ubuntu install them.
[*]Tried enabling desktop effects... got error message "Composite extension not available". :(
[*]Changed /etc/X11/xorg.conf for "composite" "0" to "composite" "1"... restarted the X system...
[*]Still not able to enable the desktop effects... got error message "Desktop effects could not be enabled" :( .
[*]Then installed xserver-xgl..... restarted the machine and ........finally got the desktop effect enabled.
[/LIST]

If it was Windows ... it would be a matter of few clicks. Got the answer why windows is so popular and widely used OS.

You should never post in frustration, though I truly do feel your pain.

However, as someone who provides windows based tech support to Idaho idgits, I can assure you, Windows does thouroughly suck too.  I spent three days trying to cobble a driver together in order to "downgrade" a Vista Toshiba to XP.  The laptop was only sold at Walmart and Toshiba had no listing for it on their website.  It had a Radeon adapter (I forget the number, I think it was an XL1350) which according to ATI/AMD, did not exist.

Oh what fun...

That being said, I've been having similar issues with Intrepid. The stock drivers worked pretty well (better than the proprietary set), except I had some unsightly triangles in Desktop Cube when 3D Windows was enabled.  The latest Compiz update seemed to fix that, but after attempting to run an external monitor, I've been reduced to 1024X768, which would be fine if this wasn't a wide screen.  I can't seem to do anything about it.

I've always used Alberto Milone's Envyng, but he hasn't released a version for Intrepid.  So now I'm stuck.  

OK this was pretty long-winded for a bump. My bad.

---

### Post by RavanH on 2008-11-17
I have run into a similar issue with my Radeon 200M graphics:

With the **radeon** driver I can *either* have one screen with 1280x800 and Desktop Effects (compiz) *or* a second screen with different size 1024x768 along with my laptops widescreen but suddenly NO desktop effects :(

With the proprietary **fglrx** driver I can only use my laptop wide screen because as soon as I try to enable the second screen of different size in ATI Config Control Panel, all goes weird on my screen and I can only wait until the previous settings are automatically reverted after x seconds. I suspect that if the second screen had the same dimensions, it would work...

I have also noticed that the performance of the **fglrx** driver is suddenly since my upgrade to Intrepid, **EXTREMELY SLOW** ! I get bizar low FPS values in **glxgears** (I know it is not a benchmark tool) but as soon as I revert to the **radeon** driver the FPS values are around 450.000 FPS. This is much better than the fglrx driver under Intrepid but about half of what I got with the fglrx driver under Hardy :(

I am no speed junk at all, but somehow I feel a bit 'restricted' with these limitations ... At the moment the radeon driver is for me the best way because I can get at least some reasonable performance with Desktop Effects while being limited to one screen. 

Or does anyone know a way around this? Thanks for any suggestion :)
--ravan

---

### Post by Kougaiji on 2008-11-21
> **RavanH said:**
> I have run into a similar issue with my Radeon 200M graphics:

With the **radeon** driver I can *either* have one screen with 1280x800 and Desktop Effects (compiz) *or* a second screen with different size 1024x768 along with my laptops widescreen but suddenly NO desktop effects :(

With the proprietary **fglrx** driver I can only use my laptop wide screen because as soon as I try to enable the second screen of different size in ATI Config Control Panel, all goes weird on my screen and I can only wait until the previous settings are automatically reverted after x seconds. I suspect that if the second screen had the same dimensions, it would work...

I have also noticed that the performance of the **fglrx** driver is suddenly since my upgrade to Intrepid, **EXTREMELY SLOW** ! I get bizar low FPS values in **glxgears** (I know it is not a benchmark tool) but as soon as I revert to the **radeon** driver the FPS values are around 450.000 FPS. This is much better than the fglrx driver under Intrepid but about half of what I got with the fglrx driver under Hardy :(

I am no speed junk at all, but somehow I feel a bit 'restricted' with these limitations ... At the moment the radeon driver is for me the best way because I can get at least some reasonable performance with Desktop Effects while being limited to one screen. 

Or does anyone know a way around this? Thanks for any suggestion :)
--ravan

I have the same speed issue with Ubuntu's provided restricted driver.  It's very noticeably slower than it was on Hardy (I used envyng for the install on hardy though). Hey do you still get desktop effects with the radeon driver? I'm afraid of using the driver on amd's site due to the sheer amount of bad luck I've had in the past.

---

### Post by RavanH on 2008-11-24
> **Kougaiji said:**
> I have the same speed issue with Ubuntu's provided restricted driver.  It's very noticeably slower than it was on Hardy (I used envyng for the install on hardy though). Hey do you still get desktop effects with the radeon driver? I'm afraid of using the driver on amd's site due to the sheer amount of bad luck I've had in the past.

Yes with the open source radeon driver I have desktop effects. But only when using ONE monitor, my laptop screen. As soon as I try to use a second monitor (of different size) Desktop Effects get switched off :cry:

---

### Post by Schok on 2009-01-01
hey i have the same specs and its working for me with the proprietary driver. im even using compiz-fusion n things are okay-ish..only some glitches when i turn on the "3d windows" and some slowness due to too many effects on. So im only using some of the effects which is fine with me.

cheers.

---

### Post by Schok on 2009-01-08
cleopete:
> unsightly triangles in Desktop Cube when 3D Windows was enabled. The latest Compiz update seemed to fix that

How did u update compiz? I'm still having those triangles when 3d windows are enabled..

---

