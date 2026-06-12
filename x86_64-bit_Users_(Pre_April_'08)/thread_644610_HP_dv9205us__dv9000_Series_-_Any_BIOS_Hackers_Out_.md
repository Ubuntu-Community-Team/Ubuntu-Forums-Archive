---
title: "HP dv9205us / dv9000 Series - Any BIOS Hackers Out There?"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilikenwf on 2007-12-19
I'm sick of these bios bugs on my dv9205us...I can't use lapic, which is really needed, as it would enable me to use high resolution timers for a greater amount of speed...

Does anyone here know of a generic phoenix bios that would work with my laptop that has all features enabled and isn't buggy, or is anyone here able to hack bios in such a way to fix whatever is causing so many linux users these issues?

I emailed HP, and got a friendly "screw off" email reply...[the whole thing is here]("http://www.mattparnell.com/projects/gee-thanks-hp...you-suck.html"), but here's my favorite line:

> HP does not recommend installing of Linux Operating System, it could not guarantee a high level of compatibility for all basic hardware and software components...

Whatever the case, if nothing else, we should get an opensource bios written for these laptops.

---

### Post by bluedragon436 on 2007-12-19
Along the lines of this...I have an HP desktop that I enjoy using but have since rebuilt it into a regular ATX case, and since I have not gotten any help from and have actually gotten some pretty rude replys from HP would like to continue to use the computer as I have it but get rid of the HP startup screen????  The only part of my curent computer that is from the original HP is the motherboard and processor...is there a way to get rid of the HP screen???  (other than just replacing the motherboard???)....sorry to hijack your thread that wasn't the reason for my post...I am just about past aggrivated by HP's lack of decent customer service...

---

### Post by jtucke21 on 2008-01-12
Get this...with their latest bios update HP has effectively blocked anyone out of even trying to run Ubuntu from the cd...Microsux must be paying HP some pretty nice kick backs, or ol Gates gives Hp's president awesome head or something...They won't even make the past bios versions avaliable! I'll never buy another damn HP. If I'm going to spend the money on something then by God I should be able to do with it what I'd like and not blocked out by a gd bios babysitter.
Does anyone out there have any of the previous bios versions saved where they could send them, I'd be tempted to pay...

jtucke21
dv9308nr
[email]jtucke21@gmail.com[/email]

---

### Post by ilikenwf on 2008-01-12
What model do you have? F.3D Works for me!

---

### Post by cubicsilver on 2008-01-14
i had to add noapic to boot the ubuntu cd but after install i havent had to add any arguments

---

### Post by ilikenwf on 2008-01-14
> **cubicsilver said:**
> i had to add noapic to boot the ubuntu cd but after install i havent had to add any arguments

Lucky! oh...if you get any irq errors, add the argument "noirqdebug" to silence them.

---

### Post by jtucke21 on 2008-01-24
Ok did you install under the f3d bios? if so what did you have to do, run the alternate cd? I have the dv9308nr with amd64x2 1.6ghz model. When I try to run the live cd it'll act like it's going to boot but just hangs and gives me a black screen and the disk drive stops reading. I've tried the regular and the versions for the 64x2 amd. Any help would be great, I'm about to just buy an asus lappy and call it quits cause asus won't try to void my warranty regardless of what os or softwares i run where hp tried to tell me installing linux would void the warranty

---

### Post by ilikenwf on 2008-01-25
> **jtucke21 said:**
> Ok did you install under the f3d bios? if so what did you have to do, run the alternate cd? I have the dv9308nr with amd64x2 1.6ghz model. When I try to run the live cd it'll act like it's going to boot but just hangs and gives me a black screen and the disk drive stops reading. I've tried the regular and the versions for the 64x2 amd. Any help would be great, I'm about to just buy an asus lappy and call it quits cause asus won't try to void my warranty regardless of what os or softwares i run where hp tried to tell me installing linux would void the warranty

Add noapic nolapic noirqdebug to the boot line...hit F6 to enter them.

---

