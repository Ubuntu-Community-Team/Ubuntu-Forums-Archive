---
title: "Gnome problems on Thinkpad T61"
date: 2007-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by CorporateFatCat on 2007-11-12
I am having very strange issues on my Thinkpad T61. I have installed Unbutu gutsy, and I installed Gnome with it.  I really like Gnome but for some reason it overwrites my directional down arrow.  So whenever I press the down arrow, it doesn't respond at all, and nothing scrolls down like it should.  I've tried other desktop environments such as Xfce and the button works fine, so I'm pretty sure its a Gnome problem.  Has anyone run into this before or know of any solutions to this?  Thanks alot in advance.

---

### Post by John Jason Jordan on 2007-11-13
> **CorporateFatCat said:**
> I am having very strange issues on my Thinkpad T61. I have installed Unbutu gutsy, and I installed Gnome with it.  I really like Gnome but for some reason it overwrites my directional down arrow.  So whenever I press the down arrow, it doesn't respond at all, and nothing scrolls down like it should.  I've tried other desktop environments such as Xfce and the button works fine, so I'm pretty sure its a Gnome problem.  Has anyone run into this before or know of any solutions to this?  Thanks alot in advance.
Do you have the Intel video or the nVidia, and which one? It should be listed by "lspci" from a terminal, in case you don't know.) Also, which driver are you using, e.g., if you have the nVidia video, do you use the open source driver that Gutsy installs by default, or did you go into System > Administration > Restricted Drivers and install the proprietary nVidia driver? 

I have a T61 with a fresh install of Gutsy and64 and all my buttons work fine. They worked fine when I used the open source "nv" driver right after installing Gutsy, and they continue to work fine now that I have installed the nvidia-glx-new driver with Restricted Drivers manager. I haven't heard of anyone else having a problem like yours, although there are occasional issues with other buttons. There is an e-list for Thinkpad owners who use Linux where you might find more information than here.

[http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad](http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad)

---

### Post by CorporateFatCat on 2007-11-13
> **John Jason Jordan said:**
> Do you have the Intel video or the nVidia, and which one? It should be listed by "lspci" from a terminal, in case you don't know.) Also, which driver are you using, e.g., if you have the nVidia video, do you use the open source driver that Gutsy installs by default, or did you go into System > Administration > Restricted Drivers and install the proprietary nVidia driver? 

I am using the restricted proprietary nVidia drivers, I haven't tried the "nv" drivers, since I was having problems with those when T61's first came out. 

> **John Jason Jordan said:**
>  I have a T61 with a fresh install of Gutsy and64 and all my buttons work fine. They worked fine when I used the open source "nv" driver right after installing Gutsy, and they continue to work fine now that I have installed the nvidia-glx-new driver with Restricted Drivers manager. I haven't heard of anyone else having a problem like yours, although there are occasional issues with other buttons. There is an e-list for Thinkpad owners who use Linux where you might find more information than here.


[http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad](http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad)

Thanks for the link I'll check it out.  But I am not sure how the buttons would be related to video drivers?  I use the same video drivers on Gnome and Xfce, and the buttons work in Xfce but not Gnome.

---

### Post by John Jason Jordan on 2007-11-13
> **CorporateFatCat said:**
> I am using the restricted proprietary nVidia drivers, I haven't tried the "nv" drivers, since I was having problems with those when T61's first came out. 
Thanks for the link I'll check it out.  But I am not sure how the buttons would be related to video drivers?  I use the same video drivers on Gnome and Xfce, and the buttons work in Xfce but not Gnome.
I'm not saying that it really is the video driver.  But Gnome and Xfce (any any other desktop) must interact with the video. It could be the combination. Since it's working for me and I haven't heard of any other T61 owner with this same exact problem, I suspect it's a setting somewhere on your installation. Nevertheless, you might try going back to the nv driver just to prove that it is not the driver. Meantime, search the e-list archives and, if you still cannot figure it out, post the query on the list. There are people on the e-list who are way smarter than me. :)

---

