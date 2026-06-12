---
title: "Some guidance please"
date: 2006-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by T313C0mun1s7 on 2006-05-22
I am an IT Consultant and as such I can not totally leave my Windows environment behind. I am totally frustrated with XP x64 at the moment so I am not going to run it anymore on my primary workstation. However, my processor is an AMD Athlon 64 X2 dual core, and since Windows XP Pro only recognizes 2 CPUs I don't feel that is an option.

So my plan was such - Run Linux with WINE for the stuff that will run well under it and VMWare Server for the stuff that won't. Anything that I can run Linux native I will. I aready use mainly cross platform apps anyhow.

My first bad asumption was that life would be better under Linux x64 than it was under Windows x64. However, it looks like that is not the case - especally where WINE is concerned. I don't want to continue to make bad asumptions so I came to the forum. Also I apologize up front for being so long winded. On to my questions.

[LIST=1]
[*]How do I install 32 bit Ubuntu on my system? I have the pressed CDs for 5.10 and  I can not boot to the live CD. I have not yet tried an install, am I going to run into the same thing?
[*]Does Linux break the 64 bit processor into two 32 bit processors? More importantly if I run an SMP kernel will I get 4 processors?
[*]Can I set the processor affinity for VMWare Server to use the second core as two processors? I have 1Gb of RAM and it would be nice to have my host system running on two processors with 512Mb of RAM and Windows in a client VM running on two processors with 512Mb RAM.
[*]Finally, and I hope this is not too taboo, should I be looking for another Distro or OS like Suse or PC-BSD? I might have considered Solaris 10 as it sould handle dual 64bit with ease, but I am not very familiar with it and I don't want to spend all of my time figguring out administration of my own computer.
[/LIST]

Thank you in advance for your help. Any other suggestions or things to look out for you might think of that I may have not are also welcome.

---

### Post by Kethinov on 2006-05-22
First, don't ever run a 64 bit OS unless you need the extra RAM capacity it affords. Otherwise it is more trouble than it's worth.

Regarding SMP, you're over analyzing this. Yes, Linux does offer superior SMP support compared to Windows (and BSD incidentally) but the level of customization you're talking about is not necessary. Strictly speaking, the Linux kernel knows how to manage processor power on your computer better than you do.

So just get a 32 bit Ubuntu install CD and have at it. The installer will know what processor(s) you have and will install an appropritely configured kernel. You don't have to deal with manually configuring kernels unless you're running something like Gentoo, or your hardware doesn't play nice with stock Ubuntu kernels for some reason.

---

### Post by T313C0mun1s7 on 2006-05-22
So then why am I not able to boot to the live CD? Does it have a more limited number of kernels? Shouldn't any i386 architecture kernel that is for a processor older than mine boot and work even it I loose some optimization? I mean in theory if Ubuntu wanted to play to the lowest common denominator and only have a 386 kernel I should still be able to boot, right?

Also, I concede that I may have over thought processor affinity (even if I have had cases in Windows where it was helpful) but how many processors will Linux see? My understanding is that would be a function of the OS not of the BIOS; as the BIOS describes the hardware to the OS so it knows what to do with it, but controlling the hardware is the realm of the operating system. So how does the Linux operating system, or I maybe it would be better to say the kernel, handle the 64 bit processor if it is a 32 bit kernel? Do I get a split processor, where one 64 bit proc acts as two, or just one 32 bit proc per core?

This may be a new area to think about when it comes to building a kernel to your processor as the only real difference between an Opteron and an Athlon X2 is how much memory you need to access. This brings multiple processors at 64 bit out of the realm of servers and on to the desktop. With the Athlon X2 available on the market the only reason to purchase an Opteron x64 is if you need more than four cores and are adding multiple physical procs, or you need more than 8 Gb of RAM. So there is now a middle ground processor for low end servers and high end desktops that falls between the standard Athlon 64 and the Opteron 64. Thus we should expect to start seeing 64 bit SMP computing hitting the desktop, it has hit mine and I configured my computer for $750 dollars. [AMD Athlon 64 X2 3800+, 1Gb RAM, MSI K8N-Neo4 Platinum Motherboard, 80 Gb SATA drive and 160 Gb ATA133 drive, LG 8x DVD+/-R/RW Optical drive]

Then again I may be once again over thinking everything. I just have an intrinsic need for details before I go jumping into changing how I am going to setup my primary workstation, the computer I use to make my living and put food in the mouths of my wife and children.

Once again thank you in advance for your assistance and Kethinov, thank you for your prompt rely.

---

### Post by T313C0mun1s7 on 2006-05-23
Quick update - I have been doing more reading to determine exactly how I this should work for me and I stumbled upon Win4Lin. Does anyone have experiance with this? The direct access to the filesystem sounds perfect for me.

Also I have been trying to figgure out for quite some time a gracefull way to get around the problem that VMWare does not allow direct hardware access so I can not burn CDs or DVDs from within the VM. Would Win4Lin allow this?

---

### Post by Kethinov on 2006-05-23
> **T313C0mun1s7]So then why am I not able to boot to the live CD?[/quote]

Any number of reasons. Most likely X11 related, not kernel related. Posting the errors you get would be helpful.

[QUOTE=T313C0mun1s7]how many processors will Linux see? My understanding is that would be a function of the OS not of the BIOS said:**
> 

It will see as many processors as you have. If you're worried the installed kernel is not seeing all your processors, run **cat /proc/cpuinfo** and that will tell you what processors the kernel sees.

[QUOTE=T313C0mun1s7]So how does the Linux operating system, or I maybe it would be better to say the kernel, handle the 64 bit processor if it is a 32 bit kernel? Do I get a split processor, where one 64 bit proc acts as two, or just one 32 bit proc per core?

64 bit processors for all current intents and purposes run just as fast in 32 bit mode when booted by a 32 bit kernel. There are really only two real world advantages you get by running a native 64 bit kernel. The first is the ability to make use of more than 4gb of RAM. The second is the ability to run programs that use 64 bit double-precision floating-point math, or similar; the number of programs which actually do this approaches zero. There are other, smaller performance benefits to running a 64 bit kernel, but they're extremely minor. So unless you need >4gb RAM or you run special software that fits the above description (which is almost nothing) then you really have no business running a 64 bit OS.

In addition, running a 64 bit kernel has a number of disadvantages. The biggest one is you will use more RAM because native 64 bit processes require more RAM space per register. Another problem is that you will have to use 32 bit versions of common programs anyway in your 64 bit OS just to ensure things actually work. For example, you'll need a 32 bit Firefox because there's no 64 bit Flash plugin. You'll need a 32 bit media player because there are no 64 bit codecs for a lot of formats. This in turn leads to having a 32 bit and 64 bit versions of tons of common libraries eating up loads more hard drive space. The list goes on. More trouble than its worth.

[QUOTE=T313C0mun1s7]Quick update - I have been doing more reading to determine exactly how I this should work for me and I stumbled upon Win4Lin. Does anyone have experiance with this? The direct access to the filesystem sounds perfect for me.

Also I have been trying to figgure out for quite some time a gracefull way to get around the problem that VMWare does not allow direct hardware access so I can not burn CDs or DVDs from within the VM. Would Win4Lin allow this?[/QUOTE]

Win4Lin is not anywhere near as fast as VMWare. I would recommend using VMWare instead of Win4Lin, and I would also recommend moving your CD and DVD burning to Linux native tools, for which there are many nice ones. In addition, a lot of the popular ones for Windows work in WINE.

If you want r/w between the virtual Windows and native Linux, just setup Samba and have the two operating systems mount each other's shares.

---

### Post by T313C0mun1s7 on 2006-05-23
Kethinov, thank you.

I still don't know how many processors I will have available because whether the 64 bit proc will be uses a a single physical proc or two 32 bit ones was not addressed. Also, cat /proc/cpuinfo gives me:
> 
john@powerhouse:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2010.313
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 3981.31

In which I see no mention of the number of processors, only the info the processor reports about itself.

I have installed the 32 bit version and it runs, but I only have one video resolution choice - 640x480 @ 60Hz. This is odd because it worked fine under the AMD64 version. So now I guess I have to troubleshoot that. I don't have the time to get anymore detailed at the moment and working at 640x480 is not fun so I will go for now. 

Does Ubantu have a good gui system information tool I can use to see what is being detected? Thanks again.

---

### Post by Kethinov on 2006-05-23
[QUOTE=T313C0mun1s7]I still don't know how many processors I will have available because whether the 64 bit proc will be uses a a single physical proc or two 32 bit ones was not addressed.[/quote]

You have one processor with two cores capable of 64 bit computing. This processor is backwards compatible with 32 bit computing. You don't have two 32 bit cores that add up to one 64 bit processor, or other such nonsense. That is not how things work.

[QUOTE=T313C0mun1s7]Also, cat /proc/cpuinfo gives me:[/quote]

It looks like your kernel is not correctly configured. You should see a line that says **cpu_cores: 2**, or see two processors on the list, but there is only one processor on the list and no cpu_cores line. Run **uname -r** and post the output. You should see something related to SMP in that line. If you don't, it is possible you have the wrong kernel installed.

[QUOTE=T313C0mun1s7]I have installed the 32 bit version and it runs, but I only have one video resolution choice - 640x480 @ 60Hz[/quote]

If you want more options here, you need to edit your **/etc/X11/xorg.conf** and add the appropriate resolutions and such. If you have an NVIDIA or ATI video card, you will need to install their proprietary binary drivers before you can expect to see any decent graphics performance.

[QUOTE=T313C0mun1s7]Does Ubantu have a good gui system information tool I can use to see what is being detected? Thanks again.[/QUOTE]

**sudo apt-get install hal-device-manager**

---

### Post by T313C0mun1s7 on 2006-05-23
You are right, I am not running an SMP kernel it seems. I never saw an option to choose a kernel and hoped that it had dertemined what I needed and installed it for me.

As far as the graphics go I think the x server is just totally misconfigured. On my first attempt to install the computer stopped responding to any keybaord entry at the point the install asks me to select a video resolution. I pushed my power button and the OS detected the shutdown request and changed to runlevel 0. At reboot I got dumped to a shell so I tried to install via the CD again. I reused my partitions but reformatted all file systems to get a clean re-install. This time it never asked me during the second stage install what video resolution I wanted. It just simply finished the install and left me at a 640x480 GPM login. I loged it and tried to change my resolution to discover I had no options. I think my video card is a ATI Radeon X300 based PCI-Express card with 256Mb video RAM, but it might be a X550 I am not totally sure and it is not marked. I will have to double check with my hardware vendor and find out what I purchased. This video card seemed to detect and work at all resolutions fine under the AMD 64 version. I will however get the driver from ATI as you suggested.

I have spent a little time in a lot of different distros, but not a lot of time in any. So I am not sure what to expect from Ubuntu.

> You have one processor with two cores capable of 64 bit computing. This processor is backwards compatible with 32 bit computing. You don't have two 32 bit cores that add up to one 64 bit processor, or other such nonsense. That is not how things work.

Windows will take a single core and use it as two 32 bit processors, rather than just using the backwards compatibility, but XP Pro will only see up to two procs. I was not sure if the Linux kernel did the same. Based on your responce I would say the answer is that It is strickly 1 proc per core - period. So I basically get two 32 bit procs available to me. This leave me in the same position I was in with Windows and was one of the primary reason I was going to jump ship. If I installed Windows Server 2003 and hacked to make it behave functionally the same as XP Pro I waould at least see four processors. However, I am not ready to turn back now as I have heard that Windows in Linux in a VM is actually faster than native (although I don't see how this could be posible through the emulation). I will consider the processor issue settled.

I was thinking that because Win4Lin was a thinner emulation layer, and had the advantage of native I/O that it might be faster, thank you for clearing that up. I think my processor had the AMD SVM (Secure Virtual Machine) technoloty that XenSource uses. This eliminates the need for performance-sapping chipset emulation. Do you know anything about Xen hypervisor paravirtualization? It it worth checking into, or is VMWare still the route to go?

It seems I already had hal device manager installed, but it is not giving me anything very usefull almost everything is listed as Unknown, even things that should easily report information about themselfs. For example, my hards drives are listed at Unknown, from Unknown vendor with an Unknown model, an Unknown device type, and Unknown capabilities. Even the status is just "status". This is the same for virtually all of my hardware.

Any suggestions? Things seem a bit thrashed to me and I am wondering if I should try another install, or download Dapper and try that. I am installing from the nice presses CDs that they package in the neat little cardboard CD case with a Install CD and a Live CD. I picked it up from a display at a local computer store. I think I already has ISOs of them, but thought the packaging looked nice. Anyhow, because it is a pressed CD I doubt the CD is bad, but it might be a little out of date. It is printed with version 5.10 so I know I am running Breezy.

One again, Thank you.

---

### Post by Kethinov on 2006-05-23
[QUOTE=T313C0mun1s7]my video card is a ATI Radeon X300 based PCI-Express card with 256Mb video RAM[/quote]

Then you need to install ATI's binary fglrx driver to get decent performance.

[QUOTE=T313C0mun1s7]Windows will take a single core and use it as two 32 bit processors[/quote]

No, Windows sees each core as a single 32 bit processor.

[QUOTE=T313C0mun1s7]This leave me in the same position I was in with Windows[/quote]

No, the Linux kernel is better at SMP than Windows because it's had support for it much longer and its been heavily refined over the years.

[QUOTE=T313C0mun1s7]If I installed Windows Server 2003 and hacked to make it behave functionally the same as XP Pro I waould at least see four processors.[/quote]

What? You have a single dual core processor, yes? This means your kernel will see at maximum two processors, regardless of the operating system.

[QUOTE=T313C0mun1s7]Do you know anything about Xen hypervisor paravirtualization? It it worth checking into, or is VMWare still the route to go?[/quote]

I don't know much. But VMWare is a lot easier. And it's worked for me for years. So I stick with it. Admittedly, videos of fast OS switching between Linux, OS X, and Windows are impressive, but AFAIK there are still technical hurdles to jump before this is viable on many people's setups. Perhaps not yours. I don't really know.

[QUOTE=T313C0mun1s7]It seems I already had hal device manager installed, but it is not giving me anything very usefull almost everything is listed as Unknown, even things that should easily report information about themselfs. For example, my hards drives are listed at Unknown, from Unknown vendor with an Unknown model, an Unknown device type, and Unknown capabilities. Even the status is just "status". This is the same for virtually all of my hardware.[/quote]

All that means is there's no specific identifier for that variable. Switch to the advanced tab to see what the kernel sees.

[QUOTE=T313C0mun1s7]Any suggestions? Things seem a bit thrashed to me and I am wondering if I should try another install, or download Dapper and try that. [/quote]

Not sure. You might try installing the k7 version of your current kernel, booting that, and checking /proc/cpuinfo again, but this is not my particular area. Or maybe there's nothing even wrong with your current kernel in the first place. I'm just guessing here, but it's a pretty educated guess.

X11 you can definitely fix by installing the correct drivers and editing your config.

---

### Post by T313C0mun1s7 on 2006-05-24
Sorry I am still on the processor issue, but yes windows will see a single core as two processors if the core is 64 bit. Therefore, it should see two cores that are both 64 bit as four processors.

The ability of Windows to emulate two processors when they did not physically exist came about with Hyper Threading technology. On an HT processor enter the task manager and you will clearly see a CPU0 and CPU1 both available. Do the same on a single core 64 bit processor in non-x64 XP and you still see two processors, but now it has less to do with thread access and more to do with emulating the 64 bit processor as parallel 32 bit processors. Now continue this logic and you will see that if a single 64 bit processor can be used by 32 bit Windows NT 5.1 and up as two processors; then two 64 bit processors should yield twice the processors as one 64 bit processor, yes? As far as cores versus processors go, the computer does not really know the difference (except that everything else the same a dual core is much quicker that two single procs) so I see no need to differentiate for the sake of this discussion.

Intel has tried to deliver the same type of thing with the HT Extreme line, but they are going the cheap route by opening up more processor threads rather than actually offering dual core 64 bit.

I am currently in the process of downloading Dapper via bit torrent. Edit: It just got done. I am going to start over from there. I have moved the ATI Driver to my file server so I can reinstall it after I install Dapper.

There was also a package I saw, but don't remember the name of, which installed a bunch of stuff that might otherwise cause headaches. It included Flash, codecs, and other fine stuff. I think I saw it in a thread on these forums about WINE, but I can not seem to find it again. If you know of what I speak could you please point me toward it?

As far as the Xen hypervisor, the biggest technical hurdle is that your processor has to support hardware virtualization on chip, which means only the newest processors. If you can not meet that requirement you can not use the hypervisor product which was developed after the formation of XenSource, which is a comerical open source company that brought about hypervisor and the cross-porting of Xen from Linux and NetBSD to Windows and Solaris. The current product is called XenEnterprise and runs on x86 architecture. The idea is that because it takes advantage of hardware virtualization in the processor and chipset, it does not need to emulate these layers and can give the client OS direct access to them, while still maintaining control over resources and priority at the host level, and keeping the clients separate from the host and each other.

This all sound great on paper, and actually runs as promised as I am to understand, but in the real would what is it like to configure, run, and maintain? It may be great for servers where you invest the initial time and then don't change much, but on the desktop what is it like? How hard it is to work with if I want to use it to let me work daily on my workstation? Those are the types of questions I was hoping to answer. I would rather settle for the easy and known (VMWare), than spend large amount of time to evaluate the unknown (Xen) at this point. So VMWare it is.

Thank you once again, as you have been an great help. I think I have made my decisions on what exactly I am going to do. So future issues and questions should warrant their own threads.

---

### Post by Kethinov on 2006-05-24
[QUOTE=T313C0mun1s7]Sorry I am still on the processor issue, but yes windows will see a single core as two processors if the core is 64 bit. Therefore, it should see two cores that are both 64 bit as four processors.[/quote]

No. One processor, two cores. The cores can be run in either 32 bit or 64 bit mode. The mode has nothing to do with how many processors the operating system sees. Only the number of cores.

[QUOTE=T313C0mun1s7]On an HT processor enter the task manager and you will clearly see a CPU0 and CPU1 both available.[/quote]

That's because there are two cores. It's not making up fictional processors.

[QUOTE=T313C0mun1s7]Do the same on a single core 64 bit processor in non-x64 XP and you still see two processors,[/quote]

This is not the case. My machine, for example, is an amd64 machine and in the scenario you describe there is only one processor present in any operating system because there is only one core.

[QUOTE=T313C0mun1s7]I am currently in the process of downloading Dapper via bit torrent[/quote]

You could have just upgraded to Dapper with apt-get, you know.

[QUOTE=T313C0mun1s7]Edit: It just got done. I am going to start over from there. I have moved the ATI Driver to my file server so I can reinstall it after I install Dapper.[/quote]

No, don't install the ATI driver from the file on ATI's website. Do it the Ubuntu way by installing it with apt-get.

[QUOTE=T313C0mun1s7]There was also a package I saw, but don't remember the name of, which installed a bunch of stuff that might otherwise cause headaches. It included Flash, codecs, and other fine stuff. I think I saw it in a thread on these forums about WINE, but I can not seem to find it again. If you know of what I speak could you please point me toward it?[/quote]

Dunno. Automatix?

---

### Post by NewbieNik on 2006-05-24
Sorry to throw my hat in the ring, but I have noticed you are talking about running VMWare on Wine. 
That says to me you are emulating a windows enviroment to emulate another enviroment....Sounds slow
Haven't seen Win4Lin, but I am running windows server 2003 Enterprise on my dapper AMD64x2 system with about 80% perfomance increase over a standard install, my secret?....
Well I use QEMU, now with antioxidants....(Dman those shampoo commercials)
Seriously, if you want to run other OSes I would highly recommend QEMU, just takes a little learning.

Yes, yes, I know WINE is not an emulator.....I'm just trying to simplify things, give me a break

---

### Post by Kethinov on 2006-05-24
I don't recall him mentioning running VMWare with WINE, but yes, if he had mentioned it then it is definitely better to use the Linux native version.

---

### Post by T313C0mun1s7 on 2006-05-24
Uh oh, I installed the one from ATI's website - no wonder it does not work. I will have to fix that now.
 
I tried three times to download the install CD, once via Bit Torrent and twice as a standard file download. I tried burning via my Ubantu workstation, and via two other Windows workstations. No matter what I did all I got was a CD that failed to load the package installer and failed MD5 using the installer internal CD check. So I used the apt-get to do the upgrade. I guess this means I still need to change my kernel to the SMP version.
 
Yes, it was Automatix. I also found Easy Ubantu after my last post. I am not sure what the real differences are, but I am running Automatix now.
 
Thank you once again for your help.
 
P.S. Just to clarify for NewbieNik I was planning ro run WINE for the applications WINE would work well for, and VMWare for the ones it won't work well for.

---

