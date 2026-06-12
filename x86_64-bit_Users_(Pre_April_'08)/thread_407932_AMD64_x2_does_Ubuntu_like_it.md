---
title: "AMD64 x2 does Ubuntu like it?"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by SJI on 2007-04-12
Hello,

I've been using Dapper and Edgy amd64 for a little while and find it quite a reasonable OS. The odd bug here and there, but they are usually sorted pretty quickly. On the whole it's been a pleasurable time.

I've just bought an AMD x2 4200+ processor figuring that I'd give my box a little extra oomph.

I'm wondering if I have made a bad here?
The Edgy install I have will not successfully boot unless I append a handful of words to the end of the kernel line to disable the second core.

I've tried booting the live CDs from 6.06, 6.10 and 7.04 but sadly to the same end as my current install.

Is this a known problem or is it my cheap machine that's the problem (or even the dumb user)?

Problem box:

AMD Athlon 64 x2 4200+
Board is nForce4-A939
GFX is PCIe nVidia GeForce 7
4gb ram
SATA HD
PATA CDroms

I'm going to try the alternate install image next, but I suspect the same result.

The most annoying part is that XP spotted the new processor and works like a charm with it.

TIA

Stephen

---

### Post by maxamillion on 2007-04-12
I think it has something to do with your mother board, my friend had a similar issue and passing the --no-acpi at boot turned out to fix the problem, but ubuntu likes the AMD X2 series very much so (my workstation at work has a X2 4600+ and has been chugging along with both cores like a champ for some time now).

---

### Post by Kilz on 2007-04-12
> **SJI said:**
> Hello,

I've been using Dapper and Edgy amd64 for a little while and find it quite a reasonable OS. The odd bug here and there, but they are usually sorted pretty quickly. On the whole it's been a pleasurable time.

I've just bought an AMD x2 4200+ processor figuring that I'd give my box a little extra oomph.

I'm wondering if I have made a bad here?
The Edgy install I have will not successfully boot unless I append a handful of words to the end of the kernel line to disable the second core.

I've tried booting the live CDs from 6.06, 6.10 and 7.04 but sadly to the same end as my current install.

Is this a known problem or is it my cheap machine that's the problem (or even the dumb user)?

Problem box:

AMD Athlon 64 x2 4200+
Board is nForce4-A939
GFX is PCIe nVidia GeForce 7
4gb ram
SATA HD
PATA CDroms

I'm going to try the alternate install image next, but I suspect the same result.

The most annoying part is that XP spotted the new processor and works like a charm with it.

TIA

Stephen

I run a amd64 x2 4600 without problems. Its a replacement for a amd64 3500 the computer came with. It was a drop in replacement, I didnt reinstall anything.

---

### Post by SJI on 2007-04-12
Thank you for the quick responses chaps.

I'll continue investigating the cause and trying different options/settings.

Maxamillion: was -no-acpi the only option required to resolve you friends x2 problem?

I have acpi=off, nosmp and noapic settings at the moment in order to get this set-up to boot successfully.

Stephen

---

### Post by defos931 on 2007-04-12
Hi, I've the same probleme as SJI.I'm running a laptop:compaq turion64 x2nforce chipset and I can't boot with the cd-rom.

thanks for any help!!!

ps: first time with linux!!!

---

### Post by stmiller on 2007-04-13
Check for a bios update for your motherboard. Or email the manufac. I emailed Shuttle who promptly emailed me back a new bios not yet available on their site to support my AMD X2 3600 chip.

---

### Post by SJI on 2007-04-13
I've been through all the Bios' for my board but none have made any difference.

I've also logged an issue with Elite Group, fingers crossed they'll come up with a new bios too :D

I can hope.

If all else fails i'll grab a new board and see how that goes.

Stephen

---

### Post by alinuxfan on 2007-04-14
my (k)ubuntu loves them.  They even cycle down when not being used....but they are nice when I am opening up and doing about a hundred things at once
:guitar:

---

### Post by defos931 on 2007-04-14
Finally, with a little command( linux noapic nolapic acpi=off pci=noacpi ) on the boot menu from the alternate Ubuntu cd (with the oem install option press F6 to ad the command line)
eveything work great for NOW!!

good luck

---

### Post by carl gleaves on 2007-04-14
does this command just allow you to run the live cd, and if so from that can you install ubuntu without any issues?

---

### Post by bugler on 2007-04-14
I had problems with my hp laptop turion x2 dv6000 not booting cd.  I fixed it by using noapic for boot command.  i would try adding just one command at a time and try and boot.  Then try multiple commands.  When you get the right combo, whammo.

Yes ubuntu works great with x2's.  my lappy is working hard right now under feisty, and before under edgy.  Enjoy.

---

### Post by mrreality13 on 2007-04-16
> **SJI said:**
> I've been through all the Bios' for my board but none have made any difference.

I've also logged an issue with Elite Group, fingers crossed they'll come up with a new bios too :D

I can hope.

If all else fails i'll grab a new board and see how that goes.

Stephen

If you end up getting a new board i have a biostar  t-force 6100-939
 (running 6.10 on 1 hd and 7.04 on a diff one)  (its no longer on new egg but i think bio star is linux friendly in general)   with a x2 4200+ and 2 gigs that loves linux and a  //  gigabyte 7600 gs p-cie
:guitar:

---

### Post by Jouke74 on 2007-04-16
The ACPI commands can be added to the Menu.lst of grub behind the Kernel. That way you don't have to type them every time. Another option is to reinstall Ubuntu after saving all your important data. Use the alternate CD and also start this one with noacpi options, this is probably better as new settings will be made for your system.

---

### Post by SJI on 2007-04-16
It gets stranger and stranger...

I've manaed to get one distro CD to boot to gnome with SMP.

6.06 LTS with a single kernel option ACPI=off will boot and run. I'm running under the CD now to type this.

My current HD install still won't load SMP, no matter what args i pass.

The latest 7.04 CD seeks my FD0 20 times and then drops to busybox; that's as far as it seems to get.

I'm unsure what to make of all this now. As 6.06 LTS boots and works from CD would this indicate that the problem lies with my BIOS (still no response from ECS rgarding this) or does the problem lie with distros after 6.06 LTS???

:confused: 

Stephen

---

### Post by jonathanku on 2007-04-25
I'm in the same situation with Edgy (Hardware: ASUS M2N4-SLI // AMD64 X2 4600 // 2GB DDR2 667).

There seem to be two suggestions here - update the bios or use the boot options. I'm away home after work to try the latter..:confused:
linux noapic nolapic acpi=off pci=noacpi 

Will report on how I get on.
JK

p.s. some more conversation going on over here:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/76989](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/76989)

---

### Post by SJI on 2007-04-25
I've done a whole bunch of testing with 7.04 installers and here is where i'm at

AMD64 installer: F4 and set graphics to 1024x768 F6 and add noapic nolapic acpi=off pci=noacpi

64bit will boot and then install.

X86 installer: F4 and set graphics to 1024x768 F6 and add pci=noacpi

X86 will boot and then install.


Oddly the F4 graphics thing seems to be important. It doesn't matter if I choose safe graphics mode or standard. If i allow a boot to proceed without setting the mode i end up at a busybox.

Hopefully the above will assist someone else...

As an aside, I don't seem able to play media from SMB shares. 
6.06 was fine, 6.10 was broken but was fixed with an update. 7.04 broken again.

Stephen

---

### Post by Footer on 2007-04-25
I really think you just need to update your mobo BIOS.

I have a similar setup to jonathanku.  My setup:

[INDENT]Asus M2N-SLI Deluxe motherboard
AMD Athlon 64 X2 4200+(65W) Windsor 2.2GHz Socket AM2 processor
Corsair XMS2 2GB (2 x 1GB) DDR2 800 (PC2 6400) Dual Channel memory[/INDENT]

and I've been running Feisty since I built it (January).  I've been adding the noapic parameter until just the other day when I finally updated the mobo BIOS to the latest.  Now she boots fine with no added parameters.

More details about my noapic thing in this thread:

[INDENT][http://ubuntuforums.org/showthread.php?p=2507342#post2507342](http://ubuntuforums.org/showthread.php?p=2507342#post2507342)[/INDENT]

:)

---

### Post by SJI on 2007-04-25
"I really think you just need to update your mobo BIOS."

I wish i could. I'm on the latest bios revision and i've logged an issue with ECS Group in Taiwan regarding the problem, but i've had no response as yet to it.

Stephen

---

### Post by jonathanku on 2007-04-27
Footer - I was hoping the BIOS upgrade would sort my problem... but alas no. My search will continue.

---

### Post by Footer on 2007-04-28
Wow, that's at least two of you whose BIOS updates did not help.  Maybe I just got lucky and should count my blessings!

Sorry to hear about your continued troubles and I do hope your research will turn up something!

:)

---

### Post by ronacc on 2007-04-28
I have installed Feisty on 3 boxes, 1 msi k8tneo2 , amd 3000+ , 2 msi k9vgm , amd x2 3800+ , 3 gigabyte ga55plus-s3g(rev-2.1) amd x2 4600+. none has required any extra boot parameters to either boot the live cd or to install.

I might have had problems with the k9vgm if I had not previously had problems with sabayon 3.26 , in trouble shooting those I found out that some mobo/chipset combos have problems with the newer kernals way of handeling  sata/pata hd's . In my case it turned out to be an older but perfectly working cd drive on the same ide cable as the dvd drive I use for booting cd/dvd's , had I not already discovered that and corrected it I may have needed boot parms on that one (or it may not have booted even with them) .

if you can get the live cd to boot in verbose mode or after it quits get to a terminal and examine dmsg look to see if there is a msg about cant find xxx (xxx is the boot drive) , that is a key that you have the problem I described above.

---

### Post by MisterD on 2007-04-28
> **Footer said:**
> Wow, that's at least two of you whose BIOS updates did not help.  Maybe I just got lucky and should count my blessings!

Make that three. And to top it off, I have the exact same motherboard as you! Updated BIOS to 0903, no love with 7.04. I could install 6.06 and 6.10 with acpi=off, but both were i386. AMD64 of 7.04 always hangs no matter what I pass to the kernel. I give up! :mad:

---

### Post by jonathanku on 2007-04-30
> **SJI said:**
> 

AMD64 installer: F4 and set graphics to 1024x768 F6 and add noapic nolapic acpi=off pci=noacpi

64bit will boot and then install.

Stephen thanks! I added this line to /boot/grub/menu.lst  (on the kernel line) and it now seems to boot cleanly. :) 

For those beginners like me with AMD64 stumbling across the same problems, do this from a terminal:
> sudo gedit /boot/grub/menu.lst then add the following: > noapic nolapic acpi=off pci=noacpi ....to the end of the Kernel line (near the end of the file - there might be a few sections with lines beginning "kernel" - the first is probably the default... other ones might be recovery mode or whatever).

---

### Post by Footer on 2007-05-01
> **MisterD said:**
> Make that three. And to top it off, I have the exact same motherboard as you! Updated BIOS to 0903, no love with 7.04. I could install 6.06 and 6.10 with acpi=off, but both were i386. AMD64 of 7.04 always hangs no matter what I pass to the kernel. I give up! :mad:

Sorry to hear about your troubles MisterD.  I guess once again I'm just lucky...?  Honestly, the 2.6.20-15-generic kernel along with the 0903 BIOS update for this mobo seemed to have solved all of my booting problems as I'm not passing any additional parameters any more.  And she's booting fine into Feisty!  Perhaps your problems lie elsewhere (video drivers or something else?)???  I'm not smart enough about the booting sequence to provide you any more assistance but perhaps there's something else besides noapic that's causing you boot problems in 7.04.

I do wish you good luck!

---

### Post by SJI on 2007-05-10
I finally have a response from ECS Group regarding the ACPI problem on their board.

"Dear Customer,

Please take a look on ubuntu forums for more info related to this issue. This is a problem related to the Linux distribution.

Thanks & regards,
Elitegroup Computer Systems EU B.V.
Technical Support Department"

Outstanding technical support :lolflag: 

Stephen

---

### Post by Footer on 2007-05-10
It took them two weeks to respond and that's the best they could come up with???  SHEESH!!!

:)

---

### Post by SJI on 2007-05-10
My sentiments exactly.

I've replied to them and will wait and see if anything comes from it, and will post any response here.

I can only assume that they are windows-centric in their support and development as they seem to target gamers with their kit.

If nothing comes of the support exchanges I guess it will have to be a replacement mainboard for this machine.

Stephen

---

### Post by 4amir on 2007-07-11
> **Footer said:**
> I really think you just need to update your mobo BIOS.

I have a similar setup to jonathanku.  My setup:

[INDENT]Asus M2N-SLI Deluxe motherboard
AMD Athlon 64 X2 4200+(65W) Windsor 2.2GHz Socket AM2 processor
Corsair XMS2 2GB (2 x 1GB) DDR2 800 (PC2 6400) Dual Channel memory[/INDENT]

and I've been running Feisty since I built it (January).  I've been adding the noapic parameter until just the other day when I finally updated the mobo BIOS to the latest.  Now she boots fine with no added parameters.

More details about my noapic thing in this thread:

[INDENT][http://ubuntuforums.org/showthread.php?p=2507342#post2507342](http://ubuntuforums.org/showthread.php?p=2507342#post2507342)[/INDENT]

:)

Hi , 
I have the same problem with Ubuntu Feisty and Fedora core !! I am using the same Asus M2N-SLI Deluxe Motherboard ! I really don't know how to upgrade my BIOS ! the last BIOS update is Version  1102 I already downloaded the .BIN file from ASUS.com , could you please tell me how to update the BIOS ?:confused:

Thanks
4amir

---

### Post by MisterD on 2007-07-11
> **Footer said:**
> Sorry to hear about your troubles MisterD.  I guess once again I'm just lucky...?  I do wish you good luck!

I finally dumped the M2N-SLI on fleaBay and bought a new ASUS Crosshair, a way better mobo and no problems with any flavor of Ubuntu, 32 and 64-bit 7.04 go down and do not require any kernel parameters. So a bit costly, but in the end, it's running Fiesty, and that's what counts :)

---

### Post by Footer on 2007-07-12
> **4amir said:**
> Hi , 
I have the same problem with Ubuntu Feisty and Fedora core !! I am using the same Asus M2N-SLI Deluxe Motherboard ! I really don't know how to upgrade my BIOS ! the last BIOS update is Version  1102 I already downloaded the .BIN file from ASUS.com , could you please tell me how to update the BIOS ?:confused:

Thanks
4amir

You dump the .BIN file on a memory stick, pop the memory stick in an empty USB port, reboot the machine, go into BIOS, find the menus where you update the BIOS, then look for the .BIN file on your memory stick (it should have been mounted as a drive (D: or E: or whatever?) and install!

Sorry I can't be more specific, I'm going from  memory and it was awhile ago I did it on my system but that's basically it!  EZ!

:)

---

### Post by Bannor on 2007-07-12
I had a the same problem.  It was a while ago, but nvidia motherboard didn't work with linux out of the box.  I loaded windows then the nvidia drivers then linux.

Also try alt install disk as well.  I can't say that it will help this, but it seems to install with less problems.

---

### Post by aigarius on 2007-08-23
One other thing to try is to REMOVE all kernel options EXCEPT "root=... ro", this worked for me with HP 6715b and AMD Turion 64 X2 TL-56 processor.

---

### Post by brew1brew on 2007-08-23
I'm running 64 bit Fiesty on 

Asus M2NPV-VM NVIDIA® GeForce™ 6150 + nFroce™ 430
AMD X2 5000+
with 2 gig of DDR2 800 memory
1 SATA 250gig drive
2 PATA drives

Without any issues.

I also have it running on 

ECS GeForce 6100SM-M Socket AM2 
AMD X2 4600+
with 2 gig of DDR2 667 memory

also without issues. 

Les

---

### Post by ramadhian on 2007-09-22
I have Acer Aspier 5051ANWXMi here

* AMD64 Turion

Ubuntu 32bits work here but I still have problem with sound 

Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

---

### Post by nss0000 on 2007-09-22
Running ASUS_m2n + AMD5400+ ( Crucial RAM/NV7600 ) with DAPPERx64 for the last couple months. Bought a legacy NIC and SB16 to avoid those issues and otherwise have never had a problem. Dammfast.

---

