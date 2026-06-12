---
title: "My new system won't boot ubuntu"
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by matjosquig on 2008-04-17
I tried to boot a Ubuntu live CD.  It is the latest release version 7.10 for AMD 64 bit.  I put it in my new pc and booted from the CD.  It goes to a blank screen that says "Live Kernel" Ect but only has 2 lines.  Then i found a recommendation to add the argument acpi=off and then I get
> cpu0: MACHINE CHECK EXCEPTION                                   7 bank 3
Then some numbers and a line that say something like HARDWARE ERROR and another that says this is not a software problem.

System Specs:
> 
CPU:  AMD Phenom 9850 BE 2.5 Ghz
MOBO: Biostar TA700
2x2GB DDR2 800 ram
Geforce 8800GT
CD/DVD drive
WD 500 GB HD 7200 RPM


Everything is set to its factory default settings I haven't touched the BIOS other than to boot the CD.

I would really like some help solving this problem.  If any more information is needed just ask.

---

### Post by chewearn on 2008-04-18
Do you have any other OS you can test the machine with?

The error message is obvious: it's a hardware problem.  But the question is can you trust the message?  Thus, using another OS to verify.

Else, if you can try run memtest.

---

### Post by felker2 on 2008-04-18
Have you googled for it? I found these two URLs:

[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

> A Machine Check Exception, also called MCE, is a computer hardware error which occurs when a computer's central processing unit detects an unrecoverable hardware problem.

The error is usually due to failure or overstressing of hardware components where the error cannot be more specifically identified with a different error message. Diagnosing the error message can be difficult, although Intel Pentium processors do generate more specific codes which can be decoded by contacting the manufacturer.

MCEs require a restart of the system to continue normal operation and often indicate a long term problem of a general nature.

[http://lkml.org/lkml/2006/10/17/362](http://lkml.org/lkml/2006/10/17/362)

> You missed the blatantly obvious error message:
"This is not a software problem!"

Immediately followed by:
"contact your hardware vendor"

Please follow that advice

So to me this looks like a hardware error. Not a Ubuntu thing.

A few things to could try before you contact the supplier of your new hardware:
[LIST]
[*]Make BIOS-settings even safer.
[*]Remove a memory module
[*]Try "pci=nomsi irqpoll noapic acpi=off" as Ubuntu boot options.
[*]Try other hardware: other video hardware, disable onboard hardware
[/LIST]


HTH

---

### Post by matjosquig on 2008-04-18
Yea it is definately a hardware problem.  I tried to install XP and it froze halfway into loading the installer, and I also tried Solaris and it froze as well.  I will try the recommended solutions and repost with the results.

And what hardware vendor would I contact if that doesn't work?

---

### Post by HipShot on 2008-04-18
When you do resolve your hardware problem, be aware that you will be facing another issue with your video card, (8800GT).

You may want to download the alternate install CD or edit out "quiet splash" from the grub menu.

---

### Post by matjosquig on 2008-04-18
Ok I tried multiple different combinations of RAM and I still got the error.  I also tried running that command and I got the same results as before.  The only other video card I have is PCI and my computer won't boot without a PCI-E card inserted.  I don't know what else i could configure or remove. 

Are there any other solutions I could try or some way to determine which part is defective if one of them is because I still have a 30 day replacement guarantee on all the parts with about 23 days left.

I really appreciate all the help so for and would really like to figure this out.

---

### Post by HipShot on 2008-04-18
Try booting your machine with DMA addressing turned off in the bios.

Edited to add:

What is the output of your power supply? That looks like a hungry system.

---

### Post by cubeist on 2008-04-20
I don't think that mobo can support 125w amd quad-core 9850BE,
see this link

[http://anandtech.com/weblog/showpost.aspx?i=427](http://anandtech.com/weblog/showpost.aspx?i=427)

sorry mate...

---

### Post by him610 on 2008-04-20
[HTML]Are there any other solutions I could try or some way to determine which part is defective if one of them is because I still have a 30 day replacement guarantee on all the parts with about 23 days left.
[/HTML]

That paragraph was posted two days ago which means you now have only 21 days left out of your original 30 days. Within the 30 days (21 remaining for you) you will need to obtain an RMA, repackage the defective board, ship it back to the vendor who must receive it within the original 30 days.

It appears as if you have a defective board. You might want to make a decision at this point  and return the defective board without further delay. 

Good luck.

---

