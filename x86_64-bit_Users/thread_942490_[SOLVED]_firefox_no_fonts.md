---
title: "[SOLVED] firefox no fonts"
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by shane2peru on 2008-10-09
Ok, I'm back to 64bit after a bit of a break.  I just bought a new laptop (64bit amd Turion X2 ultra processor) with ATI Radeon graphics card.  ATI seems to be working rather well.  Had minor issues wireless, got that resolved.  Ok, now I have firefox giving me problems.  I open it up (got flash installed) and it has no fonts what so ever!  They are not small, they are non-existent.  No text shows up at all.  All the pictures show up, flash works like a charm, no fonts.  Any ideas would greatly be appreciated.  Thanks!

Shane

PS - I did all the updates, so Firefox3 is up to date.

---

### Post by shane2peru on 2008-10-09
> **shane2peru said:**
> Ok, I'm back to 64bit after a bit of a break.  I just bought a new laptop (64bit amd Turion X2 ultra processor) with ATI Radeon graphics card.  ATI seems to be working rather well.  Had minor issues wireless, got that resolved.  Ok, now I have firefox giving me problems.  I open it up (got flash installed) and it has no fonts what so ever!  They are not small, they are non-existent.  No text shows up at all.  All the pictures show up, flash works like a charm, no fonts.  Any ideas would greatly be appreciated.  Thanks!

Shane

PS - I did all the updates, so Firefox3 is up to date.

OOOOPS  :redface:   :oops:   :redface:

My bad, turns out it was a font issue.  I had pasted fonts into the /usr/share/fonts folder, and they didn't have the correct permissions.  All fixed.  

Shane

---

### Post by practic on 2009-06-08
Thanks for posting that...I just ran into the problem also. I don't know how it happened as I don't remember manually copying any fonts. Had to install Opera just to search the web for the answer! It seems that the culprit was the msttcorefonts directory in 

/usr/share/fonts/truetype. 

I turned on Octal Permissions in Nautilus and could see that that folder had 700 instead of 755 permissions (and the icons showed an X on them, and I couldn't view the files inside the folder). I dropped to the terminal in the msttcorefonts directory and issued:

sudo chmod 755 *

This seemed to fix it. I also found a few other font folders at the same level which had the same problem so I fixed those also. It occured to me afterwards, that I probably should have done a recursive chmod from within the whole fonts folder:

sudo chmod -R 755 *

---

### Post by shane2peru on 2009-06-08
Glad you got some use out of this post!  

Shane

---

