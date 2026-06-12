---
title: "Vista/Gutsy Dual-Boot, Sharing SB, TB, and FF Data - Permissions NIGHTMARE"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by coldstatue on 2008-04-25
I seriously doubt that this is 64-bit-specific, but I am on an AMD 64 with the 64-bit version of Gutsy.

I used a folder on my NTFS partition for sharing my ics files, firefox and thunderbird profiles, etc. (Probably a bad move)

Things worked great, going back and forth between Vista and Ubuntu, but now I have permissions problems when trying to access these folders in Linux.

Launching gksudo nautilus and attempting to change ownership fails. Every option goes back to how it was before I changed it. I have attempted at various levels of the hierarchy I am trying to access. 

ntfs-g3 and ntfs-config are both installed. The latter has rw activated. rw is in my fstab.

I have tried changing things in Windows, but can't figure that out.
EDIT: if I right-click on a folder in win, go to properties, and uncheck the read-only box, it goes through the process of applying changes, but if i go back into the properties, that box is checked again!

I can't even run firefox's profile manager in Ubuntu - I get a message that firefox is already running, etc. pkill firefox does not resolve this. I have to beet into windows to use firefox now. 

I am on the road right now, and need windows to jump on various wireless networks, as ndiswrapper likes to grab a hold of one and refuse to hook up with another once I travel. That's really why I still need windows.
Still, I'd like for this to work this way.

I have no idea what I did to cause this, but my battery died the other day, and win did a restore system state or something. I guess it cold have happened then.

Any easy fix here where I don't have to make a new fat partition and remove firefox and all?

thanks in advance.

---

### Post by coldstatue on 2008-04-25
unfortunately, with so much fiddling, I'm not sure how I did it, but it is fixed. 

Sorry i have no record for you, future reader with the same issue

---

