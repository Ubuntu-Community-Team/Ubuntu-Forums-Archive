---
title: "yaboot Tip and the Wiki Page Re: Losing the Menu on Startup."
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-03-20
In regards to [this page](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot?highlight=%28yaboot%29) in the Wiki, someone needs to add a tidbit under "You lost the yaboot menu!" as I cannot create an account to change it myself (something about maintenance).

If Ubuntu is NOT on your FIRST partition, you can easily get the yaboot menu back by simply entering

**sudo ybin**

from the command line.  At least for me, I got my yaboot menu back automagically upon reboot.  (Yes, I know about holding down Option, but that's not the point.)

This isn't very clear in the Wiki and could confuse a newbie.  The YDL discussion makes the process more complicated than it ought to be.

Unfortunately, if you're like me with a bootable OS X partition on an external drive for backups, you'll have to hold down option to select it upon startup otherwise you will have your MBR overwritten again.

---

### Post by ssam on 2006-03-20
it is sort of in there but just to clarify should i change the paragraph
> If your yaboot menu partition is NOT the first bootable partition (goes against all install recommendations) then you will have to edit ?FirmWare or startup using the Linux installer disk and run the ybin application to tell your Mac that you want the yaboot menu to be the "startup disk" (ybin is in some ways the Linux analogue for the Startup disk control panel/preferences pane in Mac OS).

to

> If Ubuntu is NOT on your FIRST partition, you can easily get the yaboot menu back by simply entering

```
sudo ybin
```

from the command line.

i guess there should be a note about how to boot to the point where you can run the command. does holding option let you boot to a point where you can do this? i could change the paragraph to

> If Ubuntu is NOT on your FIRST partition, you can easily get the yaboot menu back. Hold down option at boot and choose linux. once you are logged in run

```
sudo ybin
```

from a terminal.

---

### Post by AlphaMack on 2006-03-20
Holding down Option is indeed an option if you have a newer "New World" Mac.

It would definitely be a lot more straightforward to specify holding down Option to select the Ubuntu partition and then once logged in to enter 'sudo ybin.'

---

### Post by ssam on 2006-03-20
done :-)

---

