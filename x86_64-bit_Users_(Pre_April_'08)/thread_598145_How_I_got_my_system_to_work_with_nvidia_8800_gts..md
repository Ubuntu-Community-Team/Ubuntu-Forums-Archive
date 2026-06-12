---
title: "How I got my system to work with nvidia 8800 gts."
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by steeviee on 2007-10-31
First of all I just want to thank everybody on this forum who helped me out. This is a collection from several different users on this forum and alot of Google-ing. I am just putting this all together, because I was not able to get Ubuntu loaded by one thread alone. I hope this helps other persons who are having the same problem.
 My system is a 4 core Q6600, MSI 680i SLI MB, 4 gigs ram, and two 8800 gts video cards. The problem I had was when I tried to install Ubuntu using the live cd the screen went blank. I never could get the live cd to work. Here is how I got Ubuntu loaded on my system.

Step 1 download the [COLOR="Red"]Alternate[/COLOR] cd and burn it to disk.

Step 2 Install a [COLOR="Red"]command line[/COLOR] and follow tthe onscreen instructions until installed, then reboot.

Step 3 When you have command prompt type "sudo passwd" and type your password 3 times, you'll see.

Step 4 Type "sudo apt-get install nvidia-glx-new" and press "y" when prompted

Step 5 Type "sudo nvidia-glx-config enable"

Step 6 Type "sudo nvidia-xconfig"

Step 7 Type "sudo apt-get install gdm" and press "y" when prompted

Step 8 Type "sudo shutdown -r now" Reboot and wait for command prompt.

Step 9 Type "sudo apt-get install ubuntu-desktop" ( or you can do tasksel whichever you prefer) This may take a while, after complete restart using sudo shutdown

Step 10 press esc when loading to get in the grub menu and use "recovery mode"

Step 11 At the command prompt Type "nano /boot/grub/menu.lst" and scroll down until you see the first line that starts with Kernel and remove the "splash" from the end of the line.

Thats it! you should be able to load Ubunu and get in gnome.

Again I take no credit for this I want to give credit to the people on this forum who suggested these commands (you know who you are when you read this). I just wanted to put it all in one place so it may help people with similar configurations start using Ubuntu and not get discouraged like I almost did. Thanks to everyone on this forum for being so helpful I appreciate your patience, I only hope that this helps out in some way.

If anyone has any suggestion doing this more efficently I am sure that there is room for improvment here.

---

### Post by RunawayBishop on 2007-11-01
Thanks for this steeviee - this was the exact problem i was having. really usefull to have all the steps in one post, thanks a million dude.

---

