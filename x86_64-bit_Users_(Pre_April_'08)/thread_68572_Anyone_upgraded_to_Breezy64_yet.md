---
title: "Anyone upgraded to Breezy64 yet?"
date: 2005-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kemotaha on 2005-09-23
I was wondering if anybody has upgrade to Breezy64 I am looking to soon but want to make sure it isn't go to killl my system.  I can stand updates often adn a crash here and there.

Thanks

Kemo

---

### Post by GuyveR800 on 2005-09-23
It works for me, but I haven't used it intensively yet.

---

### Post by mlomker on 2005-09-23
I've heard that gnome is okay but Kubuntu is too unstable.

---

### Post by banjo04414 on 2005-09-24
I have installed it on my amd 64 bit box. Just downloaded the latest a few days ago. Using the Kubuntu version. The install went smoothly, but when I got to the desktop it was missing quite a few applications. Constantly locks up, has problems with [funny lines appear on the screen] with the video, apt doesn't work, etc.,etc. Frankly, I was surprised at the instability of the pre-release. Thinking about junking it until the actual release comes out. A large download that seems to need some serious work to get it running right. Don't know about the Ubuntu Gnome version. Hope this helps make up your mind. :|

---

### Post by mlomker on 2005-09-24
> I have installed it on my amd 64 bit box. Just downloaded the latest a few days ago. Using the Kubuntu version.

I didn't have those kind of issues.  Sounds like a video driver and not sure what else for you.

My big problem was the broken control panel applets.  For example, the time was one hour off and there was no way to fix it because the control panel time section was inaccessible.

---

### Post by Kemotaha on 2005-09-27
I use Gnome, so I decided to go for it.  What did I have to lose? ( a bunch of time reinstalling Hoary).  I have been impressed.  It is cleaner, yet doesn't have the flash of the x86 version.  Usplash isn't working, but all the applications that I use are.  There is some major descrepiencies between x86 and AMD64, but oh well.  I wanted to be on the edge of technology when I bought the system.   I will stay with breezy for now.

---

### Post by Kuolio on 2005-09-27
I've been using breezy for few weeks now. Looks and feels good and stable, I haven't had any problems. Ach, one bad thing though: dist-upgrade didn't work for me, it borked my box, so I went the clean install way.

---

### Post by Etnu on 2005-09-27
I just bought a new notebook, and thought I'd give ubuntu a try (I've been using deb for most of my linux installs). I wanted a dual boot system, so installed XP Pro x64 first, then installed Breezy.

Everything installed fine, but it just locks up randomly when I try to login (if I click on any of the menus on the login screen it locks up immediately, and if i log in it'll lock up while it's attempting to load).

System is as follows:

Turion 1.6Ghz
ATI RS480M chipset
ATI 200M video
Some generic audio / LAN
1GB RAM

I'm downloading 5.04 instead now; I figure the worst-case scenerio is that it crashes as well.

---

### Post by mlomker on 2005-09-27
> ATI 200M video


Are you using the 'radeon' or 'ati' driver in your /etc/X11/xorg.conf file?  You could run **dpkg-reconfigure xserver-xorg** from the 'rescue' prompt to try the other.

---

### Post by Etnu on 2005-09-27
I'm using whatever the default was. I'll have to fire it up again and double check, but thanks for the advice.

I can run bash just fine, it's launching GNOME that seems to be the problem. Anybody else hitting this same wall here? I'd prefer to use GNOME over KDE, but if people are getting stable Kubuntu setups I'm willing to compromise.

---

### Post by Etnu on 2005-09-27
Ok, I didn't see an option for 'radeon', only ati.

It lets me log in, but if I click on any of the menus on the login screen it'll lock, and it locks up when the splash screen comes up after logging in. 

Weird.

---

### Post by mlomker on 2005-09-27
Try 'vesa'.  It's slow and reliable.

---

### Post by Etnu on 2005-09-27
Yep, that works. Thanks.

Now to start poking around with trying to find radeon drivers that work.

---

### Post by sfabel on 2005-09-27
Yes, I have - running on an HP Pavilion AMD Athlon64 Dual-Core 3800+. Runs fine!

I still don't know how to go about a decent solution regarding the compatibility issues - for example, having the w32codecs made usable to me. I'm not much into the chroot solution as it requires two times the effort to keep everything up to date and -to me- is simply not worth the trouble.

If anyone knew any good solution regarding this - I'd be grateful.

Cheers,
Stephan

---

### Post by mlomker on 2005-09-27
> If anyone knew any good solution regarding this - I'd be grateful.


There are a number of how-to's on the forums.  I have mplayer32 working.

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

---

### Post by sfabel on 2005-09-27
Hi mlonker,

thanks for the uncountable answers so far. :-)

One question though: when using mplayer in general, if I fullscreen it, the picture doesn't scale, but instead stays small with a large black border around it. Know what I mean?

Is there a config option where I can alter this behavior? Under gxine DVD playback works fine, albeit too fast.

Cheers,
Stephan

---

### Post by mlomker on 2005-09-27
> Is there a config option where I can alter this behavior? Under gxine DVD playback works fine, albeit too fast.


To be honest, I installed it just to see if I could but I don't actually use it.  There are *so* many media players that you could just try a few more of them: totem, vlc, kaffeine (kde).

---

### Post by banjo04414 on 2005-09-27
Maybe I'll try the "vesa" thing. I also think it's the video card, as in my setup I'm currently using the "sis chip" on the MB. I did recofigure- xserver to use the "sis" driver but guess it didn't work. I removed it completely, so if I re-install I'll set it up to use "vesa"  at the boot prompt and see if that works. Otherwise it doesn't do a complete install and half the programs are left out.:smile: 

Compaq SR1536NX
AMD64
1024 memory
9 in 1 card reader
dvd +r(lightscribe)
"sis chip" 128mb shared memory

---

### Post by Etnu on 2005-10-02
Here's a follow up:

I managed to get hardware mostly working. No sound as of right now (some realtek AC97 integrated audio on the lap top), no working DVD playback (of course...), weird resolution on the login screen, and the occasional flicker.

After I booted, I downloaded ATI's proprietary driver, installed it, configured x, and now everything looks good. I'm able to run it at all the supported resolutions (max on this is 1280x800 - wxga).

No crashes at all.

So, overally I'd say it looks like breezy seems to mostly work on turion chipsets. I'm about 99% certain that I'll find solutions for the other non-functional things in the next few weeks, once work lets up a bit and I've got the spare time.

Now if only if 64 bit Windows XP would be so easy. Half of the 32 bit programs simply won't run at all.

---

### Post by rplantz on 2005-10-03
I just did it.
I wanted to partition my disk, so I did a clean install from CDROM.
It went very smoothly, and it fixed a couple of important (to me) things. Now I can turn on my usb printer after booting. And OpenOffice prints just fine.
The only issues I've seen so far (about an hour) are due to my not being quite as careful as I should've been when I backed up my data. Just to be sure, I did it two ways. I used cp -r to copy my home directory to an external disk. I also tarred my account and sent it to my Mac. The thing I screwed up was permissions. A friend even suggested to me that I use rsync, but I forgot.
Oh well, this is mostly a hobby for me. So now I can learn more as I work to restore things back where I want them. Actually, I wanted to change some things anyway. So a (relatively) clean slate isn't a bad thing for me.
But, if you have some important things and don't have the time to play, I suggest that you pay attention to permissions when you back up, especially if you do a clean install.
Overall, I'm *very* happy with it.
Bob

---

### Post by hva on 2005-10-07
i upgraded to breezy on a nforce4 motherboard, athlon 64/3000+.
it mainly worked, but i can't enable dma on ide disks again (already tried all the fixes proposed on doc and forum, no luck), and **openoffice, both 1.5 and 2 version, segfaults immediately at launch**.
has anyone experienced similar problems? any hint?

---

### Post by Drain on 2005-10-09
[QUOTE=hva]i upgraded to breezy ... **openoffice, both 1.5 and 2 version, segfaults immediately at launch**.
has anyone experienced similar problems? any hint?[/QUOTE]

I had problems with OpenOffice when I initially upgraded to Breezy on my x86 box, and noticed in the apt-get process in the last 24 hours that OpenOffice was one of the packages flying by... it seems to be working for me now. I have no idea about the AMD64 version though. Good luck!

---

### Post by hva on 2005-10-09
[QUOTE=hva]i upgraded to breezy on a nforce4 motherboard, athlon 64/3000+.
it mainly worked, but i can't enable dma on ide disks again (already tried all the fixes proposed on doc and forum, no luck), and **openoffice, both 1.5 and 2 version, segfaults immediately at launch**.
has anyone experienced similar problems? any hint?[/QUOTE]

Now I've found out that if i do
**export LD_LIBRARY_PATH=/usr/lib32** or if i do
**ldconfig /usr/lib32**
then both openoffice 1.5 and openoffice 2 work.
maybe i have to look at my ld.so.conf file, should i put /usr/lib32 there?
Anyway, i think there is some problem with 2.6.12-9 kernel, as there's no way to set DMA for my ide drivers, even if i make sure that module amd74xx is loaded before ide modules, while i have no problems with hdparm using the old 2.6.8 hoary kernel.

---

### Post by jarchack on 2005-10-10
I've got an AMD64 3500 laptop on the way and I'm still trying to decide whether or not to go with a 64 bit install. Is there really a difference in performance? And is it worth running some stuff with 32 bit libraries (I assume you can do a chroot w/ubuntu)? 

As much as I like Ubuntu I may still try a custom build with gentoo or debian and if it gets borked I can use my ubuntu cd. But most likely the main issue will be getting 3d out of the radeon chipset. Anyone successfull with the ATI drivers for the radeon xpress 200? And does the broadcom 802.11g work with the 64 bit build?

---

### Post by garciadc on 2005-10-11
I have a AMD64 mobile 2700 laptop and 5.10 seemed to work great--rt2500 wireless worked upon install (which didn't happen in 5.04), but still working on DVD/RW.  The screensavers are all working better, but CPU usage jumps way up.  I noticed that the CPU frequency scaling monitor didn't work--was constantly at 100% (proc has PowerNow Technology); the comp started to warm up significantly (usually slightly warm), and the fan was always running.  I left the laptop plugged in, but I assume the battery would rapidly reach empty.

But after I updated (using update manager), the lower panel wouldn't show any open programs.  It scared me so I went back to 5.04.  Two tears in a bucket.  I also noticed after I updated and restarted both amd64 and i386 5.10, I could no longer find the terminal.  I guess it's due to the "preview" status of the dist?

I also have two desktops I installed 5.10 on.  One 2GHz P4 and the other 1GHz AMD Athlon (not sure how old it is, maybe ~2000).  They seem to be working great, no big performance enhancement, except that The AMD desktop only works with Linux, and constantly freezes w Windows. 

I also got those funny lines between an edge of contrasting graphics on the AMD desktop, but the resolution was too great.  I lowered it to 1024x768 and all is well.

I think I'm going to figure out what the heck I'm doing with 5.04 on the  AMD64 (seems harder to get everything to work) untill the official 5.10 release comes out, but I am leaving 5.10 on the desktops, making one a server--which means time for more coffee, I mean ubuntu.

---

### Post by Pablo_Escobar on 2005-10-11
Heck, I have AMD64 and I'm on Hoary 32bit.
With the new and very awaited release of Breezy I'm going to switch to 64bit.
Flash problems ?? Mplayer problem ?? Let me have'em !! I bought my AMD64 for something. 
64bit community must grow strong if we're to make pressure on Macromedia and others to make 64bit applications :)

Count me in as of Friday as a 64bit OS user :)

---

### Post by TheJoker on 2005-10-11
[QUOTE=Etnu]I'm using whatever the default was. I'll have to fire it up again and double check, but thanks for the advice.

I can run bash just fine, it's launching GNOME that seems to be the problem. Anybody else hitting this same wall here? I'd prefer to use GNOME over KDE, but if people are getting stable Kubuntu setups I'm willing to compromise.[/QUOTE]

Give tihs a go?
[http://ubuntuforums.org/showthread.php?p=401663#post401663](http://ubuntuforums.org/showthread.php?p=401663#post401663)

---

### Post by JeanBrownHarrell on 2005-10-13
I tried ...it installed fine but when I rebooted it started to boot and then hung right after it started booting the 2.6.12-9 amd64 kernel.  I have tried numerous times.  I reported it as a bug on 9-30-2005 and it is being worked on by somebody but it is not fixed yet and there is apparently one other person who has almost the same problem and almost the same hardware.  Breezy is not ready for release yet at least until they fix this bug.  If it is released, then it was released way too prematurely.  It is far too buggy and unstable for official release.  They should cancel the official release until they fix the bugs.  I like it a lot but won't even consider it until they fix the bugs.  Right now I'm having to run FC4-the 64-bit version as I type this.  I don't have a choice.  Hoary-5.0.4-amd64 runs great on my Athlon 64 3400 until I upgrade it to Breezy and reboot and then it fails partway through the boot.  It starts to boot...it shows what is in grub and gets to the part about decompressing linux and then says booting the kernel and then it says "ALERT!  /dev/hde1 does not exist.  Dropping you to a shell. and the next line shows a blinking cursor like this one-->"_".  So if they ever fix it then it will be a great wonderful distro.  I have a MSI K8T-NeoFisr2 motherboard with an AMD Athlon 64 3400 processor with an Nvidia GeForce FX 5200 256 MB agp8x video card with a LCD monitor-a ViewSonic VE510b [monitor cost me $430 total].  Wonderful system that works great with everything until this.  I have thought about reinstalling FC2-i386 but would like to try Ubuntu Breezy.  Tried Debian but too many problems although I like it a lot.  My only other choice is Red Hat Linux 7.3 or Red Hat Linux 9.  Anybody have any ideas--be my guest.  I would love to hear them.

Sincerely,

Jean Brown Harrell

---

### Post by metoo on 2005-10-13
Jean,

this line "ALERT! /dev/hde1 does not exist." made me thinking...

What kind of hard disk do you have? Do you really want to access a 5th Parallel-ATA device or do you have a S-ATA drive?

Reason why I ask:
At the beginning of the 2.6.x kernel series, the S-ATA drives where treated as Parallel-ATA devices but starting at /dev/hde. So even with only a single S-ATA drive in the system, you would access it as /dev/hde .
However quiet some time ago (around 2.6.8 ?) this changed and S-ATA drives are now treated as SCSI devices in the kernel. The 2.6.12-x kernel wants something like /dev/sda now for a single S-ATA hard disk.

If you want to try this, you can from within the grub menu:
- at boot tab to the breezy entry in the grub menu (with cursor keys)
- hit e (for edit, at the bottom of the screen are the options)
- tab to the line showing the /dev/hde1
- hit e
- change /dev/hde1 to /dev/sda1
- (guessing here: ) hit enter or b (for boot directly)

If this brings you up - good.
Note, that changes done in the grub menu are NOT permanent, so you can try things here. Every re-boot will you bring back to the original state.
If you want that permanently fixed, you have to change the entry as root in the file /boot/grub/menu.lst  .

Not sure, if another future kernel update would break this then again, but if, you now know how to boot into the system and then you obviously have to re-configure grub somehow. This is beyond me.

May be this helps...

---

