---
title: "Good old printer problems"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by sambarusty on 2008-11-18
I am new to ubuntu, not new to Linux, but I had a fairly successful install of the latest version.  The only thing I have run into so far, and I am not sure if it is related to the 64 bit drivers or not, is that I can't print from the web.  It starts and then stalls.  The print queue remains in a pending state.  I have an older Lexmark X73 that I did have working with Linux at one point, (maybe I shouldn't have touched anything, but it is too much fun not to).  But this time around I am not having as much luck.  It is a usb printer. I have a Amd 64 athlonX2 machine. I am using firefox 3.0.3.  I am just wondering if I am missing something obvious before I settle in for a day to figure out I did something silly.  Thanks in advance.

---

### Post by Arup on 2008-11-18
I sometimes run into this problem as well, my workaround is I switch to user mode with Opera and then print, it works out fine or else I would save to PDF with FF and print, both work out well.

---

### Post by sambarusty on 2008-11-18
typically I will just copy it into office and print, but I was just wonder if anyone figured out how to get it fully working.  Thanks

---

### Post by sambarusty on 2008-11-24
I did try a couple of things to no avail.  I did an apt-get install xpp.  Also did apt-get install of gtklp.  I added a file in /etc/gtk-2.0/gtkrc and added the line gtk-print-backends = "lpr,file". What this allowed me to do was to try several different print commands in the print dialog.  I tried lpr, xpp, and gtklp.  All of which start printing and then stop prior to completing the page.  The interesting thing is it does not always happen.  I tried it on one forum and it printed to completion.  I try it on this thread for example and my problem comes back. Hmmm.  So I thought maybe it was a firefox thing and downloaded and installed Opera.  Same behavior was exibited.  I tried several different drivers for lexmark under the printer installation area and either get nothing (which would be expected when trying random drivers) or the same behavior as the one that is suppose to go with the printer.  So I am wondering if I have a driver problem, but I see online that people have gotten the Lexmark X73 to work with Firefox.  I am kind of confused.  I think I gave it a valiant effort though.  Does anyone got any other tips or tricks to try. Keep in mind it does print just fine off a program such as open office word processor, so it is not an issue where it doesn't work at all.

---

### Post by sambarusty on 2008-12-03
Found something interesting, it seems to have to do with the portable printer stuff, I have the same issue in document viewer and Gimp etc.  The only thing that seems to print on my printer is open office.  Any one know of a scanner, copy, printer that just works in linux with a reasonable ink cost.  I am hoping to go new enough where I am not paying $35 a cartridge for ink and print heads x2 for cartridges(black and color).  Yes I know there are alternatives to the lexmark cartridges, but you know what I am talking about. 70 dollars for ink refills this next time around or buy a new printer that just works with linux as opposed to trying to fight with it may be a great alternative to my problem.  Lexmark doesn't even play nice with windows, so what would I really expect, correct? I am looking for suggestions. Any scanner, copy printers that work reasonably well on both openoffice, mozzilla, and doc viewer.  This would solve my problem.  Preferably worked with existing drivers, not a lot of messing around with stuff.  I want a compatible printer (so out of the box).  My printer fights have just been annoying if you can't tell.  Thanks All.

---

### Post by sambarusty on 2009-01-09
Found one. Just to let anyone know who is interested, the HP Officejet J4680 All-in-One works great with Ubuntu.  Very pleased with my purchase.  It was easier to get it set up with Ubuntu then it was in Windows.  The Photo copy feature doesn't even require an Xsane scan.  It seems to be a great machine thus far.

---

### Post by kindafunnylookin on 2009-02-01
> **sambarusty said:**
> Found one. Just to let anyone know who is interested, the HP Officejet J4680 All-in-One works great with Ubuntu.  Very pleased with my purchase.  It was easier to get it set up with Ubuntu then it was in Windows.  The Photo copy feature doesn't even require an Xsane scan.  It seems to be a great machine thus far.
I walked in the door 37 minutes ago with that printer - in the sealed box - and already have all 4 functions working with no tweaking or hacking. My best printer experience in 29 years of messing with 'em. Real good quailty printing, both blk and color. A little slow, but under 100 USD.

---

