---
title: "Update to Firefox 2.0.0.12 -- Missing Plugins?"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by stanleypane on 2008-02-16
I recently ran the Ubuntu automatic updater and it installed Firefox 2.0.0.12. Now, I have no plugins listed when I view the about:plugins page. Everything is missing, flash, mplayer, java, etc...

If I try reinstalling them, they seem to work fine, but for some reason they aren't recognized by Firefox? Any ideas?

Oh yeah, I'm running 32-bit Firefox on a 64-bit install.

---

### Post by Kilz on 2008-02-16
> **stanleypane said:**
> I recently ran the Ubuntu automatic updater and it installed Firefox 2.0.0.12. Now, I have no plugins listed when I view the about:plugins page. Everything is missing, flash, mplayer, java, etc...

If I try reinstalling them, they seem to work fine, but for some reason they aren't recognized by Firefox? Any ideas?

Oh yeah, I'm running 32-bit Firefox on a 64-bit install.

The automatic updater on a 64bit system will update the 64 bit version of Firefox from the Ubuntu repositories. Exactly how did you install a 32bit version of firefox?

---

### Post by stanleypane on 2008-02-17
I was able to figure this out by doing some more digging on my system.

To be honest, I can't remember the exact process I went through to install 32-bit Firefox on my system. The automatic updater has always *appeared* to update my 32-bit install. When I start firefox32, and do a Help>About Mozilla Firefox, it shows 2.0.0.12, yet I've never manually updated and all I ever run is the automatic updater that comes with Gutsy. Any explanations here? I'm really curious.

Anyhow, I have a /usr/**lib32**/firefox32 and a /usr/**local**/firefox32. Not sure what's going on there. All of my plugins were present in the /usr/lib32 directories, but not the /usr/local directories. I just copied the appropriate files over and now everything runs fine.

---

