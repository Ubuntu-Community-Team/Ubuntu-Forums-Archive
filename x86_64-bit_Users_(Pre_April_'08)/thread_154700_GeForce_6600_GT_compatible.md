---
title: "GeForce 6600 GT compatible?"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by MiD-AwE on 2006-04-03
Hi all,
[INDENT]I'm a newb, but I've been using linux Xandros for sometime and I love to cutomize my system, so I've become comfortable messin'.
  
Now, here's my issue. I was running ubuntu breezy64 without any issues for quite a while, but after I upgraded to a GeForce 6600 GT AGP 8x it works up until Gnome starts then the screen garbles. I've even tried the live cd to no availe.
  
I follow instructions well if anyone is willing to help me fix it..?
  
By the way,  I'm dual booting ubuntu & Xandros and the GeForce 6600 GT works fine in Xandros.
  
[/INDENT]Thanks

---

### Post by evilpig on 2006-04-03
Hmm, I have the same graphics card as you and it works fine. Maybe there is another issue. Have you made sure that the default video system in the BIOS is set to AGP?

---

### Post by MiD-AwE on 2006-04-03
Thanks for the reply.
[INDENT]I have all of the settings correct in BIOS. The card works fine for Xandros. 
  
I've tried to re-install ubuntu doing full format and still no luck. I'm completely at a loss since the LIVE CD shows the same problem...:-k
[/INDENT]

---

### Post by johnnymac on 2006-04-03
I have the same card too and no probs.  What you could do is uninstall the NVidia drivers and re-install them.  If you followed most of the how-to's you can just do it through synaptic.

---

### Post by cronholio on 2006-04-04
Or try this: [http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

It helped me.

---

### Post by ShakingSpirit on 2006-04-05
I had this exact same problem with that card :) The open source 'nv' driver doesn't appear to like it in some cases! :)

To fix, when Ubuntu boots and the screen fills with crap, press CTRL+ALT+F1 to get to a shell. Log in, then  type
```
sudo pico /etc/X11/xorg.conf
```
Scroll down the file until you reach your graphics card section; it should look something like this:
> Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:5:0:0"
EndSection

Alter this so that instead of saying *Driver "nv"* it says *Driver "vesa"*, so you should have something that looks a bit like this:
> Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "vesa"
        BusID           "PCI:5:0:0"
EndSection

Press CTRL+X to quit, making sure you press Y to save :) 
Press CTRL+ALT+F7 to return to your garbled screen, then CTRL+ALT+Backspace
If all goes to plan, Xorg will now be using the 'vesa' driver, and you should see a nice ubuntu login screen :)
After you've finished setting up your system, you should probably either follow the link in the post above, or another one of the guides to installing the 'official' nVidia driver, as the 'vesa' driver wont give very good performance in games, or other graphically-demanding software :)

---

### Post by MiD-AwE on 2006-05-29
Thanks for the replies. I had to complicated the matter by trying to run twinview so now I'm restling with that one as well.

I followed the advice here and got it up long enough for me to try the twinview settings and now I can't even reach the login screen. All I get now is a warning message telling me to try again once I have a proper configuration. Maybe it's a gnome thing. I love gnome, KDE is cool but gnome feels more like LiteStep on winblows. Anyway, I know that others have successfully set up twinview with the 6600gt so It can be done ;)

Does anyone know what is the easiest way to replace the xorg.conf file back to the default? Should I just do a fresh install of Ubuntu? (Is the dapper beta mature enough to try?)

Thanks

---

### Post by hesee on 2006-06-03
[QUOTE=ShakingSpirit]I had this exact same problem with that card :) The open source 'nv' driver doesn't appear to like it in some cases! :)

To fix, when Ubuntu boots and the screen fills with crap, press CTRL+ALT+F1 to get to a shell. Log in, then  type
```
sudo pico /etc/X11/xorg.conf
```
Scroll down the file until you reach your graphics card section; it should look something like this:


Alter this so that instead of saying *Driver "nv"* it says *Driver "vesa"*, so you should have something that looks a bit like this:


Press CTRL+X to quit, making sure you press Y to save :) 
Press CTRL+ALT+F7 to return to your garbled screen, then CTRL+ALT+Backspace
If all goes to plan, Xorg will now be using the 'vesa' driver, and you should see a nice ubuntu login screen :)
After you've finished setting up your system, you should probably either follow the link in the post above, or another one of the guides to installing the 'official' nVidia driver, as the 'vesa' driver wont give very good performance in games, or other graphically-demanding software :)[/QUOTE]

Hey, I have this same card and problems with it in dapper. I run xserver-xorg cofiguration, but didn't know what to put for BusId. The default was
BusID "PCI:1:0:0", but now xorg cannot find any card. How do I know what is the BusId. I have Epox EP8k9a7i motherboard and card is in agp slot(naturally). It was probably correct first(before reconfiguration), because i saw some strange lines on the screen, but I forgot to take backup of xorg.conf. 
Can anyone help?


Edit: Wrong forum (Breezy). Well. in case some someone reads this, i got my screen working. Just installed nvidia-glx drivers, and modified xorg.conf to use "nvidia" instead of "nv". BusID was actually "PCI:1:0:0".

---

### Post by MiD-AwE on 2006-07-15
Just an update:

Everything was fixed with the dapper install. If you are having the same issue I had, I strongly suggest installing Dapper. It fixed my issue and now I'm not only running Twinview on the 66oogt but I have xgl compiz running with Xgames Doom 3 is better than on winXP. I run highmode 1600x1200 and get nice frame rates. Very playable. Hope to see you in the Dapper forums.

---

