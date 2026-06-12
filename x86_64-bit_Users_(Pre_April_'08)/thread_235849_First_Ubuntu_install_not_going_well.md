---
title: "First Ubuntu install not going well"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomdkat on 2006-08-13
Hi! I'm starting my very first Ubuntu install on an AMD Athlon 64 based system and it's not going well *at all*.  :(

The boot CD boots fine and it loads fine but at 640x480 resolution, which isn't that big of a deal except the installer must expect a higher resolution since I can't access any of the "Ok" or other buttons.  :(

So, I can specify the installation language of "English" and I must use the "Tab" key to press the "Ok" or "Next" (since I can't see it) button.  Then, on the timezone window I can choose my timezone location from the menu but can't use tab or anything else to press the "Ok" or "Next" or whatever button. 

That's where I'm stuck.  :(

The motherboard has an integrated ATI XPRESS 200 video adapter.  I was able to boot an EliveCD that used the Vesa X driver to get 1280x1024 screen resolution but I can't get Ubuntu to use any resolution other than 640x480.

Help!!!!!!!!!!!!!!!!!!!!!!

Peace...

---

### Post by Kilz on 2006-08-13
> **tomdkat said:**
> Hi! I'm starting my very first Ubuntu install on an AMD Athlon 64 based system and it's not going well *at all*.  :(

The boot CD boots fine and it loads fine but at 640x480 resolution, which isn't that big of a deal except the installer must expect a higher resolution since I can't access any of the "Ok" or other buttons.  :(

So, I can specify the installation language of "English" and I must use the "Tab" key to press the "Ok" or "Next" (since I can't see it) button.  Then, on the timezone window I can choose my timezone location from the menu but can't use tab or anything else to press the "Ok" or "Next" or whatever button. 

That's where I'm stuck.  :(

The motherboard has an integrated ATI XPRESS 200 video adapter.  I was able to boot an EliveCD that used the Vesa X driver to get 1280x1024 screen resolution but I can't get Ubuntu to use any resolution other than 640x480.

Help!!!!!!!!!!!!!!!!!!!!!!

Peace...

I recommend using the Alternate install CD. It doesnt have the fancy graphics, and the screen resolution wont matter. After install you can follow [this ATI howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually") or use a install script like the one in my signature. As a fellow ATI express 200 owner let me recommend staying away from the 8.25.18 drivers presently in the repositories like the plague. Install the 8.27.10 drivers from ATI.

---

### Post by tomdkat on 2006-08-13
Thanks for the tip!  I'll give the alternate CD image a try.  :)

Peace...

---

### Post by tomdkat on 2006-08-14
> **Kilz said:**
> I recommend using the Alternate install CD.Thanks!  Worked well.  :)

> After install you can follow [this ATI howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually") or use a install script like the one in my signature. As a fellow ATI express 200 owner let me recommend staying away from the 8.25.18 drivers presently in the repositories like the plague. Install the 8.27.10 drivers from ATI.Ok, I tried using the script in your sig and got this:

```
Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up module-assistant (0.10.2) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
./ATI: line 4: unexpected EOF while looking for matching ``'
./ATI: line 32: syntax error: unexpected end of file
tom@linux:~/Desktop/ATI$

```Any ideas?

Peace...

---

### Post by Kilz on 2006-08-14
Looks like i backspaced one to many when editing the line below it, sorry, fixed and uploaded a new version.

---

### Post by tomdkat on 2006-08-14
Thanks man, that worked!  I'm now running @ 1280x1024!  Thanks!

I was *this* close to giving up on running 64-bit Linux natively on my Athlon 64 based system but now that I've got my resolution, I think I'm set! 

Now, I'm off to learn about the world of Ubuntu.  :D

Peace...

---

### Post by Kilz on 2006-08-14
> **tomdkat said:**
> Thanks man, that worked!  I'm now running @ 1280x1024!  Thanks!

I was *this* close to giving up on running 64-bit Linux natively on my Athlon 64 based system but now that I've got my resolution, I think I'm set! 

Now, I'm off to learn about the world of Ubuntu.  :D

Peace...

Your welcome, if you run into any problems just post back to the forum. :D

---

### Post by tomdkat on 2006-08-14
I do have a quick question:  Why did I have to install this driver to get the desired resolution?

When I booted my EliveCD 0.4 CD, it loaded a Vesa driver and then prompted whether I wanted to use the GPL radeon driver or the flgrx (or the ATI driver) or the Vesa driver.  I chose the GPL radeon driver and it worked fine.  Why wasn't the GPL radeon driver part of Ubuntu's X.org installation?

Peace...

---

### Post by Grey on 2006-08-14
It is a part of Ubuntu's installation.  The problem is that your video card is likely too new to be supported by the ati driver, so you must use the proprietary fglrx driver.

---

### Post by tomdkat on 2006-08-14
> **Grey said:**
> It is a part of Ubuntu's installation.  The problem is that your video card is likely too new to be supported by the ati driver, so you must use the proprietary fglrx driver.Ok, then why was I able to use the radeon driver when I booted the EliveCD?  The [EliveCD](http://www.elivecd.org/) is a Debian-based live CD that features Enlightenment as the window manager.

This isn't a big deal now that I've got the other driver installed.  I'm just trying to understand what's going on.  :)

Peace...

---

### Post by Kilz on 2006-08-14
> **tomdkat said:**
> Ok, then why was I able to use the radeon driver when I booted the EliveCD?  The [EliveCD](http://www.elivecd.org/) is a Debian-based live CD that features Enlightenment as the window manager.

This isn't a big deal now that I've got the other driver installed.  I'm just trying to understand what's going on.  :)

Peace...
Its possible that the driver in the Elive cd is a newer version than the one in Dapper. 
It may also be a question of how free the driver they are using is. Some distro's believe the live cd is a install, they do not install the live cd to a disk so they believe that its ok to use the proprietary driver.
I will admit that some people have problems building and installing the driver. That's why I think some developers install proprietary drivers on a live cd. Its also the reason I created the install script. To make it as easy as possible.
Ubuntu strives to be as free as in freedom as it can. It allows you to install those things Debain calls non free by yourself later if you choose. Since the ATI driver is proprietary this may be the case.

---

### Post by tomdkat on 2006-08-14
Ok, that's cool.  The EliveCD offers options of using the GPL radeon driver, the proprietary ATI driver, or the Vesa driver.

Anywho, I'm up and running now so I'm happy.  :)

Peace...

---

### Post by eadgbe on 2006-08-19
I have the same exact setup, and I found that alternatively if you don't want to download another 600 mb cd you can alt-right click in the installer window, select "move", then move the window around to see everything. It's tedious, but it worked.

---

