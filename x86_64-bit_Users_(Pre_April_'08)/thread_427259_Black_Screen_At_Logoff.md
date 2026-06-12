---
title: "Black Screen At Logoff"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by xflatlinex on 2007-04-29
I am running Feisty64 on an AMD64 and when I logoff to try to switch to a different user, I just get a black screen and have to manually hold down the power button to power off the PC.  I searched the forums and could not find anything solid to help me, does anyone have any suggestions?

---

### Post by kuja on 2007-04-29
The only thing I've ever seen cause that was a graphics driver issue, particularly, fglrx.

---

### Post by xflatlinex on 2007-04-29
> **kuja said:**
> The only thing I've ever seen cause that was a graphics driver issue, particularly, fglrx.

Do you have any suggestions as to how to fix it?  I have a ATI RADEON XPRESS 1150 in a Gateway MT6456.
Thanks in advance.

---

### Post by Tanker Bob on 2007-04-29
My screen also goes blank on shutdown, but the computer isn't locked up.  If I wait a while, the screen comes back on the restart.  The same thing happens after GRUB takes my menu choice--blank screen until the login screen comes up.  Not sure why it does this, but it's only a minor annoyance.  

I'm using an NVIDIA 8800 GTS, so I don't think it's related to your card manufacturer.

If you haven't already, you might just try to wait a couple of minutes and see if the screen comes back.  I was resetting my PC every restart for a while until I decided to wait and see what happened.  The login screen takes longer to appear than I would expect, but it does appear.

---

### Post by xflatlinex on 2007-04-29
> **Tanker Bob said:**
> My screen also goes blank on shutdown, but the computer isn't locked up.  If I wait a while, the screen comes back on the restart.  The same thing happens after GRUB takes my menu choice--blank screen until the login screen comes up.  Not sure why it does this, but it's only a minor annoyance.  

I'm using an NVIDIA 8800 GTS, so I don't think it's related to your card manufacturer.

If you haven't already, you might just try to wait a couple of minutes and see if the screen comes back.  I was resetting my PC every restart for a while until I decided to wait and see what happened.  The login screen takes longer to appear than I would expect, but it does appear.

Thanks,  I will try that next logoff, maybe I am just not being patient enough.

---

### Post by Tanker Bob on 2007-04-29
Patience was the key for me.  I find that it seems longer when there's nothing to look at.  Gotta have visual entertainment.  :)

---

### Post by jkwarras on 2007-04-30
Note: Use it at yor own risk.

Asuming that you uses fglrx driver, you could try this (I was having the same problem and now it's solved):

1) sudo gedit /boot/grub/menu.lst
2) add this at the end of the first OS choice: vga=791
3) reboot

This should solve shutdown and switch user hangs. At least it did for me.

---

### Post by xflatlinex on 2007-05-05
> **jkwarras said:**
> Note: Use it at yor own risk.

Asuming that you uses fglrx driver, you could try this (I was having the same problem and now it's solved):

1) sudo gedit /boot/grub/menu.lst
2) add this at the end of the first OS choice: vga=791
3) reboot

This should solve shutdown and switch user hangs. At least it did for me.

Here is what I have in my menu.lst file.  Please be more specific as to where to place it.  I have more but I only pasted the important part I think you are referring to.
Thank you

///START MENU.LST FILE

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7a9cd742-679f-4123-a5fc-047aa111a438 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
vga=791

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7a9cd742-679f-4123-a5fc-047aa111a438 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault

---

### Post by aashay on 2007-05-05
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=7a9cd742-679f-4123-a5fc-047aa111a438 ro quiet splash** vga=791**
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by xflatlinex on 2007-05-05
> **aashay said:**
> title Ubuntu, kernel 2.6.20-15-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=7a9cd742-679f-4123-a5fc-047aa111a438 ro quiet splash** vga=791**
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

hmm, didnt seem to work. I added the VGA=791 and rebooted, still no luck. Anyone else here have any other suggestions?
Thanks

---

### Post by marsmissionaries on 2007-05-05
If you're using the FGLRX driver, that is the problem. The fglrx driver, it pains me to say it: sucks.

I have the EXACT same issue, my solution: don't log out. 

There is no fix for this issue currently, and there are many people having the problem (a google search for fglrx log out problems will show you this). nVidia users who report similar problems are having completely different problems so their solutions will not work for fglrx users. The bug is in the fglrx driver. reverting to the open source ATI driver fixes the problem but disables direct rendering.

So you have to pick one: Good graphics, no log out, or bad graphics and a fully functional system.

---

### Post by hnfmr on 2007-05-05
seems to be an issue of ATI card drivers..at least for Xpress (integrated) series

there is a solution I can roughly remember:

add a line in your /etc/X11/gdm/gdm.conf-custom

under [Daemon] add this line
```
AlwaysRestartServer=true
```

---

### Post by xflatlinex on 2007-05-05
> **hnfmr said:**
> seems to be an issue of ATI card drivers..at least for Xpress (integrated) series

there is a solution I can roughly remember:

add a line in your /etc/X11/gdm/gdm.conf-custom

under [Daemon] add this line
```
AlwaysRestartServer=true
```

NICE!!! YOU ARE THE MAN..if you are indeed a man.
Thank you very much. It werks

---

### Post by marsmissionaries on 2007-05-06
> **xflatlinex said:**
> NICE!!! YOU ARE THE MAN..if you are indeed a man.
Thank you very much. It werks

Congrats, that didn't work for me when i tried.

---

### Post by xflatlinex on 2007-05-06
> **xflatlinex said:**
> NICE!!! YOU ARE THE MAN..if you are indeed a man.
Thank you very much. It werks

Ok, now that it works any hints on the same problem with hibernate and standby.  I get the annoying error sound when I return and it tells me it failed to hibernate.

---

### Post by juxtaposed on 2007-05-09
> seems to be an issue of ATI card drivers..at least for Xpress (integrated) series

there is a solution I can roughly remember:

add a line in your /etc/X11/gdm/gdm.conf-custom

under [Daemon] add this line
Code:
AlwaysRestartServer=true

I have this problem too, and I tried that, didn't work. Then I found this:

> > An effective workaround on my machine has been to set AlwaysRestartServer=true
> in /etc/gdm/gdm.conf. Using this, GDM has not frozen at all any more, and I can
> still access my text consoles regularly. The documentation for this option in
> gdm.conf is "If you are having trouble with using a single server for a long
> time and want gdm to kill/restart the server, turn this on."

Similar, but it worked :)

---

### Post by xflatlinex on 2007-05-09
> **juxtaposed said:**
> I have this problem too, and I tried that, didn't work. Then I found this:



Similar, but it worked :)

Can you please tell me where I would add the AlwaysRestartServer=true in that file?

---

### Post by juxtaposed on 2007-05-10
> **xflatlinex said:**
> Can you please tell me where I would add the AlwaysRestartServer=true in that file?

It's at line 97 for me.

This is what it is defaulted to:

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
# AlwaysRestartServer=false

This is what I have it at:

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
AlwaysRestartServer=true

---

### Post by xflatlinex on 2007-05-10
> **juxtaposed said:**
> It's at line 97 for me.

This is what it is defaulted to:

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
# AlwaysRestartServer=false

This is what I have it at:

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
AlwaysRestartServer=true

Hmm, didnt work, I am getting an error of "HAL failed to hibernate". Something along those lines.

---

### Post by stchman on 2007-05-16
> **hnfmr said:**
> seems to be an issue of ATI card drivers..at least for Xpress (integrated) series

there is a solution I can roughly remember:

add a line in your /etc/X11/gdm/gdm.conf-custom

under [Daemon] add this line
```
AlwaysRestartServer=true
```

You rock, that worked like a charm.  How did you know that?

Thanks a bunch.

---

### Post by karhulitos on 2007-05-19
I had black screen issue also, Feisty and ATI Xpress 200M (Acer Aspire 5044WLMi).
I did Envy according to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Now logoff works (login screen comes a bit slower than it used to BUT it works :))

---

### Post by louaym on 2007-06-10
Thank you hnfmr

it had worked for me too

---

### Post by stchman on 2007-08-17
> **xflatlinex said:**
> I am running Feisty64 on an AMD64 and when I logoff to try to switch to a different user, I just get a black screen and have to manually hold down the power button to power off the PC.  I searched the forums and could not find anything solid to help me, does anyone have any suggestions?

My ATI equipped laptop had a similar problem.  I fixed it by doing this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Look in the Logoff black screen portion.

---

### Post by fiatguy85 on 2007-09-01
That is the same solution listed earlier in the thread.  It worked for me as well on a Gateway MX6453.

---

### Post by Icebear on 2007-09-02
Hi I also use a 64 amd machine with a ATI graphic card and I have the same problem. What I do when I want to log out to log on as a different user I press Ctrl, Alt and Backspace which sends me to the log on screen

---

