---
title: "which kernel to choose ?"
date: 2009-08-16
forum: x86 64-bit Users
---

### Post by dino99 on 2009-08-16
Difficult for a newbie to choose a kernel with synaptic: there are numerous & with exotic names.

Ok, with a 64 bits processor it's logical to install a 64 bits Os.
but which one is the best:
 - do i choose linux-generic or linux-generic-pae ?
 - what about linux-rt or linux virtual ?

I've search about a topic explaining the differences & advantages/disavantages but don't succeed.

I think that synaptic should not only give technical description but explain the real particularity of each one.


When i see all the modules loaded by the kernel, which i not necessary need & slow down the system, fill the logs & eat memory, it's difficult to understand that module pae is not included by default in the standard package.

---

### Post by Malta paul on 2009-08-16
With Ubuntu 9-04 the current Kernel is 2.6.28-15. 
But if you wish you can use the latest stable version which is 2.6.30-02063004. will work OK :)

---

### Post by mazz0 on 2009-08-16
Sorry, I'm not even attempting to post an answer here as I have no idea.  But I'm curious - why are you installing a new kernel via synaptic?  Shouldn't that be left to the update tool?

---

### Post by bedtime_with_the_bear on 2009-08-16
Not wanting to sound dismissive, but the version you got when you installed Ubuntu is most likely the most appropriate one for you, unless you have very specific requirements.

PAE is a feature of your CPU and the kernel to allow a 32-bit system (OS and programs) to use more than 4GB of physical memory. You're using 64-bit Ubuntu so you don't need to worry about this as you can already address at least 16TB of physical memory with 64-bit.

Any modules installed will (should) only be loaded if the hardware that they support is present.

Try aptitude, it does give you a description and short explanation of the packages. From memory, the -rt kernel has certain real-time scheduler patches applied, and the -virtual includes support for bare-metal hypervisor functionality - probably Xen, though similar performance and functionality can be had with kvm, which does not require a new kernel as packages are available that are ready built for your existing kernel.

Unless you have a specific reason to install other kernels, as mazz0 said, you should probably just let update-manager handle everything.

That said, if you are trying to understand the kernel and how it interacts with your hardware at a lower level, it might be worth installing the source, and building it a few times with different combinations of configuration. Building your own kernel is also a great way to tune your configuration and remove drivers for hardware you wither don't have or are certain you won't ever use so that might be something you would want to look into. Just be sure not to remove every Ubuntu provided kernel - you'll want a known-good kernel to boot into if your newly built kernel doesn't boot or doesn't contain crucial drivers.

---

### Post by sanderj on 2009-08-17
> **bedtime_with_the_bear said:**
> Not wanting to sound dismissive, but the version you got when you installed Ubuntu is most likely the most appropriate one for you, unless you have very specific requirements.


Exactly! I 100% agree.

---

### Post by Malta paul on 2009-08-17
Totally agree with you guys. Just for info you can get .deb versions of the Kernel from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
I would retain the original version in case the one you try doesn't work
satisfactory!
:)

---

### Post by Yellow Pasque on 2009-08-17
rt = real-time (mainly for audio production IIRC)
pae = physical address extension, since you see this, you probably installed 32-bit Ubuntu

---

### Post by cybrsaylr on 2009-08-18
> **Malta paul said:**
> With Ubuntu 9-04 the current Kernel is 2.6.28-15. 

Just updated my destop to this Kernel which was added first on the bootup list.
Went from 2.6.28-14 to 2.6.28-15 after a restart.

However When updating my newer Toshiba laptop to 2.5.28-15 yesterday after reboot the new Kernel 2.6.28-15 was not added to the bootup list and I'm still using the 2.6.28-13 Kernel!

Anyone know why it didn't go to 2.6.28-15 after update and reboot?

Using 64 bit 9.04 on laptop and 32 bit 9.04 on desktop.

---

### Post by Malta paul on 2009-08-19
cybrsaylr, You can first check out you new kernel 2.6.28-15 which will have been added to your boot menu but not to the grub menu. When you boot up your computer and go into the grub menu press the 'e' button and change the 2.6.28-14 to 2.6.28-15 in the two lower lines,  'b' to boot with this kernel, and give it a try.

This will not make any permanent changes. If all is well use alt-f 2 and type 'gksudo nautilus' [careful, you are now in permanent root]
go to Places>home>"up arrow - twice" to /  
go to boot>grub, make a backup of 'menu.1st.
Open the 'menu.1st' file & find the entries for the -14 kernel and change to -15 
Save the file and reboot your computer.
The grub will now be changed to -15, and you will be now be booting with this configuration.

Have fun:)

---

### Post by uncleV on 2009-08-19
My first post here.

[Malta paul]("http://ubuntuforums.org/member.php?u=166032"),
in the /boot/grub/ directory of my 9.04x64 the file is named "menu.lst" and not .1st. The difference is "l" vs. "1" in the extention. Are you sure about ".1st"?

---

### Post by uncleV on 2009-08-19
> **mazz0 said:**
> Sorry, I'm not even attempting to post an answer here as I have no idea.  But I'm curious - why are you installing a new kernel via synaptic?  Shouldn't that be left to the update tool?

It sounds like "Canonical-supported Open Source software (main)" in Software Sources is unchecked so Update Manager is not proposing automatically upgrading of the kernel?

---

### Post by Yellow Pasque on 2009-08-19
Manually editing menu.lst and trying to boot a kernel you don't have will probably be painful. Patience!

Sometimes it takes a while for the updates to propagate through the mirrors. For example, I just got the update from 2.6.28-14 to 2.6.28-15 today.

---

### Post by cybrsaylr on 2009-08-20
> **Temüjin said:**
> Manually editing menu.lst and trying to boot a kernel you don't have will probably be painful. Patience!

Sometimes it takes a while for the updates to propagate through the mirrors. For example, I just got the update from 2.6.28-14 to 2.6.28-15 today.
I just got the updates to 2.6.28-15 a couple minutes ago and did them, then rebooted as instructed. After reboot I'm still running 2.6.28-13

2.6.28-15 is not listed on the Grub menu!

I can swear I did these same updates to 2.6.28-15 last night with the same results on this same laptop with 64 bit Ubuntu 9.04!

My destop running 32 bit Ubuntu 9.04 did the updates to 2.6.28-15 and is now running 2.6.28-15 and the 2.6.28-15 kernel was added to the Grub menu!

I don't know why the desktop changed to the new kernel but my laptop won't and continues to run the 2.6.28-13 kernel!

---

### Post by Malta paul on 2009-08-20
UncleV, [Ref #10] you are correct, sorry it was my typo. Thanks for correction :(

---

### Post by ken78724 on 2009-09-05
am challenged by all the excellence found here. doing a search for 2.6.28-15 synaptic package manager I found I must have it installed but after attempting to install OSS4 and somehow losing sound and not being able to get audio, video or mic for skype, I sure wished I had not tried to fix a car that ran. At least before the OSS4 install attempt I had I presume ALSA sound

 Temüjin, I went to the Sound of Linux and say power to all the hard work. 

Q for all: have I just failed to perfect OSS4 or for simplicity should I try to go back to ALSA Sound, which had empowered me to hear

---

### Post by DeMus on 2009-09-06
> **sanderj said:**
> Exactly! I 100% agree.

Well, I use the 2.6.30 and it was the first kernel without errors using Jaunty. I run a program called Boinc which uses my PC power for all kinds of projects from the University of Berkeley. I run this 24/7 on all 4 cores at 100% and with the previous kernels 2.6.28-13 , -14 and -15 I had computation errors. With the 2.6.30 I don't have them anymore.
It's the latest stable version at the moment. You can get it [_here_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by theZoid on 2009-09-07
> **DeMus said:**
> Well, I use the 2.6.30 and it was the first kernel without errors using Jaunty. I run a program called Boinc which uses my PC power for all kinds of projects from the University of Berkeley. I run this 24/7 on all 4 cores at 100% and with the previous kernels 2.6.28-13 , -14 and -15 I had computation errors. With the 2.6.30 I don't have them anymore.
It's the latest stable version at the moment. You can get it [_here_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

What kind of computation errors?  I don't quite understand how the kernel could be responsible for that.  Thanks

---

### Post by OttoDidakt on 2009-09-25
DeMus

Would you tell us how you upgraded to 2:6:30?   I've installed and reinstalled Ubuntu 9;04 and then tried numerous ways to get BOINC going for Einstein/gravity waves but I  keep getting computational errors.
Reading lots of different ways to install the latest versions of BOINC and the right parts of Linux for a 64 bit system shouts the need for some better help.

Anything will be better than going back to Windos.

Otto

---

### Post by DeMus on 2009-09-25
> **OttoDidakt said:**
> DeMus

Would you tell us how you upgraded to 2:6:30?   I've installed and reinstalled Ubuntu 9;04 and then tried numerous ways to get BOINC going for Einstein/gravity waves but I  keep getting computational errors.
Reading lots of different ways to install the latest versions of BOINC and the right parts of Linux for a 64 bit system shouts the need for some better help.

Anything will be better than going back to Windos.

Otto

**_@ OttoDidakt_**

Hi,

The linux kernel 2.6.30 can be found at the following website:
[_Kernels_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/")
You have to install 3 files:

```
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb	
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```
When clicking the files you get a choice to install them using gdebi or to save them. Choose install.
There is just one thing: the order in which you install them is important. Don't panic: when choosing the wrong file first in gdebi it will tell you it is missing some dependences. The right order is the one written above.
When done simply re-boot and you'll see the new kernel mentioned at the top of the Grub list.


[B][U]@theZoid
[/U][/B]

When you are familiar with the Boinc program you know that sometimes a workunit ends with a computational error. Something along the way goes wrong and it can mean your computer has been crunching for a few seconds in vain, or maybe even an hour.
After switching to Jaunty I had that a lot. After installing kernel version 2.6.30 in Jaunty this stopped.
So, yes, I do believe it is something in the kernel which is different in the 2.6.30 version compared to the 2.6.28 or 2.6.29 versions.

---

### Post by OttoDidakt on 2009-09-26
DeMus

Thank you. That worked just as you said unlike the other instructions I found.

Now would you be able to help me get and install the latest BOINC version which is an .sh type file?
 [http://einstein.aei.mpg.de/download/boinc/dl/boinc_6.6.40_x86_64-pc-linux-gnu.sh](http://einstein.aei.mpg.de/download/boinc/dl/boinc_6.6.40_x86_64-pc-linux-gnu.sh)
Previously I tried 'sh boinc_6.6.40...gnu.sh' but it ended up in the wrong place and perhaps had the wrong permissions and 'sudo aptitude install boinc-client boinc-manager' could work but how do I put the two boincs in the right folder.

Again any help is good of you.

Otto

---

### Post by OttoDidakt on 2009-09-26
DeMus

It showed as 2:6:30 but BOINC 6:2:81 lost all the downloaded work...

Any thoughts anyone?

Otto

---

### Post by chefbodini on 2009-09-26
Why not use the version built for your distro?

---

### Post by DeMus on 2009-09-26
> **OttoDidakt said:**
> DeMus

It showed as 2:6:30 but BOINC 6:2:81 lost all the downloaded work...

Any thoughts anyone?

Otto

Sorry. You installed kernel version 2.6.30 and it works? I read that in your previous post here.
Now you have problems with Boinc. That's something completely different.
You tried to install Boinc 6.2.81? Why? I run 6.6.31 already, although I must admit I forgot where I got it from.
When having problems with Boinc wouldn't it be better to ask the guys at the Boinc forums? There is a special forum for Linux people. The address is: [Linux forum]("http://setiathome.berkeley.edu/forum_forum.php?id=13")
It's not that I don't want to help you. I am glad I have Boinc running but I most certainly am no expert here. I installed it a long time ago, even when using Hardy. Just copied the Boinc folders into the new home folder, made a link to my desktop and continued crunching.
You know you can install Boinc manager 6.2.18 from Synaptic? No hassle with .sh files which, in my experiences so far, are a pain in the b*tt. Pardon my French.
Few questions just out of curiosity:
Which Boinc manager do you run, or did you run before starting to update?
Which projects are you running?

---

### Post by theZoid on 2009-09-27
> **DeMus said:**
> **_@ OttoDidakt_**

Hi,

The linux kernel 2.6.30 can be found at the following website:
[_Kernels_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/")
You have to install 3 files:

```
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb	
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```
When clicking the files you get a choice to install them using gdebi or to save them. Choose install.
There is just one thing: the order in which you install them is important. Don't panic: when choosing the wrong file first in gdebi it will tell you it is missing some dependences. The right order is the one written above.
When done simply re-boot and you'll see the new kernel mentioned at the top of the Grub list.


[B][U]@theZoid
[/U][/B]

When you are familiar with the Boinc program you know that sometimes a workunit ends with a computational error. Something along the way goes wrong and it can mean your computer has been crunching for a few seconds in vain, or maybe even an hour.
After switching to Jaunty I had that a lot. After installing kernel version 2.6.30 in Jaunty this stopped.
So, yes, I do believe it is something in the kernel which is different in the 2.6.30 version compared to the 2.6.28 or 2.6.29 versions.

Thanks Demus for the above information.  I've had one kernel panic with stock kernel, I'll try the one you listed above.  :)

---

### Post by OttoDidakt on 2009-09-27
DeMus

Thanks thus far.

I thought you had a similar set-up so you might be the easiest source of help.

I'm trying to BOINC for Einstein (gravity waves). No matter what I do I can't install anything but BOINC 6:2:18. via Synaptic (including sudo and aptitude but perhaps into the wrong directories).
Yes that was running with computational errors before the move to Ubuntu 2:6:30 and after that the work just disappeared after downloading it.
Is 6:2:18 the right version for this distro as it comes with the latest one? The BOINC site says no but I am too new to find what's going on.
The Linux link is to SETI and I searched there before discovering your post.

I started with a clean 130 Gb hard drive, 4 Gb of ram and twin 3 Ghz core2duo chips E6850 just to BOINC so it can all be wiped and started anew. 

! Otto

---

### Post by OttoDidakt on 2009-09-27
DeMus and others

Perhaps you should also know it is Intel not AMD and that I log in as a user not root. From what I've read there is no root account only temporary elevation to that status.

Otto

---

### Post by OttoDidakt on 2009-09-28
Streuth!

While you were sleeping I found [http://www.getdeb.net/search.php?keywords=boinc](http://www.getdeb.net/search.php?keywords=boinc)
which it says is for Jaunty 64 via Deb so I ran the three installation files for BOINC 6:4:5.

It seemed to be alright installing and appeared as 6:4:5 (including in Synaptic's list as the only installed BOINC) and yet after downloading all the work again it reported the result absent and computational errors!

I think the problem is connected to permissions or the folder it's in.

Help!
Otto

---

### Post by OttoDidakt on 2009-09-29
DeMus et all

Tullio spotted the problem (at [http://einstein.phys.uwm.edu/forum_thread.php?id=7596  ) ]("http://einstein.phys.uwm.edu/forum_thread.php?id=7596")
Even if you install 64 bit Linux on a 64 bit machine warnings won't come up when you install the 32 bit Einstein crunching suite. You have to install the right 32 bit libraries.

Using Tullio's sudo aptitude install ia32-libs didn't quite get all of them apparently so I tried sudo apt-get install ia32-libs libstdc++6 libstdc++5 freeglut3 from the link Gary included and now IT WORKS.

Otto

computational errors on 64 bit Linux

---

### Post by dino99 on 2009-10-05
> **chefbodini said:**
> Why not use the version built for your distro?

in fact, i'm trying to built a realtime system for a specific financial prog. My goal is to reduce latency.

---

