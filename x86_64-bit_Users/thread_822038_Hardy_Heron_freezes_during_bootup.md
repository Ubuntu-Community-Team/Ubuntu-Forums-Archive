---
title: "Hardy Heron freezes during bootup"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by yongjunj on 2008-06-07
Hi all,

I recently got a new HP Pavilion a6460t, and I'm having trouble getting Hardy Heron to run nicely.

First of all, the machine would "usually" (I think it might be a race condition) just freeze during bootup even right after fresh installation, and it does so consistently after the following bootup message:

r8169 Gigabit Ethernet driver 2.2LK loaded
eth0: RTL8168c/8111c at 0xffffc20001048000, XX:XX:XX:XX:XX:XX, XID 3c2000c0 IRQ 506

I googled around for a bit and found [this post]("https://answers.launchpad.net/ubuntu/+question/3247"). Adding pci=nopci flag seemed to solve the problem, until I did a set of software updates that installed the 2.6.24.18 kernel. I'm thinking one of the updates besides the new kernel is the culprit, because now neither the 2.6.24.16 nor the 2.6.24.18 kernel would boot fine. I've already tried the following four flags:
1) pci=nopci
2) acpi=off
3) acpi=noirq
4) pci=noacpi

This has me pulling my hair at the moment; could someone please enlighten me?

Thx,
Jun

---

### Post by Victormd on 2008-06-07
are you adding "pci=nopci" or simply "nopci"?
When I had to use this before, I used only nopci (without the pci=)
Try that... the ones I would use in your case are the **nopci** and **noapic** instead of noacpi

---

### Post by Victormd on 2008-06-07
Ultimately your kernel line in the menu.lst should look something like this
> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash nopci noapic

Note: try one parameter at a time...

---

### Post by yongjunj on 2008-06-12
Thanks, Victormd. I'll try that and post my results soon :)

---

### Post by probin51 on 2008-06-13
Had a similar problem with a ASUS Laptop recently. Victormd's solution got around the boot up problem.

You can read a little background here:

[http://wiki.linuxquestions.org/wiki/APIC](http://wiki.linuxquestions.org/wiki/APIC)

You may be able to disable ACPI in the BIOS

[http://wiki.linuxquestions.org/wiki/ACPI](http://wiki.linuxquestions.org/wiki/ACPI)

I'm looking to replace the laptop soon. When I do, I'll confirm compatibility before I do.

e.g. here

[http://www.linuxhardware.org/](http://www.linuxhardware.org/)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Hope these links help!

---

### Post by yongjunj on 2008-06-17
Sorry for the late post. My machine is a dual-boot system, and I had some work running on WS2003.

I just tried your suggestions, and neither worked. I did find a post about Hardy Heron's compatibility with my network card (RTL8168c/8111c), though: [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

What's interesting is that in my case the network card worked perfectly before the update, and when Hardy does successfully start up.

I'm convinced that it's something about my network card; I'll post more info once I make any progress on this issue.

Thx!

---

### Post by gwilki5691 on 2008-06-23
Hi all,
I have a similar problem, but mine's a little more confusing.
I have a fresh install of hardy, dual booting with XP. XP runs fine and all my hardware works perfectly.
When I first installed hardy it was fine. Then I enabled the compiz effects & restricted Nvidia drivers and now when I boot up straight into hardy from grub it freezes just before the login window should appear and the screen remains black.
However, if I first boot into Windows XP, reboot and then select hardy from grub it boots fine and I have wobbly windows and emerald themes. Once hardy is booted I can restart / reboot as often as I like and it works perfectly everytime. The problem only seems to occur when I boot hardy from cold. Booting windows to boot hardy is rather annoying.
Obviously the restrcted drivers and X config must be ok as it does work if you boot windows first. I thought it may be a fault with my graphics card so I changed it for a similar card from my 2nd pc, but that cured nothing.
Any ideas?

---

### Post by gwilki5691 on 2008-06-23
Continued from previous post.....

Ooooh! I forgot to mention, I tried with Nvidia 7600GT 256MB and now Nvidia 6600GT 128MB both with dual DVI screens. When it boots however it works flawlessly and the fully compiz'd desktops work a treat with 2 rotating desktop cubes and loadsa wobbly windows.

---

### Post by slymi2005 on 2008-06-23
Gee this sounds oddly familiar. I'm having a similar problem to you gwilki and I have the same network card as yongjunj. After first installing ubuntu 8.04 I had to install the nvidia drivers and I used envy and it worked fine but then it started freezing after selecting ubuntu in the boot menu and I keep having to go to recovery mode and fixing xserver which gets rid of my compiz effects and now I can't get into ubuntu. I tried uninstalling envy through recovery mode but it can't connect online so I keep jumping back and forth blaming my network card and my nvidia 8500 gt. I wish ubuntu weren't do damn complicated. I would hate to abandon ubuntu and have to use vista.

---

### Post by yongjunj on 2008-06-24
slymi, did you get the same bootup message as I did?
I haven't looked much further into this because I'm running my system on WS2003 partition at the moment.

My problem wasn't graphics card related, and I'm not using envy or compiz effects, so I can't say anything on gwilki's symptoms. Sorry gwilki, but I guess you'll have to find another thread or start your very own :(

I don't know if you guys noticed as well, but I've been seeing unusually large amounts of updates being pushed daily since I installed Hardy. I believe the latest kernel right now is something like 2.6.24.19. You might want to try these updates and see if it solves your problems.

It would be helpful to know what boot message you're getting before it freezes, though. When grub screen shows up, edit the boot parameters and remove the "quiet" and "splash" flags, and you'll see all the bootup messages instead of the dull splash screen.

---

### Post by slymi2005 on 2008-06-25
how would I go about doing that?

---

### Post by yongjunj on 2008-06-25
I couldn't find any article with screenshots, but here's a tip from [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto):

Modifying boot options in GRUB
If you need to get into the grub menu, to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts. By default you have to press 'ESC' very quickly. To increase this time edit the grub configuration file /boot/grub/menu.lst, increasing the seconds in the TIMEOUT part. Alternatively you could have the menu always come up at boot time. To do this, comment out 'hiddenmenu' by inserting a # at the beginning of the line.
After pressing 'ESC' you will be presented with a list of kernels and operating systems that you can boot. To modify the boot options highlight
the operating system you want to edit and press 'e'. There you will be presented with lines starting with 'root', 'kernel', 'initrd', 'quiet' and 'savedefault'. To receive a more verbose boot process you can remove the 'quiet' line by highlighting it and pressing 'd' to remove that line. You will also need to highlight the 'kernel' line press 'e' to edit and remove the word 'splash' from the end of the line . After making any necessary modifications you can press 'b' to boot that operating system. These modifications will not persist across reboots.

---

### Post by gwilki5691 on 2008-06-26
Thanks yongjunj, I am taking your advice and starting a new thread about my problem. I have tried all sorts of things over the last few days, but sadly I still have to boot into Windows before booting Hardy.
TTFN :)

---

### Post by yongjunj on 2008-07-03
Ok, so one of the original problems was that when Hardy does boot up (with or without the boot options - nopci and/or noapic) I don't have ethernet connection, even though it autodetects the network card (RTL8168c/8111c).

It now seems that I get the ethernet connection if I boot into WS2003 first and then (soft) reboot into Hardy. This struck me as being quite interesting because I came across a very similar issue on my old file server running FreeBSD with VIA VT612x gigabit ethernet card. This is a known, documented issue in FreeBSD community:

1) [http://www.freebsd.org/cgi/query-pr.cgi?pr=106851](http://www.freebsd.org/cgi/query-pr.cgi?pr=106851)
2) [http://www.freebsd.org/cgi/query-pr.cgi?pr=87316](http://www.freebsd.org/cgi/query-pr.cgi?pr=87316)

My file server is a multi-boot system (FreeBSD and Hardy). The problem was that the network card wouldn't initialize in FreeBSD after rebooting from Hardy. The only solution (without modifying the code) I found was to simply disconnect the power cable from the power supply for a while, wait for a flag bit on the ethernet card to be "automagically cleared" (as in link 2), and then boot straight into FreeBSD.

As for my new desktop, my best guess right now is that WS2003's RTL8168c/8111c driver does some magic that makes Hardy's RTL8168c/8111c driver happy when it loads... Don't quote me on this, though; I'm still looking into this...

FYI, my WS2003 is WS2003 Enterprise R2 x64. I just checked on Device Manager and I'm using Realtek's (not Microsoft's) RTL8168C(P)/8111C(P) PCI-E Gigabit Ethernet NIC driver version 5.686.103.2008.

---

### Post by yongjunj on 2008-07-03
Just checked Realtek's website ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)), and they released a new Linux driver on 4/22/08, which means the driver that shipped with Hardy is most likely older. I'll try this new driver and post the result soon.

---

### Post by nyn2000 on 2008-08-11
Hi
I am facing a boot-up problems and after reading the forums I found yours closest to mine. I am using 64 bit version and nvidia gfx drivers.
First time I boot into Hardy, I get some message- ...aperature not found try rebboting.. the message just falshes and I could never read it fully.The boot-up works fine after I reset the computer- I mean it happens only once. I feel bad about resetting the computer and I have not yet tried booting into windows before going into Hardy.
Have you found a solution yet. Pl let me know

Thanks.

---

### Post by yongjunj on 2008-08-12
Hi nyn2000,

I believe my problem has more to do with my lan card than my graphics card; I never had any issues with the graphics card, but gwilki5691 (who has posted on this thread before) has had some issues with his/her graphics card. I think his/her issue might be more closely related to yours. Did you try searching for his thread on the board?

Jun

---

### Post by nyn2000 on 2008-08-13
Hi

I am facing the same problem with my GForce Fx5200. How have you solved the problem ? Pl let me know.

Thanks

---

### Post by yongjunj on 2008-08-13
nyn2000,

I just searched for gwilki5691's thread, and it seems his question went unanswered.
My issue was with the lan card driver, and I had to replace the driver to the newest version posted on the manufacturer's website.

I also just looked at Hardy Heron's hardware compatibility list (HCL), and it seems your graphics card is supported: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

So could it be that it's something other than the graphics card that's the problem?

---

