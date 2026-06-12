---
title: "Boots to blank screen now?"
date: 2008-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gfahey on 2008-02-20
Had Gutsy running great for 2 weeks. Everything fine. 

I bot it up this morning and nothing. Blank screen. 

Dell Vostro 1000 with Integrated ATI Radeon  Xpress 1150 HyperMemory and 2GB RAM.

I did nothing before this at all. No fooling around or installs of anything. 

Man, I sent untold hours getting this right and now this. I am so frustrated. 

Sending out an SOS now. Thanks for any help.

---

### Post by Yellow Pasque on 2008-02-20
Press Ctrl+Alt+F1. Does this get you back to the terminal?

If so, and you're using the proprietary ATI "fglrx" driver, try this:
```
sudo aticonfig --initial -f --overlay-type=Xv
```
Reboot. See if that works.

---

### Post by gfahey on 2008-02-20
No. I could not get that.

Strange but, after a hard reboot several times it is back now. Odd but, I'll take it. 

Thanks though.

---

### Post by Yellow Pasque on 2008-02-20
Glad to help.:lolflag:

---

