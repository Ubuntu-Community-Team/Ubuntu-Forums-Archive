---
title: "Hanging on a G3"
date: 2006-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Seco on 2006-04-05
I have no clue why, but I can't seem to get past the login screen. It loads up fine, with an incorrect address for something (From past experience, I think that's due to it not being shut down properly), and then I get the login screen. I type in my user and password, I get the brown non-textured background, a normal cursor, the startup sound, and that's it.

Nothing more.

The CD isn't at fault, because I've tried two of them. There are no problems with installing it to begin with since I let it judge it's partitions for itself, although it seems slow as hell installing/configuring Python.

Specs of my G3:
Indigo iMac G3
400Mhz
512Mb RAM
10Gb HDD.
The rest is standard.

So far, I managed to successfully log in once.

Help?

---

### Post by linear on 2006-04-05
Before you do anything else, check for the [Ubuntu Date Bug]("https://wiki.ubuntu.com/UbuntuDateBug").

---

### Post by Seco on 2006-04-06
That would make sense, sicne the CMOS battery is kaputt and OSX kept complaining that it was set before 1970...

I'll post in here again if it doesn't work.

---

### Post by Seco on 2006-04-06
OK, that worked, but my backup battery for teh clock is still kaputt, and I can't get the clock sync'd because it's not connected to the internet.

If anyone has any instructions to help with an iMac G3 DV (Summer 2000) model, please let me know. All the other ones are newer, and don't help.

---

### Post by jdp on 2006-04-06
Is there something in the page link taht isn't working to set the date, or is it something else?  Other than getting the x.org file changes to work on an iMac (well documented on the [forums](http://ubuntuforums.org/showpost.php?p=409203&postcount=1)) there isn't much else that causes trouble.  You can buy a new PRAM battery for $5-10 and once you install it and set the date, things should be fine for a few years.

---

### Post by bodycoach2 on 2006-04-06
I had the same problem: couldn't fully boot if I wasn't connected to the internet. If I was connected, I booted fine. I installed KDE, and tried booting from that, without the internet. Worked fine.

My current workaround: Boot into KDE, the log out, and log in through GNOME. I like KDE, but perfer Gnome.

Danny

---

