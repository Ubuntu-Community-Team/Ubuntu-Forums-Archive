---
title: "Can AMD 64 x2 Turion mobile technology tl-50 run any Linux distro?"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by qwertzqwertz on 2008-11-05
I'm running a laptop with
AMD 64 x2 Turion mobile technology tl-50
2GB Ram

I'm new to Linux and thought I'd try to dual boot with my WinXP Pro.  I have tried installing Ubuntu 8.1, Mint 5, Xubuntu 8.1, and lastly OpenSUSE 11.0... all 64bit versions.  I keep downloading and they keep failing.

Usually the install would just give me a black screen and then my system would hang. But the last ones I tried (Xubuntu and OpenSUSE) failed and gave me the message "Aperature beyond 4GB. Ignoring".

Could somebody help me out?  I'd really like to get it running on my machine! =o

---

### Post by Carrat Wellness on 2008-11-05
Hi qwertz,

Could you be a bit more specific on your laptop specs? Does it run a live system of any of the distros you mention properly?

I used to have an MSI Megabook laptop with a TL-50 cpu and 2Gb of RAM, running Hardy without trouble (after some initial searching to get past black screens). The acpi is a problem in those models, selecting the acpi=off did the initial trick for me.

---

### Post by soxs on 2008-11-05
I had a laptop with that CPU and it worked, though it depends extremly on your biso, if it is sensible to run linux. Some laptop bioses are so buggy, acpi can't be run and therefor the "unplugged" time decreses to about 20-30mins (like mine did)

---

### Post by qwertzqwertz on 2008-11-05
Here's my laptop specs:
- Tsinghua Tongfang (chinese laptop brand)
- 1.61GHz AMD Turion(tm) 64 X2 Mobile Technology TL-50
- 2GB RAM

I tried Fedora 9 Live CD on my laptop this morning and it gave me the Graphical menu but when I selected to install it gave me the "Aperature beyond 4GB. Ignoring." error again. :-(

Being totally new to Linux... what does this mean exactly?
> "The acpi is a problem in those models, selecting the acpi=off did the initial trick for me."

---

### Post by soxs on 2008-11-05
Nothing, just get used to, it's caused by messy bios whcih does not enable IOMMU (correct my if this shortcut is wrong) and leads finally you to loose 64 MB of ram (which doesn't matter at all, as this only happens byond 3.x GB)

---

### Post by qwertzqwertz on 2008-11-05
I wish it were only that I would lose 64MB of RAM.  When I get the error "Aperature beyond 4GB. Ignoring." my system hangs and I can't continue with the Linux install.

I've never been able to get Linux running on my machine.

---

### Post by soxs on 2008-11-05
> **qwertzqwertz said:**
> I wish it were only that I would lose 64MB of RAM.  When I get the error "Aperature beyond 4GB. Ignoring." my system hangs and I can't continue with the Linux install.

I've never been able to get Linux running on my machine.

Oh, that's bad. Unfortunatly I don't know what to do.
Btw. adding keyowrds is good, but you must seperate them by commas ( , )

---

### Post by randiroo76073 on 2008-11-05
Have you gone into your BIOS and disabled ACPI as was mentioned by Soxs, this seems to help alot of laptop users

---

### Post by sdudley on 2008-11-05
I have an older HP/Compaq nx6325 with the AMS Turion 64x2 chipset and 4GB. Works fine with Fedora 8 & 9 32 or 64 bit. I get the aperature error with each version and it doesn't appear to affect the performance. At the moment I am running Ubuntu 8.10 and for the first time I have Compiz running without any crazy X11 downgrade or hacking the Radeon driver. Incidentally I did encounter a black screen and apparent kernel crash when using the Ubuntu alternate installer on both the 32 and 64 bit versions. I wanted full disk encryption which seems to only be available on the alternate installation version of Ubuntu 8.10 and 8.04 whereas in Fedora 9, it's an option on the normal install process.

---

### Post by qwertzqwertz on 2008-11-05
> **randiroo76073 said:**
> Have you gone into your BIOS and disabled ACPI as was mentioned by Soxs, this seems to help alot of laptop users

I'm running a Tsinghua Tongfang laptop and I have "Phoenix Trusted Core" BIOS... and I can't find any settings for Advanced Configuration and Power Interface (ACPI).  

Is there any way to get around that?

---

### Post by soxs on 2008-11-06
Yes, when you put in your cd at boot time, ubuntu will pop it with the default menu. There is an option to add aditional kernel parameters (though it is NOT named like that, must be hotkeyed from F1-F9). Apend a space and afterwards: ```
acpi=off apm=off
```

---

### Post by qwertzqwertz on 2008-11-08
Awesome!  Thanks SOXS!  
I got Mint 5 working by adding the "acpi=off" to the boot string.  What does the "apm=off" do?  I did it sometimes and sometimes not but didn't notice a difference.

Thanks again! :-)

---

### Post by Martje_001 on 2008-11-08
> **qwertzqwertz said:**
> Awesome!  Thanks SOXS!  
I got Mint 5 working by adding the "acpi=off" to the boot string.  What does the "apm=off" do?  I did it sometimes and sometimes not but didn't notice a difference.

Thanks again! :-)
You can also thank him by clicking on the 'medal' in the lower-right corner of his post ;)

APM stands for [Advanced Power Management](http://en.wikipedia.org/wiki/Advanced_Power_Management). If you don't notice any difference you better put it on, it helps to increase your battery life.

---

### Post by soxs on 2008-11-08
> **Martje_001 said:**
> You can also thank him by clicking on the 'medal' in the lower-right corner of his post ;)

APM stands for [Advanced Power Management]("http://en.wikipedia.org/wiki/Advanced_Power_Management"). If you don't notice any difference you better put it on, it helps to increase your battery life.
Do it like Marje_001 said ;-)

---

### Post by PatrickVogeli on 2008-11-08
you should better look if you find a better solution... I think acpi=off makes a laptop quite unusable, I wouldn't run linux on a laptop without acpi, it's a nonsense

---

### Post by soxs on 2008-11-08
> **PatrickVogeli said:**
> you should better look if you find a better solution... I think acpi=off makes a laptop quite unusable, I wouldn't run linux on a laptop without acpi, it's a nonsense
There are other options aswell to make it work, but they seem to be somewhat more wacky, so brtuforce is the best to secure a smooth install process. Afterwards we can play around with some other options which helped other ubuntu useres aswell...

---

### Post by Artemis3 on 2008-11-08
Please specify the video card (very important), and the motherboard chipset if possible.

acpi=off is a good start, but hopefully not the solution. Its like using a sledge hammer to kill a flea.

I once found a laptop which only worked with acpi=off, until it occurred me to try and specify a framebuffer mode (eg: vga=771) instead, and it worked...

With acpi=off, for example, you might find that if you plug an usb pendrive, the icon never appears, and/or is never mounted at all and you have to mount it manually.

To answer the original question, there are no problems with the processor, but video card, motherboard chipset/bios and other peripherals can be troublesome if the manufacturer did not open the specs.

---

