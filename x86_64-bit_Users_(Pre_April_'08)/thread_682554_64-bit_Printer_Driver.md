---
title: "64-bit Printer Driver"
date: 2008-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by arigram on 2008-01-30
I am looking for a 64-bit printer driver for the Epson Aculaser C1100.
The driver that Ubuntu installs does not work.

Can someone lend me a hand?

---

### Post by str8line on 2008-01-30
Found this link on a google search.  Hope it helps.

[http://openprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100]("http://openprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100")

Chris Powell
Lemming CIR
London, ON

---

### Post by arigram on 2008-01-30
> **str8line said:**
> Found this link on a google search.  Hope it helps.

[http://openprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100]("http://openprinting.org/show_printer.cgi?recnum=Epson-ActionLaser_1100")

Chris Powell
Lemming CIR
London, ON

Thanks, but its for the wrong printer:
I am looking for Aculaser, not ActionLaser.
I know the difference is small, so its easy to make a mistake.

I found some 32bit RPMs, but with alien I can't convert them to DEBs because of the architecture difference. Also, I stay away from source files as I have not had any lack compiling anything.

---

### Post by him610 on 2008-01-30
The previous responder actually sent you to a treasure trove of printer drivers. 

If you had looked around a bit you may have found this page ...
[http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100](http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100)

You might also try the epson website.

Have fun,
Live long,
Power to the people!

---

### Post by arigram on 2008-01-30
> **hgh9mrp said:**
> The previous responder actually sent you to a treasure trove of printer drivers. 

If you had looked around a bit you may have found this page ...
[http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100](http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100)

You might also try the epson website.

Have fun,
Live long,
Power to the people!

I did "look around a bit" and the link to it its to the Avasys download page that only has 32bit RPMs and the Source, which like I mentioned are a problem to me.

---

### Post by Thelasko on 2008-02-01
A little trick to run alien when it wont create DEB files is to create .tgz files.  This is the same type of file that Slackware uses, and since Slackware is basically the granddaddy of Ubuntu (or great-granddaddy) it should install.  It does come with it's risks though.  .tgz files don't resolve dependencies on their own (no big deal you can find them yourself in the repositories) and will be more difficult to uninstall if it doesn't work or screws up your computer.  I have done it myself for my Lexmark z600 series and it worked for me.:)

---

### Post by cotcot on 2008-02-01
The epson drivers are all 32 bit (you can get them on the epson avasys website. [[COLOR="Red"]Here[/COLOR]]("http://www.avasys.jp/english/linux_e/dl_laser.html") is the 32 bit driver for your printer on this site. You can install them in a 32 bit chroot environment.

This is one of the reason I stepped back from 64 to 32 bit.

---

