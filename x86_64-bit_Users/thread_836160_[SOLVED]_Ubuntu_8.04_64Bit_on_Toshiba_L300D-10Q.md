---
title: "[SOLVED] Ubuntu 8.04 64Bit on Toshiba L300D-10Q"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by oceallaighm on 2008-06-21
Hi,

I have run both the 64 bit and 32 bit live CD's of Ubuntu 8.04 on my Toshiba L300D-10Q.

They appear to start, I can select the language and select the option to run without installing, after a short time I get a cli with the following message:- 

udevd-event [1514]: run_program '/sbin//modprobe' abnormal exit
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash) Enter 'help' for a list of built-in commands (initramfs)

I don't believe that the problem is with the CD as the 32 bit CD has been used to install Ubuntu 8.04 on to 2 other older Toshiba Satellite laptops and on to a self built AMD Thunderbird system that is 6 years old.

The spec. for the Toshiba L300D-10Q is as follows AMD Turion 64 x 2, 4GB ram and a 120GB harddisk, Display ATI Raedon X1250, LAN Realtek RTK8102E, WAN Realtek RTL8187B and Audio Realtek High Definition Audio..

The goal would be to install Ubuntu 8.04 64 bit as the default OS on the laptop, but I need to run a live CD to see if the hardware will be recognised. Although I have dabbled in Linux for over 10 years, I am neither an expert nor a techie, just a mere end user.

Any ideas anyone?

---

### Post by fmjrey on 2008-06-21
I have the same issue still unresolved, see [this thread]("http://ubuntuforums.org/showthread.php?t=791518").

---

### Post by Sakrimo on 2008-06-21
Your hardware should be fine.

I'm running 64 bit on an Acer 9300, which is an older laptop than your Toshiba i beleive. 

Only has 1x AMD 64 Turion's

Realtek WAN, you need to install propertierty drivers, but it works :)
Your audio is the same as mine too, works a treat, but i sometimes wonder why it doesn't seem as loud through laptop speakers as it did before?

I've only got 1 GB of RAM, and it runs fine, and i REALLY wanted a 64 bit system regardless of the 4GB recommendations. 


All in all, hardware should be fine. But remembering that my first instance with Linux was just over a week ago (failed attempt on Gentoo), and eventually (after downloading and having issues with boot cd's for a while) got a 64 bit Ubuntu 8.04 from Ebay :D

---

### Post by oceallaighm on 2008-06-21
Hi,

I found another thread [http://ubuntuforums.org/showthread.php?t=834640](http://ubuntuforums.org/showthread.php?t=834640).

I did try the following as suggested "What I did was boot the live CD, press F6 to add boot options, then I manuallly added "noapic" (without quotes) on the boot parameters line just before the "splash" near the end of that line." and while things did appear to go further I ended back with the same error message.

Thanks

---

### Post by oceallaighm on 2008-06-21
Hi,

Reference link to another thread in my previous post, no, it is not sufficient to just use "noapic" , it would appear that you must also disable the internal networkcard in the bios.

Thanks all.

---

### Post by fmjrey on 2008-06-21
Maybe [this thread]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg883257.html") will be helpful. Here is a [complete view of the thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749"). Will try this now...
Edit: In fact I decided to go via the wireless interface to install the latest -19 kernel and then the lan interface worked.
Getting the wireless to work wasn't easy either, and I had to unprotect my wireless network because [the present fix to get the Realtek RTL8187B working]("http://linux.toshiba-dme.co.jp/linux/eng/pc/sat_PSPD0_report.htm") freezes the machine when using encryption.

---

### Post by sayid on 2008-06-23
> **fmjrey said:**
> Maybe [this thread]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg883257.html") will be helpful. Here is a [complete view of the thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749"). Will try this now...
Edit: In fact I decided to go via the wireless interface to install the latest -19 kernel and then the lan interface worked.
Getting the wireless to work wasn't easy either, and I had to unprotect my wireless network because [the present fix to get the Realtek RTL8187B working]("http://linux.toshiba-dme.co.jp/linux/eng/pc/sat_PSPD0_report.htm") freezes the machine when using encryption.

Hello fmjrey, I haven't the same machine but the chipset in my notebook is the same.
Perhaps this post helps you.

I followed your links, perhaps the most usefull was toshiba's link.
I downloaded the driver, the file contains a version of cuervo's driver ( see this [link]("http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187b+driver")). 
If you use Toshiba's link the driver is patched, otherwise if you use cuervo's driver you should patch the driver (The tar file contains instructions for do that).

Lamentably, we haven't luck, the driver is a temporal solution for me, in this [link]("http://ubuntuforums.org/showthread.php?t=604784") (#6 and #7 posts) I've posted some details.

Ndiswrapper & 64 bits aren't working for me. Lots of people reported that have the same problem :S.

Hope this information helps you!
Regards,

Sayid...

---

