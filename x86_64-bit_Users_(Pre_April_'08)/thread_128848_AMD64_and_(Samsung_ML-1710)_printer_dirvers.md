---
title: "AMD64 and (Samsung ML-1710) printer dirvers"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by kalinga on 2006-02-12
On transition to AMD64, OS kbuntu 5.10 breezy, I find that my printer (Samsung ML-1710P, parallel port) doesn't work. 

I've got the 32 version of the same OS running on my old PIII and there the same printer works perfectly. For both systems I've follwed exactly the same procedure, using the KDE setup tool. The printer is detected automatically and starts up when the test page is sent BUT with the AMD it doesn't print anything.

On Samsung's website there are only drivers for "386" and "ppc", no 64-bit stuff. I've tried installng the "386" but I can't even get the installation script to run. This was not necessary on the PIII.

So. I'm stuck. How do I get my printer working with the new OS?

---

### Post by rplantz on 2006-02-16
I'm running gnome, not kde, and I have an ML-1430. When I upgraded from Hoary to Breezy, the printer stopped working. Using the gnome printing tool (in gnome it's System->Administration->Printing), I deleted my printer. Then I plugged it in and turned it on. I also did this with my Epson all-in-one at the same time. When I used the Printing tool to add printers, both the Samsung and the Epson were detected. I simply used the suggested drivers, which were already installed. I did not get drivers from Samsung or Epson. Both printers worked just fine. Not only that, even the scanning part of the Epson all-in-one works.

I'm not sure, but I think the key here is to have the printer turned on when you add it so the system can pick the correct driver for you.

---

### Post by kalinga on 2006-02-17
Thanks for the reply. Are you using a 64-bit installation? As I said, my printer problems started on moving to the AMD 64 version of kbuntu. Yes, the KDE printer tool finds and identifies the printer. My problem is that it doesn't print. 

Any ideas? Anyone?

---

### Post by rplantz on 2006-02-18
[QUOTE=kalinga]Thanks for the reply. Are you using a 64-bit installation? As I said, my printer problems started on moving to the AMD 64 version of kbuntu. Yes, the KDE printer tool finds and identifies the printer. My problem is that it doesn't print.[/QUOTE]

Yes, I'm running 64-bit installation.

Have you tried deleting your printer, then reboot. Turn the printer on, then add the printer.

For what it's worth, I've installed KDE several times and played with it. At least with my 5.10 version on AMD64 (64-bit installation), I've had terrible results. Konquerer takes several times as long to load a web page. At one installation, Kontact got really messed up, and I had to remove all KDE things.

I've also tried xfce since it's supposed to be "lean and fast." It seems to save about 50 MB of RAM, which isn't very significant out to the 1 GB I have installed. Worse yet, it takes about twice as long to load as Gnome. And most of the applications I use actually take longer to load.

I haven't done a careful analysis, but so far (using 5.07 since July and 5.10 since October), the default Ubuntu (with Gnome) seems like the fastest and most stable installation on my 64-bit installation.

---

