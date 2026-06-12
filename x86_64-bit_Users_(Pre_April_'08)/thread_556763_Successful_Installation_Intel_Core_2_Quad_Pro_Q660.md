---
title: "Successful Installation: Intel Core 2 Quad Pro Q6600"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by njpatel on 2007-09-21
Hey,

Just thought I'd let anyone looking to buy a Intel Quad Core system that Gutsy 64bit installation works brilliantly.

The full system specs are:

Processor: Intel Core 2 Quad Pro Q6600 "LGA775 Kentsfield" 2.40GHz (1066FSB)
Motherboard: Asus P5K Intel P35
Memory: 4GB (4x1GB)
Graphics: GeForce 8400 GS (512Mb)

One thing that I came across is that the bootsplash doesn't seem to work for me, either in the livecd, or after the installation (but this doesn't matter as much as a cold boot takes about 12 secs).  So when installing, don't think that the livecd has frozen, just wait a while and it'll boot into the desktop, then install as normal.

Screenshot (for what its worth :-): [http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg](http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg)

Thanks, 

Neil

---

### Post by dabl on 2007-09-21
Yep, I'm jealous.  :lolflag:

---

### Post by IanW on 2007-09-22
Hope you got the G0 stepping version of that CPU (MUCH lower power consumption!)

---

### Post by paradoxni on 2007-09-22
Nice spec and screenshot.

Now forget the power consumption and overclock the heck out of it  :p

Have my E6600 Core2Duo running at 3.6Ghz, aircooled, idle temp 29C

---

### Post by njpatel on 2007-09-22
> **paradoxni said:**
> Nice spec and screenshot.

Now forget the power consumption and overclock the heck out of it  :p

Have my E6600 Core2Duo running at 3.6Ghz, aircooled, idle temp 29C

Niice, I haven't done any overclocking for ages, especially not on Linux. Could you point me to any how-tos or examples, I have a weird feeling I won't be able to rest until these things are running at 3.0GHz :-)

---

### Post by paradoxni on 2007-09-22
i didnt use a howto..just trial and error :)

For a start im using a thermalright ultra-120mm cooler which is a monster!

I have 800Mhz ddr2 RAM, so my aim was a fsb of 400Mhz so the RAM isnt being overclocked.

the E6600 is locked to a multiplier of 9x, so this gives me 400 x 9 = 3.6Ghz

the temps were fine but my OS froze on start up..so i kept increasing my vcore voltage until the OS would boot, then i used "crafty" to max out both cores which caused some more crashes..kept increasing vcore in stages until it was stable, now at 1.456v.

using the crafty benchmark I was gettin 6 seconds, now im getting 4, just out of  interest try it with your standard quad core:

```

sudo apt-get install crafty        'will install crafty

crafty                    'runs crafty

mt=4                    'sets number of CPU threads, in your case 4

bench                   'runs the bench  mark and gives you a time in seconds.

```

and if you want to max out all 4 cores for temp / stress testing:

```

crafty

mt=4

e3              'this is simply a valid chess move and will start crafty off on a chess game using 100% of your cpu

```

---

### Post by helliewm on 2007-09-22
My InteL Core 2 Quad Pro Q6600 arrives on Tues!  4 GIG RAM 500 gig Hard Disk, Nvidia GEFORCE 8500GT SUPER 512MB PCI-E DDR2 DUAL DVI/TV Graphics Card, Firewire, Fax Modem, 20 Dual Core DVD writer, 2nd Light Scribe DVD Writer , 10 USB 2 ports, Motherboard ASROCK CONROE1333-ESATA2 - PCI-E - SATA-RAID – SND - NET .

I am in the UK too. I bought mine from Bess-Systems of ebay. I bought the basic spec and then upgraded it. In total I have paid £550 for the above system. If you do n't mind me asking what did yours cost?   

I plan to install 64 bit Feisty and then upgrade to Gutsy.

Helen

---

### Post by dabl on 2007-09-22
While Intel provides the Core 2 BIOS updates in Linux-readable formats, their overclocking utilities are only for Windows. So, I overclocked my Core 2 Extreme (on an Intel D975 XBX motherboard) (from 2.9 to 3.3GHz) in a Win XP installation that I did only for that purpose. Once I was happy with the motherboard/CPU/RAM setup, that partition went away and has never been seen again.  :popcorn:

---

### Post by Fingolfin on 2007-09-26
> **paradoxni said:**
> Using the crafty benchmark I was gettin 6 seconds, now im getting 4, just out of  interest try it with your standard quad core:
.......and if you want to max out all 4 cores for temp / stress testing:

```

crafty
mt=4
e3              'this is simply a valid chess move and will start crafty off on a chess game using 100% of your cpu

```

The principle is the same, but do you know perhaps, are there any notable differences in measured temperatures and the times until crashes for the overclocked CPU/memory (if they occur) between tests with "crafty" in this way and "mprime"?

---

### Post by h0ax on 2007-09-30
Hi,

Did you use the alternate / text install based version ?
I put in the CD, either 7.04 or 7.1 and I get to the bootsplash to choose what I want to boot, but then nothing every comes up afterwards.

Any suggestions?  I DL'd Trial version of XP64 so that I could turn on my comp... would like to get off of it though.

Thanks!

---

### Post by paradoxni on 2007-09-30
no just the desktop-amd64 version, didnt do anything but a standard install.

---

### Post by njpatel on 2007-10-01
> **paradoxni said:**
> i didnt use a howto..just trial and error :)

For a start im using a thermalright ultra-120mm cooler which is a monster!

I have 800Mhz ddr2 RAM, so my aim was a fsb of 400Mhz so the RAM isnt being overclocked.

the E6600 is locked to a multiplier of 9x, so this gives me 400 x 9 = 3.6Ghz

the temps were fine but my OS froze on start up..so i kept increasing my vcore voltage until the OS would boot, then i used "crafty" to max out both cores which caused some more crashes..kept increasing vcore in stages until it was stable, now at 1.456v.

using the crafty benchmark I was gettin 6 seconds, now im getting 4, just out of  interest try it with your standard quad core:


Aah I see, I'm still not sure if I'll get a chance to do this or not, just too busy :-(.



> **h0ax said:**
> Hi,

Did you use the alternate / text install based version ?
I put in the CD, either 7.04 or 7.1 and I get to the bootsplash to choose what I want to boot, but then nothing every comes up afterwards.

Any suggestions?  I DL'd Trial version of XP64 so that I could turn on my comp... would like to get off of it though.

Thanks!

This is exactly what I was experiencing, there is not bootsplash (the progress bar/ubuntu logo) on the 64bit cd. You just have to be very patient while the livecd does it's stuff. Once it's done, you'll be at the live cd desktop. 

At first I really thought it isn't working, but I could here the cdrom drive, so i left it, and about 3-5 mins later I was at the desktop :-)

---

### Post by njpatel on 2007-10-01
> **helliewm said:**
> My InteL Core 2 Quad Pro Q6600 arrives on Tues!  4 GIG RAM 500 gig Hard Disk, Nvidia GEFORCE 8500GT SUPER 512MB PCI-E DDR2 DUAL DVI/TV Graphics Card, Firewire, Fax Modem, 20 Dual Core DVD writer, 2nd Light Scribe DVD Writer , 10 USB 2 ports, Motherboard ASROCK CONROE1333-ESATA2 - PCI-E - SATA-RAID – SND - NET .

I am in the UK too. I bought mine from Bess-Systems of ebay. I bought the basic spec and then upgraded it. In total I have paid £550 for the above system. If you do n't mind me asking what did yours cost?   

I plan to install 64 bit Feisty and then upgrade to Gutsy.

Helen

Well I didn't need everything (I have alot of recent computer parts lying around), but the processor, memory, case+psu, and graphics card all came in at around £450. Apart form the graphics card ([www.novatech.co.uk](www.novatech.co.uk)), I got everything form overclockers.co.uk.

---

### Post by SCS on 2007-10-01
> **njpatel said:**
> Hey,

Just thought I'd let anyone looking to buy a Intel Quad Core system that Gutsy 64bit installation works brilliantly.

The full system specs are:

Processor: Intel Core 2 Quad Pro Q6600 "LGA775 Kentsfield" 2.40GHz (1066FSB)
Motherboard: Asus P5K Intel P35
Memory: 4GB (4x1GB)
Graphics: GeForce 8400 GS (512Mb)

One thing that I came across is that the bootsplash doesn't seem to work for me, either in the livecd, or after the installation (but this doesn't matter as much as a cold boot takes about 12 secs).  So when installing, don't think that the livecd has frozen, just wait a while and it'll boot into the desktop, then install as normal.

Screenshot (for what its worth :-): [http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg](http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg)

Thanks, 

Neil
Yep. I have it installed also on a quadcore.  It is beautiful.  64bit is much much faster.  

Intel Quadcore Q6600
2GB DDR2
Nvidia GForce 7600GS 256MB using Twinview
Asus P5B Deluxe

I even have a tv tuner in there.  I had Fiesty on there 32bit. In a drunken stupor I had a bright idea to 'test' the Kubuntu desktop by installing it from the repository.  Then tried to remove it with some scripts found on these forums. Then I installed the last Tribe 5 of Gutsy and it was awful.  Attempted OpenSUSE 10.2 and didn't like it too much.  Lucky for me the new beta of Gutsy came out and everything is just beautiful.  I also have a screen shot but nowhere to put it up.

I am quite happy.


[http://www.mypicshare.com/r2noz5mmpic.html](http://www.mypicshare.com/r2noz5mmpic.html)

---

### Post by samienela on 2007-10-03
I was able to install "out of the box"  on a quad system, Q6600 (g0 stepping), Gigabyte P35-DS3R.  Only problem is, I can't get the wireless to work.  The wireless card is a D-link DSL G520. I have them on all my other Linux systems (Dapper and Feisty 64 bit versions -- they never did work on Edgy) 

I have used the same Network settings as on my AMD machines, but no joy. 

I must say, it runs Freecell beautifully, but that's not why I built it. (Folding@Home)

Is there some special trick to getting wireless to work with a Core 2 Quad machine?   

Any advice would be much appreciated - please note that I'm a near-beginner at Linux and reply accordingly.  Thanks!

---

### Post by benweston on 2007-10-04
Congratulations on the quad core! I should also be going quad core soon although I've built quite a few quad core Ubuntu systems for customers.

What's with the lack of a boot splash? And how are you doing with your GeForce 8? I can't get mine to work. Tried everything. It's the 8600GT PCI-Express and it just won't work. Currently stuck on standard drivers. Running Gutsy Tribe 5.

I haven't done any formal benching yet, but 64-Bit is noticably more responsive than i386. Even on an Athlon X2 6000+ (really need to build a better C2Q rig soon!)

---

### Post by mozkill on 2007-10-04
The BIG question is will the Asus P5K3 motherboard work that uses the DDR3 ??

---

### Post by h0ax on 2007-10-13
I cannot get Gnome to work, I get the splash screen to install; then I click "install or safe mode" either way, I wait and wait and wait.  Nothing ever shows up.
I installed Gnome in text mode, and then when I booted up the first time; nothing.
I installed KUbuntu with text mode and everything worked right away.  The only problem there is I'm not a fan of KDE.

Alas, 
I'm still stuck in WinXP x64.

Anyone want to lend a helping hand?
I have an nVidia 8800 GTS with 640MB RAM.  This is my problem, insofar as I can tell.

Thanks all(:

---

### Post by pejcao on 2007-11-06
What about lm-sensors? Does the sensors chip (a winbond one IIRC) is supported by gutsy kernel? 64bit even?

---

### Post by PokerFacePenguin on 2007-11-23
> **njpatel said:**
> Hey,

Just thought I'd let anyone looking to buy a Intel Quad Core system that Gutsy 64bit installation works brilliantly.

The full system specs are:

Processor: Intel Core 2 Quad Pro Q6600 "LGA775 Kentsfield" 2.40GHz (1066FSB)
Motherboard: Asus P5K Intel P35
Memory: 4GB (4x1GB)
Graphics: GeForce 8400 GS (512Mb)

One thing that I came across is that the bootsplash doesn't seem to work for me, either in the livecd, or after the installation (but this doesn't matter as much as a cold boot takes about 12 secs).  So when installing, don't think that the livecd has frozen, just wait a while and it'll boot into the desktop, then install as normal.

Screenshot (for what its worth :-): [http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg](http://farm2.static.flickr.com/1417/1420036294_f0bcbdf311_b.jpg)

Thanks, 

Neil


I see that you are using the generic kernel and all four gigs of your ram are showing up.  This problem has been kicking my butt.  I realize I have to recompile the kernel with >64G option  but I cannot find a concise guide to do it.  I have found lots of kernel threads, but none specific to gutsy generic kernel.  I got some advice from someone on server, but I am just too thick to work it out on my time schedule I guess.

---

### Post by blegmar on 2007-11-28
GREAT POST! thanks. I'll be replying when I install 7.1 x64 after work.

---

### Post by mozkill on 2007-11-30
using the ASUS P5K-E , with 64-bit ubuntu, I also don't see the framebuffer bootsplash.  After starting the computer there is about a 4-5 minute wait before X-Windows login appears.  I have quad-core 2.4 .

---

### Post by mr_firefox on 2007-12-05
I'm also in the market for a 4Gb quad core PC!

I would be grateful if you could let me know where you bought your boxes from.

I'm looking to pay around £500 max!

Thanks.

---

### Post by ganja_guru on 2007-12-08
4-5 min wait to bootup on a Quad Core is a bit much. See if this helps speed up your bootup time:

1). sudo gedit /boot/grub/menu.1st
2). FInd the line which says:

/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
(or something similar)

just remove the 'splash' word and save the file.

---

### Post by mariusmeyer on 2007-12-18
Hey njpatel, where did you get your desktop theme? It looks AWESOME! Thanks to this thread, I'm giving the 64-bit Gutsy a shot. Don't know why, but I have always used the 32-bit version =P hopefully it'll work out for me as well, since my rig is practically identical to yours.
Cheers!

---

### Post by mariusmeyer on 2007-12-18
> I cannot get Gnome to work, I get the splash screen to install; then I click "install or safe mode" either way, I wait and wait and wait. Nothing ever shows up.

Anyone want to lend a helping hand?
I have an nVidia 8800 GTS with 640MB RAM. This is my problem, insofar as I can tell.


This is what happens for me as well. Doesn't matter if I choose normal install or safe graphic, either way, a message saying "kernel alive" pops up, and then the screen goes black. I can hear the CD-ROM work for a minute or two, and after it has done it's job (appearantly) nothing happens. I have an XFX GeForce 8800 GTS as well, only it's the 320 MB version. I bet this is the problem.
Other specs: MSI P35 Neo, Core 2 Quad Q6600, 2 GB RAM.

---

### Post by danilobx on 2007-12-28
Hi im having this same problem too. After choosing to install on the live cd for ubuntu 64bit, the cd-rom drive will spin for around 30s and than it stops, completely stops and screens is black.

q6600 4gb ram 8800gt MSI p35 NEO motherboard

Any help?

---

### Post by Alan Painter on 2007-12-29
> **PokerFacePenguin said:**
> I see that you are using the generic kernel and all four gigs of your ram are showing up.  This problem has been kicking my butt.  I realize I have to recompile the kernel with >64G option  but I cannot find a concise guide to do it.  I have found lots of kernel threads, but none specific to gutsy generic kernel.  I got some advice from someone on server, but I am just too thick to work it out on my time schedule I guess.

Also just installed Gutsy generic (2.6.22-14-generic X86_64), had to remove "splash" and "quiet" to get to boot other than "recover" mode.

Doesn't seem to recognize 64-bit mode.  

It's a MSI 7358 motherboard with Q6600 and 4Gig of memory.  

Any pointers appreciated.  Still searching, of course.

---

### Post by JayBee808 on 2008-01-02
> **danilobx said:**
> Hi im having this same problem too. After choosing to install on the live cd for ubuntu 64bit, the cd-rom drive will spin for around 30s and than it stops, completely stops and screens is black.

q6600 4gb ram 8800gt MSI p35 NEO motherboard

Any help?

I get the same problem on a P35 q6600 w/ GF8800gts.
To boot the LiveCD I remove the "quiet" and "splash" commands by pressing F6 when the disc starts.
I also had to remove these from the GRUB menu after the installation.  It is easiest to do it while still booted into the LiveCD:

sudo gedit /boot/grub/menu.lst
 ...then remove the quiet and splash screen options from each GRUB entry.
This always works for me.  I have plain Ubuntu and UbuntuStudio installed on this machine.  Same problem both times.

---

### Post by ~LoKe on 2008-01-02
The only way I was able to install with my quadcore was to boot the alternate CD.

---

### Post by HangLoose on 2008-02-03
@LoKe:
Could you please post your specs ?
Im getting my machine probably next week and would like to know if i will have the same problems as you.

Thanks

---

### Post by andre_ribeiro on 2008-04-10
Hello guys,

i recently bought a quadcore too. I also have a P5K Premium WI-Fi, 4gb dd2 800mhz corsair and a samsung 500 gb 7200rpm hard drive.
I installed ubuntu gutsy 32bits and fedora 8 64 bits. But the perfomance is really really poor.
Also, my hard drive is makink too much noise when using those systems.
I have windows vista installed too, and its very fast and noiseless.

Coud be a hardware compatibility issue?
or maybe a problem with my hard drive,  besides windows vista works perfectly?  :confused:

I'm desperate to use  linux again.  :(

thaks for any help.

andre

---

### Post by helliewm on 2008-04-10
Is it your hard drive making the noise or your PSU? I had to replace the PSU on my literally brand new quad core.

What graphics card do you have?

What is happening to give you poor performance, what are the exact problems you are having?

Helen

---

### Post by andre_ribeiro on 2008-04-10
hi,

its my hard drive that is making too much noise.
I have a 8600 GT.

well, the os takes too long to load x, or start gnome for example.
also, the response time is high.

thanks for the reply,

andre

---

### Post by HangLoose on 2008-04-11
andre...
try to install gkrellm and check the graphs of load per time...
also check in the system monitor which processes have more load and memory...
i have removed tracker from my system even though its a quad core cos it was just lagging my system...

---

