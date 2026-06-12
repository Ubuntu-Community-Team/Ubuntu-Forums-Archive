---
title: "Very Poor performance"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by twade on 2008-12-02
My apologies if this is a repeat question, and my apologies if it is vague, I'll provide any info I can.

I've got an HP 6516b (Turion 64 X2, 2G ram, ati radeon xpress 1250 graphics).  I recently installed 64 bit Kubuntu 8.10 to replace the 32 bit Kubuntu 8.04 that I previously had (performed very well).  Unfortunately the performance is horrible.  I mean Vista on a Pentium I bad.  I've installed the fglrx driver.  the "Hardware Drivers" installer always crashed, so I ended up doing it from the command line (hopefully correctly).

Any help would be appreciated before I give up and drop back to 32 bit.

additional symptoms:
I should probably add that the fan is running continuously despite acpi -V only showing 32 deg C
also, the live CD was the same.  Very slow with very slow install

---

### Post by twade on 2008-12-02
fixed with the noapic boot option from this thread:
[http://ubuntuforums.org/showthread.php?t=964249](http://ubuntuforums.org/showthread.php?t=964249)

My apologies for the spam and for blaming my problems on 64 bit :p

---

