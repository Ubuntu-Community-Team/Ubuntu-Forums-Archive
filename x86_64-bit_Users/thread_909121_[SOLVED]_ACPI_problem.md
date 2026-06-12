---
title: "[SOLVED] ACPI problem"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2008-09-03
Every time I'm starting Ubuntu I always have to boot with the *acpi=off* option. If I don't I end up with the busybox thing and nothing happens. 

What is a probable reason for this? 

What can I do to avoid having to enter grub and edit the boot options every time i start my PC?

I'm running Ubuntu Desktop Edition 8.04.1 (64-bit) and I have a computer with:

CPU: Intel Core 2 Duo E8400
Motherboard: Abit IX38 QuadGT
RAM: 2 GB Corsair DDR2 800 MHz
GPU: NVIDIA 8800GTX

I greatly appreciate all good replies.

PS: I'm new to Linux, so all instructions have to be step by step...

---

### Post by Gabt on 2008-09-03
You could edit the boot line and permanently append acpi=off to it.
Or turn ACPI off in the bios, but remember your windows install (if u have one) will most likely need it. Had same problem but with gentoo linux (my acpi works on ubuntu) and i turned acpi in the bios off, then windows gave me that lovely blue screen it has built in. I would say adding acpi=off is the most practical idea.

[ACPI](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

---

### Post by IntuitiveNipple on 2008-09-03
> **Linux user 66 said:**
> Every time I'm starting Ubuntu I always have to boot with the *acpi=off* option. If I don't I end up with the busybox thing and nothing happens. 

What is a probable reason for this? 

Hi '66.

Would you please make a report in the [Ubuntu bug-tracker](https://bugs.launchpad.net/ubuntu/+source/linux). Make the title of the bug-report "ACPI: Abit IX38 QuadGT fails to boot without acpi=off". The package the bug is in will be **linux** (that's the kernel itself).

In the description give a description of the problem and information about your PC as you have here but in addition attach the reports requested in this [Ubuntu Kernel Team Bug Reports](https://wiki.ubuntu.com/KernelTeamBugPolicies) Wiki help page. Follow the instructions in the section "Minimal information" initially, and we'll ask for additional information once we've had a chance to examine the issue.

Once you've submitted the bug subscribe the Kernel ACPI Team to it, using the link on the right side of the page "Subscribe someone else" and enter "ubuntu-kernel-acpi". That'll ensure I and others get an email notification so we can take a look.

---

### Post by Eren on 2008-09-03
use vga=771 parameter at menu.lst file for this. i use this too. temporary solution.

---

### Post by Linux user 66 on 2008-09-03
Thanks for your suggestion, Gabt. However, I don't know how to *permanently* append *acpi=off* to the boot line. Some instruction would be much appreciated =)

---

### Post by Linux user 66 on 2008-09-03
> **IntuitiveNipple said:**
> Hi '66.

Would you please make a report in the [Ubuntu bug-tracker](https://bugs.launchpad.net/ubuntu/+source/linux). Make the title of the bug-report "ACPI: Abit IX38 QuadGT fails to boot without acpi=off". The package the bug is in will be **linux** (that's the kernel itself).

In the description give a description of the problem and information about your PC as you have here but in addition attach the reports requested in this [Ubuntu Kernel Team Bug Reports](https://wiki.ubuntu.com/KernelTeamBugPolicies) Wiki help page. Follow the instructions in the section "Minimal information" initially, and we'll ask for additional information once we've had a chance to examine the issue.

Once you've submitted the bug subscribe the Kernel ACPI Team to it, using the link on the right side of the page "Subscribe someone else" and enter "ubuntu-kernel-acpi". That'll ensure I and others get an email notification so we can take a look.

Will do. Do you have anything else to suggest?

---

### Post by IntuitiveNipple on 2008-09-03
> **Linux user 66 said:**
> Will do. Do you have anything else to suggest?
Once we can see the details we'll be in a position to figure out a solution. Right now I'd suggest stocking up on coffee and sleep in preparation for the debugging :)

---

### Post by IntuitiveNipple on 2008-09-03
> **Linux user 66 said:**
> Thanks for your suggestion, Gabt. However, I don't know how to *permanently* append *acpi=off* to the boot line. Some instruction would be much appreciated =)
Use the Text Editor to open the GrUB boot menu:
```

gksudo gedit /boot/grub/menu.lst

```
Scroll down towards the end where you'll find the kernel entries. They'll look something like this:
```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/VGencrypted-root ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

```
Edit the line beginning "kernel", adding the kernel command-line options you need at the end, so in this example it would become:
```

kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/VGencrypted-root ro quiet splash acpi=off

```
Save the file. Next time the system boots that option will be used.

---

### Post by Linux user 66 on 2008-09-03
> **IntuitiveNipple said:**
> Once we can see the details we'll be in a position to figure out a solution. Right now I'd suggest stocking up on coffee and sleep in preparation for the debugging :)

Alright. Thank you for your time :)

---

### Post by Linux user 66 on 2008-09-03
> **IntuitiveNipple said:**
> Use the Text Editor to open the GrUB boot menu:
```

gksudo gedit /boot/grub/menu.lst

```
Scroll down towards the end where you'll find the kernel entries. They'll look something like this:
```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/VGencrypted-root ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

```
Edit the line beginning "kernel", adding the kernel command-line options you need at the end, so in this example it would become:
```

kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/VGencrypted-root ro quiet splash acpi=off

```
Save the file. Next time the system boots that option will be used.

Thanks for the detailed instruction!

---

### Post by clubsoda on 2008-09-04
A bit quick with the "SOLVED" tag, no?
I have a similar problem with an older machine (Napoli Trigem, not AMD 64 but I doubt that's relevant) and kernel 2.6.24-21.  Removing "quiet" and "splash" from the boot options I can see the machine hangs in an infinite loop with something like ```
ACPI Error (evgpe-0705): No handler or method for GPE
```
ACPI was working on this machine as recently as kernel 2.6.22-14.

Moreover, Eren's suggestion of adding "vga=771" works without having to disable acpi.  Why should the graphic mode have anything to do with it?

I'm going to try vga=792 next, see if I can get the XFCE running rat into the centre of the screen at 1024x768.

---

### Post by IntuitiveNipple on 2008-09-04
> **Eren said:**
> use vga=771 parameter at menu.lst file for this. i use this too. temporary solution.
**Eren**, could you add a comment [to the bug report](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/264358) and include the output of
```

lsusb

lspci -nn

```
**clubsoda**, can you do the same please?

I want to collect a list of affected hardware to determine if there is a common component causing this.

---

### Post by Eren on 2008-09-04
> **clubsoda said:**
> A bit quick with the "SOLVED" tag, no?
I have a similar problem with an older machine (Napoli Trigem, not AMD 64 but I doubt that's relevant) and kernel 2.6.24-21.  Removing "quiet" and "splash" from the boot options I can see the machine hangs in an infinite loop with something like ```
ACPI Error (evgpe-0705): No handler or method for GPE
```
ACPI was working on this machine as recently as kernel 2.6.22-14.

Moreover, Eren's suggestion of adding "vga=771" works without having to disable acpi.  Why should the graphic mode have anything to do with it?

I'm going to try vga=792 next, see if I can get the XFCE running rat into the centre of the screen at 1024x768.

i don't know any idea too. when i'm using arch linux i must add the vga=771 line too. i think it's kernel based maybe or bios needs an update but, yeah we got a big but :)


> **IntuitiveNipple said:**
> **Eren**, could you add a comment [to the bug report](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/264358) and include the output of
```

lsusb

lspci -nn

```
**clubsoda**, can you do the same please?

I want to collect a list of affected hardware to determine if there is a common component causing this.
ok bro, i add this outputs there.

---

### Post by clubsoda on 2008-09-05
Arrggh, this is gettin' ugly.
I'm finding that the "vga=" trick isn't reliable on cold starts, only reboots.
To ensure a boot on first power-up my best bet is a previous kernel or to disable ACPI.  After that I can reboot into the 2.6.24-21 kernel using vga=***.

---

### Post by go_beep_yourself on 2008-09-15
To make it anything permanent, it should be put after defoptions= in the menu.lst, or else the those options you had to the kernel line will be lost when a new kernel is installed (update-grub runs). After adding to defoptions, you should run sudo update-grub, and then you will see it in the kernel line too. For example, I changed mine

# defoptions=splash quiet

to this

# defoptions=splash vga=791

---

### Post by clubsoda on 2008-09-16
My booting reliability has improved to over 80%, still using the vga=*** trick.  I think the improvement was achieved by checking the "Save session for future logins" box when shutting down.

However, I have another problem which appears to be ACPI related.  If I do a normal shutdown from Xubuntu my LCD screen becomes locked in standby mode (orange LED) and will not fire up automatically on the next boot nor respond to a manual press of its power button.  The only way to revive the screen then is to unplug it from the power momentarily.  
I can avoid this lockup by switching the monitor off before shutting down or by using an earlier kernel version.

Edit: Oh, and the 2.6.24-21-generic kernel breaks Xubuntu's "Quit" command in the Applications menu too.  Strangely, the panel "Quit" button still works as normal.

---

