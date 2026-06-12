---
title: "Stay away from HP ZV6000 series laptops"
date: 2005-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eraser on 2005-05-25
Hello,

     I recently got a good deal on an HP ZV6000 series laptop, featuring an AMD 64 CPU.  I went ahead and got it, with the intent of installing Ubuntu on it.

     Unfortunately the video card that comes with the laptop (ATI Radeon Express 200M) is very new and there are no X.org drivers for it.

     Ubuntu does show a graphical login screen, however when trying to log in the laptop freezes, the only way out is to shut it down.  I tried installing both Breezy and Hoary on it, with the same result.

     After being unsuccessful with Ubuntu, I tried to install Fedora on it, Fedora does allow you to log in to Gnome (although at an ugly 600x800 resolution) , however it doesn't recognize the touchpad, making the laptop unusable.

     For the time being I am stuck with Windows XP home on this laptop :(

     I just wanted to warn any potential buyers out there that this model is not Linux friendly.

Eraser

---

### Post by tread on 2005-05-25
Have you tried Fedora Core 4 - Test release 3? I've heard good things about it.

---

### Post by Eraser on 2005-05-25
[QUOTE=tread]Have you tried Fedora Core 4 - Test release 3? I've heard good things about it.[/QUOTE]

Yes, that is the version I tried, after some research I found out tha the stock Fedora Kernel does not support /dev/psaux, which happens to be the device that Knoppix (and perhaps Ubuntu too, quite frankly I can't remember if it did recognize the touchpad).  I tried compiling a stock kernel with support for that device, unfortunately   It didn't go as expected (some initrd something or other file that was supposed to be created wasn't).

I'll try reinstalling Ubuntu and using the vesa driver for the time being.

Eraser

---

### Post by BigCdaAnswer3 on 2005-05-26
I wouldn't necessarily say that you're laptop isn't linux friendly, it just is fairly new so the linux support is not the greatest. I have a HP zv5000 laptop, and i bought it brand new, and I had many of the same issues you have except I have an Nvidia card. I don't know if you have the same touchpad as I do, but whenever you get into X, try doing:

modprobe -r psmouse
modprobe psmouse

This was a bug in Ubuntu that I quite frankly just figured out by playing around w/ it by accident, that I never reported (prolly shoulda, but just too lazy), so give this a shot. If that works just add those two lines to your gdm startup script. 

Also, I almost guarantee you the support you will have in breezy even by the end of summer should be good enough to have a usable ubuntu setup w/ prolly only a couple quirks here and there.  \\:D/

---

### Post by ::DoGG:: on 2005-05-26
I got the same prblem some time ago when i bought Compaq Presario r3000 with amd64, after 4 days of digging on the net o succesfully got everything worked out. And there was NO support for linux in that laptop. Since then my opinion is that there aren`t  any anti-linux laptops, sometimes we jus don`t have enough patience :D

---

### Post by Eraser on 2005-05-26
Thanks for the words of encouragement.

I am happy to report that I was able to install Hoary on the laptop, not everything is working (yet) but at least it installed.  :) 

I am using the vesa driver for x.org, therefore I have no 3D acceleration.

I did learn about the trick of unloading and reloading the psmouse module by surfing around the web, it does work with this model as well.  I haven't been able to get the touchpad scrollbar to work, any hints for this?

I just got x.org working last night, I haven't had  a chance to try to get the wireless working, from what I have read, looks like I'm going to need ndiswrapper to get it going.

BTW, the reason Fedora would not recognize the touchpad at all is because their stock kernel does not support /dev/psaux.  A custom kernel needs to be compiled to add support.  In any case, I wanted Ubuntu on the laptop, not Fedora, and I am relieved that I got it to work (with some caveats, but still).

Eraser

---

### Post by ::DoGG:: on 2005-05-27
Great to  her it :D
I got on my Compaq Synaptics touchpad. It only works when i load tsdev, evdev and psmouse modules in correct order, and in xorg.conf for mouse i have to use /dev/evdev since it`d working with events. Lot of troble but a great success :D Keep up a godd work.

---

### Post by Eraser on 2005-05-27
[QUOTE=::DoGG::]Great to  her it :D
I got on my Compaq Synaptics touchpad. It only works when i load tsdev, evdev and psmouse modules in correct order, and in xorg.conf for mouse i have to use /dev/evdev since it`d working with events. Lot of troble but a great success :D Keep up a godd work.[/QUOTE]

I don't seem to have a /dev/evdev device, however, I tried using /dev/gpmdata, which is what I had been using all along.  I'm happy to report that after loading the modules you mentioned, in the order you mentioned, the touchpad scolling is working :D

Thank you very much for the information.

Eraser

---

### Post by ::DoGG:: on 2005-05-27
No problem, glad i could help. :D

---

### Post by NickB on 2005-05-29
Here's my setup, hope it helps you:

1. Put atiixp as the first line in /etc/modules or else your disk will be very, very, very, very slow.  Very slow.

2. If you have trouble with the keyboard, press fn+shift after booting.

3. The ati driver for xorg works fine, but you need Option "NoAccel" true.

4. If you have problems with the touchpad, rmmod psmouse and modprobe psmouse and restart gdm.  Alternately, add those commands to /etc/X11/xinit/xserverrc.

5. Lots of people are having success with ndiswrapper for the wireless adapter.  I had it working 1 time but never again.  Don't know what I did to fubar it.

I'm working on getting the latest driver from ATI to work with xorg, no success yet.

Nick

---

### Post by NickB on 2005-05-30
As an update, I did get the the latest fglrx64 driver (8.13) from ATI running.  I just aliened the rpm and installed (--force-overwrite), and in combination with the aforementioned atiixp module, it works fine without compiling the fglrx kernel module.  I changed "ati" to "fglrx" and commented out the Load "dri" line (not sure if it would work).  Nice to have the 2d acceleration at least.

Nick

---

### Post by NickB on 2005-06-06
I got the latest fglrx kernel module to compile and load (in a custom built kernel), but it was too flaky to be any use, and DRM is documented not to work anyway.  So I am sticking with using the fglrx X driver without the kernel module, since I don't play games in linux anyway.

Other than that, my zv6000 is 100% with ubuntu.  Aside from the timing issues that are not specific to the zv6000.

Nick

---

### Post by NickB on 2005-06-06
I just upgraded to kernel 2.6.12-rc6, and it solved all my remaining problems.  It properly initializes the keyboard without finger tapdancing, and the double clock speed can be resolved by passing "no_timer_check" as a bootparam.

Good luck to anyone with a zv6000 series...
Nick

---

### Post by sh4d0wstr1f3 on 2005-06-08
Nick: this thread single handedly solved much grief. Have you thought about writing a HOWTO for zv6000 users? If you're not interested, let me know, because this thread really solved all of my problems. It's great to find the solution on the net, but even better when you only have to go to one spot.

Thanks so much!  :)

---

### Post by NickB on 2005-06-08
Thanks, I've been meaning to get around to doing just that, but haven't quite found the time.  When I do I'll link it at [http://www.linux-laptop.net/](http://www.linux-laptop.net/) as well.

Nick

---

### Post by sh4d0wstr1f3 on 2005-06-08
[QUOTE=NickB]I just upgraded to kernel 2.6.12-rc6, and it solved all my remaining problems.  It properly initializes the keyboard without finger tapdancing, and the double clock speed can be resolved by passing "no_timer_check" as a bootparam.

Good luck to anyone with a zv6000 series...
Nick[/QUOTE]
Just to verify -- you built this kernel manually vs. pulling it from some bleeding edge apt repository, right?

---

### Post by NickB on 2005-06-08
I downloaded the latest rc from kernel.org and then copied config-2.6.11-1-amd64-k8 to .config in the source tree.  Then I used make-kpkg to make a kernel package.  The actual command line I used was:

fakeroot make-kpkg --bzImage --initrd --revision 20050605.1 --append-to-version -amd64-k8 binary

That'll make all your packages, including kernel-headers (which you'll need to compile ndiswrapper).  I further configured my kernel to trim out some modules I'll never use, but it should work fine as is.  If you still want the nice framebuffer console, you'll have to configure the framebuffer device as static rather than as a module.

Good luck,
Nick

---

### Post by OneSeventeen on 2005-06-15
Okay, I just wanted to kind of prod you in the direction of writing that tutorial... I'm really stoked to hear you got this working, and I have a *slightly* better idea of what I need to do.

Unfortunately, I've never compiled my own kernel, don't know where half the config files are for linux (make that 99%), and am kind of curious how to download and compile stuff when I can't even get my laptop to start up....

any general tips on the basics used to get this working, and maybe I can just research what you've mentioned thus far with the knowledge of how to get a system up that will allow me to edit text, compile kernels, and whatnot?


Thanks, and thanks again for posting your findings!  I can't wait to get this set up and running in its full potential!!!

Have you run blender3d by any chance on this machine with ubuntu 64?  (I'm assuming performance will be better, as the windows ATI drivers keep blender3d from running anywhere near the speed it should.)

---

### Post by NickB on 2005-06-15
Haven't run blender, but the video recoding I've done is lightning quick.

Here's some rough steps to compiling your own kernel, but you might want to look here: [http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)

1. Download your kernel source from kernel.org
2. Get everything you need to build a kernel, usually just apt-get install kernel-package should do the job, but also apt-get build-dep linux-image-XXX (it doesn't matter which one, they all use the same tools) just to be sure.  Also apt-get install ncurses for make menuconfig if you want to customize the kernel.
3. untar the kernel source
4. Copy /boot/config-XXXX from the latest kernel you can apt-get of your arch to .config in the top level of the kernel source tree.
5. Type something like this to make the kernel packages:
  fakeroot make-kpkg --bzImage --initrd --revision 20050605.1 --append-to-version -amd64-k8 binary

What comes after --revision can be whatever you want, I like using a serial date.  --append-to-version is not strictly necessary, but mirroring the naming convention in debian is nice.

6. There will be some "unconfigured" items in the .config, due to extra things in the latest kernel.  Use your best judgement when answering the questions (usually "m", but don't quote me on that ;)).
7. That will make the kernel image, headers, source and doc packages.  Install at least kernel-image-XXX.deb and kernel-headers-XXX.deb, reboot, then rebuild the other kernel modues you might need (probably just ndiswrapper; the fglrx kernel module for 2.6.10 won't work for you anyway).

For some reason, the config file doesn't pick up the vesa console, I suspect it's in the initrd in pre-packaged kernels.  I just make menuconfig and select "y" instead of "m" to make it static in the kernel.  Otherwise, remove any vga=xxx lines in /boot/grub/menu.lst or you won't be able to use the console!!

That's just a rough start, good luck!
Nick

---

### Post by OneSeventeen on 2005-06-16
Okay, so here's the big question: in order to compile my own kernel, I download the kernel source...

to do that, I must have a working OS already, right?  So how do I get the initial ubuntu installed so I can start compiling and configuring?

Is there a way to install it as usual but tell it to just stick with the command line in the beginning instead of automatically going into gnome and locking up?


I'm trying XP x64 right now and absolutely hate it... I get way better benchmarks even when using 32-bit benchmarking apps, but practically none of my hardware works.  I figured, if I'm going to have to mess with drivers anyway, might as well run ubuntu!

---

### Post by NickB on 2005-06-16
To get on the network with a zv6000, you can't put noapic or any other apic-disabling parameters on the boot line.  The network card just won't work.  I was able to get on the network with 2.6.10 and install the 2.6.11-amd64-k8 kernel, albeit with many apic errors that froze the system up to 1 second.  But once you get 2.6.11 running it solves a lot of problems, like a working atiixp IDE driver and fewer APIC apic errors, which don't freeze the system when they do happen (just fills your syslogs).

As for the gnome lockup problem, when gdm first comes up, press control-alt-f1 to get to the console, log in as root (or sudo su), and shut down gdm with /etc/init.d/gdm stop.  Edit /etc/X11/xorg.conf and add Option NoAccel yes to the video driver section (where you see the ati driver being loaded).  Then start gdm back up with /etc/init.d/gdm start, or just work from the console.  That'll get you at least running.

Alternatively, just boot up in recovery (i.e. single user) mode from grub.  Single user mode should work to get you to a 2.6.11 kernel and/or fix your xorg.conf file.

Good luck,
Nick

---

### Post by nocturn on 2005-06-17
[QUOTE=NickB]To get on the network with a zv6000, you can't put noapic or any other apic-disabling parameters on the boot line.  The network card just won't work.  I was able to get on the network with 2.6.10 and install the 2.6.11-amd64-k8 kernel, albeit with many apic errors that froze the system up to 1 second.  But once you get 2.6.11 running it solves a lot of problems, like a working atiixp IDE driver and fewer APIC apic errors, which don't freeze the system when they do happen (just fills your syslogs).

As for the gnome lockup problem, when gdm first comes up, press control-alt-f1 to get to the console, log in as root (or sudo su), and shut down gdm with /etc/init.d/gdm stop.  Edit /etc/X11/xorg.conf and add Option NoAccel yes to the video driver section (where you see the ati driver being loaded).  Then start gdm back up with /etc/init.d/gdm start, or just work from the console.  That'll get you at least running.

Alternatively, just boot up in recovery (i.e. single user) mode from grub.  Single user mode should work to get you to a 2.6.11 kernel and/or fix your xorg.conf file.

Good luck,
Nick[/QUOTE]

I'm considering buying a zv6068EA, I really want a zv5474EA but it is no longer available...
I had written it off, but this thread makes me wonder again...

---

### Post by NickB on 2005-06-17
[QUOTE=nocturn]I'm considering buying a zv6068EA, I really want a zv5474EA but it is no longer available...
I had written it off, but this thread makes me wonder again...[/QUOTE]
It's not easy getting it running in the stock install of Ubuntu 5.04, but I have gotten everything to work except for accelerated 3d, which is really ATI's fault.  It took me about a month to get here, but knowing everything I know now, I could get another one up and running from scratch in about a day.

I haven't messed with software suspend/hibernate, as I really don't know anything about it.  So I don't know if that stuff works at all.  That may be important to you.

Nick

---

### Post by OneSeventeen on 2005-06-21
Just an update, it appears eraser got the ATI drivers working by grabbing a new copy from ATI's website and converting it from RPM to deb and then installing...

Here's the link:
[http://zv6000forums.com/viewtopic.php?t=124](http://zv6000forums.com/viewtopic.php?t=124)

(which is also cool for anyone else using a zv6000 series laptop anyway)

---

### Post by NickB on 2005-06-21
I haven't gotten direct rendering to work in any combination of kernel or ATI driver.  Indeed, doing an alien of the 8.13.3 driver for xpress 200 motherboards DOES give you great results for 2D, but I have never gotten 3D rendering to work.

Nick

---

### Post by OneSeventeen on 2005-06-22
Oh, one tiny update that I discovered yesterday, you should, in fact, stay away from HP zv6000 series laptops...

it is a socket 939 AMD 64 processor running on a motherboard that doesn't support dual-channel memory!

Imagine buying a used Dodge Viper and finding out the fuel lines were replaced with new ones half the diameter they should be.  And on top of that, they are locked in place so there is no possible way to change them, and the dealership you bought the car from won't give you your money back, nor do they plan on ever fixing the problem.

AMD made the comment that a 939 AMD 64 4000 running in single-channel mode is the same as running a 754 AMD 64 3400.

On top of that, HP mentioned in an email to me that they do not, nor will they ever, support any 64-bit versions of windows on my laptop.

I'm still hoping to get linux installed on this machine, but you can bet this is the last HP product I'll ever buy.

---

### Post by nocturn on 2005-06-22
[QUOTE=OneSeventeen]
On top of that, HP mentioned in an email to me that they do not, nor will they ever, support any 64-bit versions of windows on my laptop.

I'm still hoping to get linux installed on this machine, but you can bet this is the last HP product I'll ever buy.[/QUOTE]

Are you serious?    They won't support 64-bit windows, but it should run, no?
Most vendors only support the OS that came with the machine.

I recommend that you give this as much publicity as possible (the Dual-channel issue).

Can you post the E-mails here?

---

### Post by FluffyElmo on 2005-06-22
A bit off topic, but HP has announced that it's actually supporting Ubuntu on some of it's laptop models. They all seem to be Intel based, but it's a step in the right direction?

> The company confirmed that it is working with Ubuntu, one of the smaller Linux distribution providers, to offer its customers an operating system that is tailored to work 100 percent with the hardware - including wired and wireless network, Bluetooth IrDA and IEE1394 - of selected notebooks. Supported devices are the notebook models nx6110, nc6120, nc6220, nc6230, and nc6000. 

[http://www.tomshardware.com/hardnews/20050512_124421.html](http://www.tomshardware.com/hardnews/20050512_124421.html)

---

### Post by NickB on 2005-06-22
[QUOTE=nocturn]Are you serious?    They won't support 64-bit windows, but it should run, no?[/QUOTE]
In theory, but I got the exact same line from HP when I called them.  They will not support me if I upgrade to XP Pro (mine came with home), nor if I upgrade to 64-bit windows.  They didn't outright say it wouldn't run 64-bit windows, but they did go so far as to say I would void my warranty if I did.

Nick

---

### Post by nocturn on 2005-06-23
[QUOTE=NickB]In theory, but I got the exact same line from HP when I called them.  They will not support me if I upgrade to XP Pro (mine came with home), nor if I upgrade to 64-bit windows.  They didn't outright say it wouldn't run 64-bit windows, but they did go so far as to say I would void my warranty if I did.

Nick[/QUOTE]

Can they do that?  I mean, does the contract say that intalling another OS (even another Windows) voids the warranty?

I'm still considering HP, even with extended warranty, but it will be running Ubuntu (My home has been windows-free for 6 years now).

---

### Post by nocturn on 2005-06-23
[QUOTE=NickB]In  but they did go so far as to say I would void my warranty if I did.
[/QUOTE]

Do other companies void their warranty, say when you install Linux?
I'm specificly thinking about Acer...

---

### Post by OneSeventeen on 2005-06-23
Actually installing any other OS does not void your warranty at all.

They just won't support the 64-bit versions of windows (or linux for that matter), meaning you cannot get 64-bit drivers for your hardware from them.  (you have to find the beta versions elsewhere, which I haven't gotten to work yet.)

The dual channel memory thing was responded to with "Did we actually advertise Dual Channel Memory?"  and I mentioned that Advertising a 939 AMD 64 was implying it, but they weren't buying.

The person on the phone told me these laptops were geared for the average consumer, and that is the business HP is in.  When I asked about some form of compensation, even if it was in the form of cheap ram to bring my machine up to what I was expecting it to be, they said no.

If you catch this soon enough, you should see my website's new home page:
[http://www.woventhorns.com](http://www.woventhorns.com)

I'm going to reboot and give ubuntu a try on this thing, so hopefully I'll be posting again shortly via linux!

---

### Post by OneSeventeen on 2005-06-23
Okay, here's what's going on now that I'm trying to install (not live CD like I was doing before).

Boot with: "linux vga=711"
Install
wait
wait
wait
done!

get the log on screen,
hit ctrl alt f1
black screen

Any ideas?  I'm assuming there should be something here....  but I get nothin.

I've also noticed I never set a password for root, so how do I su?

---

### Post by NickB on 2005-06-23
Try booting vga=0 instead of 771.  If that works then for some reason the vesa console is not loaded as a module (or compiled in the kernel).  If you get vesa working, you may want vga=791 instead.

To get to root, log in with the account you created during install and do "sudo su -" and enter YOUR password.

Nick

---

### Post by OneSeventeen on 2005-06-24
Okay, apparently there is a hardware issue that is not always apparent on every laptop... basically the monitor thinks the pc is shutting down, and it dimms dramatically.

When I hold the monitor at an angle and press my face 2 inches from it, I can barely see the words.

Also, I have spoken with HP, and they called me back, treating me like a valued customer, and have remedied the situation.  (still no dual channel memory, but they made it worth it for me to stay with their products)

---

### Post by NickB on 2005-06-25
Hooray!  I finally got the ATI drivers to work with DRI.  Using the latest drivers released a couple days ago:

[https://support.ati.com/ics/support/KBAnswer.asp?questionID=19511](https://support.ati.com/ics/support/KBAnswer.asp?questionID=19511)

I am using a patched 2.6.11.12 kernel (for the no_timer_check fix, just copy include/asm-x86_64/io_apic.h from 2.6.12 into your 2.6.11.12 tree), as it fubars my screen and keyboard on 2.6.12.  Of course, the source in /lib/modules/fglrx has to be patched before it will compile, but see the ATI howto elsewhere in these forums.

Good luck with yours!
Nick

---

### Post by OneSeventeen on 2005-06-28
I didn't patch my kernel to get the driver working, do I still get the shiny 3d accelleration without patching?

I'm hoping to wind up playing doom 3 and counter strike on this.

(a friend of mine claims doom 3 runs much smoother on his linux box than his windows box)

---

### Post by NickB on 2005-06-28
Patching doesn't matter for the ati driver, but it will implement the no_timer_check fix for the fast clock/rtc, which also matters if you want video, games, etc. to run at the right speed.

Nick

---

### Post by nocturn on 2005-06-29
It may be crazy, but I'm still contemplating buying this machine...
If I could find a zv5474EA, I would go for that one, but this is the replacement.

The Acer I selected reportedly works very nice with Ubuntu, but Acer support in my region seems crap (even with the extended warranty) and the machines show a lot of defects.

---

### Post by bassgoonist on 2005-06-30
[QUOTE=::DoGG::]I got the same prblem some time ago when i bought Compaq Presario r3000 with amd64, after 4 days of digging on the net o succesfully got everything worked out. And there was NO support for linux in that laptop. Since then my opinion is that there aren`t  any anti-linux laptops, sometimes we jus don`t have enough patience :D[/QUOTE]
Eer...of course you had the same problem...hp laptop == over priced compaq laptop with HP logo on it. Seriously...they make you pay like 10% more for the hp logo...

---

### Post by neo88 on 2005-07-12
I also have the same laptop, I am running Fedora Core 4 after running it in text mode in Fedora Core 3 for a month :( Everything works fine, I even get spotty 3d acceleration support from the VESA driver, but teh touchpad doesn't work. I tried everything you guys suggested, and nothing worked, I even succeeded in crashing X a few times. It appears that I do not have the command modprobe on my machine. And my mice come from /dev/input/mouse0 or  /dev/input/mice or /dev/input/mouse1. Any ideas? Oh, and one more thing. My system clock is really really fast. Really Fast. Like three times faster than it should be. How do I slow it down?

neo88 (Philip Haddad)

---

### Post by wingedlizard on 2005-08-30
[QUOTE=neo88]I also have the same laptop, I am running Fedora Core 4 after running it in text mode in Fedora Core 3 for a month :( Everything works fine, I even get spotty 3d acceleration support from the VESA driver, but teh touchpad doesn't work. I tried everything you guys suggested, and nothing worked, I even succeeded in crashing X a few times. It appears that I do not have the command modprobe on my machine. And my mice come from /dev/input/mouse0 or  /dev/input/mice or /dev/input/mouse1. Any ideas? Oh, and one more thing. My system clock is really really fast. Really Fast. Like three times faster than it should be. How do I slow it down?

neo88 (Philip Haddad)[/QUOTE]

has anybody got a fix for this?  I just tried 2.6.13 with no luck.  noapic fixes this but it causes eth0 problems.  unfortnately, I can't use cvs due to the clock problem ( slow clock but no network/  fastclock with network causes clock skew).

I've heard that there was a patch out but it only worked with 64bit kernels.  How do you compile a 64bit kernel?   Is it just a kernel compile? What else needs upgraded to 64bits? 

my ubuntu is the normal x86 install.

---

### Post by NickB on 2005-08-31
Hm... I distinctly remember posting how to do this, but I can't seem to find it.  I am currently running 2.6.11.12, which works great with the ATI fglrx driver.  The general steps for compiling a kernel are as follows:

1. apt-get install build-essential kernel-package
2. Download your kernel source from kernel.org
3. Unpack the source tree, cd to it
4. Copy the /boot/config-* file that is closest to the version of the kernel you're compiling to .config in the linux source directory.
5. make-kpkg --bzImage --initrd binary (you may want to use other options, see the man page for make-kpkg).  Press return for the default when asked for config options (usually safe).
6. Install the resulting packages using dpkg

If you're unsure about any of these steps, you may want to search for a howto for building debian kernel packages.  It's not difficult, but it's not straightforward how to solve problems.

Nick

---

### Post by NickB on 2005-08-31
I uploaded my kernel debs here [http://nick.borko.org/ubuntu/](http://nick.borko.org/ubuntu/) but no promises that it will work for you.

Good luck,
Nick

---

### Post by metalLord on 2005-09-29
hi i'm italian and i've the same laptop.

with hoary the system was too slow too use it, so i've changed to breezy.
with breezy all is going well. when you first install it remember to edit /etc/X11/xorg.conf selecting the vesa drivers for your (our) videocard.

bye!

---

### Post by grabbies200 on 2005-10-01
hello, i installed the fglrx drivers and i am running the kernel provided by nick borko. it seems to be working fine, but if i try to run the ati control panel i get this error
libexpat.so.0: cannot open shared object file: no such file or directory.
i have installed libexpat1, but still i get the same problem. does anybody knows how to get the ati panel to work

---

### Post by Vladtux on 2005-10-04
Hey Guys after read a lot and try a lot toot  get DRI=yes for Ati drivers...

Well I have breezy install in my laptop. then install kernel 2.6.12-9-amd64-k8 and
found the solution here 

[http://72.14.207.104/search?q=cache:yxyu9wguUPkJ:www.ubuntu-es.org/node/3674+ubuntu+ati+facil&hl=es&lr=&strip=1](http://72.14.207.104/search?q=cache:yxyu9wguUPkJ:www.ubuntu-es.org/node/3674+ubuntu+ati+facil&hl=es&lr=&strip=1)

That say:

1.- sudo apt-get install linux-header-version-of-you-kernel
2.- sudo apt-get install linux-restricted-modulos-version-of-you-kernel
3.- sudo apt-get install xorg-driver-fglrx
4.- modprobe -r fglrx
5.-backup your xorg.conf then execute fglrxconfig.(this works for me)
6.-in /etc/modules put fglrx
7.-Reboot the laptop and in the BIOS change Sideport for UMA (yeah is the only way :( )
8.-For fix the clock problem put no_timer_check in the grub(I found the solution in this forum :D )
9.-And you can change the resolution in xorg.conf where say 1280x1024 for 1280x800

Well I think is all :cool: 

I hope this help someone :)

---

### Post by NickB on 2005-10-05
Well I can confirm that it does indeed work for me as well, but it sucks that you waste all that onboard video memory and have to use main RAM to use the driver :(  Not even SidePort + UMA works; only UMA.

Nick

---

