---
title: "athlon 64  kernel dies at boot from ubuntu 7.10 64bit cd"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by yaywoop on 2007-10-25
I downloaded the latest 64bit ubuntu to install on a AMD Athlon 64 3000+ with the gigabyte K8nf-9 motherboard. when I boot off the cd, after the kernel loads from the boot screen, it displays "Kernel alive" "kernel direct mapping tables up to 100000000 @ 8000-d000" at the bottom of the screen. then "Loading, please wait..." briefly at the top.
then the video output turns off and the caps and scroll lock led's flash.

I have tried the cd on another (core2 duo) computer and it boots perfectly.
I also had a look at the bios, but couldn't find anything useful. is there a boot option I should be putting to the kernel?

thanks

---

### Post by endymon on 2007-10-25
Can you edit the bootup options by removing quiet & splash ?

This should do the trick and if not you will at least get more detailed diagnostics.

---

### Post by ACLerok on 2007-10-25
Sounds like you're having ACPI issues. 

try adding acpi_use_timer_override or acpi=off at boot time.

---

### Post by BogusJoe on 2007-10-25
I had the same issue, but after I set the system back to normal...no overclocking, it worked. Even if you overclock the memory it may do the same.  Set memory timings to auto.  This may not be the case for you.

---

### Post by Tosa on 2007-10-25
Same with me (Core Duo). The installation went on after I manually set resolution to 800/600/16.

HTH

---

### Post by yaywoop on 2007-10-25
> **endymon said:**
> Can you edit the bootup options by removing quiet & splash ?

This should do the trick and if not you will at least get more detailed diagnostics.

I tried this and it seemed to work.
my system is not overclocked at all. however, windows xp did have some problems with it, some auto updates caused the system to crash at startup and windows always took ages to load. even when it was freshly installed. I don't know if that is relevant.

---

### Post by yaywoop on 2007-10-25
> **ACLerok said:**
> Sounds like you're having ACPI issues. 

try adding acpi_use_timer_override or acpi=off at boot time.

ok so i installed ubuntu from the live desktop. the same thing happens. removing splash does the job. this makes me think that the video mode is unsupported. what option do i pass to change video mode?
and X does not correctly recognize the resolution, it uses 1280x768. my screen's native resolution is 1280x1024.
btw acpi_use_timer_override and acpi=off don't work.

I also tried loading defaults for the bios, that made no difference

thanks

edit: I tried passing vga=771 and even vga=769. it made no difference :( I guess i will just not use the splash screen

---

### Post by jaybombalous on 2007-10-27
There is a config file that u can manually set the resolution for the splash screen, but for the life of me I can not find it in the search function. this is getting frustrating.

Ubuntu works and loads fine, its this damn website that doesn't work!!!!

---

### Post by UltimaLTD on 2007-10-27
Hello,

I'm having EXACTLY the same problem.
I have the same processor, and I'm experiencing the same effects.

I've seen the possible solutions above, but I have no idea how to implement them.. 
I'm somewhat of a Linux noob. 
If anyone could help me directly, or write out what to do that'd be appreciated.

Thanks!

- Mike

---

### Post by Therion on 2007-10-27
Curious if either of you have nVidia 8000 series video cards...  Anyway, I had this problem and here's what worked for me:

Boot from the LiveCD.
When the GRUB menu comes up hit "Escape" and select "Recovery Mode".
You'll seem some screens scroll by and wind up at a command prompt.
At the command prompt:
```
nano /boot/grub/menu.lst
```
Scroll down past all the # signs and look for the first line that starts with Kernel.  It's a long line of code that will go off the end of your display.  Use the arrow keys to get to the end where you'll see the word "splash".
Remove the word splash from that line.
Ctrl+X, confirm the overwrite and reboot.

This should get you to the desktop where you can install Ubuntu to your hard drive.  AFTER it's installed to your hard drive, you'll need to **re-edit** menu.lst because now you're booting from your hard drive and not the LiveCD. 

Follow the above steps again once you've booted from your hard drive and you should then be prompted about installing the Restricted Driver automatically.  Install the driver and you should be good to go from there.

Search the forums about how to get your boot-screen back.  Nothing worked for me, so I just live without a boot screen.

---

### Post by jaybombalous on 2007-10-27
But there is another solution, its manually setting the resolution in a config file for the splash screen. It has to be 1024 x 768 or whatever it was. 

I know thats what is wrong here because if my monitor can't display a resoltion it goes into power saving mode. Thats the exact reaction I get and it will return to login in exactly the same amount of time it takes to boot ubuntu. Its all to much of a consequence to be anything else in my case.

NOW where is that stinking config file????

---

### Post by jaybombalous on 2007-10-27
^^^^ your fix above by removing the splash works because it doesn't have a problem displaying text with the no splash login. :) I think I am getting warmer.

---

### Post by Therion on 2007-10-27
> **jaybombalous said:**
> NOW where is that stinking config file????
Are you looking for: **/etc/usplash.conf** perhaps?

---

### Post by pony-tail on 2007-10-27
I have the same issue withe the Ubuntu 64 7.10 live cd
The Kernel dies in the same place .
The machine is a Shuttle SN25P CPU is X2 4600+ Video is ATI X850XT PE Monitor is ViewSonic 22inch LCD (1680x 1050) ram is 2 x 1024 Corsair XMS (also tried Kingston HyperX 2x 512 C2) 
Have tried various resolutions and acpi=off noapic nolapic and various others but it hard locks and needs to be powered off to reboot
This system is currently running Mepis64 without issue

---

### Post by pony-tail on 2007-10-27
A combination of nosplash + noX  got it to boot to a command prompt .
After reconfiguring the xserver I have managed to get the live cd up using the ati xorg driver .
But with the issues I am having with the live cd I am VERY reluctant to install on a stable working machine.
I was going to replace Mepis with Ubuntu but their implementation of X is a little too flakey for my liking
Just tried the CD on another machine (also nForce 4 but with nVidia Sli setup ) same thing !

---

### Post by pony-tail on 2007-10-27
Back again I installed Ubuntu64 even though it had issues !
The result is that If I boot the default kernel - it hard locks in the same place .
If  I boot the recovery kernel it boots up fine .
Now - If when I boot up the recovery kernel I type startx I get a warning about privileged user and a correctly configured xserver at the correct resolution (1680x1050) - but no network .
So I believe the issue to be kernel related - not - xserver related .
Anybody got ideas .
Any log files I should look for ?

---

### Post by duffernix on 2007-10-28
What ended up working for me was to unhook my machine from my kvm switch and 1650x1080 monitor, and hook it up to an old dell 15" crt, generic keyboard, & mouse. The install & following reboot + updates went flawlessly. Installed the restricted driver (nvidia), rebooted and all was well.  When the machine was hooked back up to the widescreen monitor & kvm, it refused to boot. I rebooted into the recovery kernel and issued the "sudo dpkg-reconfigure xserver-xorg" command. Everything was correctly detected (except I changed the nv module to the nvidia module) so I accepted all prompts. After that the machine has been quite content. Hope that this helps in some way.

---

### Post by pony-tail on 2007-10-28
Changing the /boot/grub/menu.lst  (changed splash to nosplash) got it to boot !
aiglx and compiz are working fine !
But - it hangs for quite some time at the point where it was freezing previously - no hdd activity , no other sign of life , and then the text scrolls past and everything boots up fine
Tried it with one of the GF7950 out my Sli windbox and the live cd locked up as well , but a little later at the  "loading please wait"  or whatever, was only there for a split second - then black screen flashing keyboard lights monitor power down the same as before !
So it is not specifically Radeon related ( ati cards are my first suspect with Linux boot issues)

---

### Post by yaywoop on 2007-10-28
wow wow wow. i think we are getting some different issues here...
my original problem was the kernel crashing when it tried to display the splash screen (keyboard led's flashing). I disable the splash screen and everything works.
it may be a graphics driver problem, I have an ATI RX700 card. the problem must be with the framebuffer in the kernel, because X has no problems. and I think its only the 64bit kernel I was having this problem with. 

and there is a faster way to pass options to the kernel at boot than editing the menu.lst file.
i think you press F6 at the cd boot menu, that lets you edit the boot parameters directly. then you can just remove "splash" and boot away. 
after you install, you press "e" at the grub boot menu of your install which lets you edit the kernel options. once the installation is booted, edit menu.lst
thats how I did it anyway.

---

### Post by yaywoop on 2007-10-28
interesting. i changed the /etc/usplash.cfg file to 800x600 and the kernel still crashes before the splashscreen

---

