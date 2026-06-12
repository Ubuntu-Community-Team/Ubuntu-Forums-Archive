---
title: "Nvidia Restricted Drivers dont work after Installing 64 bit 9.04"
date: 2009-06-13
forum: x86 64-bit Users
---

### Post by TheTampaSaint on 2009-06-13
Hello, I use CentOS and the Nvidia drivers work fine for me.  I have 2 monitors on separate 6200 cards and run xinerama.  I don't have any choice because I am using a clovertown server with only PCI so the GeForce 6200 cards were the best I can get and they only have a DVI each.  But as I say it works great.

I tried installing 9.04 Ubuntu.  After loading the restricted nvida driver and rebooting, I don't even get a display at all but boot into non-X.  I tried one version back of the restricted driver and still no luck.  

For giggles I also tried nvidia's driver from their website after re-installing - same results.

I am attaching the Xorg.0.log file crash from ubuntu AND the same log on the working CentOS installtion on the same hardware.  Anybody have an idea how I can troubleshoot this?  I am lost here.

TIA

---

### Post by slamhound on 2009-06-13
I think the issue is the two cards.  To get my two cards working, I had to run

nvidia-xconfig -a

(as described here:  [http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/) )

Also, the first time I tried it, I got an error message saying that it couldn't find libnvidia-cfg.so.1 

But this link helped me solve that:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863)

I had to create a symbolic link to the version specific libnvidia.cfg.so.1 file.

---

### Post by matthewjames on 2009-06-13
Ok. Here is what I would say to do, worked for me. Completely remove the drivers you installed for the card. Go to hardware driver in System/Administration. Check and install Nvidia Accelerated graphics driver (180). After this reboot. Then go into administration and Nvidia X Server Settings. A popup window should appear, follow its directions. To restart the x server do the following:

```
sudo /etc/init.d/gdm restart
```

You might get frozen at a black screen saying reloading. If so just ctrl-alt-delete and let your system reboot. Everything should be done, good luck :)

---

### Post by deadguy on 2009-06-13
I had this same problem.  Apparently, Xinerama doesn't work with multiple cards in newer versions of Xorg.  I was able to get my triple head setup back by downgrading X to Hardy's version.  Here's how I did it: [http://www.softmechanics.net/Xinerama_with_Multiple_Graphics_Cards_in_Ubuntu_Jaunty]("http://www.softmechanics.net/Xinerama_with_Multiple_Graphics_Cards_in_Ubuntu_Jaunty")

Hope it helps!

---

### Post by TheTampaSaint on 2009-06-14
Thanks this suggestion worked perfectly.  I followed the instructions and grabbed the very latest driver.

Worked perfectly as described in that link, and I did not need the symbolic link either.

Thanks to all the other good ideas too.

Oops I meant to respond to slamhound's post, that was the first one I tried and it worked.

---

### Post by TheTampaSaint on 2009-06-17
The only remaining problem was that when shutting down the kernel crashes; this was resolved by booting "nosplash".

---

### Post by matthewjames on 2009-06-19
I would have no idea about that, sorry man good luck in finding that out :)

---

### Post by dcompiled on 2009-10-24
I just installed ubuntu for the first time on my EVGA 790i system.  I have 2x 8800GTX (Nvidia graphics cards) in the case and frankly I dont care about hardware support for advanced graphics in linux but under the recommendation of a system popup I agreed to update drivers.  Now on startup the system fails to load a desktop hanging on a message about "Battery State" which is odd because this computer is a desktop.  Others have suggested to remove the nvidia driver for the system but since I have no knowledge about any advanced stuff with linux maybe someone can give me step by step instructions so I can get back to my desktop.

TIA
Alex

---

### Post by slamhound on 2009-10-25
If you are using the two cards for multiple monitors, then see my post above.  The links in that post give step by step directions.  It doesn't involve removing the drivers, just configuring them for multiple gpus.  If you are using the two cards for sli, then I think that there is a different solution.

---

