---
title: "Ubuntu 64 bit on a samsung q310"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by Jophish on 2008-10-03
I can install the 32 bit version fine, However I would really like to utilise all of my 4gb of ram, and some other 64 bit features. However when I run the CD and either select install, or try to go to desktop, It reports:

Kernel alive
Kernel really alive

Then it flashes a few lines at the top of the screen (too fast for me to read) and then restarts my computer.

Could it be that this laptop is not 64 bit capable?

---

### Post by Kilz on 2008-10-03
> **Jophish said:**
> I can install the 32 bit version fine, However I would really like to utilise all of my 4gb of ram, and some other 64 bit features. However when I run the CD and either select install, or try to go to desktop, It reports:

Kernel alive
Kernel really alive

Then it flashes a few lines at the top of the screen (too fast for me to read) and then restarts my computer.

Could it be that this laptop is not 64 bit capable?

I took a look at the spec's . If yours has a core 2 duo its 64bit. You might want to try the alternate install cd.

---

### Post by Jophish on 2008-10-03
Well, after installing the 32 bit version from the live CD I am getting a problem while booting, it hangs on "loading hardware devices"

I'm afraid  have had no luck with the alternate CD. What do you think could be the problem?

---

### Post by Sef on 2008-10-03
1) Did you md5sum the downloads?

2) Did you burn the iso at 4x or less?

3) Have you checked the cd integrity?  Instead of booting or installing, go down the list to 'Check Disk for Errors'.

---

### Post by Kilz on 2008-10-03
> **Jophish said:**
> Well, after installing the **32 bit version** from the live CD I am getting a problem while booting, it hangs on "loading hardware devices"

I'm afraid  have had no luck with the alternate CD. [B]What do you think could be the problem?
[/B]
You are installing a 32bit version.

---

### Post by Yellow Pasque on 2008-10-04
I take it you're using the Intrepid beta (Ubuntu 8.10) version?

---

### Post by Gilbuzz on 2008-10-04
I bought a q310 today. Can confirm neither 8.10 or 8.04 64 bit install at all. Cant even run a CD check as all that happens is that it says "Kernal" at the bottom, then it reboots.

---

### Post by dumzdej on 2008-10-06
I've also tried to install both 8.04 and 8.10 without success on Q310 (64-bit version I mean). Also I've tried Fedora 10 beta - I managed to install it but then I had the reboot while udev have been initialised. The x86 version is working quite fine though (tried 8.04 and 8.10). BTW I recommend 8.10 cause the kernel have the drivers for wifi and lan and most of the things are working out of the box. Apart from the fact that I had to switch of splash cause it crashes the system - was stopping at 'loading hardware drivers' (for 8.10, which is weird cause on 8.04 it was working fine).

---

### Post by blackaardvark on 2008-10-08
bump

I have the same problem.

---

### Post by TheBigF2 on 2008-10-17
I too have tried (from LiveCD) (k)ubuntu on a Samsung Q310. The 8.04 live CD was okay and booted up, but without WiFi or ethernet working. The later is not a surprise since the drivers are not there I understand.

Unfortunately, the The 8.10 beta live CD (which should include kernel support) hung at the "loading hardware" stage. I know that the 8.04 iso was burned at 4X speed, but am not sure about the 8.10 version, and will check the CD tonight.

Incidentally, Slackware 12.1 boots, loads, runs etc okay, but again without WiFi and ethernet. 

Basically, I don't mind which distribution I use, as long as it allows me onto the internet!!

So any guidance on how to get 8.10 to start up, or drivers etc for 8.04 would be [COLOR="Blue"]wonderful![/COLOR]

---

### Post by TheBigF2 on 2008-10-18
A follow up - the alternative 8.10 beta CD loads ok, ethernet works and the system appears to transfer okay to the hard drive. However, on re-booting, into the newly loaded system, I get two types of errors firstly:

uvesafb: failed to execute /sbin/v86d ..... vbe_init() failed with -22

and then a few lines later:

Loading hardware drivers  ..............

and then things hang and I need to reboot.

Any pointers? Anyone? I have tried the directions above and they have not worked for me.

---

### Post by Jagot on 2008-10-24
I have no solutions, but I too am seeking them.  I thought I'd mention though that Mandriva 2009 works pretty much perfectly with the Q310, but I'd still prefer Ubuntu.

---

### Post by dumzdej on 2008-10-25
> **TheBigF2 said:**
> A follow up - the alternative 8.10 beta CD loads ok, ethernet works and the system appears to transfer okay to the hard drive. However, on re-booting, into the newly loaded system, I get two types of errors firstly:

uvesafb: failed to execute /sbin/v86d ..... vbe_init() failed with -22

and then a few lines later:

Loading hardware drivers  ..............

and then things hang and I need to reboot.

Any pointers? Anyone? I have tried the directions above and they have not worked for me.
As I said before you have to switch off splash that mean delete the option 'splash' in kernel line in 'menu.lst'. In grub it is possible to do it temporary (just for this boot) editing the boot options (press 'e, then find the line and delete the option, and boot pressing 'b').

---

### Post by Jagot on 2008-10-31
Bump.

I was hoping the final release would sort out these issues, but still no luck with the 64bit version, though 32 installs and seems to work.

---

### Post by TheBigF2 on 2008-11-02
Have installed Kubuntu 8.10 (32 bit) on the Samsung Q310 without the splash screen (see earlier post in this series). So far very pleased with it, KDE4 is fast and responsive (as it should be on a machine of this spec.) 

The WIFI, ethernet etc all work okay, however the Fn keys generally do not. Most significantly for turning the external monitor on and the WiFi off.

Now being comfortable with 32-bit I'll try 64-bit again.

TheBigF2

---

### Post by davbren on 2008-11-07
Any Q310 users got the brightness to work at all?

---

### Post by swf22 on 2008-11-10
I've got 64-bit Intrepid working on a Q310, including WiFi, apart from anything to do with ACPI. In order to make it boot at all I had to add the option "acpi=off" or "acpi=ht" to the boot options in grub. Without this then it just continually reboots. I haven't even been able to find out which particular stage is causing the problem since the screen scrolls and disappears too quickly. It reboots well before the kernel boot output is written to disk unfortunately. I've tried grabbing the boot output with netconsole as well, but it fails before the network interfaces are initialized too.

If I try and change the screen brightness, or suspend the computer, or unplug/plug in the power adapter then the machine just reboots. Has anyone managed to fix this? If not, is there any way of slowing down the messages that appear at boot so I can try and find out exactly which bit of ACPI is causing the problem?

---

### Post by swf22 on 2008-11-11
OK - Having compiled many different kernels with different ACPI options I think I've narrowed the problem down to the CPU frequency switching and thermal monitoring. With cpufreq disabled in the kernel, and the thermal and processor modules blacklisted then the system boots OK. However, I'm no closer to working out what to do to actually get things to work properly.

Incidentally, everything seems to work perfectly on a 32bit LiveCD. Unfortunately I need to run some programs that need over 3GB of RAM, so I'm stuck with 64-bit.

---

### Post by bulletq310 on 2008-12-13
After getting firmware 07SU from the samsung ( I think it was on the US page) page i was able to install ubuntu when disabling AHCI in the bios. fedora works too.
Still I am not able to use the buttons to change the brightness ... fn+up fn+down... and I already tried all the fixes in this forum.

bulletq310

---

### Post by JDShu on 2009-06-07
Hi all, I recently installed the 64 bit version of 9.04 and most things are working fine (blender runs amazingly) except for the things mentioned on this forum: 

-CPU Scaling 

-acpi (plugging in or unplugging the power restarts my computer) 

-brightness keys 

Sorry for resurrecting this topic, but has anybody managed to fix these problems since they were discovered?

---

### Post by JDShu on 2009-11-05
Update, in case anybody stumbles on this. This problem persists in Karmic as well. The workaround for all the releases is to add "mem=4096M" into grub or grub2 depending on your release. The effect will be that you can't use over 2.9 GB of RAM. (Apparently this is a BIOS problem with Samsung... WIndows 7 64bit users are having this problem as well)

Unlike in Jaunty and Intrepid, I don't think Karmic  "saves" the grub settings you used when booting into the LiveCD, so after installing Karmic, you might need to use the LiveCD to edit the grub2 settings.

Hope that helps somebody!

---

