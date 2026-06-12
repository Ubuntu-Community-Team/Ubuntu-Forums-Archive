---
title: "Screen Resolution x-64 Ubuntu 7.04"
date: 2007-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by rhmercer on 2007-04-23
I have only two(2) screen resolutions listed and they are set too low so the windows don't fit correctly. I did not have this problem with Ubuntu 6.10. How can I get a higher resolution when no other is given?????? I used the system preference screen resolution menu. I only get two options 
1) 800X600  2) 640X480 and no other. I used 1 and it is still too big of a window for mail and fire fox........ANY HELP????? Thank You for reading this!

---

### Post by brew1brew on 2007-04-23
> **rhmercer said:**
> I have only two(2) screen resolutions listed and they are set too low so the windows don't fit correctly. I did not have this problem with Ubuntu 6.10. How can I get a higher resolution when no other is given?????? I used the system preference screen resolution menu. I only get two options 
1) 800X600  2) 640X480 and no other. I used 1 and it is still too big of a window for mail and fire fox........ANY HELP????? Thank You for reading this!

I had the same issue when I booted the Feisty 64 CD. I was not able to do the install because of it. What I did to fix it was I went to "System -> Administration -> Restricted Drivers Manager" and the Nvidia driver was listed there, I enabled it. 

Now it needs to reboot after you enable it, but if your running the live CD it will just come back up without the driver. So instead of rebooting it I restarted X server by hitting cnrt-alt-backspace. X restarted with the new driver and I was able to do the full install. If you are not using the live CD then you may just need to enable the restricted driver and reboot.

I hope this helps.

Les

---

### Post by brew1brew on 2007-04-23
Hey, I just checked my work computer and it was not using the restricted driver, I enabled it and with the restricted driver enabled I had only 800x600 & 640x480. I disabled the restricted driver and got full screen res back.

again I hope this helps

Les

---

### Post by boogachamp on 2007-04-23
I need to check this on my install.  I have more than 2 resolutions, but not the resolution that I use.

---

### Post by Bobcatben on 2007-04-23
i cant even get the restricted drivers to work on the 64bit version, xserver just crashes, and if i manualy install it from nvidia, it still crashes, but atleast it tells me it does, with garbled text.

---

### Post by aimran on 2007-04-23
I fixed my screen resolution this way. Open xorg.conf...

sudo gedit /etc/X11/xorg.conf

find the lines where you find a list of resolutions... and edit and add the desired screen resolutions. There will be multiple lines for screen resos. Try the line for 24 bit and add your desired reso.

Hope it helps. Sorry not at linux comp so can't pint point the exact commands and xorg.conf line :(

---

### Post by John.Michael.Kane on 2007-04-23
This thread [http://ubuntuforums.org/showpost.php?p=1691257&postcount=2](http://ubuntuforums.org/showpost.php?p=1691257&postcount=2) may help if your trying edit xorg by hand.

---

### Post by ronocdh on 2007-04-23
> **brew1brew said:**
> I had the same issue when I booted the Feisty 64 CD. I was not able to do the install because of it. What I did to fix it was I went to "System -> Administration -> Restricted Drivers Manager" and the Nvidia driver was listed there, I enabled it. 

Now it needs to reboot after you enable it, but if your running the live CD it will just come back up without the driver. So instead of rebooting it I restarted X server by hitting cnrt-alt-backspace. X restarted with the new driver and I was able to do the full install. If you are not using the live CD then you may just need to enable the restricted driver and reboot.

I hope this helps.

Les
I didn't know this at first, but installation is possible in super-huge-and-ugly resolution, even though the windows are too big for the screen, because holding the alt button makes a window draggable by clicking anywhere on it! Hopefully this tip will serve someone well.

---

### Post by brew1brew on 2007-04-23
> **ronocdh said:**
> I didn't know this at first, but installation is possible in super-huge-and-ugly resolution, even though the windows are too big for the screen, because holding the alt button makes a window draggable by clicking anywhere on it! Hopefully this tip will serve someone well.

yup, that would have helped me out, but I was able to get it done my way :)

---

### Post by jespdj on 2007-04-23
I have the same kind of problem with Ubuntu 7.04 x86_64, but I have an ATI video card (X1600).

I installed the ATI restricted driver via the menu option System / Administration / Restricted Drivers Manager. After rebooting, I do have some higher resolutions, but still the native resolution of my screen (1920 x 1200, it's a Dell 2405 FPW) is not listed.

So I edited the resolutions in /etc/X11/xorg.conf by hand and rebooted again, and now I can use 1920 x 1200.

Looks like the missing resolutions is a bug in the 7.04 installation? I didn't have this problem with the 6.10 x86_64 installation (it automatically picked up 1920 x 1200 after installation).

---

### Post by AscendedDaniel on 2007-04-23
I started with the restricted drivers, but got drivers for my video card from the manufacturer's website (BFG Tech, 6600GT). The install worked perfectly, but I still couldn't get the full resolution that my monitor was capable of. To fix this, I edited the xorg.conf file manually. All I did was add "1680x1050" under each list of resolutions (one for each color depth). so instead of "____x____" "____x____" it reads "1680x1050" "____x____" "____x____".  

Hope this helps.

---

### Post by rhmercer on 2007-04-24
I went to the Restrected Drive Manager and enabled the Nviada and re-booted. It came up and I set the screen resolution to the 1280X960 at 56Hz and all works OK.

Thanks to all for this fast turnaround on my problem. ***_THANKS_***:popcorn:

---

### Post by traffas on 2007-04-24
jespdj:

Is you card the PCIe EAX1600? You're running Feisty x64? You're able to use fglrx simply by enabling the restricted drivers?

---

