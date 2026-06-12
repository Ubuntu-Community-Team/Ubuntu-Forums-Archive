---
title: "64 bit Ubuntu 8.04 Nvidia Driver help"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by zuknivek on 2008-05-08
When i installed 7.10 i had the option to install the nvidia restricted driver but i thought that i would do the long upgrade to 8.04 first before i installed my nvidia driver. Now that i upgraded i cant find how to enable my nvidia restricted driver for my 7600gt. When i click System->Administration->Hardware Drivers it says No Proprietary Drivers are in use on this system. Please help.

---

### Post by sowelie on 2008-05-08
Try doing it manually:

```
sudo aptitude install nvidia-glx-new
```

---

### Post by saru411 on 2008-05-08
have you started your pc since the updtaes.....after every major pack of updates i find it useful to restart my pc. i know that linux doesnt need to be restarted but i find that restarting helps with the o/s finding hardware.

good luck

---

### Post by killall-9 on 2008-05-09
Hi !

Try this very nice Howto for Nvidia cards and Ubuntu!

[http://wiki.ubuntu-forum.de/index.php/Nvidia_installieren](http://wiki.ubuntu-forum.de/index.php/Nvidia_installieren)

I hope its no problem because its in german!

---

### Post by rayman_3d on 2008-05-09
u can download it using Envyng

sudo apt-get install envyng-gtk

---

### Post by StefAndrew on 2008-05-09
I have a similar problem, after installing 64bit, and going to hardware drivers, it shows nvidia_new as enable, but status says not in use.

---

### Post by Melk79 on 2008-05-13
StefAndrew, when this happened to me, I followed the directions under the third sticky link from this forum.  You basically just check the box or uncheck and recheck the box.  Ubuntu will install the driver automatically after that and all should be good to go.

---

### Post by Sef on 2008-05-15
> i know that linux doesnt need to be restarted

That's not quite true.  More correct is GNU/Linux rarely needs to be rebooted (restarted.)  If there is a upgrade to the kernel, then you will need to reboot the system for the changes to take effect.

---

### Post by e-mitc2h on 2009-02-17
I have the exact same problem as the one described in the original post. The problem is, I tried everything mentioned in this thread, and nothing works.

When I start the nvidia-settings utility:

sudo nvidia-settings

It tells me that I am not using the nvidia driver, and that I should run nvidia-xconfig (sudo nvidia-xconfig) to configure correctly the xorg.conf file. I do this, and restart the X server (or the computer, I tried both).

Then, I get this little window asking me if I want to run Ubuntu in low-resolution mode or to manually configure the display (before Ubuntu itself starts), which is a sign that something is wrong with the xorg.conf file.

When I reconfigure the display using this, I get back to the point where nvidia-settings tells me that I am not using the driver. This has been driving me crazy...

Any ideas?

---

### Post by tenmoi on 2009-02-17
@e-mitc2h
If every other method has failed you then you can do it manually by downloading the corresponding driver for your card from NVidia then:
purge-remove *nvidia*, restricted-module*
ctrl+f1+alt
sudo /etc/init.d/gdm stop
sudo sh /pathtoyourdriver.run
ok and ok and ok ...
sudo /etc/init.d/gdm restart

and every thing is ready to serve you!

P.S
If you're a newbie then do some search on this forum. There's hoards of Q&A like this to help you.

---

### Post by RaveJunkie on 2009-06-05
I found this video tut that fixed it for me..... might help you

[http://linuxcrypt.net/?p=255&cpage=1#comment-1809](http://linuxcrypt.net/?p=255&cpage=1#comment-1809)

---

