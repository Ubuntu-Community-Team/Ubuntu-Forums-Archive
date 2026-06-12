---
title: "Ubuntu help for linux newbie"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by hippomofatumas on 2006-01-28
Hi all,

I have recently gotten interested in the world of linux, and I've done a lot of research. I decided to install Ubuntu on my new pc. It all seemed to be going great, but I got an error after the reboot saying something about an x server error. Looking at other problems like this on forums, I think it means my graphics card or my monitor is not being recognized. I really don't know anything linux wise, so I desparately need some help here. I really want to give it a try.

Thanks,
hippomofatumas

hp a1230n
amd 64 3800
200gb sata
1 gb ddr400 ram
ati radeon xpress 200
hp mx705 monitor

---

### Post by JAwuku on 2006-01-28
Hi there, and welcome to the world of Ubuntu! :D 

I'm sorry to see you come up against a brick wall. Hopefully people on these forums can be of assistance.

first of all, there are a few things you can do to ensure the system is detecting your ATI card.

If you type in ```
sudo lspci
```

it should show a list of devices in your PCI slots, including the Radeon.

The X-server is configured via a text file called **/etc/X11/xorg.conf**

and you can automatically configure it via the command ```
sudo dpkg-reconfigure xorg
```

If this is not successful, could you please post a listing of the /etc/X11/xorg.conf

hope this is of some help

Jason

---

### Post by alamba on 2006-01-28
Have a look at this thread [http://www.ubuntuforums.org/showthread.php?t=122593](http://www.ubuntuforums.org/showthread.php?t=122593)

Do the vesa thingy and get up and running and then post as request by Jason.

Akshay

---

### Post by hippomofatumas on 2006-01-28
Okay,

It worked when I did duso dpkg-reconfigure xserver-xorg and changed the driver to vesa. I can now boot into ubuntu completely. yay! but I checked my screen resolution when the option came (1280x1024) and chose to use it, but it still boots into 1024x768.

how do I change my resolution to 1280x1024? and do I need to change the driver from vesa to ati (radeon xpress 200), or does it not really matter?

Also, I can't connect to the internet, but here in xp I can. So how do I go about remedying that problem?

thanks,
hippomofatumas

---

### Post by hippomofatumas on 2006-01-28
Hi again,

I just did a complete reinstall and did the autoupdate, and I have connection (I'm in ubuntu now), and my resolution is at 1280x1024! don't know how it happened, but it did. But now I need to install my ati driver, because the screen is flashing and jumpy, just like it was with xp. but with xp it was real easy to install the driver. I don't think it's as easy with ubuntu.

can someone please guide me through setting up my radeon xpress 200 driver?

thanks,
hippomofatumas

---

### Post by JAwuku on 2006-01-28
[QUOTE=hippomofatumas]Okay,

It worked when I did duso dpkg-reconfigure xserver-xorg and changed the driver to vesa. I can now boot into ubuntu completely. yay! but I checked my screen resolution when the option came (1280x1024) and chose to use it, but it still boots into 1024x768.

how do I change my resolution to 1280x1024? and do I need to change the driver from vesa to ati (radeon xpress 200), or does it not really matter?

thanks,
hippomofatumas[/QUOTE]

Hi hippomofatumas,

congrats on now booting to a graphical screen! You can either stay with the "vesa" option, but you will not be taking advantage of the advanced 3D graphics of the ATI card.

Fortunately, ubuntu does have its own dedicated ATI drivers, but they are not installed by default.

The Ubuntu web site has detailed instructions on how to install them. With the new drivers, the 1280*1024 resolution should become available.

Check out [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

[QUOTE=hippomofatumas]Also, I can't connect to the internet, but here in xp I can. So how do I go about remedying that problem?[/QUOTE]

What do you use to connect to the Internet? Linux in general has only limited support for internal PCI dial-up modems.

You would do better with either an external serial modem, a dedicated Ethernet card, or an Ethernet adapter that plugs into a spare USB slot.

My own Ethernet port on the motherboard mysteriously stopped working recently, but my USB Ethernet adapter (a Netgear FA-120) works seamlessly).

---

### Post by hippomofatumas on 2006-01-28
Okay,

I have internet working fine. I guess the updates helped with that or something.

However, even after following all of the sudo commands listed under the link you gave me, and then reconfiguring the xserver thingy to use fglrx driver, it didn't work. I have reverted to vesa.

So, what do I do now?

Thanks,
hippomofatumas

---

### Post by hippomofatumas on 2006-01-29
Okay,

I've been browsing around on the internet looking for help, and I've found pages describing my problem and how to fix it. But I can never do te terminal commands right, even though it looks the exact same. Ah! 

I am really getting into linux, and the terminal is pretty cool I just don't know how to use it that well. I've been brainwashed by windows until recently.

I just need my ati drivers! why is it so hard?

hippomofatumas

---

### Post by alamba on 2006-01-30
Post the link u're following and the errors you get when you type the same exact thing.

Akshay

---

### Post by pbaehr on 2006-01-30
I recently set up ubuntu on my system which is very similar to yours. I have the same video card. It's working quite well using the fglrx driver. You can get it through apt-get from ubuntu or from the ati website (latest version). I believe I've made both work, equally well.

It's working quite well EXCEPT 3d acceleration is not working. I've yet to find someone who has successfully enabled 3d acceleration with this card. If you're not interested in that, I think you'll be plenty satisfied with the drivers available.  I'd post details on what I did to set it up but I've made so many changes and tried so many different methods while trying to set up hardware acceleration that I've completely forgotten how I made it work initially.

If you do manage to enable 3d acceleration on this card I'd be very interested to hear what driver you're using.

Good luck.

---

### Post by hippomofatumas on 2006-01-31
I've gone to [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI), and there are two methods. The first one I did successfully, but my screen still flickers and is not as stable as it is with xp. The second method is where I have problems. I think if I did that one correctly, it would work, but I can never get it right. The console always gives me an error of some sort.

Can anyone walk me through this process step by step? I'd be forever obliged.

Thanks,
hippomofatumas

---

### Post by jon_gunnar on 2006-01-31
[QUOTE=hippomofatumas] I did that one correctly, it would work, but I can never get it right. The console always gives me an error of some sort.

hippomofatumas[/QUOTE]

It would be much easier to help if you posted the error messages you get.

---

### Post by hippomofatumas on 2006-02-08
okay,

sorry for delay, i'm sick and in lots of ap classes with no internet in my room yet. 

I can't get past the second terminal entry. "chmod +x ati-driver-installer-<version>.run"

chris@ubuntuchris:~$ chmod +x ati-driver-installer-8.21.7-i386.run
chmod: cannot access `ati-driver-installer-8.21.7-i386.run': No such file or directory
chris@ubuntuchris:~$ chmod ~/ati-driver-installer-8.21.7-i386.run
chmod: too few arguments
Try `chmod --help' for more information.
chris@ubuntuchris:~$ chmod +x /home/chris/desktop/ati-driver-installer-8.21.7-i386.run
chmod: cannot access `/home/chris/desktop/ati-driver-installer-8.21.7-i386.run': No such file or directory


so, i obvously don't know what i'm doing. i'm also currently logged into the i686 kernel i have. i don't need to be in the original i386 kernel in order to do this do I? 

ah!

thanks,
hippomofatumas

---

