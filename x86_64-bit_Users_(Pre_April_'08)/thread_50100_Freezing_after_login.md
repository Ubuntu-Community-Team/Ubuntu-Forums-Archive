---
title: "Freezing after login"
date: 2005-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsaumer on 2005-07-19
Hello, this is my first attempt of installing ubuntu 64 bit on my new Compaq Presario laptop with a AMD 3200+ 64 bit processor. 

Everything went fine, except for when I try and log in.

When I log in, the small splash screen comes up and then freezes.

I have no clue how to fix this at the moment, any help would be greatly appreciated!

Thanks,
jsaumer

---

### Post by moises on 2005-07-19
Hi jsaumer
I had a similar problem with mine (not a laptop)
I just booted with the recovery option and the next time I tried, it worked fine
Hope it helps

---

### Post by jsaumer on 2005-07-19
I just gave that a try.

I booted into recovery mode, rebooted, then in the default mode.  I logged in and the same thing happened, froze on the small splash screen after the music.

Thanks for the reply though.

---

### Post by Jet2k5 on 2005-07-19
Tell us some more info about your system .. as far as what the video card is and stuff.

---

### Post by filterban on 2005-07-19
Hard freezes are usually a result of a video card configuration issue.

There is a very similar problem that occurs with some ATI video cards.  This can be fixed by switching to the "vesa" video driver instead of "ati" in /etc/X11/xorg.conf.

Try searching these forums for "ati" and "freeze", assuming you have an ATI card.

---

### Post by joekr on 2005-07-19
If you've recently upgraded to kernel 2.6.11 in Synaptic, you'll have to add *inotify* to your kernel arguments.

Without further info there's not much else help we can contribute... we need **details** ;)

---

### Post by jsaumer on 2005-07-19
Fresh install off of a 5.04 AMD 64 disk

Fresh Partition

Comp Stats:
AMD Turion 64 Mobile
ATI Radeon XPRESS 200M

If you need any more, just ask


I just tried setting these kernal flags in GRUB and it still froze in the same spot:
acpi=off noapic pci=biosirq vga=normal apm=off ide=nodma

---

### Post by DancingSun on 2005-07-19
My hunch is that it's your graphics chip or motherboard.  I'm not 100% sure, but there are many posts that experienced similar problems, and they all use ATI Radeon XPRESS.

Check and see if your hardware is compatible with Ubuntu.  I remember there's a wiki page on it.

---

### Post by filterban on 2005-07-19
[QUOTE=jsaumer]Fresh install off of a 5.04 AMD 64 disk

Fresh Partition

Comp Stats:
AMD Turion 64 Mobile
ATI Radeon XPRESS 200M

If you need any more, just ask


I just tried setting these kernal flags in GRUB and it still froze in the same spot:
acpi=off noapic pci=biosirq vga=normal apm=off ide=nodma[/QUOTE]


See this [post](http://ubuntuforums.org/showthread.php?t=46056&highlight=RADEON+XPRESS)  about switching to the VESA driver.  I'm 95% sure it's the open source ATI driver.

---

### Post by jsaumer on 2005-07-19
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "ati"
        BusID          "PCI:1:5:0"
        Option         "NoAccel"               "true"
EndSection
```

Is what fixed it!!!

THanks for your help everyone.

With my 200 series chip, it is a MUST to have the Option "NoAccel" "true"

---

### Post by filterban on 2005-07-19
[QUOTE=jsaumer]```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "ati"
        BusID          "PCI:1:5:0"
        Option         "NoAccel"               "true"
EndSection
```

Is what fixed it!!!

THanks for your help everyone.

With my 200 series chip, it is a MUST to have the Option "NoAccel" "true"[/QUOTE]


Are you sure?  This may affect performance adversely.  Try using the following instead (switch to vesa driver, enable acceleration):

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "vesa"
        BusID          "PCI:1:5:0"
#        Option         "NoAccel"               "true"
EndSection
```

---

### Post by HankB on 2005-07-27
Can I hijack this thread and ask in general how satisfied you are with the laptop?

I'm thinking about the HP L2000 which is also Turion based and uses the same chip set (ATI RADEON XPRESS 200M.) As I understand it, this is not just the video chip but is the system chip set. Is that what you have found? Does it include 10/100 Ethernet? Have you had a chance th check out other things like sound, USB, 1394? Oh, I'd be interested in suspend and hibernate too.

I'm psyched about Lance and think it would be neat to have this special edition laptop, and that's aside form the fact that it is AMD64 based. But I've not heard a lot of good stuff about ATI chip sets and it won't be worth the trouble if it won't run Linux.

thanks,
hank

---

### Post by gtpanger on 2005-07-27
I have a L2005cl and I like it alot :) 

things that work:

bluetooth
sound
ethernet
video (somewhat, if you want native rez then use the "ati" and "noaccel")
touchpad
usb
modem (finds it, havent dialed out)
burning dvd/cd

things that dont work:

wifi (ndiswrapper to fix, havent done yet)
volume/mute buttons

things i havent tested:

firewire (should work)
suspend/hibernate
6way card reader

issues:

200m driver problems
dma problem (stuttery when drive reads) .11 kernel fixes
laggy/sluggish (double clock speed problem) .11 kernel fixes

i've tried SuSe and get vesa only, same with Fedora Core 4. although, this laptop is faaaast in fedora, it has the newer kernel. so i'm 100% sure that this laptop will be as fast in ubuntu once it gets supported more.

so far i havent heard anything bad about these new ati chipsets, problem is the are soooooo new that there isnt any real support for em yet. i wouldnt be scared off from it for that reason. :) its lightyears better than my last laptop with the uber crappy S3 UniChome video that is still bound to "vesa"

go lance!

---

### Post by HankB on 2005-07-28
[QUOTE=gtpanger]I have a L2005cl and I like it alot :) 
things i havent tested:

firewire (should work)
suspend/hibernate
6way card reader
[/quote]
Thanks for the info.

I'd be real interested in hearing about the suspend/hibernate when you give it a try. I  can live w/out hibernate but really need some sort of suspend.
> 
go lance!Amen! Too bad he's gone now, but I understand the desire to spend time with his family. And it's cool that he goes out on top.

---

