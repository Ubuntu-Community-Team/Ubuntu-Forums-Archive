---
title: "emachines m6807 screen dims during boot"
date: 2005-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by rmchan on 2005-04-25
This is driving me crazy.

Ubuntu hoary installed perfectly.  I installed it as test compared against my normal "testing" debian 32 bit version.  So far, everything works great - video (except 3d), sound, even ndiswrapper wireless!

The only problem that I see is that every time the machines boots up, as the kernel is firing up, my screen goes to its dimmest setting, so I have to whack the fn keys to bring it back to normal.

Anyone?

---

### Post by Vache on 2005-04-26
[QUOTE=rmchan]This is driving me crazy.

Ubuntu hoary installed perfectly.  I installed it as test compared against my normal "testing" debian 32 bit version.  So far, everything works great - video (except 3d), sound, even ndiswrapper wireless!

The only problem that I see is that every time the machines boots up, as the kernel is firing up, my screen goes to its dimmest setting, so I have to whack the fn keys to bring it back to normal.

Anyone?[/QUOTE]
 Hey, rmchan!

I am the proud owner of an Emachines M6805 (Our laptops are identical except yours has a DVDRW in place of my CDRW). I am using [Gentoo](http://www.gentoo.org) (They have, IMHO/experience, the best AMD64 support out of any of the distros). All that aside, I had the same issue with the laptop screen dimming on each boot. I was only able to fix it by turning off the monitor power management features in the kernel, which can only be done (to my knowledge) with a kernel recompile.  ](*,)  Our laptops have some special issues in regards to linux... Make sure you get the newest BIOS installed, or you'll run into all kinds of goofy power management issues! The bios is available right off Emachines' website, [www.e4me.com](http://www.e4me.com)

---

### Post by rmchan on 2005-04-26
[QUOTE=Vache]Hey, rmchan!

I am the proud owner of an Emachines M6805 (Our laptops are identical except yours has a DVDRW in place of my CDRW). I am using [Gentoo](http://www.gentoo.org) (They have, IMHO/experience, the best AMD64 support out of any of the distros). All that aside, I had the same issue with the laptop screen dimming on each boot. I was only able to fix it by turning off the monitor power management features in the kernel, which can only be done (to my knowledge) with a kernel recompile.  ](*,)  Our laptops have some special issues in regards to linux... Make sure you get the newest BIOS installed, or you'll run into all kinds of goofy power management issues! The bios is available right off Emachines' website, [www.e4me.com](http://www.e4me.com)[/QUOTE]


I had gentoo with amd64 running for a while, but I don't think I really need the "efficiency" to compile everything all the time (besides - I'm a long time debian user).  I use my lappy for work (I'm a developer), so having the machine chugging away compiling all the time slows me down!

Anyways, thanks for the pointer, I'll be recompiling a new kernel soon.

---

### Post by Tremblay on 2005-05-14
I also have an emachines m6805, same problem with Hoary (didn't have it with Warty), it appears to be due to a poor ACPI (see: [http://www.ubuntuforums.org/showthread.php?t=23179)](http://www.ubuntuforums.org/showthread.php?t=23179)), using option acpi=off with the boot kernel solves the problem (and creates a few more?) :P

Anyway, I was wondering what kind of performance you were getting out of your eMachines, FPS-wise. With ATI's drivers I'm getting 1321 with glxgears and 265 with fgl_gears. I've seen scores around 2500-3000 posted on these forums, and I'm wondering if I did something wrong or if that's the best I'll get from my laptop.

---

### Post by NoTiG on 2005-05-14
I would just like to mention that the 32 bit vs doesnt have this problem........

[QUOTE=Tremblay]

Anyway, I was wondering what kind of performance you were getting out of your eMachines, FPS-wise. With ATI's drivers I'm getting 1321 with glxgears and 265 with fgl_gears. I've seen scores around 2500-3000 posted on these forums, and I'm wondering if I did something wrong or if that's the best I'll get from my laptop.[/QUOTE]

Yesterday ... after i first installed the ati drivers (i installed the ones from the repository.... not from the ATI site)..... i got around 1321 fps.. i just ran it again though and now im getting 3400 for no reason . nothing changed..........

---

