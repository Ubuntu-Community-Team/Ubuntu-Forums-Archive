---
title: "can i have some AMD64x2 advice?"
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesford on 2006-06-05
hello

my old 32 bit system is ready to be replaced, and ive decided to go for a system like below but open to suggestions:
amd64x2 4200+
Asus A8N-SLI Premium, nForce4
XFX GeForce 7900GT 256MB GDDR3 eXtreme
2gb ram

so my questions
1) am i likely to run into more problems with a 64 bit system thatn 32 bit,if so which?
2)i presume i use the 64 bit ubuntu cd for installation? or would it require some sort of special 64x2 iso?
3) can i tecnhically install 32 bit dapper on a 64 bit system like this? if so what are the implications?
4) are generally the same packages available in the 64 bit repos?
5) am i right in thinking that the correct kernel for 64x2 would be the K8-smp kernel?
6) do you reckon the above hardware is compatible with linux?
7) anything else i should think about?

thanks in advance

---

### Post by JoWilly on 2006-06-05
You are good to go.

Same packages are availalbe for almost everything BUT: If you want to play 100% flash you will need to install 32 bit firefox. Have a look at the nice wiki on this, link is posted in the threads here. Also, if you want to play wmv, you need 32 bit mplayer with w32codecs.


64bit is good and a "little" faster and the browser thing is easy to fix. However, if you are a newbie, 32 bit dapper will be best for you (can be installed with no other implications than not beeing able to address more than 4GB mem).

EDIT: yes you use the 64bit cd.

---

### Post by jrobbio on 2006-06-05
*1) am i likely to run into more problems with a 64 bit system thatn 32 bit,if so which?*
Mainly with certain drivers and plugins (FLASH!!!) that have yet to be implemented into 64 bit systems.  There are ways round this, but it is comparatively messy.  There are programs that cannot yet be compiled e.g. Wine; that a lot of people want to use, though again there are work arounds for this 

*2)i presume i use the 64 bit ubuntu cd for installation? or would it require some sort of special 64x2 iso?*
Yes or download an iso from here [http://www.ubuntu.com/download](http://www.ubuntu.com/download) . 
 
*3) can i tecnhically install 32 bit dapper on a 64 bit system like this? if so what are the implications?*
Yes you can without any major implications.  The build isn't optimised for your processor so in short you are not going to be able to fully utilise the cpu in a 32 bit system.  However, there are people who have claimed not to see a difference between the 32 and 64 bit systems.  You are going to see the most benefit when using larger programs e.g. 3-d design as a lot of programs are yet to really utilise 64-bit so it is very much a watch this space issue.

*4) are generally the same packages available in the 64 bit repos?*
Yes, but for now you may need to wait that little bit longer for them if they are uncommon.  It may be that the 64 bit becomes the more popular over time.

*5) am i right in thinking that the correct kernel for 64x2 would be the K8-smp kernel?*
See [http://www.ubuntuforums.org/showthread.php?t=184829](http://www.ubuntuforums.org/showthread.php?t=184829)

*6) do you reckon the above hardware is compatible with linux?*
Yes it recognises my Asus A8N-SLI deluxe straight off and my Geforce 6600 too.  You may want some other advice about the Nvidia and ATI situation, because I haven't got my head round it.

*7) anything else i should think about?*
If you really wanted a sandbox system, you could install more than one version of Ubuntu on the same hard drive and give it some more investigative thought.

---

### Post by JoWilly on 2006-06-05
[quote=jrobbio]
There are ways round this, but it is comparatively messy.  There are programs that cannot yet be compiled e.g. Wine; that a lot of people want to use, though again there are work arounds for this 
[/quote] 

... the workarounds are to easily install the 32bit deb packages. (easy, but again, if you are a newbie, 32bit is better for you).

---

### Post by jamesford on 2006-06-05
thanks for replies so far. i dont wanna be a newbie and go with 32 bit unless i have to :P

still a couple of weeks until i buy the new computer tho, just wanted to get some advice in advance :)

---

### Post by maury on 2006-06-05
Here is my system,  It's been running like a Champ from day one. It did blow a MB after about 18 months but that happens sometimes. 
My System :  Built 3/04
Original MB ASUS K8V- Expired 11-13-05
Gigabyte GA-K8NS MB - Installed 11-05
AMD_64 3200+ CPU
e-GeForce FX 5200 Nvidia AGP Video
1024 2700 DDR-SDRam
Removable IDE 133 or 100 Hard Drives
Note! Very Stable- Never seen Windows
Primary OS - Simply Mepis but I have run many distros on it sucessfully.
Right now I'm useing Dapper AMD_64
Linux User #280929

---

### Post by st4rdr1ft3r on 2006-06-05
riiight well, there's little point in getting a 4200+, get a 2006 3800+ they all overclock better than any 4200+'s I've seen. I'm currently at 2.8ghz on air with my 3800+.
If you don't want to overclock more performance can be had either with a 4400+ or any opteron 170 or better as they both have the extra 1mb of L2 cache.

Ok the motherboard, well your not running SLI are you? If you don't plan to in the future then definitely get a DFI Lan-Party Ultra-D NF4. Its got loads more features and a much better BIOS.
If you want SLI and extra SATA controllers then get the DFI Lan-Party SLI-DR the best 939 board ever made apart from the DFI venus and you wont get one of them.

DO NOT BUY THAT CARD, XFX is having huge problems with their pre-overclocked 7900GT's dying if you must have a 7900gt get a BFG one.

what 2gb kit are you going to get? Athlon 64 systems really benefit from a low CAS latency due to their integrated memory controller so try and get a kit with 2-3-2-5 1T timings, Corsair make great kits.

---

### Post by hajk on 2006-06-05
Choose a large HD, like 250GB -- then install 64-bit and 32-bit in their own 100GB partitions, leaves another 50GB for some other future use. Initially, you'll probably use the 32-bit version as your main environment, after a while you may change -- I know I did already.

Built my machine 3 months ago (see below), would change the Opteron 165 to 170 if I had to build it now. Cheapest GeForce 6200 should be OK for most (no noisy fan), unless you're a gamer. Most mobos come with a noisy fan on the Northbridge chipset -- consider replacing it with a passive cooling block (Zalman) before you install any other stuff on the mobo.

Have fun!

---

### Post by Pancetilla on 2006-06-05
I recently built/purchased this CPU

Athlon 64 X2 +3800
2 Gb RAM
Gigabyte 7600 GT Silent Pipe
Samsung Spinpoint
in Abit An32-Sli motherboard with passive cooling
in a Antec p150 case

-------> quiet (almost silent), fast and Ubuntu works alright from the start (I usually got one of the CPUs coding my CDs at a 20x speed in Soundjuicer -a serious improvement from my previous 5x speed in AMD Athlon +2200 and the other for DVDs or whatever)

---

### Post by MojoWorkin on 2006-06-05
In my system, it didn't recognize the AMD X2 as such, it calls it Opteron... close, but not accurate.
It also didn't recognize my BFG 7900GT, it calls it "generic".
I neither recognizes my Samsung 930B LCD, and I can't get the default resolution (1280x1024) from the monitor, (max: 1024x768 75Hz).
But, it runs fine so far (3 days), yours should as well.

---

### Post by jrobbio on 2006-06-05
[QUOTE=MojoWorkin]In my system, it didn't recognize the AMD X2 as such, it calls it Opteron... close, but not accurate.
It also didn't recognize my BFG 7900GT, it calls it "generic".
I neither recognizes my Samsung 930B LCD, and I can't get the default resolution (1280x1024) from the monitor, (max: 1024x768 75Hz).
But, it runs fine so far (3 days), yours should as well.[/QUOTE]

Did you select the higher resolutions when you were installing Ubuntu?

---

### Post by TonyXPER on 2006-06-06
If you are waiting few more weeks before purchasing it, why don't you wait another few weeks for conroe, and then buy it. Don't know will you able to get your hand on one, since initial release will have low supply and really high demand. You might get a better deal on the X2 4200 since if conroe is a bargin, AMD will drop price.

---

### Post by MojoWorkin on 2006-06-06
No, there was no choices available for screen resolution, using the LiveCD installer. 
I found out, the text based version allows this.
Still stuck @ 1024x768 . . .
Also tried adjusting in: (not auto-detect)
sudo dpkg-reconfigure xserver.xorg
But that didn't work either.

---

### Post by angkor on 2006-06-07
[QUOTE=jamesford] and ive decided to go for a system like below but open to suggestions:
amd64x2 4200+
Asus A8N-SLI Premium, nForce4
[/QUOTE]

It'll work perfectly.

I just bought an Amd64 x2 3800+ and installed both 32 and 64 bit versions. The 64bit version *feels* faster but I haven't benchmarked yet.

Think again about buying the 4200+ by the way. I've got the same motherbord as you wanna buy (only I have the SE version) and it has a standard overclock utility. I've been running this proc on 2200Mhz for about 4 days now with stock cooling. No increase in temp whatsoever (36 celsius) and no stability issues either. That means that I'm running the 4200+ effectively for the price of an 3800+.

I think I'll buy a better cpu cooler and try to make it run at 2400Mhz. These procs are amazing!

---

### Post by xelink on 2006-06-25
if it's going to be a few weeks, go with intel's Conroe insteed, it's cheaper faster, and uses less energy, and this is coming from someone with a system which exceeds that of an fx60/fx62 on an undervolt


if for some odd reason you do go with the k8 though...
go with the 32 bit version. unless you're running rather odd scientific applications or are in a server like enviroment, the performance boost is minimal. The diferences between the k7 core and the k8 core are so minimal that the k7 specific kernal should run more or less at 100% efficiency on the k8.


if not, go with conroe and get the 686smp kernal.

---

### Post by Winblowz on 2006-06-25
[QUOTE=jamesford]hello

my old 32 bit system is ready to be replaced, and ive decided to go for a system like below but open to suggestions:
amd64x2 4200+
Asus A8N-SLI Premium, nForce4
XFX GeForce 7900GT 256MB GDDR3 eXtreme
2gb ram

so my questions
1) am i likely to run into more problems with a 64 bit system thatn 32 bit,if so which?
2)i presume i use the 64 bit ubuntu cd for installation? or would it require some sort of special 64x2 iso?
3) can i tecnhically install 32 bit dapper on a 64 bit system like this? if so what are the implications?
4) are generally the same packages available in the 64 bit repos?
5) am i right in thinking that the correct kernel for 64x2 would be the K8-smp kernel?
6) do you reckon the above hardware is compatible with linux?
7) anything else i should think about?

thanks in advance[/QUOTE]
I have the same motherboard and an X2 +3800. It runs great for me:D I haven't really seen the full potential of my processor though, because I have no experience in overclocking and don't want to fry my computer. 

I'm using both the 32-bit and 64-bit Kubuntu versions (k7 and k8 kernels), but I haven't really noticed a significant difference between the two. Like others said, I'd get a large hard drive, but I'd make one big /home partition and use it for every OS installed.

---

### Post by Brando569 on 2006-07-02
i have the asus/x2 3800 setup but mine seems to work wierd/slow sometimes. sometimes i think its cuz i bought it OEM off of ebay and the dude sent it to me wrapped in tissue paper! :mad:

---

### Post by pharcyde on 2006-07-02
I love 64-bit Ubuntu with my x2.  It responds so much faster than my XP system ever did.  While it does take a little time to get a few 32-bit apps working (i.e. wine, mplayer, firefox w/ flash, etc.), it's not that hard and a lot of the info can be found on the forums.

---

### Post by vigleik on 2006-07-02
Just one thing to check if you install 32bit ubuntu, is if it recognizes both of the cores. It's kind of a waste to buy a dual core and then only use one core. I have a 3800x2, and when I installed the regular 32bit dapper it only used one of the cores. I guess that could be fixed with a kernel recompile, but that's not for the faint of heart. With the 64bit version this was no problem. 

Vigleik

---

### Post by JoWilly on 2006-07-02
[quote=vigleik]Just one thing to check if you install 32bit ubuntu, is if it recognizes both of the cores. It's kind of a waste to buy a dual core and then only use one core. I have a 3800x2, and when I installed the regular 32bit dapper it only used one of the cores. I guess that could be fixed with a kernel recompile, but that's not for the faint of heart. With the 64bit version this was no problem. 

Vigleik[/quote] 
After installing the 32bit version, you just need to start synaptic and install the right kernel for your cpu to get dual core support... (the default i386 kernel is not smp) ;)

---

### Post by vigleik on 2006-07-02
[QUOTE=JoWilly]After installing the 32bit version, you just need to start synaptic and install the right kernel for your cpu to get dual core support... (the default i386 kernel is not smp) ;)[/QUOTE]

Well, that shows you how hard I tried to get that working. All I did after installing was download and burn the 64 bit version, before installing that next to the 32 bit version. I never looked back. Still, I shouldn't spread lies about how hard something so easy is. I apologize.

Vigleik

---

### Post by w6kkt on 2007-01-05
James, I just put together the system in my signature.  I really like the Opteron 170 and my OCZ VX ram.  The Opteron is the easiest overclocker I have ever used. 

Good Luck with your new system

Jesse

---

### Post by Ocxic on 2007-01-05
Automatix 64bit edition, i lost the link but it's out there, and will install 32bit stuff for you too.

---

### Post by FLPCGuy on 2007-01-05
> **JoWilly said:**
> After installing the 32bit version, you just need to start synaptic and install the right kernel for your cpu to get dual core support... (the default i386 kernel is not smp) ;)

Now there's something that should be a sticky in this x64 thread.  A real gold nugget of wisdom amid a lot of fools gold.  Thank you.


If Synaptic fails to do the kernel change, isn't it simply a matter of changing the link for vmlinuz to point to the new kernel (like swapping an old Mac system file) or is there some installation process?  SuSe's RPM update always trashed my SuSe 9.1 if I downloaded any kernel related update.

---

### Post by Unterseeboot_234 on 2007-01-07
Athelon Opteron 64 (AMD X2) with the 128-cache, , SCSI Samsung 250gig installed the 64-bit Live CD in 12 minutes. nVidia GEForce 7300 is PCIe and has on-board sound chip that optimizes gaming I found out. I only have one resolution for my monitor.

For rendering in Blender 3D and vid capture with Kino, this 64 setup out-performs the 32-bit. Most of the headaches I've seen on these forums is trying to untangle the browser set-up, especially java. Bear in mind the java SDK for 64-bit does not have a plug-in. Sun expects us to config our own 32-bit browser and 32-bit plug-in. So I do prefer the Swiftfox-32 bit because it downloads faster using DSL, much faster than any of the home-brew 32-bit browsers. So, if you go for the 64-bit, config the browser to get the flash, the MPlayer and so forth. Then, I'd recommend this link to untangle the java plug-in.

[**Custom Java install**]("http://www.ubuntuforums.org/showthread.php?t=319138")

Use Automatix2 and packages. It was Automatix that installed the 64-bit nVidia driver. If you go for building software, check up on **build-essential** and **checkinstall**. I have built and uninstalled software. Using packages makes it a much cleaner process. In fact, the only drawback to 64 bit has been the lack of off-the-shelf software. I like 64-bit. I upgraded with the idea to stay 64-bit on as much of the software as I can and ignore the rest. So far, so good.

---

