---
title: "Firefox 3.0.12 not saving bookmarks!"
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by al688 on 2009-07-29
Since updating firefox I am unable to save any new bookmarks.  The bookmarks I saved prior to the update are still present and everything else works fine.  The new bookmarks are present until I close firefox and reopen it, revealing only the bookmarks saved prior to the update.  Saving a new bookmark, uploading it to xmarks and then overwriting the system bookmarks does not rectify the problem.  Bleachbit is disabled but has never given me problems prior anyway to this upadate.

Any ideas?

---

### Post by philinux on 2009-07-29
Save a copy of your bookmarks to say your desktop. Close Firefox. Rename your .mozilla folder to say .mozilla.bak then restart firefox and import your bookmarks.

This will generate a brand new profile folder. You'll have to get your addons back from mozilla.

I've got rid of bleachbit it can cause problems.

---

### Post by al688 on 2009-07-29
Thanks for the reply.  I'll give it a go tomorrow, bit busy at the mo, I'll let you know if it solves it.

---

### Post by al688 on 2009-07-30
Tried this and had no joy.  Bookmarks weren't located in mozilla file but in /etc/firefox3.0/profiles.  Tried renaming files with no success, even after completely removing and reinstalling firefox problem still persists .  I have also discovered that I can't delete any bookmarks either, they reappear after firefox is restarted!    Help!!

---

### Post by al688 on 2009-07-30
Solved! Did a fresh install, and everything seems ok.

---

