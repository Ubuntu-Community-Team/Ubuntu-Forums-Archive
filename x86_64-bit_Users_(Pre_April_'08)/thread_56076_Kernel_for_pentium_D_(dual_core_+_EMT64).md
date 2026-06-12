---
title: "Kernel for pentium D (dual core + EMT64)"
date: 2005-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kikoolol on 2005-08-11
Hi everybody !

I would like to know which smp kernel I have to use for a pentium D (to enable both cores) on a 64 bits ubuntu install (I'm posting on this subforum because it's 64 bits related, sorry if it was a wrong idea  :razz: ).

Thanks for your replies !

Kikoolol \o/

---

### Post by nocturn on 2005-08-11
[QUOTE=Kikoolol]Hi everybody !

I would like to know which smp kernel I have to use for a pentium D (to enable both cores) on a 64 bits ubuntu install (I'm posting on this subforum because it's 64 bits related, sorry if it was a wrong idea  :razz: ).

Thanks for your replies !

Kikoolol \o/[/QUOTE]

I think you'll need an smp kernel for dual cores, can anyone confirm this?

---

### Post by Kikoolol on 2005-08-11
Yes, I need a smp kernel but I don't know which one, according to my 64 bits architecture (because the ubuntu 64 bits distro is called the AMD64 version, so I'm a little bit confused with the names of kernel packages !).

---

### Post by DancingSun on 2005-08-11
I believe EMT64 is essentially AMD64 as Intel licensed the x86_64 technology from AMD (IIRC).  It just has to be named differently, probably because of company pride and marketing concerns.

---

### Post by Kikoolol on 2005-08-11
Okay, but concerning the kernel, things are not very clear for me. Here are the possible packages on the repos :

linux-image-2.6.10-5-686-smp_2.6.10-34.3_i386.deb <--- 32 bits archi ?
linux-image-2.6.10-5-amd64-k8-smp_2.6.10-34.3_amd64.deb <-- for amd k8 processors ?

So which one ... (or others ?)  ](*,)  it's so complicated !  :wink:

---

### Post by DancingSun on 2005-08-11
Hmm, you probably be safer to use the generic AMD64 kernel...but I don't see the smp version of that in Synaptic...

You might want to do a search on the forums for your processor, and see if anybody else is successfully running Ubuntu on it.

Edit:
[This](http://ubuntuforums.org/showthread.php?t=49368&highlight=dual+core) might be helpful, even though it's a thread about AMD64.  At the very end of that thread, somebody posted that the CPU is too new and will need a newer (2.6.12) kernel to utilize the 2 cores.

---

### Post by tseliot on 2005-08-12
I guess the appropriate architecture would be IA64 (as it is Intel based), maybe with smp in your case. Have you added all the repositories in your /etc/apt/sources.list from the Ubuntu Unofficial starter guide AMD64?

You shoud find the right kernel in the Universe repositories (just open Synaptic after having set up all the repositories and use "search" to find the right kernel)(or just type "linux" in the search field), it should be something like this "linux-image-2.6.11-1-[COLOR=Red]itanium-smp[/COLOR]" .

Remember NOT TO UNINSTALL your previous kernel so as to switch back to it in case anything goes wrong (it's just a precaution).

Tell me if it worked for you.

Alberto


P.S. I have an AMD64, I've never used an EMT64 so maybe I'm wrong. So USE THIS AT YOUR OWN RISK.

---

### Post by Kikoolol on 2005-08-12
Thanks for your answers. In fact I'll get this config very soon ! I was just gathering information about my new hardware, I was using a Kubuntu Hoary on my previous PC. I first didn't know if I was going to install a 32 bits or a 64 bits kubuntu version (with a dchroot to run 32 bits-only applications). By the way, any suggestions about this, is 64 bits version worth it ?

Then, this kernel matter ... well I think I'll install my kubuntu first then deal with it later ! But if I can't enable both cores ... that's sucks ! Maybe I'll eventually have to download the source of the kernel and compile it, but using a binary package would be easier !

Wait & see ...  :-P

---

### Post by Kikoolol on 2005-08-12
Huum, found this on [http://packages.debian.org](http://packages.debian.org) :

Package kernel-image-2.6-em64t-p4-smp

    * stable (base): Linux kernel image for version 2.6 on Intel EM64T SMP systems
      103: amd64 i386

I think I need this kind of stuff ! But I can't find it on the ubuntu repositories ... can I use the debian package instead ?

---

### Post by DancingSun on 2005-08-12
[QUOTE=tseliot]...it should be something like this "linux-image-2.6.11-1-[COLOR=Red]itanium-smp[/COLOR]"...[/QUOTE]
EMT64 is different from the Itanium 64-bit architecture!  Itanium uses the IA64 architecture, which is very different from the x86 design!  You'll need to look for either the kernel for amd64-**generic** or amd64-**xeon**.  But like I said, I don't see a smp version of these kernel available in Synaptic, so you might end up having to compile one yourself...which is out of my knowledge range :-P

---

### Post by tseliot on 2005-08-12
[QUOTE=DancingSun]EMT64 is different from the Itanium 64-bit architecture!  Itanium uses the IA64 architecture, which is very different from the x86 design!  You'll need to look for either the kernel for amd64-**generic** or amd64-**xeon**.  But like I said, I don't see a smp version of these kernel available in Synaptic, so you might end up having to compile one yourself...which is out of my knowledge range :-P[/QUOTE]

Thanks for making things clear :) 

However if you want to compile a kernel there's a very good (and easy) guide right here:
[http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065) 

Download Ubuntu kernel sources in Synaptic and follow th instructions of the guide.

In addition you can use the command (instead of compiling and configuring the kernel from scratch):

"sudo make oldconfig" (so as to keep all the settings of  your current kernel and to save a lot of time)

and then just edit the configuration (following the instructions) (e.g. by using "sudo make menuconfig") and look for "smp" and "EMT64" architecture.

It's very easy (and satisfying ;-) )

---

### Post by Kikoolol on 2005-08-12
Okay ! Thanks for your great help. I'll post on this thread when I can run some tests !

---

### Post by Kikoolol on 2005-08-14
Hmmm, guess I found it ([http://packages.ubuntu.com](http://packages.ubuntu.com)) :

Package kernel-image-2.6.11-9-em64t-p4-smp

    * breezy (base): Linux kernel image for version 2.6.11 on Intel EM64T SMP systems [universe] 

It's named kernel-image, not linux-image as usual :) now let's try it !  \\:D/

---

### Post by tseliot on 2005-08-14
Are you sure you want to use a breezy kernel? They might have some issues (I know it because I used them). Why don't you compile a kernel from Ubuntu Hoary kernel sources?

It's very easy, try my guide for newbies and choose the right architecture (everything it's explained in my HOWTO), it's here, have a look:

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by kondor on 2005-08-14
[QUOTE=Kikoolol]Hmmm, guess I found it ([http://packages.ubuntu.com](http://packages.ubuntu.com)) :

Package kernel-image-2.6.11-9-em64t-p4-smp

    * breezy (base): Linux kernel image for version 2.6.11 on Intel EM64T SMP systems [universe] 

It's named kernel-image, not linux-image as usual :) now let's try it !  \\:D/[/QUOTE]

Kikoolol: Let us know what you do and how it worked. I just got a box with the Intel dualcore and I am  curious. I am particularly interested in any liabilities that might pop up with the 64-bit kernel versus the regular SMP kernel. I think on the Win64 side there are serious driver problemos. Also, I think I read just the other day that Redhat has released an "optimized" kernel for the Intel dual-core but I can't remember where I read it. Don't know just what changes they incorporated but I think the Intel product is a bit different than AMD 64bit. I got a media edition so it will be awhile before I surrender it to Linux. I need to be sure that all the junk on this thing works under Linux. I have other boxes for Linux.  Thanks! :razz:

---

### Post by Kuolio on 2005-08-17
[QUOTE=kondor]Kikoolol: Don't know just what changes they incorporated but I think the Intel product is a bit different than AMD 64bit. I got a media edition so it will be awhile before I surrender it to Linux. I need to be sure that all the junk on this thing works under Linux. I have other boxes for Linux.  Thanks! :razz:[/QUOTE]

Intel added one 64bit processor-command more than AMD64 uses. One command, geeeezzz.. well, it would have kinda sucked for intel to just hop-on for a 100% amd ride, so they made one processor call of their own :D Maybe RH has specialy "tweaked" kernel to use that ONE freeking processor command  ](*,)

---

### Post by cmgustavo on 2006-01-23
[QUOTE=Kikoolol]Hmmm, guess I found it ([http://packages.ubuntu.com](http://packages.ubuntu.com)) :

Package kernel-image-2.6.11-9-em64t-p4-smp

    * breezy (base): Linux kernel image for version 2.6.11 on Intel EM64T SMP systems [universe] 

It's named kernel-image, not linux-image as usual :) now let's try it !  \\:D/[/QUOTE]

I installed by synaptic the package kernel-image-2.6.11-9-em64t-p4-smp, but it not run :(

I had a message that can't mount /dev/sda6 that is where is the root.

My grub configuration is:

title           Ubuntu, kernel 2.6.11-9-em64t-p4-smp Default
root            (hd0,1)
kernel          /vmlinuz root=/dev/sda6 ro quiet splash
initrd          /initrd.img
boot

I don't know why don't run, becouse the F6 term see a prompt, and I did:

# cat /proc/cpuinfo

And I got 2 (two) processors with flags lm (em64t)

My cpu is an Intel 630 3.0ghz.

Gustavo

---

### Post by oleoleole on 2006-01-24
[QUOTE=cmgustavo]I installed by synaptic the package kernel-image-2.6.11-9-em64t-p4-smp, but it not run :(

I had a message that can't mount /dev/sda6 that is where is the root.

My grub configuration is:

title           Ubuntu, kernel 2.6.11-9-em64t-p4-smp Default
root            (hd0,1)
kernel          /vmlinuz root=/dev/sda6 ro quiet splash
initrd          /initrd.img
boot

I don't know why don't run, becouse the F6 term see a prompt, and I did:

# cat /proc/cpuinfo

And I got 2 (two) processors with flags lm (em64t)

My cpu is an Intel 630 3.0ghz.

Gustavo[/QUOTE]

Well, the kernel runs, but there something about mounting of partitition. Check if the FS is loaded in modules, i guess ext3 and almost all FS types are module-based. 
You need to make an initrd: 
sudo mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp
or something, and you must load it in grub (I see it's already loads initrd, but maybe it's not working with new kernel).

I don't know if this helps, but you can give it a try.

---

### Post by cmgustavo on 2006-01-24
I don't know what happened.

I delete initrd.img-2.6.11-9-em64t-p4-smp from /boot and i excecute mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp, but this not create anything and saw the follow message:

> root@nippur:/boot# mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp
find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

In the /lib/modules/2.6.11-9-em64t-p4-smp there are almost all the same modules that my stable 2.6.12-10-amd64-generic, but ext3 modules is there!

I don't know the problem, but i compile the source kernel and try it.

---

### Post by cmgustavo on 2006-01-24
I don't know what happened.

I delete initrd.img-2.6.11-9-em64t-p4-smp from /boot and i excecute mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp, but this not create anything and saw the follow message:

> root@nippur:/boot# mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp
find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

In the /lib/modules/2.6.11-9-em64t-p4-smp there are almost all the same modules that my stable 2.6.12-10-amd64-generic, but ext3 modules is there!

I don't know the problem, but i compile the source kernel and try it.

---

### Post by cmgustavo on 2006-01-24
I don't know what happened.

I delete initrd.img-2.6.11-9-em64t-p4-smp from /boot and i excecute mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp, but this not create anything and saw the follow message:

> root@nippur:/boot# mkinitrd -o initrd.img-2.6.11-9-em64t-p4-smp
find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -mindepth option after a non-option argument -type, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

In the /lib/modules/2.6.11-9-em64t-p4-smp there are almost all the same modules that my stable 2.6.12-10-amd64-generic, but ext3 modules is there!

I don't know the problem, but i compile the source kernel and try it.

---

### Post by 76thParadox on 2006-02-19
I also have an Intel Pentium D (sitting inside a HP xw4300) and things are running quite well with the amd64-k8-smp kernel that is provided by Ubuntu.  You need to change over to this SMP kernel after install but asside from that all is running very well.

---

