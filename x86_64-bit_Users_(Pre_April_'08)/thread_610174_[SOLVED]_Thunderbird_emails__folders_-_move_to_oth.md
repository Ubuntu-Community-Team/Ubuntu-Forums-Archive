---
title: "[SOLVED] Thunderbird emails / folders - move to other computer"
date: 2007-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-11-11
Is there a tool that will let me back up my Thunderbird emails / folders / calendars, so that I can synchronize it on my other computers?

If not, how would I go about accomplishing this?

Thanks...

---

### Post by crjackson on 2007-11-11
This a good luck bump.  I have 666 beans without it.

---

### Post by Kilz on 2007-11-11
> **crjackson said:**
> Is there a tool that will let me back up my Thunderbird emails / folders / calendars, so that I can synchronize it on my other computers?

If not, how would I go about accomplishing this?

Thanks...

Copy the .thunderbird folder from your home directory.

---

### Post by warp99 on 2007-11-11
You can copy the entire sub-folder of your thunderbird email onto the other machine. The mail folder is a sub-folder of thunderbird  hidden in your home director. It should look like this:

**/home/<username>/.mozilla-thunderbird/<unique-number-generated>.default/Mail/mail.<name-of-provider>**

The exact mail location can be checked in Thunderbird by going to Edit > Account Settings > Server Settings. The last fill in box called "Local Directory" has the exact name and all of your mail is in that folder.

You can copy the entire folder to the new machine to the same location or choose another location then change the Local Directory folder to the new folder, just make such your new location has the correct read/write permissions.  :)

---

### Post by crjackson on 2007-11-12
Okay, thanks for the info.

---

### Post by crjackson on 2007-11-12
Thanks it worked.  I was also able to restore my disk image of Feisty and grab my archived information, then restore gutsy and pull in the mail folders.  Worked like a charm.

---

### Post by Atticka on 2007-11-12
Along the same lines....

I have a similar situation, can I copy the Thunderbird files from a Windows installation into the Thunderbird installation in Ubuntu?

---

### Post by crjackson on 2007-11-12
> **Atticka said:**
> Along the same lines....

I have a similar situation, can I copy the Thunderbird files from a Windows installation into the Thunderbird installation in Ubuntu?

I would think so, just make sure it has the same directory layout.  Make a backup copy of your current Linux-Thunderbird directory just is case it fails.  If it doesn't work, just copy your backup over into the working directory to restore.

---

