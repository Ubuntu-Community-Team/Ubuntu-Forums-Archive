---
title: "Stuck at Install"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonyr1988 on 2007-01-05
I just upgraded my Desktop (new motherboard, RAM, graphics card, processor, etc.) and I went from 32-bit to 64-bit. I've never had a 64-bit machine before, so I'm a total n00b at this. Here are my trials:

I tried the Edgy AMD64 CD. The first time I booted it, it said "Loading Linux Kernel" and (very slowly...) went to 100%. Then it said:

> Decompressing Linux...

Invalid compression format (err=1)

-- System halted

I restarted and tried again. This time...the "Loading Linux Kernel" hit 100% much more quickly (about the same as all other times I've tried the LiveCD) and even went to the loading screen (although it was black / white instead of the regular brown colors). Then, the screen went completely blank. I waited well over 15 minutes and absolutely nothing happened.

I tried it with the Dapper AMD64 CD, with similar results.

I tried it with the Edgy AMD64 Alternate CD and got much further (partitioning and everything). However, I get to "Select and install software" and it freezes at 6%. It says "Please wait..." at the bottom. It's been stuck there well over 30 minutes.

Any ideas what I should do?

Should I try to re-burn the CDs? Although the LiveCDs were burned at 48x, I burned the alternate at 8x :) so that shouldn't be a problem.

If needed, I can supply more info about the machine. The basics are in my sig.

---

### Post by kebes on 2007-01-05
It could be a motherboard conflict. (Couldn't find your mb spec in your sig, so I can't be sure.) For some chipsets you need to boot with special kernel flags (like "noapic" or whatever). The details depend on your motherboard...

---

### Post by tonyr1988 on 2007-01-05
I figured I'd have some sort of problem, changing everything at once. :) Then again, my graphics card, RAM sticks, and processor weren't compatible with my new motherboard, so I decided to do it all at the same time. :) What should I specifically be looking for? The chipset is nVIDIA nForce4, and I've got all the other specs with me. Should I try noapic and just experiment with different ones? Should I stick with LiveCDs or the alternate CD?

---

### Post by tonyr1988 on 2007-01-05
Tried booting Edgy LiveCD with noapic and nolapic

Same error as the first time..."invalid compreed format --system halted"

---

### Post by kebes on 2007-01-05
Well of course it's different for each different motherboard. However there's no harm (that I'm aware of) in trying to boot with different kernel options and just "seeing what happens." Like I said it's a good idea to do searches on the exact model number for your motherboard on various forums. Also a good idea is to check any error messages from the kernel.

Some options that have been helpful in the past:

acpi=off
noapic
nolapic
all-generic-ide
pci=nommconf
irqpoll


You can try those (in various combinations!) and see what happens. As I recall some of the issues with nForce series have to do with BIOS power management, which is why "noapic" sometimes fixes it. (See also BIOS options.)

Other things to try are to flash the BIOS to the latest version (sometimes the manufacturer has fixed a serious bug that is preventing the boot). Also you should check the options in your BIOS... maybe disabling something will make it suddenly work.

In the past I've found the Alternate CD works better for these things because it is 'simpler' so you avoid at least some possible issues.


Another thing to think about (since this is a whole new system with new components) is weird hardware compatibility issues. For instance awhile back I was building a new computer and put some nice OCZ RAM into an ASUS motherboard... but it turned out that the OCZ ram required a high voltage (2V), whereas the motherboard wouldn't consistently supply above 1.7V. Switched to different RAM (equally good, but able to run at lower voltage) fixed the problem immediately.

So it's worth (for instance) doing a memtest to see what happens. Also worth taking out a RAM chip (if you have two) and see if that makes a difference... or unplugging various devices/cards and seeing what happens.


Sorry no definate answers for you... just some things to try. Good luck.

---

### Post by tonyr1988 on 2007-01-05
One more update: I tried it in VMWare (under WinXP...eek) and it worked perfectly. I still see the ugly black / white loading screen, but everything else works like a charm. Any clue why that happens? Could something be wrong with my graphics card?

---

### Post by tonyr1988 on 2007-01-05
Thanks for all the info! :)

I'm trying to do searches for this motherboard, but so far I haven't found anything (it's a Mach Speed MSNV-939). It also doesn't look like there are any BIOS updates for it.

I'm trying different combos for boot options right now - most of them give me the black/white loading screen and then go blank (on the LiveCD). Should I try those same boot options for the alternate CD? I assumed apic, etc. had to do with the display, which wasn't a problem for the alternate.

As far as hardware compatibility...everything seems to work fine under WinXP - does that mean anything?

I'm also going to start trying some other LiveCDs I've got and see if I can get anything to work.

---

### Post by kebes on 2007-01-05
> **tonyr1988 said:**
> One more update: I tried it in VMWare (under WinXP...eek) and it worked perfectly. I still see the ugly black / white loading screen, but everything else works like a charm. Any clue why that happens? Could something be wrong with my graphics card?

Sorry I don't understand? You tried ~what~ in VMWare? Do you mean you tried using the CD in a virtual machine and it installed?

Do you mean that you have WinXP running on the computer? (That you can't install Edgy to...)

EDIT: sorry our posts crossed each other! So since XP works on the new hardware that makes a hardware conflict unlikely... I would still recommend trying the Alternate CD with the options mentioned.

---

### Post by tonyr1988 on 2007-01-05
Yeah, I've got WinXP on my desktop (that I'm having problems with) and I don't see any obvious hardware problems.

I tried the Edgy AMD64 LiveCD iso in VMWare under WinXP, and it installed / runs perfectly. (I didn't use the actual CD...only the .iso, so there is a potential for problems during burning - but on all 3 CDs?)

I'll keep trying different options throughout the day. Thanks for all the help, kebes - I wouldn't know where to start without your posts.

---

### Post by tonyr1988 on 2007-01-05
Sorry to keep replying to this with short snippets, but I may be (close to) finished getting Ubuntu to work.

I'm doing the alternate AMD64 CD with noapic and nolapic, and it's installing software at the 45% mark, whereas it would always get stuck at 6% (I tried several times in the past, and it'd always get stuck at the same spot).

It already partitioned everything alright and installed the core components. IIRC, once the software is installed, I put GRUB on there (shouldn't be any problems) and boot into my fresh Ubuntu! :)

Thanks for the tips again....hopefully everything works alright.

---

