---
title: "Lenovo X300 intel 4965agn wifi WPA/WPA2 not working"
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by toskala on 2008-10-09
Hi there,

I just got myself a Lenovo X300, so far all works fine except the Intel 4965agn wireless device.

Here is what I did so far:

- Installed Ubuntu 8.04 64bit release. 
- Upgraded the kernel to 2.6.24-21-generic.
- Installed WICD

All this did just partially help. The driver seems to have problems connecting to accesspoints using WPA/WPA2. I discovered an unprotected AP here and the card connected to it just fine.

I stumbled over a couple of websites that claim to host proper solutions for that card, but for some reason I don't get that working.

Main website I was looking at is [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org), didn't enlighten me.

I've tried building the compat-wireless drivers from source, which can be found here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) but they actually won't even compile.

So here I am, stuck. Is there anyone out there who got this solved?

Cheers,
toskala

---

### Post by John Jason Jordan on 2008-10-09
> **toskala said:**
> I just got myself a Lenovo X300, so far all works fine except the Intel 4965agn wireless device.

Main website I was looking at is [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org), didn't enlighten me.

I've tried building the compat-wireless drivers from source, which can be found here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) but they actually won't even compile.
I have a 4965agn in my Lenovo T61. There have been issues with it, but I have it working fine now. Having said that, I never connect with WPA/WPA2.

I suggest you go to the Linux Thinkpad e-mail list. I think you will lots of people there who are more knowledgeable than me:

The linux-thinkpad mailing list home page is at:
[http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad]("http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad")

---

### Post by toskala on 2008-10-09
Thanks for that hint, I didn't even know there is such a mailinglist :-).

But I have an update to the whole thing. 
I was checking out the current GIT sources from component-wireless drivers directly from kernel.org. Good news is the fresh checkout compiles but when I try to load all modules I get unknown symbol errors in dmesg when loading iwlwifi_mac80211.

This somehow could maybe sorted out but I didn't figure out how, yet.

Cheers,
toskala

---

### Post by Robstarusa on 2008-10-10
I think 2.6.26/2.6.27 are supposed to have large wifi improvements for that card.

Rob

---

### Post by toskala on 2008-10-10
Another Update... :-)

I just downloaded the Intrepid Ibex daily cdimage and started the LiveCD. Wireless does unfortunately still not connect to WPA/WPA2 out of the box.

I guess I'll have to wait 'till Intrepid is released, 30.Oct isn't that far and give the update to kernel 2.6.27-7 a try then, current livecd includes 2.6.27-6 with which there was no luck.

Btw. is the e1000e bug already fixed in 2.6.27-6?

Cheers,
toskala

---

### Post by toskala on 2008-10-12
Okay guys, I have that damn thing working now. The solution is kind of stupid.

I have an Netgear accesspoint here that allows me to create a wireless lan with WPA2-PSK, remember PSK stands for Pre-Shared-Key. 

Keeping this in mind I was trying to set up a connection in WICD with authentication type "PSK". Just like I configured in the accesspoint.

It never worked until I accidentally connected today using the WICD authentication type "Password".

Can anyone explain this to me? Why is the setting in WICD obviously wrong? Do I miss something?

Cheers,
toskala

---

