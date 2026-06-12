---
title: "External screen + sleep on a PowerBook 6,8 12&quot;"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by pau on 2005-12-17
Hi,

so... I got a brand new powerbook 12" from my institute but cannot stand MacOSX... I gave fink + ports a chance but it's too widgy for me and I hate the terminal they have... Installing the ports takes ages and the result is not nice and fragile...

I want GNU/Linux on my ppc box.

Now I am working from an ubuntu installation (breezy) but have two main problems:

1- An external screen will not work (at least I tried to give a talk and the video projector was not showing anything)

2- Sleep is not working

Let's put it in this way: I'd be happy if the external screen would work on GNU/Linux . I need this for my work. Sleep is not so important, but would be nice yet, of course

/proc/cpuinfo


```
 processor   : 0
 cpu      : 7447A, altivec supported
 clock    : 749MHz
 revision : 0.5 (pvr 8003 0105)
 bogomips : 747.52
 machine     : PowerBook6,8
 motherboard : PowerBook6,8 MacRISC3 Power Macintosh
 detected as : 287 (PowerBook G4 12")
 pmac flags  : 0000001a
 L2 cache : 512K unified
 memory      : 1280MB
 pmac-generation   : NewWorld
```


Please please help me and tell me it's possible...

I have also been trying to have a look at dapper but the cd will not boot... Even with the alternative option given at boot

thanks,

Pau

---

### Post by pau on 2005-12-19
bump...

---

### Post by pauljwells on 2005-12-19
Sorry Pau

I have the same hardware and I'm afraid to tell you that neither sleep nor external display are supported (yet). Both are down to the fact that there are no nvidia linux ppc drivers. You don't get 3D accel either for the same reason. Don't throw away OSX just yet. 

As a work around for external display I use (I hate to say it) Virtual PC on OSX (yes, M$) with Ubuntu loaded. This is in addition to dual-booting OSX and ubuntu

I think that with Qemu you might be able to run a virtual ubuntu machine on top of OSX (rather than the painfully slow emulated one in VPC), which would be a better work-around. I haven't tried this yet but I plan to soon.

welcome to the 'niche'!

BTW, if you 'hate' OSX so much you can always run X11 in rootless mode and run Gnome or KDE as your WM. You can get away from most of the OSX specific incompatibilities by installing onto a unix format drive instead of HFS+, so you get proper treatment of upper/lower case. Again, not something I've tried (As I love OSX ;)) but have a go and post your results...

---

### Post by pau on 2005-12-19
[QUOTE=pauljwells]

I think that with Qemu you might be able to run a virtual ubuntu machine on top of OSX (rather than the painfully slow emulated one in VPC), which would be a better work-around. I haven't tried this yet but I plan to soon.

welcome to the 'niche'!

BTW, if you 'hate' OSX so much you can always run X11 in rootless mode and run Gnome or KDE as your WM. You can get away from most of the OSX specific incompatibilities by installing onto a unix format drive instead of HFS+, so you get proper treatment of upper/lower case. Again, not something I've tried (As I love OSX ;)) but have a go and post your results...[/QUOTE]

Aaaaargh... these are BAD news...

Can you please elaborate a bit more on this rootless thing? Gnome or KDE are not just WM but meta-thingies and a pain in the neck to install via fink... not to say impossible to install at all

So you suggest to give the disk an ext3 format, for instance? Would this help the copy and paste issue, for example?

---

### Post by pauljwells on 2005-12-19
When you are running Apple's X11 app you press cmd-a (if I remember correctly) and it sets the X11 window to completely obscure the aqua one, then you can fire up gnome (exec gnome-session) or kde (startkde) from the xterm and it gives you something that looks like linux did three years ago :/

You are still crippled by the number of packages that are ported to OSX.

You can't use ext2/3 formats with OSX - you have the choice of HFS+ or UFS. If you use UFS there are some bits of OSX that don't work, or at least not as well as with HFS+, but in HFS, files like, for example, Make and make are the same file, whereas with UFS Make and make are different  HFS+ is case preserving, but not case sensitive, whereas UFS is case preserving and case sensitive. What this means is that using UFS can often make porting apps from other unix flavours to OSX a much simpler job, but you probably still end up having to hack at source code...

For me, I have found the best solution to our problem to be this:

Buy an external firewire drive
Install Carbon-Copy-Cloner (free OSX program)
use CCC to backup your OSX partition to the external drive
Reformat the PB drive to two partitions - OSX (HFS+) and the rest free space. The free space should be the first partition.
Boot up from the firewire drive and use CCC to copy back your OSX install to the PB
Install Ubuntu on the freespace (it formats this as ext2)
Install the ext2/3 file support in OSX 'system preferences' app (from sourceforge). This lets you mount the ubuntu / directory in OSX so you can move files from one partition to the other.
Use ubuntu for all your real work (what it's good at), copy what you need to present over to the OSX partition and use OSX to run pretty graphics shows.

OSX is unbeatable at presentations and the dual screen support is excellent. Take advantage of both systems. The only thing you can't do is show stuff actually running on ubuntu, unless you go the VPC or Qemu route.

I'm afraid that by running linux on a mac you have set out on a difficult route!

---

### Post by pau on 2005-12-19
Hi pauljwells,

[QUOTE=pauljwells]When you are running Apple's X11 app you press cmd-a (if I remember correctly) and it sets the X11 window to completely obscure the aqua one, then you can fire up gnome (exec gnome-session) or kde (startkde) from the xterm and it gives you something that looks like linux did three years ago :/[/QUOTE]

right, but I find it extremely difficult to have a fully functional gnome desktop with the fink packages... the dependencies are not fully solved and the gnome-terminal is not woring... KDE is not listed anymore on fink

[QUOTE=pauljwells]
You are still crippled by the number of packages that are ported to OSX.

You can't use ext2/3 formats with OSX - you have the choice of HFS+ or UFS. If you use UFS there are some bits of OSX that don't work, or at least not as well as with HFS+, but in HFS, files like, for example, Make and make are the same file, whereas with UFS Make and make are different  HFS+ is case preserving, but not case sensitive, whereas UFS is case preserving and case sensitive. What this means is that using UFS can often make porting apps from other unix flavours to OSX a much simpler job, but you probably still end up having to hack at source code...[/QUOTE]

this sounds a bit strange to me... but I believe you mate... Can you be a bit more precise about the "some bits of OSX that don't work"?

[QUOTE=pauljwells]
Use ubuntu for all your real work (what it's good at), copy what you need to present over to the OSX partition and use OSX to run pretty graphics shows.

OSX is unbeatable at presentations and the dual screen support is excellent. Take advantage of both systems. The only thing you can't do is show stuff actually running on ubuntu, unless you go the VPC or Qemu route.

I'm afraid that by running linux on a mac you have set out on a difficult route![/QUOTE]

yes, indeed...

but you didn't get my point... I do need the external screen for my work, because I spend about 10 hours per day in front of a pc, which will be this PPC laptop, but it happens to be a 12" one and I don't feel like burning out my eyes, so I WANT an attached external screen to it... I have a big one close to it, on my desk, and I would like to use it... with ubuntu... but it seems impossible now...

](*,)

---

### Post by pauljwells on 2005-12-20
I'm afraid I've pretty much reached the limit of my knowledge on all this. You'll have to look around the forums to get further. One thing is for sure though, at the moment you cannot get your PowerBook to power an external screen with Ubuntu :( Sorry...

---

### Post by dombleu on 2006-01-06
Is there any ongoing project to get this video card working under linux PPC?

---

