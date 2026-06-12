---
title: "Installation Trouble"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheMindField on 2005-12-13
Hello Everyone.  I am having trouble installing Ubuntu on my laptop. Here are my system specs:

HP Laptop (ZW6000)
AMD 64 Athlon Processor
512 DDR Dual Channel Ram
80 Gig Harddrive
Current OS: Windows XP Home Edition

I have tried both the regular version of Ubuntu, and the AMD 64 version, and with both of them I get the exact same problem.  I pop in the CD, restart my computer, and the Ubuntu screen comes up.  I press 'enter' just like it says, and it begins loading the kernel, etc.  Then, once it has finished, the screen simply goes black, and nothing happens.  This went on for about 5 minutes until i finally gave up with both versions.  This also happens with the 'Live' Regular Ubuntu CD I tried.  Anyone have any ideas/solutions?

Thanks,  TheMindField

---

### Post by tburns on 2005-12-14
You may try passing some kernel codes at boot time. Check out this forum posting [http://ubuntuforums.org/showthread.php?t=75002](http://ubuntuforums.org/showthread.php?t=75002)

---

### Post by Hoop on 2005-12-14
You Should use AMD64 version.How far exactly does it get, Does it install Base system ? Does it copy packages ? Does it install completely but you can't log in ?

At a guess without further info you could try the following.

Boot Install CD then at the ':' prompt don't just push enter, type the following:

debian-installer/framebuffer=false

then push enter.

You could also try typing:

noapic debian-installer/framebuffer=false

if you think its a hardware issue. Post results back here remembering exactly how far the installation went.

---

### Post by alamba on 2005-12-14
This is a problem with some of the HP laptops. I have a DV 1350 and it took some time to figure this out. Here's the solution:
1. Make sure u're using the correct .iso for your architecture. In your case AMD64 version as hoop pointed out.
2. Turn up your volume on the laptop and try the live CD again. Your screen remains blank however you here the "ping sound" that ubuntu makes when the login screen appears.
3. This means that while the OS is loading up just right the display is the only problem.
4. Login into the single user mode via grub and naviagte to /etc/X11
5. vi xorg.conf
6. Down the file you will see an entry for Section "Device"
7. There would be another sub entry in this called Driver. The value of this would be "i810". 
8. Change this to "vesa"
9. Save the file and reboot, you will be up and running.
10. Incase your laptop is a widescreen laptop like mine is, there are a few more steps that need to be completed to get native resolution. In that case just shout out and I'll send you those steps. (Hint: Modeline entry in xorg.conf)

Hope that helps.

Akshay

---

### Post by TheMindField on 2005-12-14
Okay, I'm not currently at my house, so I can't try and see how far the installation actually gets.  

My laptop is a widescreen one, so it would be very helpful if you could tell me how to set the resolution for that.  Also, i'm not sure how to edit the "xorg.conf" file.  is there somethign you need to type at the live cd prompt before you press enter and continue to the OS? thank you everyone for your help. i will download the live version for AMD64 processors. I have already downloaded the AMD 64 install CD, but had the same problem with the display.  Thank you everyone for your help. 

-TheMindField

---

### Post by TheMindField on 2005-12-15
Okay, thank you everyone for your help. I finally was able to get the live CD to work, by passing the code 'live noapic nolapic".  However, this led me to another problem.  When I finally reached the login screen, it was just blue and white lines covering the screen.  Nothing i did, including 'ctrl+alt+backspace', 'alt+f1', 'alt+f2', 'alt+f3', had any effect.  Does anyone know what i can do to fix this problem?

Thanks, TheMindField

---

### Post by cadumg on 2005-12-19
I am trying it with the installation CD, not the Live CD. 

I tryed some Kernel commands like "linux acpi=off noacpi" but I still getting the black screen.

Does anyone know how can I install Ubuntu on a HP Notebook ?

Thanks a lot!!

---

### Post by cwaltzer on 2005-12-19
Hello I have a widescreen laptop and install went fine after "linux noapic nolapic" command at install, but when going to first login, I get an X error.  I do not know what to do to fix this.......
My laptop is an AMD Turion 64 1.8, Compaq Presario V2311US with a widescreen.  I have had other versions of linux running on this laptop, but was unable to get WiFi and sound to work, I was hoping to try out Ubuntu and see where it goes.  It has the ATI 200M onboard video. Thanks in advance for anyones help   :confused:

---

### Post by alamba on 2005-12-20
Hey guys...did anyone get this to work? Sorry I missed out on the thread...incase u still don't have it up feel free to post and i'll help (to the best of my ability, which itself might be limited!!)

Akshay

---

### Post by dsierpin on 2005-12-21
Hi all-

I've got an HP zv6000, and I had the same problems as MindField.

When you get to the GRUB menu, you have to boot the Recovery Mode option.  Then, you find your xorg.conf file, (mine was at /etc/X11/) and cd to that directory.  Open the file with:

```
nano xorg.conf
```

Find the section "DEVICE" that your video card is in.  My video card is an ATI Radeon Xpress 200M.  Add the following line:

Option            "NoAccel"

Save the file with Ctrl-X, and reboot.

Hope this helps!

---

### Post by Giant81 on 2006-01-19
But how do I get the LiveCD to boot on a ZV6000?  I can get through hardware detect and base install, but when X loads up I see the Ubuntu Spash screen and hear the start up sound... but just after that.. .it freezes solid.  I've tried the horay for X86 and for AMD64.  They both do the same thing.  

Anyone have any luck?  Thank you

---

### Post by blissfulpenguin on 2006-01-19
A few ideas:  While I haven't had the same problem with this release, I did have a similar problem before.  Make sure the installation CD is clean, and if that doesn't work, boot the CD with an alternative image (you'll just press F3 or something like that to see your boot options.).  I'm no expert, but I'm sure you'll find it is worth the effort!

Best of luck! :KS

---

### Post by dsierpin on 2006-01-19
> But how do I get the LiveCD to boot on a ZV6000?

I haven't had any luck so far with the LiveCD.  If all you want to do is check out some of the base installation packages, maybe someone here who knows what they're doing can give you a boot parameter to change the video driver to vesa or kill the 3D acceleration.

In any case, I think that the best option with the ZV6000 is installing rather than using the LiveCD, because there are so many things you have to do to make it work, and you can't install any fixes with the LiveCD.  Even if you manage to find some boot parameter that will get you a working driver for the video card, you need to install hsfmodem to use the internal modem (which was a must for me, but it won't work with the AMD64 version), you have to use ndiswrapper to get the wireless card working, and you're probably going to want to get the fglrx driver for the video card. 

Other things that you'll probably also want to tackle are the media card reader, the volume controls (touching them freezes the system so you have to restart), the touchpad (too sensitive, you'll need to make some changes to xorg.conf I think to fix this), and Totem (I got it to open once with ATI's proprietary driver, but it still wouldn't play video files).  As with any distribution, you'll also need to install some packages to play music files (mp3s at least).  Maybe there's a way to do all this with the LiveCD, but I haven't figured it out (again, hoping someone with some know-how will chime in here).

Tweaking ubuntu to work with your system is the fun part anyway, so why bother with the LiveCD?  Just set up a partition dedicated to Ubuntu, set aside some time and have fun! ;)

---

### Post by korakde on 2006-02-07
Have you tried typing 'live-expert' when you start the boot process. Then the os keeps asking you questions. Just keep pressing 'Enter' till you are asked to specify the driver for your ATI radeon card. Choose VESA instead of ATI. I have the very same chipset, had the same problem and solved it in this way. You'll get more details in the thread 'Live CD does not work'
Hope this helps

---

### Post by ralpho on 2006-10-21
burn the iso to a dvd not a cd end of troubles.

---

