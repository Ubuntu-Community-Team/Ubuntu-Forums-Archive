---
title: "Broadcom 802.11g Chipset (Airport Extreme) Reverse Engineered"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Entity on 2005-12-05
[http://bcm-specs.sipsolutions.net/announcement.pdf](http://bcm-specs.sipsolutions.net/announcement.pdf)

---

### Post by ssam on 2005-12-05
this looks like good progress.

lets hope the driver project goes smoothly.

---

### Post by jecos on 2005-12-06
Yeah I hope its out before the kernel switches to 4k stacks only.. ndiswrapper needs 8k stacks..

---

### Post by AhronZombi on 2005-12-06
it works now [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) woot

---

### Post by ssam on 2005-12-06
[https://lists.berlios.de/pipermail/bcm43xx-dev/2005-December/000582.html](https://lists.berlios.de/pipermail/bcm43xx-dev/2005-December/000582.html)

> I am writing this mail on my PowerBook and it is sent
wireless to my AP.
That means, we can transmit real data, if you did not get it, yet. :)

That does _not_ mean, that it completely works, yet.
The team is in the progress of writing a SoftwareMAC layer,
which is needed for the bcm device. The SoftMAC is still very
incomplete. So do not expect to do any fancy stuff like WPA
or something line that with it.
Please be patient, thanks. :)

---

### Post by spoetnik on 2005-12-06
Let's hope this will be implemented in the next ubuntu release!!!

---

### Post by Entity on 2005-12-06
[QUOTE=spoetnik]Let's hope this will be implemented in the next ubuntu release!!![/QUOTE]

It is already in Dapper's kernel :)

$ cat /boot/config-2.6.15-6-powerpc |grep BCM43 && cat /boot/config-2.6.15-6-powerpc |grep SOFTMAC
CONFIG_NET_BCM430X=m
# CONFIG_NET_BCM430X_DEBUG is not set
CONFIG_IEEE80211_SOFTMAC=m

---

### Post by jecos on 2005-12-06
[QUOTE=Entity]It is already in Dapper's kernel :)

$ cat /boot/config-2.6.15-6-powerpc |grep BCM43 && cat /boot/config-2.6.15-6-powerpc |grep SOFTMAC
CONFIG_NET_BCM430X=m
# CONFIG_NET_BCM430X_DEBUG is not set
CONFIG_IEEE80211_SOFTMAC=m[/QUOTE]

sweet changing to dapper on my laptop to test it.. 

This threads needs a sticky!

---

### Post by spoetnik on 2005-12-06
Do I understand this right?? A dist-upgrade to daper will give me airport extreme support??

tears in my eyes!!

This is one of those days!!
Huray for Ubuntu, and those people reverse engineering the Broadcom driver!!

---

### Post by tokyovigilante on 2005-12-06
A dist-upgrade at this stage won't get you the driver I don't think. The code has yet to make it from the BCM430X team to Kernel.org, into a 2.6.15 (>2.6.14-3 anyway) kernel and back to us.

In the meantime, I'd suggest getting the source code for the 2.6.15 series kernels from the Dapper repos, building a custom kernel from your Breezy config, then obtaining the SVN driver from Berlios and building it yourself. 

Currently I think it's just Managed mode, monitor with WEP encryption, no adhoc/WPA yet, but it's awesome what they've been able to achieve just through reverse engineering in the face of massive opposition from Apple/Broadcom.

Now there's **nothing** to stop me running Linux on my iBook!

(EDIT) I've just seen this for Gentoo, you shouldn't have too much trouble translating for Ubuntu.[http://forums.gentoo.org/viewtopic-t-409194.html]("http://forums.gentoo.org/viewtopic-t-409194.html")

---

### Post by tokyovigilante on 2005-12-06
Sorry I lied, the latest version went into the 2.6.15-7 kernel on Dapper this morning.

> Changes:
linux-source-2.6.15 (2.6.15-7.9) dapper; urgency=low
.
   Changes by Ben Collins:
.
   * Patch from Keybuk: Revert some of our modular ide patch. The general issue
     is that we do things different in dapper than we did in breezy, which
     makes this patch wrong now.
.
   * Applied patch for via-sound irq problem (from breezy).
.
   [B]* Added HP 4318 id to bcm43xx driver.
.
   * Upgraded bcm43xx and softmac to latest code. Should have working xmit/recv[/B]
     now.
.

---

### Post by autumnsweater on 2005-12-06
So, I'm a complete Linux newbie, and from reading this thread I gather that I can somehow run Ubuntu now with my Airport Extreme card, but I'm not gathering exactly *how* I can do that. Any chance someone can write an idiot-proof step-by-step? Because I want to get Ubuntu on my iBook posthaste.

---

### Post by tokyovigilante on 2005-12-06
> **autumnsweater]Any chance someone can write an idiot-proof step-by-step? Because I want to get Ubuntu on my iBook posthaste.[/QUOTE]
Hmm, that's a big question all in one go  said:**
> 
You would also have to obtain the firmware (with fwcutter from your MacOSX partition).

You'll need to extract the firmware from the Apple driver using fwcutter:

```
sudo apt-get install subversion
svn checkout http://svn.berlios.de/wsvn/bcm43xx/trunk fwcutter
cd ~/fwcutter
make
sudo make install
```

Get the Airport firmware either by downloading from the Apple site, or use the one from your MacOS install: /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2. I think this only works for Panther and below, Tiger users will need to download the old version from Apple.

```
fwcutter /path/to/AppleAirPort2
sudo make installfw
```

Now that the firmware is in the right place:

```
modprobe bcm43xx
iwconfig
```

Try it out!!

Get the name of the wireless connection from iwconfig (will probably be eth1 if your wired network is eth0).

```
sudo iwconfig essid <Your ESSID>
sudo iwconfig mode managed
sudo ifconfig <wireless connection> up
dhclient <your wireless connection>
```

If DHCP doesn't work, try assigning a static IP.

If you're happy and it isn't too broken for you to use, then install Dapper using the latest Install daily build CD, and repeat the above instructions.

If the Dapper LiveCD is to broken for your system, try a Breezy (5.10, current stable) LiveCD. Wireless won't work on this, but you should be able to get an idea of how the system runs. You'll need to install Breezy and build a new kernel and the drivers if you have to go this way.

At the moment the above is an amalgamation of various sources and refdoc's helpful input below. If you have issues check the Gentoo Howto above, I'll try the above myself over the weekend and make any corrections, and possibly make a proper Howto. If anyone spots corrections let me know (partic concerning the svn section).

Bottom line try a Dapper LiveCD and see how you go :).

---

### Post by Entity on 2005-12-06
[QUOTE=tokyovigilante]A dist-upgrade at this stage won't get you the driver I don't think.[/QUOTE]

The driver is in the kernel... but it is already obselete just like the softmac is also present in kernel.

[QUOTE=tokyovigilante]In the meantime, I'd suggest getting the source code for the 2.6.15 series kernels from the Dapper repos, building a custom kernel from your Breezy config, then obtaining the SVN driver from Berlios and building it yourself.
[/QUOTE]

I think it won't build because of the bcm430x and softmac present in Dapper's kernel. I would build the custom kernel with these modules disabled. Then it would compile.

---

### Post by tokyovigilante on 2005-12-06
> **Entity]The driver is in the kernel... but it is already obselete just like the softmac is also present in kernel.[/QUOTE]


[QUOTE=tokyovigilante]Changes:
linux-source-2.6.15 (2.6.15-7.9) dapper said:**
> * Upgraded bcm43xx and softmac to latest code. Should have working xmit/recv
now[/B]


This was posted to the dapper-changes list this morning, I inferred from it that if you built a 2.6.15-7 kernel from the new sources with the *CONFIG_NET_BCM430X=m* and *CONFIG_IEEE80211_SOFTMAC=m* options set, ie build BCM430x and SoftMAC as modules then modprobed them and added them to /etc/modules that Airport Extreme wireless would work without further ado. I'll give it a go tonight and see what happens.

---

### Post by refdoc on 2005-12-06
You would also have to obtain the firmware (with fwcutter from your MacOSX partition).

---

### Post by tokyovigilante on 2005-12-06
[QUOTE=refdoc]You would also have to obtain the firmware (with fwcutter from your MacOSX partition).[/QUOTE]
Thanks refdoc you're right. You can also extract it from the drivers at Apple website.

The link to the Gentoo Howto above mentions the process of obtaining the firmware, and the rest of the instructions should be relatively easy to adapt to Ubuntu.

---

### Post by refdoc on 2005-12-07
'bcm43xx' needs to be added to /etc/modules.


all 'fw' modules otained with fwcutter need to be copied into /lib/firmware.

---

### Post by refdoc on 2005-12-08
I have installed the new kernel and did the fwcutter bit.

I certainly have gained a new network card ion ifconfig , but unfortunately not much more as yet.

dhclient eth1 leads to nothing at all, and occasionally the system freezes and needs to be hard reset.


But i am happy. This will in a short while work fine and then I will delete the OSX partition...

---

### Post by tokyovigilante on 2005-12-08
You'll need to set up the wireless connection before using it. I've added a bit to the above instructions. Thanks for being brave and trying this out!

---

### Post by bartong on 2005-12-09
So I'm not too keen on recompiling anything and am more than willing to wait for this to be included in Ubuntu "out-of-the-box".

Could someone enlighten me though:  What are the chances that this could make it into the final public release of Ubuntu 6.04 Dapper Drake?

If it is included, will it be as simple as install and go, the same as it is for existing supported wireless devices?

---

### Post by monway on 2005-12-09
[quote=bartong]So I'm not too keen on recompiling anything and am more than willing to wait for this to be included in Ubuntu "out-of-the-box".

Could someone enlighten me though: What are the chances that this could make it into the final public release of Ubuntu 6.04 Dapper Drake?

If it is included, will it be as simple as install and go, the same as it is for existing supported wireless devices?[/quote]

I can see by the time Dapper is released, it might be backported. Something like this generally does not get in the initial release however, followup update might. Either way I can see it showing up in a backport around the time of release of Dapper. Unless otherwise, the dapper dev team accepts it into mainstream.
my 2cents.

---

### Post by Janfi on 2005-12-09
[QUOTE=refdoc]I have installed the new kernel and did the fwcutter bit.[/QUOTE]

1) Did you install the kernel binary from dapper, or a recompiled kernel from linux-source-2.6.15 (2.6.15-7.9) provided in dapper ?

2) I tried to compile kernel from linux-source-2.6.15 (2.6.15-7.9) provided in dapper. I'm not used to do this on ubuntu/debian (but with mandriva), so after compilation and installation success, I can't boot on my new kernel. When I select it on yaboot, there is a kernel panic (/boot/initrd.img : not such file, ramdisk load fail). I suppose that it's because I forgot to add the option ```
--initrd
``` to my ```
make-kpkg --append-to-version=blahblah kernel_image
``` :oops: 

Should I add "binary" equally ? The result would be ```
make-kpkg --append-to-version=blahblah kernel_image --initrd binary
```


Can you confirm this ? Thank you in advance.

---

### Post by tokyovigilante on 2005-12-09
[QUOTE=monway]I can see by the time Dapper is released, it might be backported. Something like this generally does not get in the initial release however, followup update might. Either way I can see it showing up in a backport around the time of release of Dapper. Unless otherwise, the dapper dev team accepts it into mainstream.
my 2cents.[/QUOTE]

The open source driver is included in Dapper now, and it is possible for the fwcutter utility to be included, and it most likely will at least be in universe. However the Apple firmware for the Airport is not able to be distributed as it is proprietary code. So this is unlikely to ever work "out of the box." A possible workaround could be to include the fwcutter utility with a script to extract the firmware from a MacOS mount or from a downloaded driver, but the firmware cannot ship with Ubuntu.

[QUOTE=Janfi]Should I add "binary" equally ? The result would be
make-kpkg --append-to-version=blahblah kernel_image --initrd binary
[/QUOTE]
Appending binary won't hurt, but I haven't had problems with kernels built without it however. The --initrd is essential to allow the kernel to load ide/sata etc drivers that have been built as modules.

If you're using Dapper anyway the best option would be to upgrade to the standard 2.6.15-7 kernel, but if you're using Breezy the Dapper kernel is incompatible, and you'll have to recompile one. I doubt the 2.6.15 kernel will be backported to Breezy, it would break too much else, plus currently the driver (barely) works on open networks only, so that's not much good for general use.

I haven't been able to get my iBook to boot from an external USB drive to test this, so I'll download a LiveCD tonight and try that.

---

### Post by refdoc on 2005-12-09
There is no need to compile anything. The new dapper kernel has the feature, just simply not loaded as a default - for obvious reasons.

---

### Post by Entity on 2005-12-09
[QUOTE=refdoc]I have installed the new kernel and did the fwcutter bit.

I certainly have gained a new network card ion ifconfig , but unfortunately not much more as yet.

dhclient eth1 leads to nothing at all, and occasionally the system freezes and needs to be hard reset.


But i am happy. This will in a short while work fine and then I will delete the OSX partition...[/QUOTE]I have the same problem.

[QUOTE=tokyovigilante]You'll need to set up the wireless connection before using it. I've added a bit to the above instructions. Thanks for being brave and trying this out![/QUOTE]That make sens since you can't use it before setting it up right?! The freeze problem remains. Not sure if it's a BCM43XX or SOFTMAC problem... but let's wait for newer code ;)

---

### Post by refdoc on 2005-12-09
Setting it up - how do make it accept a WEP code - or doe sthis not yet work?

---

### Post by bartong on 2005-12-09
[QUOTE=tokyovigilante]The open source driver is included in Dapper now, and it is possible for the fwcutter utility to be included, and it most likely will at least be in universe. However the Apple firmware for the Airport is not able to be distributed as it is proprietary code. So this is unlikely to ever work "out of the box." A possible workaround could be to include the fwcutter utility with a script to extract the firmware from a MacOS mount or from a downloaded driver, but the firmware cannot ship with Ubuntu.[/QUOTE]

Right, now I see the issue.  But still, if the driver is included in Dapper, no doubt someone will write a howto or a script to make it easy for newbies like myself to extract/download the firmware and get everything working.  I hope! :p

---

### Post by tokyovigilante on 2005-12-09
[QUOTE=refdoc]Setting it up - how do make it accept a WEP code - or doe sthis not yet work?[/QUOTE]
I don't think it does yet, but if it did, the command would be
iwconfig <wireless net> key <your WEP key here>.

[QUOTE=bartong]But still, if the driver is included in Dapper, no doubt someone will write a howto or a script to make it easy for newbies like myself to extract/download the firmware and get everything working. I hope! [/QUOTE]
The above instructions should be enough to get the driver running with the current install/live CDs. Its inclusion in Dapper is not an issue as it is now a part of the standard kernel and built as a module by default. As I've said whether it works for you is independent of the Ubuntu devs, but up to the BCM430x team. They've done extremely well to get this far, but if you're planning to use this for some real work, you'd be better off waiting for WEP/WPA support and some bugfixes.

---

### Post by zoglesby on 2005-12-09
Alright, so I would like to install the new drivers but I can't get Dapper to install on my PowerBook (it frezzes after the cd is ejected on the unmount file system step). I was just going to compile the new kernel and everything that I need to get it to work on Brezzy but I can't seem to find a copy of the 2.6.15 kernel any place that I look all that I can find is patches. Can anyone help me with either problem (ie the install or finding the kernel) Thanks.

---

### Post by tokyovigilante on 2005-12-09
[QUOTE=zoglesby]Alright, so I would like to install the new drivers but I can't get Dapper to install on my PowerBook (it frezzes after the cd is ejected on the unmount file system step). I was just going to compile the new kernel and everything that I need to get it to work on Brezzy but I can't seem to find a copy of the 2.6.15 kernel any place that I look all that I can find is patches. Can anyone help me with either problem (ie the install or finding the kernel) Thanks.[/QUOTE]

I'm not sure what's going on with your install problem, did yaboot install properly? Are you trying to dual-boot MacOS and Linux?

The latest version of Dapper has the 2.6.15-7 kernel by default, so that shouldn't be an issue. If you have a pre 20051208 version, you can obtain the latest kernel via an ```
apt-get update
apt-get upgrade
```
 ```
apt-get install linux-image-2.6.15
``` will explicitly get it for you.

---

### Post by zoglesby on 2005-12-09
I think that yaboot installed properly. I didn't get any errors. I have tried a few diffrent daily builds of dapper and they all fail at the end of the first stage of install just after the cd is ejected and it goes to unmount the files system it stops. I am not trying to dual boot. My PowerBook is a 12 inch 1.33 GHz if that helps any.

---

### Post by worm13 on 2005-12-10
[QUOTE=refdoc]Setting it up - how do make it accept a WEP code - or doe sthis not yet work?[/QUOTE]
WEP works great. I'm working with my ibook throw a 64bit encrypted wireless. 

I have written a howto install airport extreme in breezy. You can found it in [Catalan]("http://bulma.net/body.phtml?nIdNoticia=2262") and [Spanish]("http://www.ubuntu-es.org/node/11044"). Maybe i will wrote a traduction to English. The problem is just I think that my english is so poor :???:

---

### Post by zoglesby on 2005-12-10
I really just need you to translate a lines, and then I would be golden.

> cambiau allà on posi "breezy" per "dapper"

Thanks. I think that I can figure it out if I know what that means.

---

### Post by MetalMusicAddict on 2005-12-10
Is any of this gonna help Dell users with Broadcom based cards?

---

### Post by wanderfowl on 2005-12-10
[QUOTE=worm13]WEP works great. I'm working with my ibook throw a 64bit encrypted wireless. 

I have written a howto install airport extreme in breezy. You can found it in [Catalan]("http://bulma.net/body.phtml?nIdNoticia=2262") and [Spanish]("http://www.ubuntu-es.org/node/11044"). Maybe i will wrote a traduction to English. The problem is just I think that my english is so poor :???:[/QUOTE]


I'll try a translation, give me an hour or so, I'll post it here.

---

### Post by wanderfowl on 2005-12-10
[QUOTE=wanderfowl]I'll try a translation, give me an hour or so, I'll post it here.[/QUOTE]

Airport Extreme on GNU/Linux
Posted by Worm on Sat, Dec. 10th, 2005 -10:47- Hardware

This article is a translation of the article of the same name that was already published in Bulma.  (Translated again into English.  Errors are possible, and apologized for in advance)

Finally, we can enjoy native support for the Airport Extreme and other cards with the bcm43xx Chipset.

At the moment the drivers are very unstable and don't support some things, but still, they work!  Here, I'll give the steps to install the drivers in Ubuntu.

First Step: Obtain the 2.6.15 Kernel

The drivers only function with the 2.6.15 Kernel (or higher), so we must do this.  I recommend that you all download the latest kernel from the Dapper repository, it already has the bcm43xx module incorporated, and this will save us some work.  
Instructions for installing the Kernel:
    * #cp /etc/apt/sources.list /etc/apt/sources.list_breezy
    * #gedit /etc/apt/sources.list
    * change everything that says "breezy" to dapper
    * #apt-get update
    * #apt-get install linux-image-2.6.15-7-powerpc linux-headers-2.6.15-7-powerpc linux-restricted-modules-2.6.15-7-powerpc (Attention!! Because of the high package frequency of Dapper, there's probably a more recent version.)
    * #cp /etc/apt/sources.list_breezy /etc/apt/sources.list

Second Step: Installing the drivers and their dependencies

Softmac IEEE 802.11:

    * #apt-get install mercurial
    * #hg clone [http://softmac.sipsolutions.net/source](http://softmac.sipsolutions.net/source)
    * #cd source
    * #make
    * #insmod ieee80211softmac.ko

Fwcutter:
This program extracts the firmware necessary to make the drivers work.  The archive that this program needs can be extracted from the Airport Extreme drivers for OS X.  To facilitate things, I've uploaded the necessary archive to my home server.  You can download it from here [http://62.43.5.159/AppleAirPort2](http://62.43.5.159/AppleAirPort2) (if anybody can upload it to a more trustworthy site I'd be thankful ;-))

Moving on, this is what you have to do:

    * #apt-get install subversion
    * #svn checkout svn://svn.berlios.de/bcm43xx/trunk
    * #cd trunk/fwcutter/
    * #make
    * #wget [http://62.43.5.159/AppleAirPort2](http://62.43.5.159/AppleAirPort2)
    * #fwcutter AppleAirPort2
    * #make installfw

Bcm43xx:
Finally, all we must do is install the drivers.  If you have downloaded the Ubuntu kernel, you only have to activate the module, but otherwise, you have to install by hand:

    * #cd trunk/driver/
    * #make
    * #insmod bcm43xx.ko

Fouth Step: Enjoy your Airport!

#modprobe bcm43xx  (and Enjoy!)

At this point, you should be able to see the target and you only have to configure the connection.  That said, keep in mind that this is all very new and there are usually errors.  I was unable to configure the card with the Gnome Configurer, but I have been able to configure it by hand.  

Good Luck!

(Consider the translation public domain, the author of the original article can post it on his page or use it however he'd like.  No credit necessary.  Hope this helps!  Also note that I'm just a humble Linguist and haven't actually tried this method,  Please direct support questions to the boards, as I likely can't answer them. )

---

### Post by zoglesby on 2005-12-10
[QUOTE=wanderfowl]I'll try a translation, give me an hour or so, I'll post it here.[/QUOTE]

Awsome Thanks

[QUOTE=MetalMusicAddict]Is any of this gonna help Dell users with Broadcom based cards?[/QUOTE]

We are all trying to get this working on powerpc right now because we can use ndiswrapper since its made for x86. This is the first chance that we have had to try and get Airport Extreme working.

---

### Post by zoglesby on 2005-12-10
[QUOTE=wanderfowl]

You can download it from here [http://62.43.5.159/AppleAirPort2](http://62.43.5.159/AppleAirPort2) (if anybody can upload it to a more trustworthy site I'd be thankful ;-))[/QUOTE]


[http://www.ghostcorp.net/AppleAirPort2]("http://www.ghostcorp.net/AppleAirPort2")

---

### Post by ssam on 2005-12-10
[QUOTE=MetalMusicAddict]Is any of this gonna help Dell users with Broadcom based cards?[/QUOTE]

it should do. as its open source it should work on any architecture.

the owners of recent macs are very excited because they have no way to use their built in wireless before.

---

### Post by zoglesby on 2005-12-10
So I am trying to compile softmac and I am getting this error.
```
Dzoglesby@ppc:~/source$ make
make -C /lib/modules/2.6.15-7-powerpc/build M=/home/zoglesby/source modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-7-powerpc'
  CC [M]  /home/zoglesby/source/ieee80211softmac_io.o
/home/zoglesby/source/ieee80211softmac_io.c:442: warning: &#8216;ieee80211softmac_send_ctl_frame&#8217; defined but not used
  CC [M]  /home/zoglesby/source/ieee80211softmac_auth.o
  CC [M]  /home/zoglesby/source/ieee80211softmac_module.o
/home/zoglesby/source/ieee80211softmac_module.c: In function &#8216;ieee80211softmac_create_network&#8217;:
/home/zoglesby/source/ieee80211softmac_module.c:311: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:312: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:313: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:313: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:314: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:315: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:315: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
/home/zoglesby/source/ieee80211softmac_module.c:315: error: &#8216;struct ieee80211softmac_network&#8217; has no member named &#8216;supported_rates&#8217;
make[2]: *** [/home/zoglesby/source/ieee80211softmac_module.o] Error 1
make[1]: *** [_module_/home/zoglesby/source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-7-powerpc'
make: *** [modules] Error 2

```

---

### Post by zoglesby on 2005-12-10
I found the problem on the gentoo forums

> softmac build is a bit broken but you can use an older changeset. maybe try this link:

[http://softmac.sipsolutions.net/source/?cmd=archive;node=2167883c86e8ea1917999cafcd9854e3f6494b31;type=gz](http://softmac.sipsolutions.net/source/?cmd=archive;node=2167883c86e8ea1917999cafcd9854e3f6494b31;type=gz)

---

### Post by zoglesby on 2005-12-10
I have everything installed now but the settings for the card will not stay. I need help configuring the card with WEP.

---

### Post by tokyovigilante on 2005-12-10
[QUOTE=wanderfowl]
Second Step: Installing the drivers and their dependencies
[/QUOTE]
You shouldn't need to do this if you've downloaded the kernel as a binary. If you've built it from source it will also build the drivers for you.

[QUOTE=zoglesby]Alright, so I would like to install the new drivers but I can't get Dapper to install on my PowerBook (it frezzes after the cd is ejected on the unmount file system step).[/QUOTE] 
I had the same issue on my iBook, just hit Option-Command-Power to force a restart, it will boot and the installer will continue.

The second stage of the 20051209 install is running now, I'll have a fiddle and post up how (if) i get it to work.

---

### Post by tomislavmedak on 2005-12-10
when i'm trying to compile softmac i get the following error:

```
coyu3@ko3moc:~/source$ make
make -C /lib/modules/2.6.15-7-powerpc/build M=/home/coyu3/source modules
/usr/src/linux-headers-2.6.15-7-powerpc/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-7-powerpc/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-7-powerpc'
  CC [M]  /home/coyu3/source/ieee80211softmac_io.o
/bin/sh: gcc: command not found
make[2]: *** [/home/coyu3/source/ieee80211softmac_io.o] Error 127
make[1]: *** [_module_/home/coyu3/source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-7-powerpc'
make: *** [modules] Error 2

```

what should i do? is it a wrong version of GCC?

---

### Post by russ816 on 2005-12-10
I get an error about an undefined symbol when trying to run insmod ieee80211softmac.ko. It compiles just fine but I can't get past that. Anyone have any ideas?

---

### Post by zoglesby on 2005-12-10
[QUOTE=russ816]I get an error about an undefined symbol when trying to run insmod ieee80211softmac.ko. It compiles just fine but I can't get past that. Anyone have any ideas?[/QUOTE]


I got the same error but when I dmseg'ed I still saw the softmac stuff in there so I just keep going and it seemed to work. I just can configure my card to work with my access point, and I don't think that it has anything to do with that.

---

### Post by craks on 2005-12-11
[QUOTE=tomislavmedak]when i'm trying to compile softmac i get the following error:

```
coyu3@ko3moc:~/source$ make
make -C /lib/modules/2.6.15-7-powerpc/build M=/home/coyu3/source modules
/usr/src/linux-headers-2.6.15-7-powerpc/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-7-powerpc/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-7-powerpc'
  CC [M]  /home/coyu3/source/ieee80211softmac_io.o
/bin/sh: gcc: command not found
make[2]: *** [/home/coyu3/source/ieee80211softmac_io.o] Error 127
make[1]: *** [_module_/home/coyu3/source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-7-powerpc'
make: *** [modules] Error 2

```

what should i do? is it a wrong version of GCC?[/QUOTE]


apt-get intall build-essential

---

### Post by wanderfowl on 2005-12-11
[QUOTE=craks]apt-get intall build-essential[/QUOTE]

Beware, that should probably be:

apt-get install build-essential

(The S was missing, and I know things like that have screwed me up immensely in the past.  No disrespect intended to anybody, just trying to do a little preemptive helping.)

---

### Post by calcioguy9 on 2005-12-11
I'm trying to make the switch to linux and I know nothing yet, but in order for me to seriously start using and learning linux I need to have wireless working.  How likely is it in the AE will "just work" in dapper?

---

### Post by refdoc on 2005-12-11
I guess it will be fine. I have been using the card on my ibook the whole weekend on a friend's unencrypted net. I will now see whether I can get it working with wep. It freezes occasionally and causes other havoc, but it is clearly on the way of being great.

I have not compiled anything. I simply installed 2.6.15.7, did fwcutter, copied the firmware files in the relevant directory (/usr/lib/firmware), modprobed the driver, did iwconfig and then dhclient eth1.

---

### Post by hatefulthreatening on 2005-12-11
What exactly freezes? The wireless functionality or the entire kernel?

---

### Post by six6 on 2005-12-12
As I understand it: **worm13** and **zoglesby**, you are redistributing copyright firmware without legal right. From [http://developer.apple.com/faq/softwarelicensing.html](http://developer.apple.com/faq/softwarelicensing.html):
> If you use all or part of any Apple software in a program that will be distributed to other people, you need to license the use of that software from Apple Computer, Inc.Users should instead download the firmware from the [official Apple download page](http://www.apple.com/support/downloads/airport42formacosx1033.html). Use [Pacifist](http://www.charlessoft.com/) or similar to extract the "AppleAirPort2" firmware file from the dmg archive.

---

### Post by refdoc on 2005-12-12
[QUOTE=hatefulthreatening]What exactly freezes? The wireless functionality or the entire kernel?[/QUOTE]

The entire kernel I think. The computer is completely unresponsive.

---

### Post by nicholaspaul on 2005-12-13
[QUOTE=refdoc]I have installed the new kernel and did the fwcutter bit.

I certainly have gained a new network card ion ifconfig , but unfortunately not much more as yet.

dhclient eth1 leads to nothing at all, and occasionally the system freezes and needs to be hard reset.


But i am happy. This will in a short while work fine and then I will delete the OSX partition...[/QUOTE]

Delete OSX? With an OS that is so adhered to the hardware, there's no way I'm giving it up for a 'work in progress'. As fantastic as Ubuntu is, OSX is the best thing for Macintosh. Dual booting is a wonderful thing, you know.

Thanks for all the info in this thread. Cover me - I'm going in!!!

---

### Post by zoglesby on 2005-12-13
[QUOTE=nicholaspaul] Dual booting is a wonderful thing, you know.[/QUOTE]

For me its all or nothing. I have not dual booted a computer since 2001. If I am going to have Linux installed on a machine thats going to be it. This way I have no reason to not get something working. Plus I hate to reboot.

---

### Post by hatefulthreatening on 2005-12-14
It's all or nothing for me too.

I can't use OS X for long without becoming pissed off at apple and their crippleware. I can't take a screenshot of a DVD playing, I can't play ogg files in itunes, I can't use dual monitor(ibook only mirrors by default), I can't fullscreen quicktime.

Yes there are hacks to get around most of those problems. It's just insulting that I have to resort to them. All those problems, and more, are the result of apple deliberately crippling their products.

I decided my dignity was worth more than being able to use wifi.

edit: That was a big tangent of a rant. I should have posted this to the "Why did you switch to linux?" thread rather than my stupid joke.

---

### Post by pallus on 2005-12-15
[QUOTE=hatefulthreatening]It's all or nothing for me too.
I can't use dual monitor(ibook only mirrors by default)
[/QUOTE]

Hello, how can i do this with ubuntu and a ibook G4 ?
Thank you a lot.

---

### Post by jecos on 2005-12-15
[QUOTE=pallus]Hello, how can i do this with ubuntu and a ibook G4 ?
Thank you a lot.[/QUOTE]

The xserver should automatically see a second screen hooked up and display clone/mirror mode..  dualhead requires you to setup two screens in your /etc/X11/xorg.conf file 

Heres an example a section of the xorg.conf that uses dualhead

```


 Section "Device"
     Identifier                          "ATI Graphics Adapter connector 0"
     Driver                              "fglrx"
 # ### generic DRI settings ###
 # === disable PnP Monitor  ===
     #Option                              "NoDDC"
 # === disable/enable XAA/DRI ===
     Option "no_accel"                   "no"
     Option "no_dri"                     "no"
 # === misc DRI settings ===
     Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
 # ### FireGL DDX driver module specific settings ###
 # === Screen Management ===
     Option "DesktopSetup"               "(null)"
     Option "HSync2"                     "31.5 - 80.5"
     Option "VRefresh2"                  "60 - 100"
     Option "ScreenOverlap"              "0"
     Option "GammaCorrectionI"           "0x00000000"
     Option "GammaCorrectionII"          "0x00000000"
 # === OpenGL specific profiles/settings ===
     Option "Capabilities"               "0x00000000"
     Option "CapabilitiesEx"             "0x00000000"
 # === Video Overlay for the Xv extension ===
     Option "VideoOverlay"               "on"
 # === OpenGL Overlay ===
 # Note: When OpenGL Overlay is enabled, Video Overlay
 #       will be disabled automatically
     Option "OpenGLOverlay"              "off"
 # === Center Mode (Laptops only) ===
     Option "CenterMode"                 "off"
 # === Pseudo Color Visuals (8-bit visuals) ===
     Option "PseudoColorVisuals"         "off"
 # === QBS Management ===
     Option "Stereo"                     "off"
     Option "StereoSyncEnable"           "1"
 # === FSAA Management ===
     Option "FSAAEnable"                 "no"
     Option "FSAAScale"                  "1"
     Option "FSAADisableGamma"           "no"
     Option "FSAACustomizeMSPos"         "no"
     Option "FSAAMSPosX0"                "0.000000"
     Option "FSAAMSPosY0"                "0.000000"
     Option "FSAAMSPosX1"                "0.000000"
     Option "FSAAMSPosY1"                "0.000000"
     Option "FSAAMSPosX2"                "0.000000"
     Option "FSAAMSPosY2"                "0.000000"
     Option "FSAAMSPosX3"                "0.000000"
     Option "FSAAMSPosY3"                "0.000000"
     Option "FSAAMSPosX4"                "0.000000"
     Option "FSAAMSPosY4"                "0.000000"
     Option "FSAAMSPosX5"                "0.000000"
     Option "FSAAMSPosY5"                "0.000000"
 # === Misc Options ===
     Option "UseFastTLS"                 "2"
     Option "BlockSignalsOnLock"         "on"
     Option "UseInternalAGPGART"         "yes"
     Option "ForceGenericCPU"            "no"
     BusID "PCI:1:0:0"    # vendor=1002, device=4e48
     Screen 0
 EndSection
 
 Section "Device"
     Identifier                          "ATI Graphics Adapter connector 1"
     Driver                              "fglrx"
    # BusID "PCI:1:0:0"    # vendor=1002, device=4e48
     Screen 1
 EndSection
 
Section "Screen"
     Identifier  "Screen0"
     Device      "ATI Graphics Adapter connector 0"
     Monitor     "Monitor0"
     DefaultDepth 24 
     Subsection "Display"
         Depth       24
         Modes       "1280x1024" "1024x768" "800x600" "640x480"
         ViewPort    0 0  # initial origin if mode is smaller than desktop
 #        Virtual     1280 1024
     EndSubsection
 EndSection
 
 Section "Screen"
     Identifier  "Screen1"
     Device      "ATI Graphics Adapter connector 1"
     Monitor     "Monitor1"
     DefaultDepth 24
     Subsection "Display"
         Depth       24
         Modes       "1280x1024" "1024x768" "800x600" "640x480"
         ViewPort    0 0  # initial origin if mode is smaller than desktop
 #        Virtual     1280 1024
     EndSubsection
 EndSection
  
 Section "ServerLayout"
     Identifier  "Server Layout"
 

     Screen "Screen0"
     Screen "Screen1" RightOf "Screen0"
 
     InputDevice "Mouse1" "CorePointer"
     InputDevice "Keyboard1" "CoreKeyboard"
 
 EndSection 

```

---

### Post by hentaidan on 2005-12-15
And this works with Ubuntu on recent iBook G4's?

Last time I tried I only got a white screen on the second monitor. I was under the impression that we have to wait until the next version of X before the newer graphics cards are supported?

---

### Post by hatefulthreatening on 2005-12-15
Yeah, I'm running dapper on my laptop.

If you are willing to use something that'll potentially be broken for weeks at a time, dapper is the answer.

---

### Post by nicholaspaul on 2005-12-18
[I really don't care about anyone's perdantic tastes in hardware or operating systems or how they hate this or that. Use what you like and get on with it. And if you can afford more than one laptop to play with, good on ya.]

So....I got almost thru the above HOWTO instructions by Tokyovigilante. But I got stuck at the modprobe bit. 

I get:
[B]$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211_softmac (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211_softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.15-8-powerpc/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted
[/B]

i'm not a programmer and don't really understand what i'm meant to be doing here, so i'm not sure what kind of info I need to give. [H/w is a 12" Powerbook using Dapper, latest kernel, all the updates]
Thanks for any help :-)

---

### Post by robotgeek on 2005-12-18
[QUOTE=nicholaspaul][I really don't care about anyone's perdantic tastes in hardware or operating systems or how they hate this or that. Use what you like and get on with it. And if you can afford more than one laptop to play with, good on ya.]

So....I got almost thru the above HOWTO instructions by Tokyovigilante. But I got stuck at the modprobe bit. 

I get:
[B]$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211_softmac (/lib/modules/2.6.15-8-powerpc/kernel/net/ieee80211/ieee80211_softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.15-8-powerpc/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted
[/B]

i'm not a programmer and don't really understand what i'm meant to be doing here, so i'm not sure what kind of info I need to give. [H/w is a 12" Powerbook using Dapper, latest kernel, all the updates]
Thanks for any help :-)[/QUOTE]
$ sudo modprobe bcm43xx

---

### Post by tokyovigilante on 2005-12-18
Yeah users can't load kernel modules, so you need to preface them with sudo to authenticate as root. 

Add them to /etc/modules (sudo nano /etc/modules) to have them load every time you boot.

---

### Post by nicholaspaul on 2005-12-19
Thanks guys - that did the trick. But when I modprobe I get: 
[B]WARNING: "bcm43xx_microcode11.fw" not available in driver file "AppleAirPort2". Driver file is too old.
[/B]
This is using the firmware from my OSX partition. Is there a link available for Apple? Is that what I need?

---

### Post by PierreB on 2005-12-19
thanks for all guys !

I just have a newbie question: I'm running on dapper and I used the trick with fwcutter. Everything seems to work but can't surf on the Internet and when I do a ping there is no answer. Do you know were is the problem ?

---

### Post by tokyovigilante on 2005-12-20
@nicholaspaul - I don't think it's compatible with Tiger firmware. Try downloading an alternate version from the Apple site.

@PierreB - post the output of the lsmod, iwconfig and ifconfig commands. Have you set up the ESSID of your wireless interface and performed a dhclient <interface>? What type of base station are you trying to connect to and how is it connected?

---

### Post by nicholaspaul on 2005-12-21
So thats what I'm doing wrong.... i hunted around the Apple site but couldnt find it for the life of me. Anyone have a link for the correct Airport firmware? 

I have a Jaguar disc - is there a way to get the firmware out of it?

---

### Post by PierreB on 2005-12-21
here is my lsmod:

```
Module                  Size  Used by
nls_utf8                2304  1
hfsplus                94564  1
rfcomm                 47544  0
l2cap                  28516  5 rfcomm
bluetooth              62084  4 rfcomm,l2cap
cpufreq_userspace       5640  0
cpufreq_stats           6276  0
cpufreq_powersave       1920  0
cpufreq_ondemand        8284  0
cpufreq_conservative     9764  0
ipv6                  322308  6
sd_mod                 22608  2
af_packet              27144  2
dm_mod                 69744  1
usb_storage            87632  1
yealink                15712  0
bcm43xx               109128  0
ieee80211_softmac      32000  1 bcm43xx
ieee80211_crypt_wep     6496  0
ieee80211_crypt_tkip    13504  0
ieee80211_crypt_ccmp     9152  0
ieee80211              37000  2 bcm43xx,ieee80211_softmac
ieee80211_crypt         7136  4 ieee80211_crypt_wep,ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ieee80211
sr_mod                 20100  0
i2c_keywest            11968  0
snd_powermac           56224  3
snd_pcm_oss            68480  0
snd_mixer_oss          23072  1 snd_pcm_oss
snd_pcm               109828  3 snd_powermac,snd_pcm_oss
snd_timer              29156  2 snd_pcm
snd                    72468  9 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11716  1 snd
snd_page_alloc         12424  1 snd_pcm
sbp2                   26980  0
scsi_mod              178788  4 sd_mod,usb_storage,sr_mod,sbp2
apm_emu                 8364  0
ohci1394               42640  0
sungem                 38948  0
sungem_phy             10432  1 sungem
ieee1394              436400  2 sbp2,ohci1394
usbhid                 50404  0
ehci_hcd               39944  0
ohci_hcd               25732  0
uninorth_agp           11432  1
agpgart                39900  1 uninorth_agp
usbcore               155072  6 usb_storage,yealink,usbhid,ehci_hcd,ohci_hcd
tsdev                   9440  0
evdev                  12608  7
md_mod                 89208  0
ext3                  166824  1
jbd                    72436  1 ext3
ide_disk               20832  3
ide_cd                 50116  0
cdrom                  49468  2 sr_mod,ide_cd
capability              5352  0
commoncap               8256  1 capability

```

iwconfig:
```
eth1      IEEE 802.11b/g  ESSID:"reseau"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Bit Rate:54 Mb/s   Tx-Power=2346 dB
```

ifconfig:

```
eth1      Lien encap:Ethernet  HWaddr 00:0A:95:F2:C4:01
          adr inet6: fe80::20a:95ff:fef2:c401/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:348 (348.0 b)
          Interruption:52 Adresse de base:0x8000

```

The dhclient can't found any dhcp server and when I try to send boardcast ping all my packet are lost.

EDIT: I'm trying to connect to an airportbase

---

### Post by manradjan on 2005-12-21
Hello,

I'm running Breezy with the 2.6.15-9 kernel from Dapper. My Airport Express is working (except WEP).I have the latest wireless-tools available, but they complain: 

```
Warning: Driver for device eth1 has been compiled with version 19 of Wireless Extension, while this program supports up to version 18. Some things may be broken ...
```

Because of that (i think) I can't get iwconfig to show the ESSID that's begin used. Does anyone know how I can fix this? A way to get wireless-tools to work with version 19, or do I have to recompile my kernel to use version 18?

Thanks a lot!

Manradjan

---

### Post by Amaranth on 2005-12-22
Try grabbing the latest wireless-tools from dapper too.

---

### Post by robotgeek on 2005-12-22
[QUOTE=PierreB]
The dhclient can't found any dhcp server and when I try to send boardcast ping all my packet are lost.
[/QUOTE]
I am having the same issue as PierreB. 
```
sudo dhclient eth1
``` results in DHCP timing out, and not associating with a network. 
```
iwlist eth1 scan 
``` gives a list of networks scanned. so driver works and is able to scan for networks. 
```
sudo ifconfig eth 192.168.1.117
``` associates the ip, and I am able to ping the router at 192.168.1.1. However, a ping to google.com fails. (since it's not really connected to the router, and the router associates static ip's based on dhcp requests, in my case)

It's not a problem with the router, as the settings are same for my other wireless card. So, it may be an issue with dhcp utils or so?  Anyways, debug information is below. 

I am on Dapper PPC, 2.6.15 kernel. 

Edit: I forgot to mention that in my router logs, there is no request made by the machine. However, requests by the other wireless card is logged. 

ifconfig eth1
```

eth1    Link encap:Ethernet  HWaddr 00:11:24:25:43:15  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2884 (2.8 KiB)  TX bytes:14728 (14.3 KiB)
          Interrupt:52 Base address:0xc000 

```
iwconfig eth1
```

eth1      IEEE 802.11b/g  ESSID:"kobra"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Bit Rate:54 Mb/s   Tx-Power=2346 dBm   
          RTS thr:off   Fragment thr:off        

```  

sudo lshw -class NETWORK
```

*-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@10:12.0
       logical name: eth1
       version: 03
       serial: 00:11:24:25:43:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driver 0.0.1 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:80084000-80085fff irq:52

```

lsmod 
```

bcm43xx               109128  0 
ieee80211_softmac      32000  1 bcm43xx
ieee80211              37000  2 bcm43xx,ieee80211_softmac
ieee80211_crypt         7136  1 ieee80211

```

---

### Post by hatefulthreatening on 2005-12-22
[QUOTE=nicholaspaul][I really don't care about anyone's perdantic tastes in hardware or operating systems or how they hate this or that. Use what you like and get on with it. And if you can afford more than one laptop to play with, good on ya.][/QUOTE]


Well then you shouldn't have asked "Delete OSX?" and offered your opinion on the subject. :p

---

### Post by manradjan on 2005-12-22
[QUOTE=Amaranth]Try grabbing the latest wireless-tools from dapper too.[/QUOTE]
I allready installed them.Its version 27+28pre10-1ubuntu1. It still keeps complaining about the versions that don't match.

Thanks

---

### Post by XMashedPotatoX on 2005-12-23
[QUOTE=robotgeek]I am having the same issue as PierreB. 
```
sudo dhclient eth1
``` results in DHCP timing out, and not associating with a network. 
```
iwlist eth1 scan 
``` gives a list of networks scanned. so driver works and is able to scan for networks. 
```
sudo ifconfig eth 192.168.1.117
``` associates the ip, and I am able to ping the router at 192.168.1.1. However, a ping to google.com fails. (since it's not really connected to the router, and the router associates static ip's based on dhcp requests, in my case)

It's not a problem with the router, as the settings are same for my other wireless card. So, it may be an issue with dhcp utils or so?  Anyways, debug information is below. 

I am on Dapper PPC, 2.6.15 kernel. 

Edit: I forgot to mention that in my router logs, there is no request made by the machine. However, requests by the other wireless card is logged. 

ifconfig eth1
```

eth1    Link encap:Ethernet  HWaddr 00:11:24:25:43:15  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2884 (2.8 KiB)  TX bytes:14728 (14.3 KiB)
          Interrupt:52 Base address:0xc000 

```
iwconfig eth1
```

eth1      IEEE 802.11b/g  ESSID:"kobra"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Bit Rate:54 Mb/s   Tx-Power=2346 dBm   
          RTS thr:off   Fragment thr:off        

```  

sudo lshw -class NETWORK
```

*-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@10:12.0
       logical name: eth1
       version: 03
       serial: 00:11:24:25:43:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driver 0.0.1 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:80084000-80085fff irq:52

```

lsmod 
```

bcm43xx               109128  0 
ieee80211_softmac      32000  1 bcm43xx
ieee80211              37000  2 bcm43xx,ieee80211_softmac
ieee80211_crypt         7136  1 ieee80211

```[/QUOTE]

I had the same problem for a while. You just need to set up your gateway.

```
route add default gw ROUTER_IP
```

---

### Post by robotgeek on 2005-12-23
Woot! It works! Typing from the Airport Extreme Wireless (static ip )

Thanks everyone, and to the devs: great work!

---

### Post by Amaranth on 2005-12-23
When I tried to setup a static IP with sudo ifconfig eth1 ip 192.168.1.107 I get: ip: couldn't resolve host name (or something similar). Has anyone seen this?


Edit: Nevermind, a little hackery in /etc/network/interfaces and /etc/resolv.conf got it working. Too bad it died about 2 minutes later.

---

### Post by dombleu on 2005-12-23
Hi to you all, sorry to dilute the ongoing and useful discussion here, but making my aiport extreme card on my new powerbook is about to become a lifequest by my side and I was wondering: can a succesful user tell in clear what procedure is required to make that darn thing work?

Mine is receiving signal from the AP in wifi-radar, but I can't say it has done anything better...

Is there anyone invloved in the development of this bcm43xx driver in here?

how do you explicitely use iwconfig to set your connection? I've red the man, and every command seems to be accepted w/out any error. But I think I do need a little theory about ip settings.... 

any help is welcome!

---

### Post by Amaranth on 2005-12-23
I had to set my essid about 20 times before it associated, you can check `dmesg` for the SoftMAC lines that tell you if that works. After that, I had to edit /etc/network/interfaces and add ```
iface eth1 inet static
    address 192.168.1.107
    netmask 255.255.255.0
```
Or something like that, `man interfaces` shows a great example of setting a static IP. Then I ran `ifup eth1` and did the route thing mentioned above. After that I had to add `nameserver 192.168.1.1` to /etc/resolv.conf to get DNS going. Of course, two minutes later the connection died, but for a couple minutes I was on IRC and searching google.

---

### Post by blixel on 2005-12-25
[QUOTE=tokyovigilante]Get the Airport firmware either by downloading from the Apple site, or use the one from your MacOS install: /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2. I think this only works for Panther and below, Tiger users will need to download the old version from Apple.[/QUOTE]

I don't have OSX installed at all.  How can I get this file?  Can I mount my Panther CD and copy it off there?  Can I download it form somewhere?  I downloaded the AirPortSW42.dmg file from Apple's website, but I don't have any way to get the files out of the disk image.

---

### Post by nicholaspaul on 2005-12-27
This should help mount a dmg in linux: 
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

I have a Jaguar disk and would love to be able to extract the firmware from it. Anyone know how?

blixel: which file did you download? Could you give me the link? I tried a few and some were just updates, some were for the basestation (Using the same name for two products is pretty confusing!!).

---

### Post by nicholaspaul on 2005-12-29
I still get this message : 
[B]WARNING: "bcm43xx_microcode11.fw" not available in driver file "../Desktop/aa2". Driver file is too old.
[/B]
even when using a firmware version that apparently works. fwcutter reports this:
[B]
fwcutter knows your file:
  filename :  AppleAirPort2
  version  :  3.90.34.0.p11 (400.17)
  MD5      :  ca0f34df2f0bfb8b5cfd83b5848d2bf5
[/B]
Could someone please confirm that this is the correct firmware? 
Is it possible that upgrades to my Airport Extreme may affect this process?

---

### Post by dombleu on 2005-12-31
Anybody got news about what's happening with the guys/gals at berlios and their driver?

---

### Post by Amaranth on 2005-12-31
Well, it's supposedly gotten a lot better since the version that was first in dapper. Still no WEP or WPA from what I can see.

---

### Post by dombleu on 2006-01-01
And still not usable from what I can. Just hope it will get more stable real soon....

---

### Post by nicodds on 2006-01-01
[QUOTE=nicholaspaul]This should help mount a dmg in linux: 
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

I have a Jaguar disk and would love to be able to extract the firmware from it. Anyone know how?
[/QUOTE]

I think that the document doesn't apply to new dmg files, that are HFS+ formatted. At the moment, to my knowledge there's no way open new dmg files on GNU/Linux.

If you have a windows installation, you could use UltraISO to obtain the files.

Nico

---

### Post by nicodds on 2006-01-01
[QUOTE=Amaranth]Well, it's supposedly gotten a lot better since the version that was first in dapper. Still no WEP or WPA from what I can see.[/QUOTE]

New svn sources have a working patch for WEP support, I've tried it and it works quite well, except for the fact that there's a high percent of packet loss.

Nico

---

### Post by PierreB on 2006-01-02
Ok, right now everything is working at the rate 11M. Thanks everyone.

But there is still a problem. I got this error very often so I must reconfigure my chip.

```
[ 2450.687869] NETDEV WATCHDOG: eth1: transmit timed out
[ 2450.687884] bcm43xx: FATAL ERROR (TX timeout): Resetting the chip...

```

Do you have any idea ?

---

### Post by nicodds on 2006-01-02
[QUOTE=PierreB]
```
[ 2450.687869] NETDEV WATCHDOG: eth1: transmit timed out
[ 2450.687884] bcm43xx: FATAL ERROR (TX timeout): Resetting the chip...

```

Do you have any idea ?[/QUOTE]

Did you have a board with core rev < 5?

If so, things should go better in the near future. There's a issue that developers couldn't test, because they haven't this kind of hardware, but things should go better in the near future.

Nico

---

### Post by PierreB on 2006-01-02
[QUOTE=nicodds]Did you have a board with core rev < 5?

If so, things should go better in the near future. There's a issue that developers couldn't test, because they haven't this kind of hardware, but things should go better in the near future.

Nico[/QUOTE]


Sorry, don't know what is my core rev. How can I see it ?

---

### Post by amk on 2006-01-02
I am close to having the bcm43xx driver working but I am now stuck and could really do with some pointers.

THE SHORT VERSION:
1. I have successfully built and installed bcm43xx, ieee80211softmac and bcm43xx-fwcutter (one error extracting firmware file bcm43xx_microcode11.fw). These are the latest daily snapshots (20060102)

2. I can manually "ifconfig ethX up" the wireless interface and see my very open wireless network with "iwlist ethX scan". 

3. SoftMac seems to associate (from dmesg output).

4. dhclient ethX fails to get an IP address but I can manually set an IP address (in the correct range) with ifconfig.

5. I can not ping my wireless AP/router. Ping returns "Destination Host Unreachable" even though my route table looks OK:
"Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.73.0    *               255.255.255.0   U         0 0          0 eth2"

Does anyone have any ideas, pointers or RTFMs??

---

### Post by nicodds on 2006-01-03
[QUOTE=PierreB]Sorry, don't know what is my core rev. How can I see it ?[/QUOTE]

You can see it in the log, when you modprobe the bcm43xx module.

Nico

---

### Post by spoetnik on 2006-01-05
Is there some WIKI/Guide?HOWTO including all the steps one-by-one in order??

---

### Post by supermonix on 2006-01-06
Hi everybody!

I followed the howto and I stopped at the fwcutter command, because of ```
fwcutter: command not found

```

I tried to install it, but I cannot find it in the apt-get.

Please, some help? Thank you so much!

---

### Post by supermonix on 2006-01-06
I solved using ```
./fwcutter
``` :KS

---

### Post by dombleu on 2006-01-06
you can get fwcutter from:

[ftp://ftp.berlios.de/pub/bcm43xx/snapshots/](ftp://ftp.berlios.de/pub/bcm43xx/snapshots/)

but my opinion about this driver is:

If you're like me and you're not a linux network specialist, wait for a more official release. Success by my side could be resumed as: at a point or at another one, it just froze my laptop dead. Although it was quite encouraging to see the surroundings wireless networks detected, it got really frustrating to reboot and reboot and reboot...

Anyway, since the airport extreme is a common piece of hardware on mac laptops, I guess when the driver will be really ready, we'll see much more documentation on how to install it.

But let me know if you ever succeed to browse the net with it! :)

dom

---

### Post by supermonix on 2006-01-06
At this moment, I can configure eth1 and for a little while I saw the wireless network using ```
iwlist eth1 scan
```.

But... no way to ping the router, nor surf the net, obviously... :(

---

### Post by supermonix on 2006-01-07
I'm here again...

I got success with the card and the AP! Look:
```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0d:93:ea:ee:8a
Sending on   LPF/eth1/00:0d:93:ea:ee:8a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.110.7.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.110.7.1
bound to 10.110.7.6 -- renewal in 125354 seconds.
```

This means that my computer talks with the AP (10.110.7.107) and with the router (10.110.7.1), but the ping don't work:

```
PING 10.110.7.1 (10.110.7.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
```

and I cannot surf.

Any idea?

---

### Post by luithelizard on 2006-01-10
w00t!  got it working on an ibook g4 now for about an hour... no problems.  i had to drop the transfer rate down to 11M to get it to authenticate with the router, but other than that i pretty much went with the info in this thread.  thanks everyone, i've been looking into solving this problem since i got my ibook in august, i had just about given up and bought a USB wireless adapter, but i can save my money now!

---

### Post by bonvenon on 2006-01-10
Has anyone got it to work with dhcp on iBook G4?

I can make it work with static IP, but then it looses the connection to the ap every now and then.

---

### Post by madzzoni on 2006-01-10
Wauw, it seems like this project is close to be true... i really look forward to try Ubuntu on my iBook G4 1.2GHz with AE working seemsless :-)

*KeepUp the good work out there...!*

---

### Post by luithelizard on 2006-01-10
as far as i know you shouldn't really lose access to your ap even when using static ip, as long as you use an ip that's out of the dhcp range.  so far my service has been uninterrupted for about 3 hours... we'll see how it holds up.

---

### Post by nicholaspaul on 2006-01-11
Running Dapper on a 12" Powerbook (867MHz), installing the latest headers and I got Airport Extreme working!
These drivers were released today -
[ftp://ftp.berlios.de/pub/bcm43xx/sna...006111.tar.bz2](ftp://ftp.berlios.de/pub/bcm43xx/sna...006111.tar.bz2)
All I did was:
make
sudo make install
sudo modprobe bcm43xx
And it WORKS! Easy!

---

### Post by dombleu on 2006-01-11
Wrong URL.... 

this is the right one:

[ftp://ftp.berlios.de/pub/bcm43xx/snapshots/bcm43xx](ftp://ftp.berlios.de/pub/bcm43xx/snapshots/bcm43xx)

And by the way: YOU LUCKY ONE!  Sounds too good to be true....

I tried with the snapshots without success :(

---

### Post by luithelizard on 2006-01-11
mine's been working for a couple days now with great reliability.  woohoo!

only everytime i close my laptop and reopen it, or restart, etc, i have to configure my rate and essid on my interface using iwconfig.  anyone know a way to make it stick?  a config file somewhere?  

thanks to everyone who's contributed to this great thread, and especially to the driver developers.

---

### Post by chascon on 2006-01-12
For anyone that wants to try a basic (no desktop) tiny and bootable ppc CD with the 2.6.15 kernel to try this AE utility try finnix at:
[http://www.finnix.org/](http://www.finnix.org/)

I about to try this.  I'm sure it'll be more secure than dapper.  I'm not even sure if dapper has security updates put forth to it.

Chascon

Update:  I just found out that dapper does not have dedicated security repositories but security patches get applied within normal development.  This normally does not affect the interval of security patches though, I'm told in #ubuntu.

---

### Post by Deicidus on 2006-01-14
I'm having tons of trouble getting my Airport Extreme card to work on my iBook G4 with breezy. I installed the 2.6.15-12 (I'm pretty sure it was -12, either that or -11), and I got the "Dropping to a shell!" error on the next boot that is discussed but apparently not solved in other places on this forum. I don't know how to revert the kernel so I just reinstalled Ubuntu when that happened.

How can I resolve this kernel frustration so i can move on and actually try installing the wireless card drivers?

If I can't get Airport working, I'll have to go back to Mac OS X, and I really want my "switch to Ubuntu" project to be a success!

---

### Post by tokyovigilante on 2006-01-15
[QUOTE=Deicidus]
How can I resolve this kernel frustration so i can move on and actually try installing the wireless card drivers?[/QUOTE]
You can't install the 2.6.15 Dapper kernel in Breezy, as there is an accompanying new hardware detection system based on udev rather than hal. I  suspect you are being dropped to a shell because the 2.6.15 kernel cannot find your hardware on the next boot.

I suggest running Dapper if you want to get Airport Extreme running. Flight-3 should be out Monday, and should be pretty stable.

---

### Post by chascon on 2006-01-15
> only everytime i close my laptop and reopen it, or restart, etc, i have to configure my rate and essid on my interface using iwconfig. anyone know a way to make it stick? a config file somewhere?
Nto quite you're looking for maybe a script something like:
service wlan restart
service network restart

Perhaps you could throw it into a script like:
------------------------------------------------------------------------------------------------------------
#!/bin/sh

# source configuration
. pmcs-config

case "$1" in
suspend)
modprobe -r <your_module>
;;
resume)
modprobe <your_module>
;;
esac
--------------------------------------------------------------------------------------------------------

and then link it in /etc/power/event.d/. Take a look at /etc/power/scripts.d/skeleton if you need something more sophisticated.

That was from [http://ubuntuforums.org/showthread.php?t=111711](http://ubuntuforums.org/showthread.php?t=111711)

---

### Post by Deicidus on 2006-01-15
[QUOTE=tokyovigilante]You can't install the 2.6.15 Dapper kernel in Breezy, as there is an accompanying new hardware detection system based on udev rather than hal. I  suspect you are being dropped to a shell because the 2.6.15 kernel cannot find your hardware on the next boot.[/QUOTE]

Oh ok. Earlier posts in this thried made it sound as if you could upgrade the kernel within breezy without changing anything else.

> I suggest running Dapper if you want to get Airport Extreme running. Flight-3 should be out Monday, and should be pretty stable.

I'll install it as soon as it comes out. I hope it works! Thanks a lot.

---

### Post by Subudhinath on 2006-01-16
I'm thinking to buy a MacBook Pro (the soon to be released Intel-based successor of the PowerBook). When I read the stuff mentioned about it at Apple's website I couldn't find any mentioning about it having a different kind of AirPort Extreme card than the last PowerBook models.

Anyhow, now I found an article at [http://www.appleinsider.com/article.php?id=1465](http://www.appleinsider.com/article.php?id=1465) mentioning that the new Intel based Macs will have added 802.11a support, which to my understanding would mean a different kind of AirPort Extreme card, or does it just mean a firmware upgrade or a software upgrade to MacOS X? Whatever it is I hope it doesn't brake the Linux driver's support for it.

Does anybody have any ideas about this?

---

### Post by superuser on 2006-01-29
Not to get me wrong, I **do** second the idea of having native linux drivers for the card available. 

I just don't think they're ready to be used in a non-testing (productive) environment yet. I tested them with Dapper-3 some days ago and was forced insanely often to reconnet to the router due to connection loss. ndiswrapper was by far more stable.

---

### Post by double0siete on 2006-02-18
I'm still having trouble getting this wireless card working.  I've followed these instructions: [https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29](https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29)
and now I'm stuck.  I was too lazy to compile my own kernel, so I used the provided package.  Unfortunately, when installing SoftMAC or bcm43xx, I get the following error:

make: *** /lib/modules/2.6.15.1/build: No such file or directory.  Stop.

So, I figured I'd compile my own kernel.  I used these instructions:
[http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel+dpkg](http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel+dpkg)

and when I tried to create the kernel package, I got this:

arch/ppc/platforms/pmac_feature.c:66: error: static declaration of ‘feature_lock’ follows non-static declaration
arch/ppc/include/asm/pmac_feature.h:389: error: previous declaration of ‘feature_lock’ was here
arch/ppc/platforms/pmac_feature.c:119: error: static declaration of ‘uninorth_node’ follows non-static declaration
arch/ppc/include/asm/pmac_feature.h:390: error: previous declaration of ‘uninorth_node’ was here
arch/ppc/platforms/pmac_feature.c:120: error: static declaration of ‘uninorth_base’ follows non-static declaration
arch/ppc/include/asm/pmac_feature.h:391: error: previous declaration of ‘uninorth_base’ was here

I googled that found [http://www.ussg.iu.edu/hypermail/linux/kernel/0601.1/1689.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0601.1/1689.html) which doesn't sound promising.

I have no idea what to do at this point.  I'd appreciate any help anyone could give. Thanks.

---

### Post by erimar77 on 2006-02-18
[QUOTE=double0siete]I'm still having trouble getting this wireless card working.  I've followed these instructions: [https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29](https://wiki.ubuntu.com/WifiDocs/Device/AirportExtreme?highlight=%28airport%29)
and now I'm stuck.  I was too lazy to compile my own kernel, so I used the provided package.  Unfortunately, when installing SoftMAC or bcm43xx, I get the following error:

make: *** /lib/modules/2.6.15.1/build: No such file or directory.  Stop.

[/QUOTE]

you need to install the linux headers

---

