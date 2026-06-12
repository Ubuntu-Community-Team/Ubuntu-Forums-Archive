---
title: "[SOLVED] no splash screen"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by yellowbread on 2008-01-01
Upon installing a new video card (nvidia 8600 gt) I no longer get a boot splash screen. I've tried most of the possible settings for vga=*** in menu.lst, with corresponding settings in usplash.conf, but with any of the settings I've tried, after selecting the appropriate kernel to boot from the grub menu, the screen goes black until the login screen. 

Does anyone have any suggestions on what to try next?

---

### Post by John Jason Jordan on 2008-01-01
> **yellowbread said:**
> Upon installing a new video card (nvidia 8600 gt) I no longer get a boot splash screen. I've tried most of the possible settings for vga=*** in menu.lst, with corresponding settings in usplash.conf, but with any of the settings I've tried, after selecting the appropriate kernel to boot from the grub menu, the screen goes black until the login screen. Does anyone have any suggestions on what to try next?
There are hundreds of posts in multiple threads about this issue, and a bug report on launchpad as well. Lots of folks have suggested many different fixes and they have helped a lot of people get usplash working. Unfortunately, the solutions haven't helped everyone. 

I did not bookmark the threads, but if you search the forums for "usplash" you should turn them up, along with links to the bug report.

---

### Post by Laryllan on 2008-01-02
Hi there!

I am using a Nvidia GF8600GT too and found a solution for the splash screen issue with help from the german community wiki:
[http://wiki.ubuntuusers.de/Booten?highlight=%28booten%29](http://wiki.ubuntuusers.de/Booten?highlight=%28booten%29)

The usplash screen cannot be displayed, because framebuffer drivers are disabled by default in Gutsy. Do the following:

Edit **/etc/initramfs-tools/modules** and add these modules:
```
fbcon
vesafb
vga16fb
```

Then, edit **/etc/modprobe.d/blacklist-framebuffer** and comment the following lines with #:
```
vesafb
vga16fb
```

After that, you have to update the kernel image:
```
sudo update-initramfs -u 
```


After that, install **startupmanager** from the universe repository and set a propriate resolution for your gfx card/monitor setup.

---

### Post by yellowbread on 2008-01-02
Thanks Laryllan, that worked. I had tried it before without luck, but this time it worked. I wonder what I did wrong the first time? 

By the way, with a little trial and error I found the the vga16fb stuff is not necessary, at least for me. Enabling vesafb gives me the splash screen and fbcon gives text in the consoles.

---

### Post by Laryllan on 2008-01-03
No problem.

I believe they disabled the framebuffer drivers for a reason.
My system is stable since then, can you report if you encounter any instabilities?

---

### Post by yellowbread on 2008-01-05
No stability problems yet. I'll post here if I run into any.

---

### Post by Hackerbeavis on 2008-01-06
I enabled the framebuffer drivers on a Dell C610, and I noticed that I started having pretty regular problems resuming from a suspend state (with GDM running). What would happen is that I would get no video upon resume, and I don't believe that I was even getting the authentication prompt in the background, because entering my password blind didn't seem to do anything (no disk activity). I ended up having to hard-shutdown the machine and restart.

One thing I should mention is that in order to get the framebuffer drivers working on the Dell C610, I had to use the radeonfb driver instead of the vesafb driver. Even after enabling the framebuffer driver, I was unable to define a higher resolution using the vga=xxx option in GRUB, but the default mode still produced a high-res console output after the FB drivers were loaded during the startup process.

At this point, I undid all the changes I made to enable the FB drivers (from the 3rd post above), and everything is working fine now. I'm guessing that my hardware is just a little too old or flaky to be able to use FB.

Hope this helps someone.
--John

---

### Post by Laryllan on 2008-01-06
As I said, the drivers seem to be disabled for a reason.
I normally don't use any suspend modes, so I didn't encounter any problems so far.

---

### Post by yellowbread on 2008-01-06
I don't normally use any suspend modes either, but just to see, I tried invoking suspend from the shutdown menu with the same result as described by Hackerbeavis. Its not a problem for me, but good to know anyway.

---

### Post by drPJ on 2008-01-08
This did not work . . . but with these minor changes I now get the splash...

/etc/initramfs-tools/modules

```

fbcon
vesafb

```

/etc/modprobe.d/blacklist-framebuffer

```

#vesafb

```


DELL inspiron 1720
nVidia Corporation GeForce 8600M GT (rev a1)
1920x1200 screen 
ubuntu 7.10 x86_64

(I found this version on another thread but have lost the link).

---

### Post by guren on 2008-01-08
in my case, I considered **nvidiafb** cause without it, my splash screen shows but it's messed up.
i'm using a Nvidia 8400gs on a HP dv laptop

---

### Post by dnns123 on 2008-01-18
Uhm, i tried both of the solutions above, but the os wont boot anymore.
how do I undo what I've done?

---

### Post by Laryllan on 2008-01-18
Hm, not good.
Boot with a Live-CD, mount your file system and try to blacklist the kernel modules again.

---

### Post by dnns123 on 2008-01-18
Its still broken. i still get the kernel panic line when I load in the recovery mode.

---

### Post by Laryllan on 2008-01-18
I believe you have to recompile the boot module. But I have no clue how to do that.. :(

---

### Post by dnns123 on 2008-01-18
Oh man, pls help.
I cant even get to the terminal in recovery mode.

---

### Post by John Jason Jordan on 2008-01-18
> **dnns123 said:**
> Oh man, pls help.
I cant even get to the terminal in recovery mode.

When you said "i tried both of the solutions above, but the os wont boot anymore," what exactly did you do? The only solutions I see above say to:

------------
Edit /etc/initramfs-tools/modules and add these modules:
Code:
fbcon
vesafb
vga16fb

Then, edit /etc/modprobe.d/blacklist-framebuffer and comment the following lines with #:
Code:
vesafb
vga16fb

After that, you have to update the kernel image:
Code:
sudo update-initramfs -u

After that, install startupmanager from the universe repository and set a propriate resolution for your gfx card/monitor setup.
-------------

So to undo it you removed the lines from /etc/initramfs-tools/modules, then you uncommented the lines in /etc/modprobe.d/blacklist-framebuffer, then you did "sudo update-initramfs -u" again, right? And finally, you went into startupmanager and changed the video settings back to what they were originally, right? 

If you did that it should have reversed what you did. If it did not, then you did something different than the above instructions. Either that or you did not reverse everything. 

You could boot to a live CD and inspect what the above two files contain. You could also look at /etc/X11/xorg.conf and see if it lists the right video card and driver. I'm not an expert on these things, but those are some things I would try in the hopes that I'll spot something that will enable me to fix it.

Also post back with what video card and monitor you have and what their resolution options are. Maybe that will help someone smarter than me figure out what is wrong.

---

### Post by dnns123 on 2008-01-18
Heres what happened. I did the instructions above and rebooted. I found out that the kernel panicked. I used the live CD and changed both the files back to it's original state. the only thing i cant do is type "sudo initramfs-update -u" on my original Ubuntu PC sinse im using the live CD.

I use a GeForce 8800GTS and a MAG 986FS monitor.
Everything in my xorg.conf seems that same. even grub's menu.lst

---

### Post by John Jason Jordan on 2008-01-18
> **dnns123 said:**
> Heres what happened. I did the instructions above and rebooted. I found out that the kernel panicked. I used the live CD and changed both the files back to it's original state. the only thing i cant do is type "sudo initramfs-update -u" on my original Ubuntu PC sinse im using the live CD.

I use a GeForce 8800GTS and a MAG 986FS monitor.
Everything in my xorg.conf seems that same. even grub's menu.lst
When you get the kernel panic, is there a text message just before it? If not, I know there are log files that should contain what caused the kernel panic. Unfortunately, I don't know exactly which log file(s) you need to look at, but I think they are located in /var/log/. Boot with the live CD and then look to see if you can find any log files in there. Open them in Text Editor (gedit) and see if there is any reference to the kernel panic.

The first step is to figure out what caused the kernel panic.

---

### Post by Mr.Auer on 2008-01-19
This happens to me too, Im on brand new AMD X2 64 5000+ with NVidia GT 8600 / 64 bit Ubuntu. I didnt get a splash screen on LiveCD when installing, and never got one after installation - all Id get was a No Signal from my monitor until the login screen showed up.

I decided I dont need the splash anyway, and removed "splash" from kernel boot options in /boot/grub/menu.lst, and uninstalled the whole splash display utility. Now I get a nice informative view of the boot process and it all works ;)

I think Im not gonna try the fixes if it may cause other problems....Who needs a splash anyway :D

---

### Post by John Jason Jordan on 2008-01-19
> **Mr.Auer said:**
> This happens to me too, Im on brand new AMD X2 64 5000+ with NVidia GT 8600 / 64 bit Ubuntu. I didnt get a splash screen on LiveCD when installing, and never got one after installation - all Id get was a No Signal from my monitor until the login screen showed up.

I decided I dont need the splash anyway, and removed "splash" from kernel boot options in /boot/grub/menu.lst, and uninstalled the whole splash display utility. Now I get a nice informative view of the boot process and it all works ;)

I think Im not gonna try the fixes if it may cause other problems....Who needs a splash anyway :D
I need a splash screen because the text scrolling by doesn't look very slick to Windows and Mac users. I do a lot of promoting Linux at the university so I need something that looks good.

After trying every fix in all the threads on the splash screen I finally installed splashy instead.

---

### Post by dnns123 on 2008-01-19
oh man.... scrap this...
I'm gonna install Kubuntu instead and try it out.
I wanna try a new DE :)
Is there a Kubuntu release with KDE 4.0? I know it's buggy, but I wanna try it.

---

### Post by fluffybacon on 2008-01-20
Fixed it for me, 

Thanks.

---

