---
title: "printing from firefox (or varients) in AMD64 Feisty, only postscript printer availabl"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by chene on 2007-06-08
hi all,

First of all, just let be say that I cannot reproduce this problem in 32-bit version of Feisty.  I only have this problem in AMD64-Feisty.  The issue is that the firefox (32bit, 64bit, swiftfox, etc) only sees postscript printer (and only 1).  It does not see any CUPS printers.  

My setup:

2 printers (HP6L on parallel and Samsung 2010 on USB)
firefox32
firefox64
swiftfox (from automatix)

all 3 browsers, when printing is selected, only has "postscript" printer on the dialog, which is then re-directed to the default system printer.  I would like to have the option of having a dialog-popup, allowing me to select which printers I want to print to.

I have another machine with 32-bit Feisty, and the printers (via networked CUPS) shows up was CUPS/hp and CUPS/ml, respectively, where hp/ml are the names I gave to the printers.

any idea how I can fix this problem, and why I only have this probme on AMD64 Feisty?

tia,

---

### Post by brharri1 on 2007-06-08
I have noticed the same thing. You can manually edit the print command, but I don't know what to put there. Hope somebody does know how to fix this.

---

### Post by cmost on 2007-06-08
Download and install GTKlp from Synaptic, then change the postscript command to /usr/bin/gtklp.  You should then get a dialog that fully takes advantage of your printer's features.

---

### Post by brharri1 on 2007-06-08
Thank you so much!

---

### Post by chene on 2007-06-08
> **cmost said:**
> Download and install GTKlp from Synaptic, then change the postscript command to /usr/bin/gtklp.  You should then get a dialog that fully takes advantage of your printer's features.

hi,

I actually tried that (and kprinter) on 2 of the AMD64-Feisty I have and they both didn't work.  I have installed gtklp, logged-off and re-logged-in (just to make sure), go to about:config and change the print.print_command and print.postscript.print_command to /usr/bin/gtklp, but the print behaviour did not change.  I still get the default dialog, with only postscript printer listed.

when/where does the gtklp kick in?  Is there any other options I should change in about:config?

tia,

---

### Post by brharri1 on 2007-06-08
This may not make a difference, but I didn't do it through about:config. I just clicked file : print, then next to printer name click properties and put in the path to gtklp there.

---

### Post by chene on 2007-06-09
hi all,

problem solved.  I ended up deleting .mozilla directory and performed the given instruction again.  And it worked.  

thanks,

---

### Post by Didjit on 2007-08-04
Forgive my ignorance, how did you change thepostscript command to /usr/bin/gtklp?

Having the same issue.

Tx

Didjit

---

### Post by pokereth on 2007-08-08
When you hit print, then go to Properties and type /usr/bin/gtklp into the Print Command line.

---

### Post by Bozebus on 2007-09-13
I was having the same problem with Swiftfox on my Feisty 64-bit installation. Thanks for this info!! It works great now!

---

### Post by lns on 2007-09-13
Is there a way to set /usr/bin/gtklp as the default "Default/Postscript" command for all users? I'm having this printing issue on an Ubuntu LTSP server (Feisty) with ~200 elementary school students - to tell them all to use this workaround would be a major headache on the teachers. :)

Thanks for any insight!

---

### Post by Krydahl on 2007-09-18
OK, I followed the instructions and it worked, but GKTlp seems very slow to initialise. Is there any way to speed it up?

---

