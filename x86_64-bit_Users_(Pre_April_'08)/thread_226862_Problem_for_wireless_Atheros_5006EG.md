---
title: "Problem for wireless Atheros 5006EG"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bandeng3 on 2006-07-31
Hi,

Anybody have luck installed successfully for wireless Mini PCI card Atheros AR5006EG ? I've tried installed latest madwifi, but still got the message "HAL 13 - hardware revision is not supported". I can't found any 64 bit windows driver to be installed with ndiswrapper.

I'm using Benq Joybook P41, they are using ATI xpress 1100. But everytime I run 3D games in ubuntu 6.06 amd 64, the game is never loaded.I've tried (slune, penguinracer, etc).

---

### Post by Lonthong on 2006-08-05
Hello,
I also have Joybook P41.
As for yr problem with Wlan, I can't help as I have nothing to check its functioning.
However, for yr problem with 3D games, follow [this link]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually") for the fix

---

### Post by krajok on 2006-08-24
How to install driver of Graphics Adaptor ?, I can't use my Radeon Xpress 1150 on BenQ T31

---

### Post by Lonthong on 2006-08-25
> **krajok said:**
> How to install driver of Graphics Adaptor ?, I can't use my Radeon Xpress 1150 on BenQ T31
Pls follow the link that I provided above.
I would suggest method 2 with latest ATI driver.
When I wrote the above reply was still version 8.27.10 & now it has been upgraded o v 8.28.8 which also gave me no problem

Edit.
However, my card is recognized as radeon xpress 200m. see attached screenshot. You will have that ATI control panel after successful installation (applications -- accessories -- ATI control)
[IMG]http://img183.imageshack.us/img183/2412/screenshotha9.png[/IMG]

---

### Post by krajok on 2006-09-03
I still cannot use my Radeon Xpress 1150
The error I got is the same as I got on Live Installation DVD.

**** INALID IO ALLOCATION ****
Requesting Insufficient memory windows!

It detects my Radeon Xpress 1150 as 200M (RS482 5975)

When I first install using Live DVD I have to edit xorg.cfg changig the driver to "vesa" to get it work (with very slow graphics in 1024x768)

Then I try to install fglrx using atp-get, I got the same error, but longer detail in Xorg.0.log showing all supported device for fglrx driver.

Then I try with the newest download from ATI described in [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910) (I can't find the like you told), I can get it compiled and installed, but still get the same error.

Any idea ?

---

### Post by Lonthong on 2006-09-05
Just helped a friend installing Ubuntu 64 bit onto BenQ P41.
Sorry to say but I did not encounter any problem that you mnetioned.
Furthermore, I did not edit xorg.cfg at all.
After that, I installed latest ATI driver as per instuction method2 from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)
and again no problem what so-ever.
X1100 and X1150 is almost identical so it should work for you.
Have you tried another fresh install???

---

### Post by krajok on 2006-09-10
I've tried 1 time of AMD-64 version and another 2 times of i386 version fresh install.

Thanks for the link, my problem is difference.
I got **** INVALID IO ALLOCATION **** which is an Xorg bug.
[https://bugs.freedesktop.org/show_bug.cgi?id=6377](https://bugs.freedesktop.org/show_bug.cgi?id=6377)
I have to fix it with the patch #6377 above

---

### Post by sexypapa on 2007-07-27
Please anybody out there who know this "Re: Problem for wireless Atheros 5006EG" get back to the question?

I too have the same problem, but could not find any answer to resolve it, yet.

any help would be appreciated.

Thanks!

---

