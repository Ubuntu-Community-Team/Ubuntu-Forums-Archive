---
title: "Headphon jack not working after kernel update"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mixium on 2007-03-05
Hi,

I installed Ubuntu AMD64 6.10 a few days ago. At the time of installation all sound was working correctly including the speakers and the headphones. After updating the system with the 135 pending updates including the kernel the headphone jack is now unresponsive. This means that when plugging in headphones both the speakers are not muted and the headphones produce no sound.

I have read in the forums that Ubuntu does not ship "alsaconf" with alsautils. I have also read that many of the users recommend building alsa from the latest sources to remedy this. I really do not want to do this. From experience, building packages yourself is a quick hack that will be again broken the next time the distribution offers a corresponding update.

Is it possible some how to run the sound configuration program used by the installer to reconfigure the sound devices? Where do I obtain the program or script that was used to configure the sound? How do I run the sound configuration program or script?

Here is the relevant information for my system:

HP dv6000t Core 2 Duo Laptop
Speakers: Integrated Altec Lansing stereo speakers 
Dual stereo headphone jacks -- one with high-definition digital audio support (S/PDIF capable)

CPU (Processor)
Quote
processor   : 0
vendor_id   : GenuineIntel
cpu family   : 6
model      : 15
model name   : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping   : 6
cpu MHz      : 1995.805
cache size   : 4096 KB
physical id   : 0
siblings   : 2
core id      : 0
cpu cores   : 2
fdiv_bug   : no
hlt_bug      : no
f00f_bug   : no
coma_bug   : no
fpu      : yes
fpu_exception   : yes
cpuid level   : 10
wp      : yes
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips   : 3995.94
clflush size   : 64

processor   : 1
vendor_id   : GenuineIntel
cpu family   : 6
model      : 15
model name   : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping   : 6
cpu MHz      : 1995.805
cache size   : 4096 KB
physical id   : 0
siblings   : 2
core id      : 1
cpu cores   : 2
fdiv_bug   : no
hlt_bug      : no
f00f_bug   : no
coma_bug   : no
fpu      : yes
fpu_exception   : yes
cpuid level   : 10
wp      : yes
flags      : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips   : 3991.57
clflush size   : 64

Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02) (prog-if 01 [AHCI 1.0])
SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1) (prog-if 00 [VGA])
Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
FireWire (IEEE 1394): Ricoh Co Ltd Firewire device 0832 (prog-if 10 [OHCI])
Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Thanks in advance!
Michael

---

### Post by dfreer on 2007-03-05
I have the exact same laptop and the same problem (although I NEVER got the headphones/microphones to work with Linux [they work in windows], I'm wondering how your sound worked?). About a month ago when I was running x86 I tried to rebuild ALSA to the latest version, and all that managed to do was screw up my volume control (using the multimedia keys or the volume control in GNOME to adjust sound adjusted the headphone output sound. since Headphones still didn't work this largely had the result of doing absolutely nothing, sound could only be adjusted by opening the volume manager and manually changing the master volume control).

> I installed Ubuntu AMD64 6.10 a few days ago. Even though you are in the x86_64 forum, just wanted to make sure that you are running in 64-bit mode?

EDIT: BTW, this particular laptop also has dual microphones located on the screen builtin. I suspect the same reason the headphone out jack doesn't work prevents the microphones from working as well. Output of sudo lshw:
```
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:de300000-de303fff irq:66

```

---

### Post by Songwind on 2007-03-05
Did you double check that "headphones" is checked in the "Switches" tab of the volume/mixer applet?

I thought my sound had died the other day until I realized that I had to control the switch from speakers to headphones manually.

---

### Post by ffxr on 2007-03-05
to build alsa fom source isnt really a 'hack' and the only updates that might affect it are kernel updates..  i wasnt happy with the surrond sound performance from my soundcard.. getting the latest alsa drivers has really improved my sound quality.. and although it is bit of pain, i would still recommend building with the latest alsa, espicially for the newer sound chipsets.

---

### Post by mixium on 2007-03-05
> **dfreer said:**
> I'm wondering how your sound worked?).

You've got me wondering about that now. The machine came with Vista installed. I ran that for just long enough to update Norton anti-virus, thought to myself how rediculous this was since I've been "Windows free" for the past three years and then reformatted the HDD and installed Zenwalk Linux 32 bit along with the alsa-utils-1.0.13 package. I bet that is when it was working. Since Ubuntu is not currently providing this ALSA version, I may take ffxr's advice soon and build it myself.

> Even though you are in the x86_64 forum, just wanted to make sure that you are running in 64-bit mode?

Yes. I've been yearning to run in 64 bit mode for over a year now. I specifically bought this laptop with the Core 2 Duo so that I could.

> 
EDIT: BTW, this particular laptop also has dual microphones located on the screen builtin. I suspect the same reason the headphone out jack doesn't work prevents the microphones from working as well. 

I haven't even tried the microphones yet. I'll see if that is broken as well.

> **Songwind**: Did you double check that "headphones" is checked in the "Switches" tab of the volume/mixer applet?

I thought my sound had died the other day until I realized that I had to control the switch from speakers to headphones manually.

I'm not sure if I did. Thanks for the tip. Maybe this is the ticket!

> **ffxr**: To build alsa from source isn't really a 'hack' and the only updates that might affect it are kernel updates.. I wasn't happy with the surround sound performance from my sound card.. getting the latest alsa drivers has really improved my sound quality.. and although it is bit of pain, i would still recommend building with the latest alsa, especially for the newer sound chip sets.

I'm experienced in building Slackware packages but not with Debian/Ubuntu packages. For this reason and the other reason I mentioned I want to try other methods first. However I believe if I can't get it working in the next day or so I will teach myself to build *.debs. It would be sweet of you to post you build scripts for ALSA to make things easier for me. Also, I'm used to building packages on a Slackware based system where all dev packages are already installed. Currently I have a stock Ubuntu 6.10 current system installed along with some apps that I installed by running "sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev" which I needed to install the proprietary nVidia driver which helped me to obtain a much better 1280x800 resolution. What other dev packages may I need to compile ALSA from source on Ubuntu?

:) 

Thanks for all of the advice guys. I'll have fun tonight tinkering with this.

Michael

---

### Post by mixium on 2007-03-05
Hi,

I've managed to find the alsa-1.0.13 packages already built for Ubuntu (probably Feisty) here: [http://ubuntu.mirrors.tds.net/pub/ubuntu/pool/main/a/alsa-utils/](http://ubuntu.mirrors.tds.net/pub/ubuntu/pool/main/a/alsa-utils/)

I will give these a try before compiling.

Michael

---

### Post by dfreer on 2007-03-05
> **mixium:** I've managed to find the alsa-1.0.13 packages already built for Ubuntu (probably Feisty) here: [http://ubuntu.mirrors.tds.net/pub/ub.../a/alsa-utils/](http://ubuntu.mirrors.tds.net/pub/ub.../a/alsa-utils/)

I upgraded alsa to 1.0.13 using that link... i had to upgrade libasound, libc6, and maybe a few other packages to do it... still no headphone output, even after running alsamixer (no headphones option either, just Master and PCM volume control as before, although it installed correctly and:  
```
alsamixer --version
``` reports that I'm using 1.0.13, I do not trust myself to having done this correctly.

> **Songwind:** Did you double check that "headphones" is checked in the "Switches" tab of the volume/mixer applet?

The problem I'm having, and i think everyone else who has one of these sound cards, is that there is no "switches" tab in the volume/mixer applet, nor in alsamixer. All I have is the aforementioned Master and PCM controls under the "playback" tab, and capture under the "capture" tab (which, btw, doesn't really do anything because the mics don't work).

> **mixium:** However I believe if I can't get it working in the next day or so I will teach myself to build *.debs.

checkinstall works great :)

---

### Post by ffxr on 2007-03-05
i dont think i had to install any extra dev packages.. tho dont shoot me if i am wrong..  my memory aint what it used to be ; )

before i started i removed alsa:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
you'll have to reinstall your desktop & the gdm after cos apt takes these with them

```
sudo apt-get install gdm (k)(x)ubuntu-desktop
```

** i HATE the way ununtu does this!!

i remember having a few problems with the make.. on the 1.10.13 drivers & had to use the 1.0.14rc2 development release.. i dont know if this was because of my 2.6.20 kernel or my actual soundcard chipset.. 

The compile commands are in this guide under section "Using drivers from alsa-project" (along with help for most off the other things you'll need)

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

i also compiled alsa library & alsa utils as per their readmes.. i dont build debs to install as m too lazy & it may be more trouble than they are worth.. you could have a look at **checkinstall** tho im told its not 100% reliable.

post successful build; if you have problems with your soundmixer not remembering soundmixer settings after a reboot... add these lines to your /etc/modprobe.conf  ( i was scratching round for hours trying to find a solution to this largely undocumented problem..) exchanging whatever module is used for you soundcard chipset of course.. : )


```
# load/unload the volume settings on startup/shutdown
   install snd_hda_intel /sbin/modprobe \
    --ignore-install snd_hda_intel;/usr/sbin/alsactl restore
   remove snd_hda_intel /usr/sbin/alsactl \
    store;/sbin/modprobe --ignore-remove -r snd_hda_intel
```


my sound quality has improved markedly with these new alsa drivers btw & m not an audiophile and dont usually notice these things so thats really saying something : )

---

### Post by ffxr on 2007-03-05
SNAP! ; sD

---

### Post by mixium on 2007-03-06
**dfreer!**

I have found yet another user with the same exact laptop and the same exact problem. His solution was to reinstall the kernel and the Ubuntu alsa packages.

Here, read what he had to say: (Page 3, Post #29)

[http://www.ubuntuforums.org/showthread.php?t=318259](http://www.ubuntuforums.org/showthread.php?t=318259)

> Many thanks, the


```
sudo aptitude reinstall linux-image-`uname -r`
```

seems to be the key for me as well. I'd tried building Alsa 1.0.13 after the kernel update broke my sound, without any success. That image reinstall, followed by alsa, did the trick.

I'm running a HP Compaq Presario V6000T (with Edgy), and both the headphones and speakers now work again.

:)

Michael

---

### Post by dfreer on 2007-03-06
> **ffxr:** I dont know if this was because of my 2.6.20 kernel or my actual soundcard chipset..

Well, I tried compiling a 2.6.20.1 kernel today, Making sure that snd_hda_intel was built as a module, and got it to compile fine (hopefully). With the new kernel, all of my drivers from linux restricted modules wouldn't work (I figured as much, but I was under the impression that they would be IN the kernel, just disabled or something). Well, enough of all that, the main thing is that my alsamixer once again gave me a headphone volume control that didn't control anything, and the headphones still wouldn't work *sigh*. I'm guessing that I might just have to wait for the snd_hda_intel driver to be upgraded to support my system.

EDIT: Ooops didn't see your post will have to give that a whirl. Did it work for you?

---

### Post by mixium on 2007-03-06
> **dfreer said:**
> 
EDIT: Ooops didn't see your post will have to give that a whirl. Did it work for you?

No, the sound isn't working on the headphones still. I did not upgrade to the latest ALSA version by compiling. I'm still holding off on this. I may just wait until Feisty is released because I see the needed alsa package in it's repo. I know enough to know that I don't know enough about Ubuntu's packaging and configuration routines to start changing parts myself. If this would be Slackware I'd do it myself.

However, reinstalling the kernel increased by boot speed by 500%! My system boots blazingly fast now! I have seen from my experience that some packages have post-installation scripts in them that require other packages to be installed in advance. My theory is that some part of the kernel package needed to link or modify another application that was updated after the kernel was and thus voided the  post-installation configuration scheme thereby breaking something and making my system take 5 times longer to boot that it should have.

I am so happy I reinstalled the kernel now. Fast is good!

Sweet!

:)

Michael

---

### Post by jbaldus on 2007-03-07
Something similar happened to me, too.  I'm using a Compaq V6120 laptop, and I've been running Feisty on  it for a couple of weeks.  The sound and headphones have worked fine until tonight.  I installed some updates, and now the sound is acting funny.  When there are no headphones plugged in, the regular speakers do not play any sound, but when the headphones are plugged in, the speakers play, but the headphones do not.  It's like the reverse of how it is supposed to work.  Does anyone have an idea of what might be going on?  It seemed that none of the updated packages had anything to do with the sound.  Thanks

---

### Post by jbaldus on 2007-03-07
Nevermind.  I rebooted with the 2.6.20-8 kernel and the headphone jack is back to normal.  If I get some more time this week, I'll try to track down the problem, but for now I'm just happy that my headphones work.

---

### Post by dfreer on 2007-03-08
I think the problem isn't so much with ALSA as it is with the driver snd_hda_intel provided by the kernel, but that's just my guess. Hopefully feisty will have things worked out *crosses fingers*.

EDIT: BTW, reinstalling the kernel image didn't do anything for me. Didn't even get the speed boost (for some reason my laptop likes to wait about 10-20 secs before it actually starts booting) :(

---

### Post by mixium on 2007-03-08
> **dfreer said:**
> I think the problem isn't so much with ALSA as it is with the driver snd_hda_intel provided by the kernel, but that's just my guess. Hopefully feisty will have things worked out *crosses fingers*.

I am hoping for the same thing.

> **dfreer said:**
> EDIT: BTW, reinstalling the kernel image didn't do anything for me. Didn't even get the speed boost (for some reason my laptop likes to wait about 10-20 secs before it actually starts booting) :(

That is strange as we have nearly identical machines, same model and all. My machine does not wait to boot as there is only one OS on it.

Let me give more detail on what I did. I fired up "System->Administration->Synaptic" and clicked on every green box of a package's name that started with "linux" and selected "reinstall" from the popup. It was not only the kernel image I reinstalled but all related packages. Maybe one of the related packages was the silver bullet. I still do not have a grasp on Ubuntu's post-package_installation routines. I am exploring that right now.

A little off-topic. I need to configure GRUB for my laptop's video-card and screen's resolution (we have the same machine) so that I can get the boot-splash in color. Currently it is only in black&white. I'm guessing that is because the 1280x800 wide-screen resolution is not standard enough for the installer or maybe GRUB. Would you by chance have already done so and would post your settings?

:)

Michael

---

### Post by dfreer on 2007-03-09
> A little off-topic. I need to configure GRUB for my laptop's video-card and screen's resolution (we have the same machine) so that I can get the boot-splash in color. Currently it is only in black&white. I'm guessing that is because the 1280x800 wide-screen resolution is not standard enough for the installer or maybe GRUB. Would you by chance have already done so and would post your settings?

I dunno about the black and white (mine's in color) but the default boot splash has always looked like crap on this machine, and from what I hear other people have problems with it too. I currently use the usplash [_*Fingerprint*_]("http://www.gnome-look.org/content/show.php?content=50468") and add vga=791 to my kernel options in order to get it to display correctly (vga=791 changes the boot resolution to either 1024x768 or 1280x800, never been sure which). So this would be what my /boot/grub/menu.lst looks like (affected lines anyways):
```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash **[B]vga=791**[/B]
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

> That is strange as we have nearly identical machines, same model and all. My machine does not wait to boot as there is only one OS on it.

Mine only boots ubuntu (yea!), the 10-20 sec freeze occurs right after grub loads the kernel, and before it starts fsck'ing the drives. But I only reinstalled the image using the ```
sudo aptitude reinstall linux-image-`uname -r`
``` command, I'll try it using Synaptic in the way you described. Thanks!

EDIT: BTW, I have had this headphone issue in x86 as well as x86_64, just to let anyone who is reading this thread know.

---

### Post by mixium on 2007-03-10
Hi,

I managed to get everything right. My headphones now work. My GRUB splash screen is now in beautiful colors and centered. What did I do? I upgraded to Feisty Herd5 current.

Two caveats. 

1. Do not start X with the headphones plugged in. They will then work in reverse if you do that.

2. After toggling the sound applet on the taskbar "mute then unmute", it seems to make everything perfect if I have some trouble.

Here's what I did:

A.) Upgraded to Feisty from info I found in the forum:

> First, you'll want to make sure that your machine is completely up-to-date on your current release. To do this you can run the following:

sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean

Once this is finished your machine should be completely up-to-date and you're ready to upgrade. To start the upgrade process you can try one of the following methods:

ALT:F2 - gksudo "update-manager -c -d"

or you can do things manually by:

    sudo aptitude install ubuntu-desktop (or kubuntu-desktop depending on your main GDM)

    sudo vim /etc/apt/sources.list

    find/replace every instance of [current] (ie; dapper) with [future] (ie; edgy)

    Once all instances of [current] are replaced with [future] (and remember you can only upgrade one version at a time) you can run the following:

        sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean

    This will then check for the latest available versions, upgrade to them, upgrade to any additional packages and dependencies and then clean up after itself. This will take a while depending on your network connection!

    Once these steps have finished you may also want to run the same command again, to make sure you haven't missed anything. I have often found that I have needed to run the command 2x-3x after a reboot to get everything just the way it should be. Ooh, and as usual be safe and back your critical files up before you do something like this. You never know if you might run into trouble, and its a good idea to back things up anyway.

B.) Rebooted the system and reinstalled my nVidia driver:

[http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:]("http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:")

C.) Ran the commands:

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean
```

...two more time and rebooted for good measure.

Now, I am very, very satisfied! Everything works now.

:)

Michael

---

### Post by dfreer on 2007-03-10
Really, feisty fixed everything? Hmmm I've been looking at feisty the way a married man looks at a cute college coed, maybe now I'll consider upgrading... Does your webcam work at all? I've gotten mine to work in Ekiga with the uvcvideo module, but not with anything else.

EDIT: In the above guide on how to upgrade, make sure to replace any words dapper => edgy and any edgy => feisty
w00t, upgrade went really smooth, just ran update/upgrade about 3-4 times to make sure I got everything. Headphones work GREAT (although I haven't tested using two headphones at once yet), Mics still don't work, and the webcam module no longer wants to compile (although I only spent about 2 mins working on it, it appears that I need to reinstall video4linux). Whenever I plug my headphones in/out I need to toggle the mute button on and off, but I couldn't care less my sound WORKS lol.

---

### Post by mixium on 2007-03-11
> **dfreer said:**
> Really, feisty fixed everything? Hmmm I've been looking at feisty the way a married man looks at a cute college coed, maybe now I'll consider upgrading... Does your webcam work at all? I've gotten mine to work in Ekiga with the uvcvideo module, but not with anything else.

Please give me an idea or a howto as to what you did to get the webcam up.

:)

> **dfreer said:**
> 
EDIT: In the above guide on how to upgrade, make sure to replace any words dapper => edgy and any edgy => feisty
w00t, upgrade went really smooth, just ran update/upgrade about 3-4 times to make sure I got everything. Headphones work GREAT (although I haven't tested using two headphones at once yet), Mics still don't work, and the webcam module no longer wants to compile (although I only spent about 2 mins working on it, it appears that I need to reinstall video4linux). Whenever I plug my headphones in/out I need to toggle the mute button on and off, but I couldn't care less my sound WORKS lol.

Cool!

:)

I went ahead and registered to help out with testing and filing bug reports on Feisty. I think that if you and I really want this fixed we should offer bug reports so that the devs are aware of whatever problems. That is much better than just compiling the alsa driver ourselves. I should know, I am an administrator for Zenwalk Linux. If users keep quiet we will never know.

I'm going to try to pin point when we need to toggle the mute button and then file a bug report. Also, like I said earlier, if yu can get me info on how to get the camera up I will try that and file necessary bug reports.

Ubuntu gets better everyday.

:)

Michael

---

### Post by dfreer on 2007-03-11
sweet, as I have yet to file a bug report I can just show you how I did it. [This Thread]("http://www.ubuntuforums.org/showthread.php?t=373843") contains information on how to get the webcam to work with both the Ricoh Model and the Sonix Model (I happen to have the sonix), although I haven't yet gotten it to work since I upgraded to feisty. It compiled fine and I inserted the module, and when I run Ekiga I can get the blue light to turn on... and then ekiga crashes. 

See what model of webcam you have, it sounds like the Ricoh one has a driver that works great now.



BTW, we should probably make a new thread (one for the webcam) and make this thread a HOWTO.

---

### Post by mixium on 2007-03-11
Hi,

I'm not so lucky with the webcam. After downloading the driver, make & make install, modprobe, etc... dmesg shows this:

> Linux video capture interface: v2.00
uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp: 26).
uvcvideo: Failed to initialize the device (-5).
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0-c)

Ekiga also says "no device found" and there is no /dev/video0

My devices info:

# lsusb
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd

# lshw
description: Video
physical id: 4
bus info: usb@1:4
version: 1.00
capabilities: usb-2.00
configuration: driver=uvcvideo maxpower=100mA speed=480.0MB/s

I'm going to try to get with the developer and give him the info I can.

Michael

---

### Post by dfreer on 2007-03-12
> # lsusb
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd

uvcvideo was only for the Sonix webcam, NOT the ricoh one. I happen to have sonix, so I used uvcvideo.

You should try the [*_R5U870 driver_*]("http://lsb.blogdns.net/ry5u870") instead (do a sudo modprobe -r uvcvideo first), although it supports ricoh webcams I'm not sure if it works for your particular model (it appears you have 05ca:1810 whereas the model the tested was 05ca:1870).

---

### Post by mixium on 2007-03-12
> **dfreer said:**
> uvcvideo was only for the Sonix webcam, NOT the ricoh one. I happen to have sonix, so I used uvcvideo.

You should try the [*_R5U870 driver_*]("http://lsb.blogdns.net/ry5u870") instead (do a sudo modprobe -r uvcvideo first), although it supports ricoh webcams I'm not sure if it works for your particular model (it appears you have 05ca:1810 whereas the model the tested was 05ca:1870).

Yes, my webcam seems to be close but different enough to not work. I have emailed the author of the driver along with my system's info. I'm posting it for you if you're curious.

> mike@mike-laptop:/$ sudo lsusb
Bus 005 Device 003: ID 05ca:1810 Ricoh Co., Ltd
Bus 005 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 002 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000

****************************************
****************************************

mike@mike-laptop:/$sudo  lsmod
Module                  Size  Used by
r5u870                 60232  0
video_buf              29700  1 r5u870
compat_ioctl32         11136  1 r5u870
videodev               29824  1 r5u870
v4l2_common            28800  3 r5u870,compat_ioctl32,videodev
v4l1_compat            14980  2 r5u870,videodev
binfmt_misc            14604  1
rfcomm                 45352  0
l2cap                  28160  5 rfcomm
bluetooth              61828  4 rfcomm,l2cap
ppdev                  11272  0
acpi_cpufreq           10760  1
cpufreq_userspace       6176  0
cpufreq_stats           8416  0
cpufreq_powersave       3072  0
cpufreq_ondemand       10640  1
freq_table              6336  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0
video                  19080  0
sbs                    17856  0
i2c_ec                  6784  1 sbs
dock                   11968  0
container               6144  0
button                 10016  0
battery                12040  0
asus_acpi              19756  0
backlight               8448  1 asus_acpi
ac                      6920  0
ext2                   72592  1
mbcache                11400  1 ext2
ipv6                  299904  10
sbp2                   26628  0
parport_pc             40104  0
lp                     15048  0
parport                43404  3 ppdev,parport_pc,lp
snd_hda_intel          23840  1
snd_hda_codec         243200  1 snd_hda_intel
snd_pcm_oss            49408  0
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0
snd_seq_oss            36608  0
joydev                 12928  0
af_packet              27020  2
snd_seq_midi           11008  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ide_cd                 35104  0
cdrom                  40744  1 ide_cd
ipw3945               128416  0
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7749016  22
ata_generic            10244  0
ata_piix               18948  0
ieee80211              37064  1 ipw3945
ieee80211_crypt         8064  1 ieee80211
i2c_core               26624  2 i2c_ec,nvidia
intel_agp              28736  1
sdhci                  21516  0
mmc_core               31752  1 sdhci
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                43408  0
serio_raw               9092  0
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
iTCO_wdt               13648  0
iTCO_vendor_support     5636  1 iTCO_wdt
shpchp                 37404  0
pci_hotplug            36228  1 shpchp
evdev                  13056  5
tsdev                  10112  0
xfs                   533448  4
sg                     40616  0
sd_mod                 23808  7
piix                   12804  0 [permanent]
usbhid                 29088  0
hid                    34048  1 usbhid
ehci_hcd               37004  0
ahci                   26500  6
e1000                 133440  0
generic                 6788  0 [permanent]
libata                127656  3 ata_generic,ata_piix,ahci
scsi_mod              166968  5 sbp2,sg,sd_mod,ahci,libata
ohci1394               38088  0
ieee1394              369144  2 sbp2,ohci1394
uhci_hcd               28056  0
usbcore               154288  5 r5u870,usbhid,ehci_hcd,uhci_hcd
thermal                16784  0
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0
fbcon                  44416  0
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0
commoncap               9472  1 capability

****************************************
****************************************

mike@mike-laptop:/$ sudo lshw
    description: Notebook
    product: HP Pavilion dv6000 (RD869AV#ABA)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF7072YS6
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=oem-specific chassis=notebook uuid=434E4637-3037-3259-5336-001636F8AC00
  *-core
       description: Motherboard
       product: 30BC
       vendor: Quanta
       physical id: 0
       version: 66.37
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.16 (02/02/2007)
          size: 100KB
          capacity: 960KB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU T7200
          slot: U2E1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 4MB
             capacity: 4MB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: DIMM Synchronous 667 MHz ( 1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz ( 1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce Go 7400
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:dd000000-ddffffff iomemory:c0000000-cfffffff iomemory:dc000000-dcffffff irq:16
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:de300000-de303fff irq:22
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0
                resources: iomemory:d8000000-d8000fff irq:16
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@05:00.0
                logical name: eth0
                version: 00
                serial: 00:16:36:f8:ac:00
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:da000000-da01ffff ioport:4000-401f irq:506
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1800-181f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-9-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB /s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-9-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed= 1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-9-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-9-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:de304000-de3043ff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-9-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed= 480.0MB/s
              *-usb UNCLAIMED
                   description: Video
                   physical id: 4
                   bus info: usb@5:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@07:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:de000000-de0007ff irq:16
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@07:05.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64
                resources: iomemory:de000800-de0008ff irq:17
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@07:05.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de000c00-de000cff irq:11
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@07:05.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de001000-de0010ff irq:11
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.4
                bus info: pci@07:05.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de001400-de0014ff irq:11
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1880-188f irq:18
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorpCD/DVDW TS-L632D
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: HH16
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:18c8-18cf ioport:18ac-18af ioport:18c0-18c7 ioport:18a8-18ab ioport:18b0-18bf iomemory:de304400-de3047ff irq:507
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK8034GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AH30
                serial: 17UWFC6GS
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 101MB
                   capabilities: primary
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 2047MB
                   capabilities: primary nofs
              *-volume:2 UNCLAIMED
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0 :0.0.0,3
                   capacity: 14GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 57GB
                   capacity: 57GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0 UNCLAIMED
                      description: Linux filesystem partition
                      physical id: 5
                      capacity: 34GB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10001MB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 13GB
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0-18ff irq:4

****************************************
****************************************

mike@mike-laptop:/$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by mixium on 2007-03-13
Hi, 

Here is an update of the conversation between Sam and I.

> Hi Michael,

You are an individual fortunate enough to have one of the new Ricoh
UVC cameras.  They don't work with my driver, at least not yet,
because they use a different USB command set.  They don't work with
the linux-uvc driver either, because that driver doesn't know how to
use the vendor commands to upload the microcode, at least not yet.

I hope to have something worth testing later this week.  Would you be
interested in participating?

Thanks.
-Sam Revitch

Of course I told him yes.

;)

Michael

---

### Post by dfreer on 2007-03-13
Nice, hope that works out! I should probably find whoever is in charge of my uvcvideo driver because I'm still having problems with it after the kernel upgrade.

---

### Post by mixium on 2007-03-13
dfreer,

Back to the original topic (the sound woes), the amazing guys working behind the scenes have come up with a kernel patch to fix our troubles. In one of the IRC rooms I spoke to a couple of guys who pointed me to the first bug report for the sound troubles. You can read that report here: [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90775](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90775)

Here is what the guys said:

> The description is a bit misleading; the real issue is was, depending on which kernel used, either missing jack sense control or a jack sense inversion

The bug has been resolved via a kernel patch which you view here: [http://hera.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commitdiff;h=94e796e42ba693e81a0e6497d9477cdbb742ce4c](http://hera.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=commitdiff;h=94e796e42ba693e81a0e6497d9477cdbb742ce4c)

If you take a second to read the comments the devs wrote in the patch you will see that every remaining problem has been addressed. This is especially nice IMHO since it is getting fixed in the kernel which notoriously has outdated alsa drivers (it is the next step being taken from the start).

Back on the subject of the webcam they suggested once I have the new working kernel module to file a bug report against the current Feisty kernel so that it can be incorporated (hopefully).

Now those two things would make my Ubuntu experience perfect. I must say that I am very impressed with the skill of the Ubuntu developers having worked with other groups myself.

:)

Michael

---

