---
title: "Suspend and sleep on 12&quot; PowerBook G4?"
date: 2006-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by surblimity on 2006-05-06
I've poked around a lot and can't seem to find a definitive answer to this question:

I'm using Dapper Drake on my 12" PowerBook and have gotten everything up and running satisfactorily except for suspend.  I close the lid, nothing happens.  I can't make my computer sleep or suspend at all.  This is a significant problem for me and the primary obstacle to using Ubuntu as my primary OS.   I know that this has something to do with nvidia on the 12" PowerBooks.

My questions:
1) Is it at all possible to get suspend or sleep working in Ubuntu on a 12" PowerBook?
2) If it is possible, how is it done?  Can someone point me to some instructions for accomplishing this?
3) If it's not yet possible, is it something that's being worked on?  Will it ever be possible?

Sorry if this is a bit redundant, as I know that others have asked about this, but it's a crucial question and a (more) definitive answer would be great!

---

### Post by eddie303 on 2006-05-06
Try out this:

sudo echo mem > /sys/power/state

This puts my Omnibook to suspend into RAM. I know an Omnibook is far from a Powerbook, but it should work :D

---

### Post by surblimity on 2006-05-10
Thanks for the suggestion, but I think this is a far deeper problem.  Anyone else have suggestions?

---

### Post by aimislame15 on 2006-05-10
Go to the preferences panel at the top right, then to power management, where it says "running on AC" set the drop-down menu to suspend. Do the same for on battery. I had trouble figuring that one out at first, as sad as it seems.

---

### Post by surblimity on 2006-05-11
I've tried that too, aimislame15.  I think this is a bigger problem than changing settings, as indicated by [this thread]("http://ubuntuforums.org/showthread.php?t=102333"):

> 
The 12" Powerbooks are nvidia based. We don't have any idea how to
reinitialise the video, and so as a result sleep is disabled. Not a lot
we can do, I'm afraid...

I'm just trying to figure out if this is something that's being explored any further, and if there is ever going to be any hope for this particular feature.

---

### Post by farruinn on 2006-05-11
This bug has been reported: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35197]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35197"), but it doesn't appear to have been assigned to anyone yet, that's not to say someone that's not in launchpad isn't working on it though.

---

