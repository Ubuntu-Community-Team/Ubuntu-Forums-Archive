---
title: "ubuntu install / boot problem on amd64"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by rrofes on 2007-06-12
I have a new motherboard Asus M2N-SLI Deluxe with a dual core CPU Athlon64 X2 4400+, and I am trying to install Ubuntu 7.04 for AMD64. The live CD is not able to boot, first I thought that it was the APIC related problem that many people encountered and that is solved with the kernel commands "noapic nolapic pci=noacpi acpi=off..." and so on (enable_8???_timer..., nomce..) I've tried all these options always with the same result. Now I think that this is not the problem.

The last messages that I see in the screen when system is booting is:
Loading ACPI modules...
Starting ACPI services...
Starting system log daemon...
Doing Wacom setup...
Starting kernel log...
Starting system message bus dbus...
Starting hardware abstraction layer hald...
Starting DHCP D-bus daemon dhcdbd...
Starting network connection manager NetworkManager...
Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon...
Starting network events dispatcher NetworkManagerDispatcher...
Starting system tools backends system-tools-backends...
Starting Gnome display manager...
Starting common UNIX printing system: cupsd...
-> after that screen goes to black and system hangs.
The boot process don't hangs at the very begining, I have omitted all the messages previous to these last ones.

I have tried several bios versions for my mobo, always the same result.
I have cheched my ubuntu cd with md5 and it is ok, no doubt about it.
I have checked my RAM with memtest, it is ok.
I tried to change RAM to another slot, and tried the same with VGA.

Now I have installed the i386 ubuntu version and everything went ok, but I would like to install the AMD64 version!

My hardware:
Mobo: Asus M2N-SLI Deluxe, with bios 0903 (the last one released by asus)
CPU: Athlon64 X2 4400+ dual core
RAM: DDR2 1Gb 64 bit single channel Extreme Memory
HD: maxtor 250MB
VGA: ATI radeon X550

If someone can help me that would be great, I really don't know what else to try. Maybe someone encountered the same problem?
Thank you all,

---

### Post by sataniceaden saklura on 2007-06-12
coolies i had the same issue with my sys when i first tried it 
the solution i re dlded the live cd from a different sorce and it worked fine so i dunno if it will work the same for you also when you insert the ubuntu live cd it should give you a heap of options for fastes install i had to run the cd first (by this it opens up a fake ubuntu then has install drive on desktop) hope this helps 

just a question for you how are you running ddr2 on that mobo i had to replace all my ram for this bord and we got the same bord???

---

### Post by rrofes on 2007-06-12
Hello, & thanks for answering,
I downloaded the CD twice and both are identical (MD5 passed OK), then I think that the CD is ok
About the DDR2, the Asus M2N-SLI Deluxe supports that kind of RAM, and I think is the most popular kind now.
I don't understand well the other comment, what option I have to choose from live cd menu?

Bye

---

### Post by sataniceaden saklura on 2007-06-12
sorry for the late reply i am having issues with my gfx card but on the cd use the install i know there are two but use the second one from the botom of your options it runs faster and i havent had issues with it the top one crashed on me all the time good luck

---

### Post by crjackson on 2007-06-12
I'm quite sure it IS your graphics card.  I had the same issue, look at my specs.

Here's what I did...

1) Start liveCD
2) Hit F4 and change the screen resolution to 640x480
3) Select LiveCd/Install (option 1 on the 1st menu)
4) After desktop comes up, you can install if you want - I did

After installed - Edit your boot file and change "SPLASH" TO "NOSPLASH" save and you shoud be good.

Now everytime you boot, you will see text scrolling up the screen, but at least it won't hang and it runs perfectly.

Hope this helps... Keep in mind I'm a Linux newbie too....

---

### Post by rrofes on 2007-06-13
Hi community!

None of the following worked:
- try install in safe graphics mode
- F4 & select 640x480 when live cd menu appears
- VGA=792 on kernel line (I saw on forums that someone solved a similar problem with that)

The caps lock key does nothing when the pc hangs (some people reported a similar problem to mine and explained that caps lock was blinking at the moment of hang)

But there was a significant progress, a bit of light over the theme: I used an old vga that i have (S3 trio 64V+, memory 1MB: very very old!) instead of the ati radeon x550 and the amd64 ubuntu live cd was able to boot. I was not able to see the gnome desktop but I think it was a problem with the so old card. I was able to work with the console (alt+F1) in text mode, and shut down the system properly. I even heard the music that announces entering/leaving gnome.

Then I think that it is a compatibility problem with the Sapphire ATI radeon X550 XTX. I have not still solved the problem but maybe it is the cause. I will change it for an nvidia one and see what happens... I will tell something

Thanks to all following my adventures!

---

### Post by rrofes on 2007-06-18
At the end the problem disappeared installing an nvidia geforce video card instead of ati radeon... after it was a little difficult to get the resolution of 1400x1050 on that new card, but that's another issue.
Thanks all

---

