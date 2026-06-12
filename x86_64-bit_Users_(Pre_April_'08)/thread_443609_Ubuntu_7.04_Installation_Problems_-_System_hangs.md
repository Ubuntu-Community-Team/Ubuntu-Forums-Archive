---
title: "Ubuntu 7.04 Installation Problems - System hangs"
date: 2007-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by BU_ on 2007-05-14
Hello everybody,

I have a laptop Asus A6Kt based on AMD Turion 64 MT Processor.

I downloaded Ubuntu 7.04 (ubuntu-7.04-desktop-amd64.iso).

I successfully verified the md5 sum of the .iso file and burned it on CD-RW.

Then I try to boot from it. Boot is successful, and I see boot menu.

My problem is that when I choose ANY option from it my system hangs up after

 kernel alive
*The next long line is shown on the display* (also something related with kernel)
-===SYSTEM HANGS UP===- :confused: 

Can somebody help me to solve this issue?

Thank you!

---

### Post by keithching on 2007-05-15
choose the option that lets you edit the boot line.
try acpi=off in the kernel line, that worked for me

ie.
kernel   /vmlinuz-2.6.8.1-3-386 xxxxxxxx ro quiet splash acpi=off

---

### Post by BU_ on 2007-05-15
Thx a lot, that worked, and it tried to do something, but...

First I got an error message from the X server

Then I got the following:
[  212.205189] bcm43xx: Error: microcode "bcm43xx_microcode5.fw" not available or load failed

And then I was thrown into the dark console like "ubuntu@ubuntu:"

So I suppose I am able to enter commands (only if I knew some :confused: ) and constanly the errortext mentioned above appears on the screen after some interval.

Can someone advise what to do next? :) 

P.S.: I checked my installation disk again and it was ok.

---

### Post by ac3buddy on 2007-09-14
hi i got the same error message. how shouuld i resolve it

---

### Post by praxis22 on 2007-09-15
Can you run the command **lspci**

Sounds like you a have firmware driver problem.

---

### Post by PypeBros on 2007-09-15
> **keithching said:**
> choose the option that lets you edit the boot line.
try acpi=off in the kernel line, that worked for me

ie.
kernel   /vmlinuz-2.6.8.1-3-386 xxxxxxxx ro quiet splash acpi=off

tried that, and suddenly i see some message about 8254 not supported (or something) by IO-APIC ... hmm hmm ...

still, it seems to be a benign issue. i can _at least_ run the install/live CD on my nforce410+Geforce6100 mobo ^_^
(ps: i tried noapic before that, but it was of no help for me. acpi=off seems to have done the trick).

---

