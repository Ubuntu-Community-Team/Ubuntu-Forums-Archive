---
title: "Live CD - Screen Hangs"
date: 2007-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by SaddisticTwist on 2007-02-26
There's so many places to post topics, not so sure where. So this is x64 related and I'm guessing it goes here. (Sorry if I'm wrong)

I've downloaded and burned the x64 live CD. And when I run it, it loads fine. Except, when it starts. After decompressing the kernel, the Ubuntu loading screen is meant to show? (correct). 

*I'm not a first time Ubuntu user, but I'm also not an advance user.*

Now, the problem is, when the Ubuntu loading screen comes up, it comes up in a gray color and the loading bar is just a bunch of verticle lines, spaced out in gray color too. And basically it does nothing. What do I do?

System:
Kingston High performance ram 2x 1GB
MotherBoard - MSI K9NGM
HDD - Seagate 320GB (Sata)
CPU - AMD64x2 3800++ (2.0GHz)
Monitor LG Flatron 19" WS

Thanks for the support in advance.

---

### Post by John.Michael.Kane on 2007-02-26
does it finish loading or does it stall at the black and white splash screen?

Note: Checking on your board spec's shows it should be fully supported.

Have you tried re-burning the disk?

Also the Black and white splash screen is talked about here [http://ubuntuforums.org/showthread.php?t=304673&highlight=gray](http://ubuntuforums.org/showthread.php?t=304673&highlight=gray) Though i doubt this has any issue on you booting.

---

### Post by SaddisticTwist on 2007-02-26
Thanks for the link!

Well I've just read through, so what there saying is that their system still loads. Its just for the exception of the funny loading screen.

I'll try waiting abit longer. I'll get back to you if it loads or does not load. 

cheers.

---

### Post by SaddisticTwist on 2007-02-26
So it did crash. I waited. Nothing happened. But thankfully I got it fixed.

[I][CENTER]
BTW: Thanks SD-Plissken[/CENTER][/I]

> **Kateikyoushi said:**
> Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

If still a no go I would recommend the alternate install cd, which is text based so should work with your VGA, then you can install the driver after you finish the system installation.

This list is a big help (which I used), but for now just follow the steps below.
Press F6 and type the following:

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw noapic nolapic pci=irqroute pci=noacpi acpi=off pci=acpi fb=false irqpoll

Which should hopefully load, in text-mode. And finally get to the GUI! YAY! :)

---

### Post by John.Michael.Kane on 2007-02-26
Glad you found a suitable fix. Should there be any other issue please post.

---

### Post by SaddisticTwist on 2007-02-28
Aiyo!

Well, I made a post in general help about customizing a live CD. So that, when I did install it onto my system it would be perfect. But the reply was to install it 1st.

So I go ahead and install the Live CD - to make my custom CD.

Ofcourse, it had to hang just like the description above. So how? :confused:

Edit - fixed

---

### Post by John.Michael.Kane on 2007-02-28
If you want to try your hand making livecd coustom. Then have look at this [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

