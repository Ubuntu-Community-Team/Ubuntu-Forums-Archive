---
title: "Intel Mac Support?"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by obama on 2006-04-08
Hi everybody, I currently run Ubuntu 5.10 on a PowerPC G4 733mhz system. I'm thinking about getting one of the new 1.6ghz dual-core Intel Mac Minis. However, if I am going to make the change, I'll need my trusty Linux with me. Does Ubuntu support the new Intel Macs? If not, does anyone know of other distros that do?

---

### Post by mips on 2006-04-08
Gentoo. Why not just get the MAC anyway and use OSX for now until Ubuntu works on it as it eventually will.

---

### Post by obama on 2006-04-08
Thanks.  I probably will just use OS X for now, does anyone know when Ubuntu might support the new Macs?

---

### Post by jdp on 2006-04-08
The new Boot Camp software might make it possible to boot the regular x86 Ubuntu CD on an Intel based Mac.

About the only reason you'd need Gentoo is if you want to compile in EFI on your own.  Boot Camp should be much cleaner and easier to use.

---

### Post by Christiaan on 2006-04-08
[QUOTE=obama]Thanks.  I probably will just use OS X for now, does anyone know when Ubuntu might support the new Macs?[/QUOTE]

See [http://www.ubuntuforums.org/showthread.php?p=812599](http://www.ubuntuforums.org/showthread.php?p=812599)

Things should be made pretty smooth due to Apple's recent firmware update for Intel Macs.

---

### Post by 3rdalbum on 2006-04-09
There is a hacked Live CD that supports the Macintels, so maybe those same people will hack a Dapper install CD to support your new Mini.

---

### Post by Thingi on 2006-04-09
Well after installing Apple boot camp the latest dapper Live daily build boots perfectly to the gnome desktop :-) 

The video + sound hardware is supported fine but the airport card must be different to the ppc mac mini's so the hacked extreme drivers won't work :-( Will have to do a little bit of investigation! :-)

---

### Post by jdp on 2006-04-09
My post about different hardware: [http://ubuntuforums.org/showpost.php?p=897720&postcount=7](http://ubuntuforums.org/showpost.php?p=897720&postcount=7)

> So, any Intel mac has a fairly regular Intel networking chip, not the Broadcom chip used in PPC Macs with Airport Extreme. 

Really, the Intel macs just are not the same thing with an Intel CPU. Everything is new.


Apple calls it AirPort Extreme because that is the Apple marketing name for 802.11g hardware.  In PPC Macs it was a Broadcom chipset.  Even the Original AirPort cards were just slightly modified Lucent ORiNoCo 802.11b cards.  The entire chipset in the Intel based Macs is Intel based, except for the ones with a seperate ATI/nVidia GPU.  So, you'd use Intel drivers for WiFi, and I'd guess that they'd work right off if there are already drivers for the chipset in Ubuntu.  No hacking needed, I'd guess.

Let me repeat that last part of my other post, because people seem to get caught up in the marketing names: Everything is new.

---

### Post by Thingi on 2006-04-10
[QUOTE=jdp]My post about different hardware: [http://ubuntuforums.org/showpost.php?p=897720&postcount=7](http://ubuntuforums.org/showpost.php?p=897720&postcount=7)

Apple calls it AirPort Extreme because that is the Apple marketing name for 802.11g hardware.  In PPC Macs it was a Broadcom chipset.  Even the Original AirPort cards were just slightly modified Lucent ORiNoCo 802.11b cards.  The entire chipset in the Intel based Macs is Intel based, except for the ones with a seperate ATI/nVidia GPU.  So, you'd use Intel drivers for WiFi, and I'd guess that they'd work right off if there are already drivers for the chipset in Ubuntu.  No hacking needed, I'd guess.

Let me repeat that last part of my other post, because people seem to get caught up in the marketing names: Everything is new.[/QUOTE]

True, but I cant really look into it at the mo' although because although the live cd boots ok it can't be installed. No linux distro can understand the partiton map of the drive correctly at present, ubuntu daily install bombs and even gentoo can't understand the partiton layout. it's ok to create and delete partitions in ubuntu live, just not format or write to them 

Checked wireless again and it's not even detected, The intel linux drivers don't work on mac mini. The wireless is't intel its an Atheros Communications device (part # 661-3890 (marked as 603-8215-A) so hopefully will be supported by MadWifi soon.

thingi

---

### Post by jdp on 2006-04-11
I haven't done much research, but you are right about Atheros.  It seems like it may be [a crapshoot](http://www.everymac.com/articles/answers_archive/jan23_2006.html) on what chipset comes in a new Mac...

---

### Post by entangled on 2006-05-09
Hope someone's still listening after such a long gap since the last post.
The intel mac mini is a very neat package of hardware and I want to use it with a neat OS - Dapper (MacOSX hasn't grown on me, despite being a mac approver).
I have got Dapper 606 beta2 installed on my intel mac mini (without chainloading via XP!), but the Atheros 506 wireless card won't work. I have tried modprobing the ath_pci module and it runs, along with wlan and ath_hal, but still no sign of a wireless network interface. Does anyone know how to get it going?
BTW I have had to uninstall NetworkManager completely because it seemed to be preventing ifup from getting a dhcp address. Without NetworkManager ifup works well.
We do seem to have some 'fragmented' - if not exactly broken - networking packages under Dapper.

---

### Post by entangled on 2006-05-13
Next chapter in this monologue is to report that the atheros card in the intel mac mini does work. I had to uninstall restricted modules to get rid of the old madwifi modules. Then installed the src of madwifi-ng for 12th May and compiled it up to a new set of atheros modules. 
This didn't work at first but using wlanconfig, rebooting and then stopping the wired interface seemed to kick the wireless into action.
However, the data rate is quite variable, KwifiManager reports between 54 and 11 Mbps even though the base station is less than a metre away. The signal strength is fairly constant at 50 to 60 (dB SNR?). This type of behavior is seen on the mac mini with MacOSX, XP and now Ubuntu, so it is definitely a hardware problem.
Is anyone else interested in running on the mac mini? It seems a great piece of hardware and not matched by pc stuff.

---

### Post by Ptero-4 on 2006-05-13
entangled. Good to see that your Wintel Mac-mini works. But remember.
Don't play christianic/gospel audio/video content in your mini, if you do it'll probably get cooked up by it's own intel CPU.
Don't rip copyrighted CD's or download copyrighted MP3's, or it'll probably go f*ck'd up by it's intel CPU.
Don't try to run KDE or make gnome look like MacOS 9, it'll probably blow on you.
And don't do anything closelly related to critizising the gov, M$, the RIAA, the MPAA, etc (you know who), or it'll catch on fire.

---

