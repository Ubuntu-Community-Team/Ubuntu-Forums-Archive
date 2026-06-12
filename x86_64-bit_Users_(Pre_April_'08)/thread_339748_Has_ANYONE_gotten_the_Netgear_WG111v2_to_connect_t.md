---
title: "Has ANYONE gotten the Netgear WG111v2 to connect to an AP in Edgy AMD64?"
date: 2007-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_anjan on 2007-01-16
The topic's title says more than enough. Really, this seems to be a herculean task, getting wifi to work on the 64 bit edition of Edgy.

---

### Post by t_anjan on 2007-02-21
It's been a month since I started this thread. I have given up after literally trying out every helpful topic on this site.

Just wondering if anyone else has come up with something brilliant to make the WG111v2 connect to an access point....

---

### Post by phossal on 2007-02-23
Have you tried the ndiswrapper method?

---

### Post by dfreer on 2007-02-23
BTW, you should prolly keep all your posts in ONE thread t_anjan. I understand that it can be frustrating trying to get something to work... 

The original thread (or at least the one with the most information) can be found [_*here (ubuntu forums)*_]("http://www.ubuntuforums.org/showthread.php?t=338597").

---

### Post by t_anjan on 2007-02-26
> **phossal said:**
> Have you tried the ndiswrapper method?

Yes, I tried the ndiswrapper method also, before switching back to the built-in drivers. Using ndiswrapper, I could not even get the WG111v2 to associate with the AP.

Please refer to this thread for a more detailed explanation and status of my problem:
[http://ubuntuforums.org/showthread.php?t=370051](http://ubuntuforums.org/showthread.php?t=370051)

---

### Post by phossal on 2007-02-26
The default drivers do not work on the 64bit platform. They hardly work on the 32bit platform - they're *experimental*. I have an AMD64, but run 32bit Ubuntu with ndiswrapper for precisely this reason. If you installed ndiswrapper, but couldn't get the device to associate, it's as likely that you were simply using the wrong driver as it is that it doesn't work on 64. Reassuring, isn't it? When you download the drivers from Netgear, they're packaged in folders for each version of Windows. Choose XP, and your device won't work. Download version 1.3, and try the Win98 INF file.

---

### Post by t_anjan on 2007-02-26
> **phossal said:**
>  When you download the drivers from Netgear, they're packaged in folders for each version of Windows. Choose XP, and your device won't work. Download version 1.3, and try the Win98 INF file.

Let me make sure I understand you right. According to you, the only way to get even the Win 98 drivers to work with ndiswrapper is to first install the 32 bit Ubuntu?

---

### Post by phossal on 2007-02-26
No, what I meant is that *if* we assume it's possible to get up and running on 64bit Ubuntu, I would use ndiswrapper. The *default* drivers (rtl8187) barely work on the 32bit Ubuntu. So, if I had installed ndiswrapper, and found the drivers didn't work, I would try *different* drivers under ndiswrapper, because the various drivers from Netgear don't all work under ndiswrapper for every device (even on a 32 bit).

Once I had tried the six or seven drivers available from netgear, I would either give up on the WGv2, or install 32bit Ubuntu. ;)

---

### Post by t_anjan on 2007-02-27
Aren't all the drivers on the Netgear website designed for a 32 bit OS? Will those 32 bit drivers (e.g. Win 98 ) work with ndiswrapper on a 64 bit OS?

---

### Post by t_anjan on 2007-02-27
Well, answering my own query: I installed ndiswrapper following your guide at [http://phossal.com/thread?view=702216933](http://phossal.com/thread?view=702216933) .

The first problem I had was with the following command
```
sudo modprobe ndiswrapper
```

I got the following error message:
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/misc/ndiswrapper. ko): Invalid module format
```

I solved that by uninstalling ndiswrapper, manually deleting the "ndiswrapper.ko" file and reinstalling ndiswrapper.

I installed version 1.37, BTW.

Then, I carried on and rebooted the computer as given in the guide. Then, after logging back in I executed 
```
sudo ndiswrapper -l
```

This gave me the following output:
```
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: r8187)
```

All OK, right? Well, it wasn't so. On executing **"dmesg"**, I noticed this in the output:
```
[   62.751914] rtl8187: Setting SW wep key
```

This told me that ndiswrapper hadn't yet gotten control of my WG111v2. This, despite blacklisting the Realtek drivers according to the guide.

But, wait, "r8187" is not mentioned in the guide. Only the following drivers are mentioned:
```
blacklist r**tl**8187
blacklist r8187**b**
```

So I added the line **"blacklist r8187"** to the **"blacklist"** file and just to make sure, I also executed the following command:
```
sudo rmmod r8187
```

So, now, I re-inserted my WG111v2 and **dmesg** now shows this:
```
[  737.080685] ndiswrapper (check_nt_hdr:153): [COLOR="Red"]kernel is 64-bit, but Windows driver is not 64-bit[/COLOR];bad magic: 010B
[  737.080691] ndiswrapper (load_sys_files:217): couldn't prepare driver 'net111v2'
[  737.081118] ndiswrapper (load_wrap_driver:119): couldn't load driver net111v2; check system log for messages from 'loadndisdriver'
```

Now, I've got ndiswrapper taking control of my WG111v2. But I'm forced to return to my original question: [COLOR="Red"]*How do I get the Win 98 drivers to work on my 64 bit Edgy?*[/COLOR]

BTW, now I have no **wlan0** in **iwconfig**

---

### Post by phossal on 2007-02-27
> **phossal said:**
> The default drivers do not work on the 64bit platform. They hardly work on the 32bit platform - they're experimental.** I have an AMD64, but run 32bit Ubuntu with ndiswrapper for precisely this reason.** If you installed ndiswrapper, but couldn't get the device to associate, it's as likely that you were simply using the wrong driver as it is that it doesn't work on 64. Reassuring, isn't it? When you download the drivers from Netgear, they're packaged in folders for each version of Windows. Choose XP, and your device won't work. Download version 1.3, and try the Win98 INF file.

No, what I meant is that *if* we assume it's possible to get up and running on 64bit Ubuntu, I would use ndiswrapper. The *default* drivers (rtl8187) barely work on the 32bit Ubuntu. So, if I had installed ndiswrapper, and found the drivers didn't work, I would try *different* drivers under ndiswrapper, because the various drivers from Netgear don't all work under ndiswrapper for every device (even on a 32 bit).

**Once I had tried the six or seven drivers available from netgear, I would either give up on the WGv2, or install 32bit Ubuntu.** ;)

I would give up. And install 32bit Ubuntu. 

I apologize for not listing the *blacklist r8187*, it's amazing my editors missed it and still paid me. And I apologize for not having better advice to offer you for getting rolling on your AMD64 with the WG111v2. I have heard it's not possible to install the hardware on a 64bit platform, and my own experience leads me to believe that, but I'm not *certain.* I chose to install 32bit Ubuntu, as I mentioned a few posts ago, because I was sick of fighting it.

Before I managed to get the hardware working, and before confirming the different chipsets, before I had created the thread on it, I was here in the forums, impatient but hopeful, frustrated but determined, and the response I got to my questions was this: "the device is finicky, and works 50% of the time at best. You should have been more careful in selecting hardware that was compatible. Stop complaining. At least you'll know for next time."

I just wanted my advice to be slightly better than that. Regards.

---

### Post by phossal on 2007-02-27
If it shows my intent was sincere, I did some more research and this is what I've found: Netgear doesn't produce a 64bit driver for this device. Even their "vista beta" driver is 32bit. ndiswrapper runs in 64 bit mode, but according to their own forum:
> [ Can I use 32-bit Windows driver in 64-bit mode? No. ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_32-bit_Windows_driver_in_64-bit_mode.3F")

---

### Post by t_anjan on 2007-02-28
> **phossal said:**
> If it shows my intent was sincere, I did some more research and this is what I've found: Netgear doesn't produce a 64bit driver for this device. Even their "vista beta" driver is 32bit. ndiswrapper runs in 64 bit mode, but according to their own forum:

Hey, I don't doubt the fact that your intent was sincere. Why should I complain when, very obviously, you are the only one who has replied on this thread?

I've always known that Netgear doesn't support 64 bit operating systems. Indeed, I had battled his whole problem for a month earlier before giving up and taking a small break. I already had a feeling that the device may not work on the 64 bit Edgy, even though Realtek has 64 bit drivers for the WG111v2 (which I use on x6 XP). Moreover, Vistal x64 automatically downloaded and installed the Realtek driver for the dongle.

It was because I felt that 64 bit Ubuntu alone had this problem, I titled this thread as it is.

Anyway, I don't understand one thing. Since Netgear doesn't provide 64 bit drivers at all, it should mean that both Microsoft and Ubuntu are equally at a disadvantage when it comes to 64 bit versions of their respective OSes. But how come Microsoft is able to use the Realtek 64 bit drivers successfully, but Ubuntu is not?

Realtek is providing Linux drivers: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#362](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#362)

I have another doubt to be clarified. Sorry, if I'm testing your patience. The built-in drivers were the Realtek drivers. Will it make any difference if I loaded the Realtek 64 bit windows drivers through ndiswrapper?

---

### Post by t_anjan on 2007-02-28
Well, I just noticed something else on the ndiswrapper FAQ page

> **Is master mode or promiscuous mode supported? **

No! NDIS doesn't support Master/Repeater/Monitor modes. The only modes supported are Ad-Hoc and Managed. Note that some drivers may support features that are not in NDIS e.g., showing signal noise and possibly Master mode, but they are proprietary and no documentation available for them, so such features won't be supported by ndiswrapper.

When I was able to do iwlist scan, the output always used to say "Mode: Master". In fact, the only way I was able to associate with the AP was to insert the line "wireless-mode Master" in the interfaces file. Mind you, though, that I was only able to associate, but DHCP was not working. See this thread for more details: [http://ubuntuforums.org/showthread.php?t=370051](http://ubuntuforums.org/showthread.php?t=370051)

Anyway, does this mean that ndiswrapper won't work for me? Or is there some way I can change the mode in my router?

---

### Post by hise0001 on 2007-02-28
I gave up on the netgear wg111 about a year ago.  I couldn't get it to work reliably on 32bit ubuntu.  When I could connect I would experience random drops.

I got wireless bridge and haven't looked back..... though that may not be the best choice if you're using a laptop.

Good luck.

--Hise

---

### Post by flapane on 2007-02-28
My father simply gave up, with 64bit and 32bit one, and switched back to XP, he need a fully work laptop for his work

---

### Post by Genin on 2007-02-28
Hello you all,

I'm the owner of one Netgear wg111, does it means that I have no options of using my wireless network adapter if I'm 64bits Ubuntu user??????
Does anyone of you have this wireless adapter installed and working? If someone have it, please explain to us how can we do it too, I think it's not very good for Linux such kind of things..... I have been using my wireless on Windows 2000 with no problems, I can believe that it doesn't work on Linux......very bad news.

Thanks. Regards.

---

### Post by phossal on 2007-02-28
> **t_anjan said:**
> When I was able to do iwlist scan, the output always used to say "Mode: Master". In fact, the only way I was able to associate with the AP was to insert the line "wireless-mode Master" in the interfaces file.

I never use /etc/network/interfaces to configure my devices. I do it with iwconfig and dhclient. *iwconfig* lets you set the mode as an argument to the command. "man" iwconfig for details, if you haven't.

---

### Post by t_anjan on 2007-03-01
> **phossal said:**
> I never use /etc/network/interfaces to configure my devices. I do it with iwconfig and dhclient. *iwconfig* lets you set the mode as an argument to the command. "man" iwconfig for details, if you haven't.

Using iwconfig also, I need to to use "mode Master" as an argument to associate with the AP. Actually, I'm not sure there is a difference between using iwconfig or the interfaces file.

I've seen many people getting "Mode: Managed" when they do an "iwlist scan". Any idea why it is Master for me?

---

### Post by t_anjan on 2007-03-01
> **Genin said:**
> Hello you all,

I'm the owner of one Netgear wg111, does it means that I have no options of using my wireless network adapter if I'm 64bits Ubuntu user??????
Does anyone of you have this wireless adapter installed and working? If someone have it, please explain to us how can we do it too, I think it's not very good for Linux such kind of things..... I have been using my wireless on Windows 2000 with no problems, I can believe that it doesn't work on Linux......very bad news.

Thanks. Regards.

I'm also looking for someone with a success story with 64 bit Ubuntu. Nobody's answered yet.

---

### Post by t_anjan on 2007-03-01
> **hise0001 said:**
> I got wireless bridge and haven't looked back..... though that may not be the best choice if you're using a laptop.

I don't understand what you mean by a Wireless Bridge. I read a few definitions, but couldn't really understand the distinction between a WiFi Dongle and a WiFi Bridge.

---

### Post by phossal on 2007-03-01
A wifi dongle would connect to your device like our WG111v's, but a bridge connects like a router, using cat 5, but connects wirelessly to the *actual* router. The *important* difference is in the type of driver your machine would use. While installing the WG111v2 was a struggle, connecting directly to the *router*, using cat, was no problem at all. It was plug and play easy.

---

### Post by t_anjan on 2007-03-01
Oh, OK. Thanks for the quick explanation. Any idea about my wireless mode question? Why is it that I get "Master" when I scan?

---

