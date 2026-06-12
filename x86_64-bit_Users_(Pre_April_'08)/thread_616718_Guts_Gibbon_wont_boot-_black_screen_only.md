---
title: "Guts Gibbon wont boot- black screen only"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hakuka on 2007-11-18
hey everyone im quite new to this thing..this my third attempt to start using linux..i was really determined this time that ill learn how ot use it despite the fact that ive been using windows all my life so this a whole new world...
i installed ubuntu gutsy gibbon on my amd x2 64 4800+, nVidia 8600GT jsut fine.After rebooting the PC id get the boot menu with Ubuntu Kernel graphics, Ubuntu Kernel(recovery) and also for some reason instead of Windows Xp Home Edition i got Longhorn/ Vista. After i "click" the first one to boot into ubuntu kernel graphics something about kernel is loading appears and then i get a black screen saying "no Input signal" and nothing happens. I tried giving it some time but nothing. I tried installing this distro of linux about three times. The last time i was so desperate that i istalled feisty fawn and upgraded it. I worked. It woudl even boot up after rebooting. But then it did the same thing as before. I dont knwo if this has anything to do with it but i installed acronis OS selector. Now its disabled but i still cant get ubuntu to boot up. I didnt change resolution. The only thing i did was allowed restricted drivers.
i really hope itll work becasue i quite liked it so far and i wouldnt want to get stuck only with Windows.
Thank you all in advance for your responses.

---

### Post by Cute Poison on 2007-11-19
Yep... you will have to disable your restricted drivers and fiddle with the entire driver thing like me for while till you get it working. Be warned its not easy .. 
But here it is in a nut shell. Its black cos the drivers are not working. The monitors happy with what it's told but its not happy. thus the black screeen. 
its evil and we will beat it soon.

---

### Post by IanW on 2007-11-19
This seems to be a bug in the Nvidia drivers,

Try the following:-
```

1. Press escape when grub tells you you can
2. Highlight the standard boot option and press 'e' to edit the boot code
3. Highlight the line that starts with the word 'kernel' and press 'e' again.
4. Scroll to the end of the line (or press 'end' on your keyboard)
5. Delete the words 'quiet splash' from the end of the line and press return
6. Press 'b' to boot into Ubuntu.

```

This should get Ubuntu running, but once started up, don't forget to make the change permanent by doing:-

```

sudo gedit /boot/grub/menu.lst

```

and making the same changes you used above.

---

### Post by Hakuka on 2007-11-19
thanks guys a lot..ive been struggling a lot with this thing..im trying to edit the boot menu as suggested so i hope it'll work. I tried to install nVidia drivers directly from the nVidia site following these instructions

> Aaron D. Campbell wrote on 2007-04-02: (permalink)

For now, this worked for me:
Download the nVidia drivers from here: [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
Extract the drivers with the -x switch: sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
Copy the module somewhere (hopefully to be removed when they start including it in the package). I used my home directory: cp NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 ~/
Now create a link to it from /usr/lib/xorg/modules/: sudo ln /home/aaroncampbell/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so
That should do it. I also chown'd it to root:root, and chmod'd it to match all the other stuff in that directory.

Hope this helps someone. Once I did that, everything started to work fine. My dual screens, even Beryl runs smoothly (well, as smoothly as Beryl can run).



[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)

I cant get this work though. If i try to run it in terminal i get back only that sh: Can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run

i tried couple of times but cant get it working.

---

### Post by Rowdy73 on 2007-11-22
Wow!, i got it to work with my EN7900GTX video card, (no more black screen).

Just use a jump/thumb/travel drive to carry the downloaded driver to the black screen machine, (assuming you have access to two computers or a dual boot system). Plug it in to the computer that fails and BAM! it automatically recognizes it.

I'm so happy, thank you guys for helping me to get my black screen to go away.
(Gonna see if i can get Beryl now) :)

Edit:
Well, it took me one step closer anyway, i'm typing in Windows right now since i just put my laptop away..
Going to go through the motions of installing the downloaded driver into Gutsy now.

---

