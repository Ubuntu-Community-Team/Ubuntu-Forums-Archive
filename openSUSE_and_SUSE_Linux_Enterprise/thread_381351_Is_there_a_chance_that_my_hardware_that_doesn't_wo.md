---
title: "Is there a chance that my hardware that doesn't work in Ubuntu work in OpenSuSE?"
date: 2007-03-10
forum: openSUSE and SUSE Linux Enterprise
---

### Post by wersdaluv on 2007-03-10
I have spent so much time and effort trying to make my USB run in Ubuntu Eddy, but I still haven't found a solution. (See [this thread]("http://ubuntuforums.org/showthread.php?t=356269")) I have also tried Mepis and PCLinuxOS but they don't work too.

I am thinking of trying OpenSuSE and Fedora, but what hinders me from trying is the thought that they have no Live CDs and they require many CDs (I have no dvd burner).

Do you think it is worth trying OpenSuSE considering that my hardware doesn't many other distos?

---

### Post by angryfirelord on 2007-03-10
What are you trying to plug into your USB?

---

### Post by wersdaluv on 2007-03-11
I try to plug every USB device I have but none of them work. Please see [this thread]("http://ubuntuforums.org/showthread.php?t=356269") for more details.

---

### Post by ekka on 2007-03-12
Knoppix?

---

### Post by angryfirelord on 2007-03-12
Unfortunately, I don't have enough knowledge to solve your problem. If you still want to use Ubuntu, revert back to Dapper as that's still being supported & enable the backports to get _some_ up-to-date packages.

However, if you desire a newer system, I'd recommend PCLinuxOS, as it's light years better than openSuSE (in fact, if you change it to the past 7 days, it's #2 right now).

---

### Post by wersdaluv on 2007-03-12
> **ekka said:**
> Knoppix?

I'm burning the Knoppix 5.1.1 Live CD. I'll tell you how it goes. ;)

---

### Post by wersdaluv on 2007-03-12
> **angryfirelord said:**
> Unfortunately, I don't have enough knowledge to solve your problem. If you still want to use Ubuntu, revert back to Dapper as that's still being supported & enable the backports to get _some_ up-to-date packages.

However, if you desire a newer system, I'd recommend PCLinuxOS, as it's light years better than openSuSE (in fact, if you change it to the past 7 days, it's #2 right now).

Yes, PCLinuxOS looks really good. I tried Test Release 3 and I wanted to install it. It's just that, my USB doesn't work with it too.

Do you think, Dapper can solve my problem?

---

### Post by wersdaluv on 2007-03-12
Knoppix didn't work. :( 

What do I do now? :(

---

### Post by angryfirelord on 2007-03-12
Ok, so it's definitely not a software or kernel issue at all. Which means it could be a couple of things:

Check ALL of the USB ports. If you're just using the front USB, then the cable that connects it could have come loose.

Check the BIOS and see if the USB is enabled.

Plug in some device and see if power comes to it.

---

### Post by joeca0304 on 2007-03-13
What about PCLinuxOS makes it light years beyond suse? (yast as a package manager isn't an acceptable reason, smart works fine)  

I really don't understand all the hype it's been getting lately, seems like any other distro to me.

---

### Post by igknighted on 2007-03-13
Fedora and Suse DO have live CDs... try here for Fedora:
[http://linuxlookup.com/2006/dec/22/fedora_6_zod_live_cd](http://linuxlookup.com/2006/dec/22/fedora_6_zod_live_cd)
And here for Suse:
[http://en.opensuse.org/Released_Version](http://en.opensuse.org/Released_Version)
^^^you need to scroll to the bottom here, its a little obscure

---

### Post by wersdaluv on 2007-03-13
> **angryfirelord said:**
> Ok, so it's definitely not a software or kernel issue at all. Which means it could be a couple of things:

Check ALL of the USB ports. If you're just using the front USB, then the cable that connects it could have come loose.

Check the BIOS and see if the USB is enabled.

Plug in some device and see if power comes to it.

My USB works in when I boot with Windows XP.

I found out that changing the boot options make my USB run, but also stops my Wireless LAN from working (see [this thread]("http://ubuntuforums.org/showthread.php?t=356269"))

I think it's an incompatibility issue. I have been thinking of completely giving up with Linux because I only have one laptop and it doesn't work well with Linux. I just hope there is a Linux solution.

---

### Post by wersdaluv on 2007-03-13
> **igknighted said:**
> Fedora and Suse DO have live CDs... try here for Fedora:
[http://linuxlookup.com/2006/dec/22/fedora_6_zod_live_cd](http://linuxlookup.com/2006/dec/22/fedora_6_zod_live_cd)
And here for Suse:
[http://en.opensuse.org/Released_Version](http://en.opensuse.org/Released_Version)
^^^you need to scroll to the bottom here, its a little obscure

Thanks for the links. :)

It's just that I can't try SuSE because I don't have a DVD burner. I'll just improvise a solution. :D ohh.. by the way, is there an OpenSuSE live**CD**?

---

### Post by igknighted on 2007-03-13
> **wersdaluv said:**
> Thanks for the links. :)

It's just that I can't try SuSE because I don't have a DVD burner. I'll just improvise a solution. :D ohh.. by the way, is there an OpenSuSE live**CD**?

Hmmm, not that I am aware of.  With the install CD, you can download the DVD iso, leave it on a HD partition that you wont write over with the install, and point the 50mb install CD to that DVD iso file and it can use it from there.  I find that easier than d/l and burning 5/6 CD iso's.  I don't believe this works with the LiveDVD tho.  There is also a net install CD which is 44mb and you burn onto a CD.  It starts an installer that lets you install from network servers.  Finally, I highly recommend Sabayon Linux.  Look for the mini edition (last one was 3.2, although the DVD version is up to 3.26) and install that.  It has the added benefit of automatically configuring Beryl if you like, but even if thats not your thing its a tremendous distro.  Fairly cutting edge (that 3.2 which is 3 releases back - 3.2, 3.25, 3.26 - is still about a month newer than Edgy IIRC), yet still very stable with great hardware detection.  You should give it a shot (and don't be afraid of the gentoo nature... its almost easy as Ubuntu and installs just as quick)

---

### Post by igknighted on 2007-03-13
> **joeca0304 said:**
> What about PCLinuxOS makes it light years beyond suse? (yast as a package manager isn't an acceptable reason, smart works fine)  

I really don't understand all the hype it's been getting lately, seems like any other distro to me.

AGREED!!! I have found it to be an extra-buggy clone of Mandriva at best, and just a really buggy OS that isn't stable for 10 minutes at worst.

---

### Post by angryfirelord on 2007-03-13
> **joeca0304 said:**
> What about PCLinuxOS makes it light years beyond suse? (yast as a package manager isn't an acceptable reason, smart works fine)  

I really don't understand all the hype it's been getting lately, seems like any other distro to me.

1) Speed. PCLinuxOS boots up and executes applications VERY fast, faster than Ubuntu & openSuSE. Even KDE under PCLinuxOS is very fast.

2) Control Center. YaST is nice, but it's very sluggish. I found PCLinuxOS's gui administration a lot snappier and more organized than YaST.

3) Packages. PCLinuxOS uses apt-get/Synaptic, which installs packages a lot faster than openSuSE. It also has more, over 5000. openSuSE has around 3000+ (which is still fine)

> AGREED!!! I have found it to be an extra-buggy clone of Mandriva at best, and just a really buggy OS that isn't stable for 10 minutes at worst.

PCLinuxOS IS what Mandriva should have been. Trust me, the Test 3 cd of 2007 rocks! I'm using it along side of Ubuntu & Debian with no issues whatsoever.
Define what was unstable.

Anyway, I think the problem sounds like an IRQ issue, where the wireless and the mouse are trying to run off the same irq (please correct me if I'm wrong). Unfortunately, I still don't know an answer, but I'll keep looking.

---

### Post by julian67 on 2007-03-25
OpenSuse live dvd

[http://download.opensuse.org/distribution/10.2/iso/dvd/openSUSE-10.2-GM-LiveDVD.iso]("http://download.opensuse.org/distribution/10.2/iso/dvd/openSUSE-10.2-GM-LiveDVD.iso")

---

### Post by Quillz on 2007-03-25
> **wersdaluv said:**
> I have spent so much time and effort trying to make my USB run in Ubuntu Eddy, but I still haven't found a solution. (See [this thread]("http://ubuntuforums.org/showthread.php?t=356269")) I have also tried Mepis and PCLinuxOS but they don't work too.

I am thinking of trying OpenSuSE and Fedora, but what hinders me from trying is the thought that they have no Live CDs and they require many CDs (I have no dvd burner).

Do you think it is worth trying OpenSuSE considering that my hardware doesn't many other distos?
This exact scenario happened to me. For whatever reason, Ubuntu refused to recognize my monitor's native widescreen resolution. It could only be fixed by manually tweaking xorg.conf and then running 915resolution. But on openSUSE, my monitor worked perfectly, running the proper resolution by default.

---

