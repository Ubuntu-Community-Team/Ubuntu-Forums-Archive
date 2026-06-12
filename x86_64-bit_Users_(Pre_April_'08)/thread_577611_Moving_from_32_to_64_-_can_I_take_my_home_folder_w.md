---
title: "Moving from 32 to 64 - can I take my home folder with me?"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by philinux on 2007-10-16
What are the problems if any?

---

### Post by Drezliok on 2007-10-16
you should be able to if your home has it's own partition. The home only holds personal settings or the programs so I see no reason why that would fail.

---

### Post by philinux on 2007-10-16
Thanks I just wondered if there was any compatibility issue with the two systems.

My home folder is on a separate partition. I'm in the market for a new pc so I've got a usb pen drive to back up my home partition. 

Is there anything that wont transfer like wine?
I'm also using ubuntuzilla.

---

### Post by John.Michael.Kane on 2007-10-16
Looking at the below post from jocko, it's doable. however. I would still class it as not without risk.

---

### Post by rsambuca on 2007-10-16
Are you sure about that SD?  The config files in the /home folder are basically just a bunch of text files.  I am guessing, but I see no reason why they wouldn't be transferable.

---

### Post by jocko on 2007-10-16
It's absolutely NO problem to keep your /home partition.
The /home usually just contains configuration files and personal files and settings, which does not differ between 32 and 64 bit.
I've done it myself.

---

### Post by John.Michael.Kane on 2007-10-16
> **rsambuca said:**
> Are you sure about that SD?  The config files in the /home folder are basically just a bunch of text files.  I am guessing, but I see no reason why they wouldn't be transferable.

I looked through one of the text files in the home folder. Named .mozilla it has a file named compatibility.ini, and this file references Linux_x86_64-gcc3. Now on the OP machine he would in theory have a file label the same however his would point  Linuxi386-gcc3 or similar. 

That said I'm not completely sure how that folder would be handled of it would even cause issues. The rest of the folders have no references to Linux_x86_64-gcc3. 

So the OP might be ok moving to 64bit while holding his home folder. Though he should back up  info deemed valuable.

@rsambuca I amended my post.

> **jocko said:**
> It's absolutely NO problem to keep your /home partition.
The /home usually just contains configuration files and personal files and settings, which does not differ between 32 and 64 bit.
I've done it myself.

That may be well, and correct. however. just because you have done it without issue does not mean it is right for the masses to do so, and it does not mean they will not have issues.

---

### Post by jocko on 2007-10-16
> **SD-Plissken said:**
> On the other hand you want to move to a completely different architecture. Thus the info in the home folder deemed valuable will have to be backed up, and you would have to do a clean install.

The whole point of having a separate /home is that you **can** do a clean install without loosing your settings.
You just make sure to re-format the "/" but keep the /home partition.

---

### Post by John.Michael.Kane on 2007-10-16
> **jocko said:**
> The whole point of having a separate /home is that you **can** do a clean install without loosing your settings.
You just make sure to re-format the "/" but keep the /home partition.

Thats correct,however. there have been issue where settings that work on one version of Ubuntu do not carry over to the next version. 

Things change this includes settings. the user would have to make sure their current custom settings can carry over with out issues.

---

### Post by kwaanens on 2007-10-16
I've copied over my ~ as well.
I always move my whole home to another partition, and back to my new install (I try to keep the amount of partitions down so I keep home on /)
Just leave out the .gnome..., .gconf-stuff when moving to a *newer release*, because that sometimes messes up with newer versions of Gnome. Don't know if the same applies to .kde.

- Ketil

---

### Post by philinux on 2007-10-17
Thanks for replies. Looks like suck it and see what breaks.

---

