---
title: "[SOLVED] Video Driver Installation"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Talthalra on 2007-09-21
¨gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.¨

This is the message I get when I try to install my video drivers.

I´m running an ATI X1800XL

---

### Post by ddrichardson on 2007-09-21
How are you trying to install them?

---

### Post by Talthalra on 2007-09-21
I downloaded the .run files from the amd/ati website and...ran...those.

I also tried to update to the latest fglrx driver, but that didn´t work either. 

Any help is much appreciated.

---

### Post by ddrichardson on 2007-09-21
I take it you double clicked the run file from Nautilus?

---

### Post by Talthalra on 2007-09-21
Yeah....I´m supposed to do it another way, right?
Sorry, first time user, haha.

---

### Post by ddrichardson on 2007-09-21
open a terminal and type```
chmod +x filename.run
./filename.run
```
However for a binary X driver, you will need to shutdown X first```
sudo /etc/init.d/gdm stop
```
Then run the binary from the command line.
Lastly restart X```
sudo /etc/init.d/gdm start
```

---

### Post by Talthalra on 2007-09-21
Thanks!  The resolution is actually bearable now, haha.

---

