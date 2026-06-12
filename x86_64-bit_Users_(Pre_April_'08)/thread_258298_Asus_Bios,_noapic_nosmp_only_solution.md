---
title: "Asus Bios, noapic nosmp only solution?"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tappad on 2006-09-15
Hi, for a while now iv'e been booting my computer with noapic and nosmp as kernel options.
Im fed up with theese problems, caused by a bad bios release from asus.

The problem is discussed here on an asus forum.
[http://vip.asus.com/forum/view.aspx?id=20060823111425215&board_id=1&model=M2N32-SLI+Deluxe&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20060823111425215&board_id=1&model=M2N32-SLI+Deluxe&page=1&SLanguage=en-us)
Iv'e found 2 possible solutions, however, i thought i'd check with you all here if anyone tried them.

Solution 1:
Downloading an "unofficial" bios from : [http://www.frontosa.co.za/support.htm](http://www.frontosa.co.za/support.htm)

for people at : [http://www.linuxjournal.com/node/1000074#comment](http://www.linuxjournal.com/node/1000074#comment)
says it works. However im unsure about trusting them :)

Soulution 2:
As described in this mailinglist: [http://marc.theaimsgroup.com/?l=linux-kernel&m=115674436212855&w=2](http://marc.theaimsgroup.com/?l=linux-kernel&m=115674436212855&w=2)

So, anyone had any luck?

---

### Post by John.Michael.Kane on 2006-09-15
Have you tried edgy to see if support has been added. 
I would suggest that updating the bios be your last method.

---

### Post by tappad on 2006-09-16
Hi SD_Plissken!

> **SD-Plissken said:**
> Have you tried edgy to see if support has been added. 
I would suggest that updating the bios be your last method.

bugzilla at kernel.org 
:[http://bugzilla.kernel.org/show_bug.cgi?id=6975](http://bugzilla.kernel.org/show_bug.cgi?id=6975)

Those guys says it doesnt work with kernel 2.6.18rc6 witch am guessing is newer that the one used in edgy?

As for updating the bios, am also very sceptical.. Perhaps this version should come in an official release from asus soon. (Dont think it's worth taking a chance with)

---

### Post by twowheeler on 2006-09-16
Is there some reason you haven't returned the board for a refund?  Demand your money back.  Make sure you tell them that hardware incompatible with linux is totally unacceptable to you.

---

### Post by tappad on 2006-09-16
> **twowheeler said:**
> Is there some reason you haven't returned the board for a refund?  Demand your money back.  Make sure you tell them that hardware incompatible with linux is totally unacceptable to you.

I would, belive me, but i really don't have time to screw around with the manufacturer/reseller. I need my computer for everyday work :/
But, the broken ACPI/APIC is not specific to linux. It's broken in windows to, as the shutdown command doesn't work (complaining about apic)..

---

### Post by Perfex on 2006-09-18
I get this with my abit At8 32X or something similar anyway:

[4294670.828000] ..MP-BIOS bug:8254 timer not connected to IO-APIC

it will hang for a couple seconds on 64 bit, will hang indefinetly on 32 bit

---

### Post by ashram on 2006-10-14
As it seems, new firmware from asus solving noapic problem...

---

