---
title: "ubuntu and imac g3 - work or not work??!"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by shottz on 2005-10-26
I have been reading the forums here and I am getting mixed signals about ubuntu and imac g3 systems.  I am evaluating resinstalling several school labs that contain imac g3 systems with ubuntu 5.10 so, I am looking for feedback such as version and hardware configuration from those that have installed imac g3 systems with ubuntu.  We all know that ubuntu is great, but I would like to hear from those that have a first-hand perspective of installing ubuntu on the imac g3.

Thank you in advance for your time and feedback.

---

### Post by gdunlap on 2005-10-26
I've installed "Warty" onto an old "Grape" iMac G3 333 that was recently given to me and upgraded to 384MB RAM + 40GB drive, and have subsequently updated it (via apt-get dist-upgrade") to "Breezy". (BTW, the hostname is "smucker :))

Everything works great with only one exception:  3D acceleration.  I think the video chip is an ATI Mach64, and there are apparently issues with DRI and that driver, but I have seen some generic instuctions for getting Mach64 3D to work and I'll try it when I have the time.  (It's not as if it's *great* 3D anyway, but it'd be nice if it worked. :) )

Other than 3D, the machine's working great: 2D, sound, network, USB - Ubuntu runs very nicely on it and it gave that old iMac new life!

---

### Post by pvz on 2005-10-26
The only serious problem with G3 iMacs and Breezy is that it installs with wrong refresh rates in xorg.conf, leaving you with a black screen after booting.
Booting in text-only mode and changing the refresh rates to horizontal: 60-6 and vertical: 43-117 should get you up and running nicely. Or manually adjust during install by choosing expert mode.

---

### Post by DirtDawg on 2005-10-27
I've got a g3, but I'm afraid I'm not sure of the specs (if you know which specs specifically might help to know, I'll look 'em up), but I know it's about 5 years old and hasn't been upgraded. I had Warty for some time and it worked very well. I installed Hoary and it works even better. The best Linux I've tried for the my little mac by leaps and bounds. Highly recommended!

---

### Post by patrickallo on 2005-10-27
I've got Breezy working fine on a Bondi Blue G3 iMac (slot-loading from 1999) running @ 350Mhz with 320mb RAM and 6Gig HD.

Basic install got the basics right.

---

### Post by jdp on 2005-10-27
FWIW the Bondi Blue iMacs were the first runs with trayloaders.  The 350 slotload you have (and I've got one too) is in BlueBerry. ;)  Hoary seems to work fine so far.  When I get my Breezy CDs I'll see how it goes.

---

### Post by dinoj on 2005-10-28
I have Imac G3 500 MHz and first I install hoary and later I upgrade it to breezy with no other problems. Only the refresh rate and and correct video driver (The live cd is try to use vesa, not ati driver). The other problem when try to compile kernel to use my keyspan usb-to-serial module - there was some gcc issue with breeze.

---

### Post by shottz on 2005-11-09
So, you are satisfied or surprised at the performance you have with your imac g3 ?  also, again, please include your hardware config and ubuntu version.

thanks.

---

### Post by mediarevolutionary on 2007-04-18
I spent 22 hrs., 12 cds with different OS, threw the cat out the window, and was miserable - UNTIL, finally.  What a sweet sigh of relief to actually have the thing work.  enough about me


on iMac G3 pinstripe - Xubuntu (lower resource demands, they said) [6.10 Alternate]("http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/6.10/release/") install CD;

some things that may have helped: I did hook the iMac to the net; I pressed <tab> and typed "install-powerpc" at the boot prompt; I erased entire HDD to start from scratch; I burned the cd at the lowest speed for a more solid burn;

I hope this helps.  I just wanted to post what worked after using this and other forums to give my kids a sweet computer of their own

---

### Post by sciawonrose on 2007-05-02
Media nice work...

I did the same Xbuntu on  a g3 400 with 128ram but I cannot make it shutdown, nor does it play properly dvd or other video, even if I did downloaded all the multimedia stuff.

Any help or suggestion? thanks

---

