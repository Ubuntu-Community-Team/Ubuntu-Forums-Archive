---
title: "64 Bit Ubuntu?"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by webcoded612 on 2008-06-04
I'm wondering about this 64 bit stuff.  I don't know a lot about it, so let me lay out the basics here and then get some input (hopefully).

I have an AMD Athalon64 3000+ Processor @ 2.0Ghz.  I've always used 32bit versions of Windows and Ubuntu, but I notice that Ubuntu has 64bit versions, as well.

What I'm wondering is this:  

1.  Would 64Bit be compatible with my processor?  The last time I tried it (with Feisty, I think), I had a cataclysmic crash at install.  Someone here told me to try the 32bit version, and it worked (as well as Ubuntu Feisty worked, anyway, which for me wasn't very well).  

2.  Does it make a difference?  I know that 64Bit is only any good if the applications are written for it, right?  Or am I thinking dual-core here?  If I installed 64Bit Ubuntu HH, would it really make that much of a difference?

3.  Are all the problems with 64Bit common to 64Bit processors, or is it just Ubuntu isn't designed very well to work with them.  I ask because I want to know if there's a possibility of 64Bit support getting better as Ubuntu is updated, or if it's something I'd need a newer processor for.  

My system specs are this:  E-Machines W3400:  80Gb HDD, 1.5Gb DDR RAM, AMD Athalon64 3000+ CPU @ 2.0Ghz, ATI Radeon X1300 PCI-E Video @ 256MB

Any ideas?  Or am I just, as my mother would say, cruisin' for a bruisin' by messing with 64Bit?  

Thanks!

---

### Post by loudnlownoma on 2008-06-04
The 64-bit should work with any 64-bit processor.  As long as your processor support 64-bit Operating Systems, it should work fine.  Although I do see a few problems in threads where folks have issues with the 64-bit versions of Ubuntu and moving to 32-bit helps, it is in most cases more of a band-aid, and the problem is a symptom of another problem, not just that the 64-bit is no good.  I have an Intel Q6600 quad-core in my desktop running the 64-bit of Hardy without trouble as we speak.

For number 2, that is the major difference.  You really won't see much difference between the two other than in using programs written specifically for 64-bit OS's.  Also, the 64-bit will allow you to use more than the 3.whatever GB of RAM if you have it installed.

Best guess would be to get a live CD and try it out, and see how it goes really.  Every hardware configuration is going to be different, so it's hard to say how easily it will work, but I was happy with my install and had no issues outside of normal new install stuff, as I'd expect would happen with either version.

---

### Post by aeon on 2008-06-04
quick answer:

1. yes, it's a 64 bit proc so a 64bit OS will work no problem. I have the same proc and I've been running 64bit since dapper..

2. yes and no.. if you do a 64bit install then all the programs will be compiled for 64bit, the question is if the code has been optimized to take advantage of the 64 bit architecture or not. usually they are compiled from the same code as the 32 bit ones, just with different flags at compile time..
If you do alot of processor intensive stuff like video encoding or heavy mathematics programs then the 64bit version could give you a slight boost, but if not then the 32bit version works just fine..

3. I'm not shure what problems you're referring to.. I haven't had any major problems so i don't know, but usually, if something doesn't work then get the source and compile it yourself, and if you're lazy get the 32 bit package and install that, 32bit packages work on 64bit machines with a little tweaking..

my .02 $

---

### Post by jespdj on 2008-06-05
> **webcoded612 said:**
> 1.  Would 64Bit be compatible with my processor?
Yes, you have a 64-bit AMD processor, so the AMD64 version of Ubuntu works with it.

> **webcoded612 said:**
> 2.  Does it make a difference?  I know that 64Bit is only any good if the applications are written for it, right?  Or am I thinking dual-core here?  If I installed 64Bit Ubuntu HH, would it really make that much of a difference?
For processor-intensive applications, the speed difference can be up to 25%-30%. You won't notice a big difference for web browsing, e-mailing, word processing or other lighter tasks. Note that 32-bit operating systems have a 4 GB memory limit. If you have lots of memory in your computer, then the 64-bit version will allow you to use all the memory.

Almost all software that you get with 64-bit Ubuntu is 64-bit as well. There are some proprietary software packages (Adobe Flash, Skype) that are only available in 32-bit, but 32-bit software works on 64-bit Ubuntu as well.

> **webcoded612 said:**
> 3.  Are all the problems with 64Bit common to 64Bit processors, or is it just Ubuntu isn't designed very well to work with them.
64-bit Ubuntu works great, it is not so that Ubuntu isn't designed very well for 64-bit.

If you have a 64-bit processor, then why restrict yourself to 32-bit?

Read the sticky: [Advantages and Disadvantages of 64bit. (Plus install Guides)](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by webcoded612 on 2008-06-05
> **jespdj said:**
> Yes, you have a 64-bit AMD processor, so the AMD64 version of Ubuntu works with it.


For processor-intensive applications, the speed difference can be up to 25%-30%. You won't notice a big difference for web browsing, e-mailing, word processing or other lighter tasks. Note that 32-bit operating systems have a 4 GB memory limit. If you have lots of memory in your computer, then the 64-bit version will allow you to use all the memory.

Almost all software that you get with 64-bit Ubuntu is 64-bit as well. There are some proprietary software packages (Adobe Flash, Skype) that are only available in 32-bit, but 32-bit software works on 64-bit Ubuntu as well.


64-bit Ubuntu works great, it is not so that Ubuntu isn't designed very well for 64-bit.

If you have a 64-bit processor, then why restrict yourself to 32-bit?

Read the sticky: [Advantages and Disadvantages of 64bit. (Plus install Guides)](http://ubuntuforums.org/showthread.php?t=765428)

I didn't mean to suggest that 64Bit Ubuntu is bad or not designed well...I've just read about issues people have with 64Bit, and I didn't know if this was a CPU problem or OS problem.  

I guess I don't do a lot of processor-intensive tasks (except manage my themes...that sends my Cpu to 100% for some reason).  Maybe I'll use VBox to install 64Bit Ubuntu and try it out.  What do you think?   :)

---

### Post by Kilz on 2008-06-05
> **webcoded612 said:**
> I didn't mean to suggest that 64Bit Ubuntu is bad or not designed well...I've just read about issues people have with 64Bit, and I didn't know if this was a CPU problem or OS problem.  

I guess I don't do a lot of processor-intensive tasks (except manage my themes...that sends my Cpu to 100% for some reason).  Maybe I'll use VBox to install 64Bit Ubuntu and try it out.  What do you think?   :)

[85% of these people]("http://ubuntuforums.org/forumdisplay.php?f=326") have problems with the 32bit edition, does that make the 32bit version unusable? To my knowledge there is no version of any Linux distro that cant have some issues. Sadly some people look for the slightest issue as an excuse not to install the 64bit version and ignore all the other people  posting problems about the 32bit version (easily 85% of the posts on the forum).

To my knowledge it isn't possible to install 64bit Ubuntu to virtualbox. [Virtualbox cant run 64bit guests.]("http://ubuntuforums.org/showthread.php?t=773248")

---

### Post by Tyler H on 2008-06-05
The only issue I had with 64 bit Ubuntu was with Flash in Gutsy. I am now running a laptop and desktop on 64bit Hardy error free.

---

### Post by Jouke74 on 2008-06-06
This topic has already been discussed many times. Using a 64 bits vs. 32 bits OS (any OS e.g. Vista as well) and getting problems with them is very much dependent on your choice of hardware, the version of the OS (if applicable) and the software you use. Your subsequent 64 bit experience will be determined mostly by your own knowledge and capability how to deal with these problems (if there are any!). Hardy Heron 64 bit is a very good choice in this perspective, since there are not many often occurring 64bit problems left. The ones which are, can often be solved reading the forums here or elsewhere (Google is your friend).  

The same holds true for 32 bit as Kilz pointed out. However since more people use 32 bit, it's more likely that your problem has already been reported and solved. Now please note that many solves reported for 32 bit Linux work under 64 bit as well (sometimes with minor adjustments to 64 bit alternative file names / libraries). 

A big exception to this rule is 64 bit hardware drivers. 
You really need to look for 64 bit alternatives here.

Your given list of hardware does not include anything exotic, so I assume you will be fine. Just make sure you know how to handle your wireless card if you use any.

---

### Post by jespdj on 2008-06-06
> **webcoded612 said:**
> Maybe I'll use VBox to install 64Bit Ubuntu and try it out.  What do you think?   :)
Unfortunately, VirtualBox does not support 64-bit guest operating systems as far as I know, so you can't install 64-bit Ubuntu in a VirtualBox VM.

Also, running an OS in a VM is not a good way to check for hardware compatibility; the VM presents virtual (not the real) hardware to the guest OS, and if the guest OS works with the virtual hardware it doesn't say anything about if it works with your real hardware.

> **Jouke74 said:**
> A big exception to this rule is 64 bit hardware drivers. 
You really need to look for 64 bit alternatives here.
In my experience it is not hard to find 64-bit Linux drivers; most drivers, especially open source drivers, are easily available in 64-bit. nVidia and ATI have 64-bit drivers available for their graphics cards.

---

### Post by Jouke74 on 2008-06-06
> **jespdj said:**
> In my experience it is not hard to find 64-bit Linux drivers; most drivers, especially open source drivers, are easily available in 64-bit. nVidia and ATI have 64-bit drivers available for their graphics cards.

Yes, I fully agree, but the "how to's" that involve installation of 32 bit drivers usually require different steps when used for 64 bit, if they can be used at all. That was my point.

---

### Post by irumat on 2008-06-06
I'll just share my experience: I've just finished installing 64-bit Ubuntu onto my desktop AMD 64 4000. By far the biggest problems are drivers. You need to ***know*** that the hardware you have has 64-bit drivers. I had/have real problems using ndiswrapper for my Linksys Wireless USB dongle. I've managed to get it working but the machine won't boot with it plugged in; I need to disconnect it, boot Ubuntu and log in, and only then plug it in once everything is loaded. It works perfectly after that! Strange...thankfully it's on the end of a USB lead which I can keep within arm's reach. 

However, it has taken me a good portion of the last two days to sort that out (and, obviously, it's still not perfect). I was getting very irritated. Every 'solution' is essentially a stab in the dark; you don't know whether what you're reading applies to you but, hell, you end up trying it anyway. I am hoping that I'm not afflicted by any of the strange AMD64 bugs that I keep reading about - unexplained freezing etc. I've had a few freezes since I started but none in the last day. (OpenOffice crashed X and keyboard input completely; an unavailable NFS mount froze X - I needed to go to another term and kill Nautilus). I seriously thought about packing it in and just installing 32-bit but I'm glad I persevered.

Anyway, I've managed to install everything, and even built some things from source without any trouble (R - using instructions found on these forums!).

I've got PulseAudio working, Compiz working, Flash working, Acrobat Reader 32-bit, Java 64-bit installed along with Intellij IDEA, 4GB+ RAM available. It's pretty sweet.

I can't compare the performance to a 32-bit install unfortunately (only ran WindowsXP on this PC) but it's nice knowing that you're actually *using* the hardware you paid for! *Which is, from my current perspective, the only reason to install 64-bit.*

---

### Post by Mgiacchetti on 2008-06-06
"why would you want to limit yourself to 32?"

considering you wont even find half as many apps that run on 64 unless you compile them from source (if you know how) plus the fact that 64 is really only beneficial if you have 4+ gigs of memory (and who has that?)  


I have been running an AMD 64 3500+ with UB 64 8.04  for about 2 mos now, and have had no problems, aside from finding apps to run on it.... thats the fun part...

---

### Post by Mgiacchetti on 2008-06-06
> **Jouke74 said:**
> Yes, I fully agree, but the "how to's" that involve installation of 32 bit drivers usually require different steps when used for 64 bit, if they can be used at all. That was my point.

but nvidia drivers come automatically for 64 bit ubuntu hardy, if you have restricted checked...

---

### Post by Kilz on 2008-06-06
> **Jouke74 said:**
> Yes, I fully agree, but the "how to's" that involve installation of 32 bit drivers usually require different steps when used for 64 bit, if they can be used at all. That was my point. I dont think thats the case with ATI graphics drivers. The howto is the same regardless of the bit.

> **Mgiacchetti said:**
> "why would you want to limit yourself to 32?"

considering you wont even find half as many apps that run on 64 unless you compile them from source (if you know how) plus the fact that 64 is really only beneficial if you have 4+ gigs of memory (and who has that?)  


I have been running an AMD 64 3500+ with UB 64 8.04  for about 2 mos now, and have had no problems, aside from finding apps to run on it.... thats the fun part...

That is simply not true. 64bit isnt just for people with over 4gigs of ram, it isnt the only benefit.
Please list all the applications you did not find.

---

### Post by Jouke74 on 2008-06-06
I was not pointing to Video card drivers alone. With ndiswrapper for wireless you need to find a good working windows 64 bit driver, which can be difficult sometimes. Furthermore there are some extra issues with the ATI drivers under 64 bits. E.g. I don't think you need to install ia32 libs under 32 bits, which you do need for 64 bits. 

Also there is this section:

> Additional 64-bit instructions

If you have a 64 bit install, the above dpkg command may complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package:

sudo apt-get install -f

Catalyst 8.5 on 64-bit systems requires the --force-overwrite command in the above dpkg command:

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.493*.deb fglrx-kernel-source_8.493-0*.deb fglrx-amdcccle_8.493-0*.deb


Anyway, 64 bit Hardy works good with the ATI restricted drivers packages, so no issues here. I really like 64 bit, but it's good to know what you need to watch out for.

---

### Post by cariboo on 2008-06-06
I've been using 64bit since I got my latest computer (i believe it was version 6.06) I haven't had any problems that could  not be solved by searching through the forums. There a some very knowledgeable people here  and if you follow their advice you should have no problem solving any issues.

Jim

---

### Post by copyleft on 2008-06-07
I've been running 64 Bit Hardy on a desktop (Nvidia, Core 2 Duo, 4 gb ram) and it has been amazing.  It is very stable.  There have only been two, maybe 3 times that I had difficulty or found it impossible to install a program, (most recently OpenOffice 3.0 Beta).  

I followed this tutorial after install, 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)   

and all has been really good in 64 bit land.  In all honesty, I have had so many fewer problems with the 64 bit Hardy than the 32 on my Dell 1420n, in terms of plugins, etc.  

Why not give it a shot?  I'm really happy with it.

---

### Post by doorknob60 on 2008-06-07
64 bit works just fine on My parent's Kubuntu laptop. Flash, Java, Google Earth, ndiswrapper for broadcom, everything that worked in 32 bit. And things actually seem quite a bit faster than 32 bit, even though I only have 1 gb of ram so that disproves the statement that it's only worth using if you have more than 4 gigs of ram.

---

### Post by kangarooman1 on 2008-06-08
As a fellow 64-bit brother, I thought I would let you in on some of my own experiences with 64 bit Ubuntu:

- My system : SUN Ultra 20 - 64 bit dual core Opteron @ 1.8 Ghz
- I found Ubuntu-amd64 to be a lot better organised in terms of 64 bit system libraries. Something I did not find in openSuse where I had to run a lot of applications in 32 bit compatibility mode. Some applications like Eclipse simply failed to run.
- Excellent 64 bit support from Ubuntu forums and a lot of resources from debian packages.
- My processor gets taxed quite a lot for graphics intensive applications. Some applications have "hanging up" problems like - Google Earth and the Ant Spotlight screen saver. I have a Nvidia Graphics FX1400 card, but I think Ubuntu downloaded the wrong driver for it. Still investigating.
- I had problems playing Real Media files with extensions ".rn" where the Real Player refuses to play sound and video at the same time.
- Also had problems with flash applications on certain websites. An example being:
[http://www.niassembly.gov.uk/vtour/tour_frame2.htm](http://www.niassembly.gov.uk/vtour/tour_frame2.htm) ... click on "360 degree view" which tries to launch a flash player that fails on my machine.

Summary: Overall a satisfactory experience, with a few teething problems here and there.

---

### Post by User3k on 2008-06-08
> **kangarooman1 said:**
> As a fellow 64-bit brother, I thought I would let you in on some of my own experiences with 64 bit Ubuntu:

- My system : SUN Ultra 20 - 64 bit dual core Opteron @ 1.8 Ghz
- I found Ubuntu-amd64 to be a lot better organised in terms of 64 bit system libraries. Something I did not find in openSuse where I had to run a lot of applications in 32 bit compatibility mode. Some applications like Eclipse simply failed to run.
- Excellent 64 bit support from Ubuntu forums and a lot of resources from debian packages.
- My processor gets taxed quite a lot for graphics intensive applications. Some applications have "hanging up" problems like - Google Earth and the Ant Spotlight screen saver. I have a Nvidia Graphics FX1400 card, but I think Ubuntu downloaded the wrong driver for it. Still investigating.
- I had problems playing Real Media files with extensions ".rn" where the Real Player refuses to play sound and video at the same time.
- Also had problems with flash applications on certain websites. An example being:
[http://www.niassembly.gov.uk/vtour/tour_frame2.htm](http://www.niassembly.gov.uk/vtour/tour_frame2.htm) ... click on "360 degree view" which tries to launch a flash player that fails on my machine.

Summary: Overall a satisfactory experience, with a few teething problems here and there.

This is strange. Flash is hit and miss with me when I go to different websites but that link you gave, it works great for me when I click the 360 degree view.

---

### Post by bmoney80 on 2008-06-08
> **copyleft said:**
>  Why not give it a shot?  I'm really happy with it.

I was a bit apprehensive to posting a reply since I've been using ubuntu for ... oh, only about a week - but honestly, I have to agree with those who support giving 64bit a shot. 

I'm running 64bit hardy on T5540 Dell 1720 with 4gb ram, broadcom bcm4328, intel 965. I can't tell you the amount of bsod's i would get under vista due to hardware issues. I couldnt even upgrade to the eagerly awaited vista sp1. So, due to my experience with dialup irc and using dos about 15 years ago combined with my interest in desktop customization I finally decided to make the switch. Before making the switch I spent a couple weeks reading up on ubuntu so I expected some issues with drivers and what not.  

To make a long story short - I pretty much took on the idea of "Why not" when installing 64bit. If I'm going to run into some issues either way why not learn with 64bit ?? 

Well, a week later (with the help of an awesome community of experienced ubuntu users) Ive been running 64bit hardy with success. I have as stable of a wireless connection as I can get with the bcm4328. I'm getting 1400x900 display on a weak intel graphics card (and even using a few graphical perks through compiz). And most importantly, I succesfully installed virtualbox/xp to use 2 windows programs (bodog poker and zune mp3 software) and have internet, usb connectivity, and sound controls working simultaneously.  

I guess to sum up everything - over the past week I've loved my transition to ubuntu 8.04 64bit both functionally and aesthetically and I'll never go back to windows. 

I do recommend the following resources:

1. This forum.
2. [http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/) - a great support paged designed by Pjotr123 and helped a lot with multimedia settings. 
3. [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) - a great Ubuntu overview
4. [http://ubuntuforums.org/showthread.php?t=690713&highlight=virtual+machine+windows+xp](http://ubuntuforums.org/showthread.php?t=690713&highlight=virtual+machine+windows+xp) - awesome link to help getting virtualbox working.
5. [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) - a great ubuntu customization resource - very helpful.
6. [http://www.linuxalt.com/](http://www.linuxalt.com/) - The Linux Alternative Project - that provides information on windows programs and their relative linux alternatives. 

Sorry for the long post - but I've just had such a great experience and I wanted to share that with all others thinking of switching - especially to the 64bit version. 

Ben

---

