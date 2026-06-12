---
title: "Trying to run Ubuntu on a 64 bit platform. What's going on?"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tzustrategy on 2006-11-23
Hello everyone,

I've been trying to get Ubuntu to run on my brothers Athlon 64 powered tower for some time now. I've been doing this to test and see if Ubuntu works with AMD 64 bit chips, and unfortunatly I've had little luck getting it to work. 

Now I've found a laptop I'd like to get, and I'd like to run Ubuntu  on it. 

Link to product: [http://www.newegg.com/Product/Product.asp?Item=N82E16834115255](http://www.newegg.com/Product/Product.asp?Item=N82E16834115255)

As I haven't been able to run Ubuntu successfully on my brothers 64 bit powered machine, I'm hesitant to buy a new laptop if I can't run Ubuntu. I know there have been problems with 64 bit users on Ubuntu, but I've heard that you can run 32bit Ubuntu natively.

Which brings me to my questions:

1) For my brothers machine, it goes to a blank screen. I can hit control+alt+F4 and it brings up a console, but I'm not too sure what I should do from there. Does this seem like a processor or GPU problem?

2) How does one go about running Ubuntu as a 32bit system when you have the 64bit chip? Which distro should I get? i386 or AMD 64?

Thank you all so very much for your time!

---

### Post by Joe_CoT on 2006-11-23
1) This probably has very little to do with running 64 bit. Does it go to a blank screen during install, or after you've installed it and started it? If it's during install, use the alternative installation cd. it'll be a text based install, but it'll work. After that, it's it's going to a blank screen, go to the console. Then from the console, type:
```
sudo nano -w /etc/X11/xorg.conf
```

That's going to be your xwindow configuration. Here we're looking for two sections; the device section, and the monitor section. Your device section will look something like this:
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection
```
Keep in mind, by something like this, i mean it'll say 'Section "Device"', it'll have some identifier, and it'll have some driver. Change the driver line to:

```

Driver      "vesa"

```

That driver will work with 99.9% of video cards out there. Now, to the Monitor section. Find the section that looks like this:
```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
EndSection
```
Once again, the only certainly is that the section will be called monitor. Now we need to add the horizontal and vertical sync lines for your brother's monitor -- you'll need to either check the manual, or do some googling to find out your brother's monitor's specs. So let's say his horizontal sync is 50-70, and his vertical sync / vertical refresh rate is 30-150. Then add these lines to that section:
```

HorizSync 50-70
VertRefresh 30-150

```

Now save the file (ctrl + o). At this point, all we need to do is stop X again. run this (note: it'll be kdm instead if you're running kubuntu):

```
sudo /etc/init.d/gdm/stop
```
then
```
sudo /etc/init.d/gdm/start
```

It should come up without issue. If it does, you can try changing the video card driver back to what it was. If that doesn't work, you might want to try a different driver (ie Radeon instead of ATI, etc), or installing the binary driver for it.

2) A 32 bit version will run just fine on a 64 bit chip --- you'll just only be using 32 bits 8) Generally, the only problem with running 64 bit is all the 32 bit stuff out there. See [this thread](http://ubuntuforums.org/showthread.php?t=191205) for more info on getting 32 bit programs to run in 64 bit ubuntu.

As for your laptop, there's a [Laptop Testing](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5004WLMi) article for it, but it's a bit out of date. My expectation is that more things would work in versions newer than Breezy, but that's just a hunch. Looks alright. In general, check the [Laptop Testing Team](https://wiki.ubuntu.com/LaptopTestingTeam) for info like this.

---

### Post by Tzustrategy on 2006-11-23
Thanks a million! :-D 

It goes to a blank screen after the opening screen loads up.

So for an AMD64 chip, I should still use the AMD64 .iso's, right? Or would an i386 .iso work? 

Thanks! :cool:

---

### Post by Joe_CoT on 2006-11-23
Either would work. If you want to install 32 bit, use the i386 one; if you want to install 64 bit, use the AMD64 one. Neither should make a difference with the blank screen issue; odds are it's either the driver or the horizontal/vertical sync, as a explained before.

---

