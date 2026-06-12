---
title: "[SOLVED] Video Card Upgrade - ATI x800 -&amp;gt; Nvidia 7900GTO - Advice Wanted"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-12-07
I'm about to purchase an Nvidia 7900GTO to replace my ATI X800.  Not that there's anything worng with the x800, it's a great card.

The problem is I'm tired of waiting for good driver support.  I'm currently using the restricted driver from the repos.  I suspect I should disable that...???

Here's what **I THINK **I need to do.  Please correct me if I'm worng or missed any steps.

```
sudo gedit /etc/X11/xorg.conf
```
Make sure or change the device to VESA

Then I plan to..
```
sudo dpkg-reconfigure xserver-xorg
```

Reboot

Install restricted driver

**Also I would appriciate any advice as to the BEST/STABLE driver to use with this new card.**

Thanks in advance.

---

### Post by crjackson on 2007-12-07
Well I just made the purchase.  It's a done deal.  I hope to get some info soon.

---

### Post by rfruth on 2007-12-07
Please do tell cause I'me about to do something similar  (MIS = MSI in your sig?)

---

### Post by rsambuca on 2007-12-07
Be warned that the nvidia-glx-new drivers have a slow memory leak.  You will have to restart X every so often.  The video quality with them is much better than the older ones though, so I have kept them for now.

---

### Post by crjackson on 2007-12-07
> **rfruth said:**
> Please do tell cause I'me about to do something similar  (MIS = MSI in your sig?)

I just fixed the SIG, and yes, it was supposed to be MSI.  Thanks for pointing that out.

---

### Post by crjackson on 2007-12-07
> **rsambuca said:**
> Be warned that the nvidia-glx-new drivers have a slow memory leak.  You will have to restart X every so often.  The video quality with them is much better than the older ones though, so I have kept them for now.

Is that the driver that is loaded from the restricted driver manager?  Can you reccomend a driver without a memory leak?

Also, does the procedure above seem to be correct or does it need some adjustments?

Thanks

---

### Post by rsambuca on 2007-12-07
Yeah, that will work.  The Restricted Drivers Manager will load the glx-new driver though.  You can always change it later, so I would just get it up and running and it is an easy switch later if you want.

---

### Post by crjackson on 2007-12-07
> **rsambuca said:**
> Yeah, that will work.  The Restricted Drivers Manager will load the glx-new driver though.  You can always change it later, so I would just get it up and running and it is an easy switch later if you want.

Thanks - If I decide to use a later driver with envy or something, do I need to disable the restricted driver before doing so?

---

### Post by rsambuca on 2007-12-07
You would just change your xorg back to nv driver, and then remove the driver (I would just use Synaptic), and then install nvidia-glx driver.

---

### Post by crjackson on 2007-12-07
> **rsambuca said:**
> You would just change your xorg back to nv driver, and then remove the driver (I would just use Synaptic), and then install nvidia-glx driver.

Got it - Thanks.  I won't have the card for a few days (online purchase).  I'll post back with results once I get it.

---

### Post by crjackson on 2007-12-10
Still waiting for the beautiful brown truck that says UPS.

---

### Post by crjackson on 2007-12-14
WOW! That was easy...

I got lazy and didn't edit my xorg.conf or turn off restricted drivers.  I just booted into recovery mode, and it told me my video card driver was wrong.  It automatically set it to VESA, and gave me the option to PICK my driver from a long list.  I picked Nvidia and it booted right up.  Then it told me about the available restricted driver so I enabled it and rebooted.

BANG!  New card working great, and desktop effects enabled for the first time.  NICE...

I finally have a splash screen for the 1st time too.  The only problem is that now my login screen shows at 640x480.  How do I change the rez of the loging screen to match the 1024x786 of the splash screen?

---

