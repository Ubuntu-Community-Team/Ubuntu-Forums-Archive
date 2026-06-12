---
title: "Startup Manager with uSplash missing"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by AegisTalons on 2007-07-19
I just installed Startup Manager (SUM). [http://web.telia.com/~u88005282/sum/index.html]("http://web.telia.com/~u88005282/sum/index.html")

On my laptop (32bit Ubuntu Feisty), I have 1.0.8 installed. I installed the newest version on my desktop (Ubuntu Feisty x64), version 1.0.9. The thing is that the usplash section is missing in the program. Has anyone ever run into this problem or better yet has fixed it.

---

### Post by Coucouf on 2007-07-27
I haven't tested SUM lately but I have a possible explanation though.
For what I have experienced, the splash screen tends to be buggy in Ubuntu x86_64; this may be why it isn't proposed in the 64-bit version of Startup Manager.
My system used to freeze at startup with some keyboard lights flashing when the splash was enabled, so I ended up with disabling it.

You can always manually edit your /boot/grub/menu.lst as a workaround...

---

### Post by Jimmy_r on 2007-10-22
SUM checks for /sbin/usplash . If it is not there, it disables usplash settings.
This could also be caused by some crash in the code for usplash settings.
Try to run sum from command line with sudo startupmanager (yes, not gksu. gksu mutes some messages)to see if it outputs any error.

---

### Post by John Jason Jordan on 2007-10-22
> **Jimmy_r said:**
> SUM checks for /sbin/usplash . If it is not there, it disables usplash settings.
This could also be caused by some crash in the code for usplash settings.
Try to run sum from command line with sudo startupmanager (yes, not gksu. gksu mutes some messages)to see if it outputs any error.
Thanks for the suggestions, but it didn't solve the problems.

I have a fresh install of Gutsy amd64 on a brand new Thinkpad T61. I mean, I opened the box the Thinkpad came in, and inserted the Gutsy amd64 DVD before the machine was turned on for the first time. So it is a brand new install on a virgin hard disk.

I have the /sbin/usplash file. 

I tried sudo startupmanager, but it said there was no such command or program. Then I tried "sudo sum" and this time it went to a new line as though a program was being launched. But nothing appeared.

My boot line in Grub says:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=afba6df9-befb-4643-a209-841c2476a989 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

Sometimes it hangs instead of actually booting. I think there is a video driver problem, but I can't figure out what it might be. The video is:

lspci
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

I posted about the video in another thread this morning, but no responses yet.

[HTML]http://ubuntuforums.org/showthread.php?t=557581[/HTML]

I wonder if the lack of boot splash screen is related to the video problems.

---

### Post by Jimmy_r on 2007-11-18
John, I believe you have a different problem with your setup. SUM is not installed by default, and I do not think it can do much to help with your problem.

I know Usplash was disabled on some earlier versions of 64-bit Ubuntu. Perhaps it has been re-disabled?

Personally, I stopped using the 64-bit version of Ubuntu, because it was not worth the effort.

---

### Post by John Jason Jordan on 2007-11-18
> **Jimmy_r said:**
> John, I believe you have a different problem with your setup. SUM is not installed by default, and I do not think it can do much to help with your problem.
I know Usplash was disabled on some earlier versions of 64-bit Ubuntu. Perhaps it has been re-disabled?
Personally, I stopped using the 64-bit version of Ubuntu, because it was not worth the effort.
It has been some time since I posted that above, and I have not yet solved the usplash problem. I have, however, fixed the rest of the problems. Video now comes up correctly all the time. I had to fix xorg.conf because Ubuntu was not detecting the video, although it did install the correct nVidia driver when I used Restricted Drivers Manager to install it. I can also use all the special compiz stuff, although I decided I didn't really care for it and turned it back off. 

I don't know what is causing usplash not to come up. There are numerous threads on this, with a long list of fixes that others have used, but none of them worked for me. I just decided it wasn't worth the effort to spend any more time trying to fix it. 

As for 32-bit, I have all the multimedia and other stuff working on 64-bit Gutsy, so I see no need to cripple my computer by running a 32-bit OS.

---

