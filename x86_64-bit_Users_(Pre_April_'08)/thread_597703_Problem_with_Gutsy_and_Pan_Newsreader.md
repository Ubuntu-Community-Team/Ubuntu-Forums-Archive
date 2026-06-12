---
title: "Problem with Gutsy and Pan Newsreader"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by maulteez on 2007-10-30
I've just installed Gutsy and have noticed a problem with the Pan newsreader. If an image is downloaded and it is around 150k then it displays fine but if is larger than about 200k then the image is chopped off at the bottom and the remaining part is displayed as solid black. If you go ahead and save the corrupted image and open it with EOG or whatever then it displays just fine. It is only corrupted when displayed by Pan. Any suggestions as to how to correct this? TIA

---

### Post by ogregore on 2007-10-31
maulteez,
 
There is a known bug in which gdk-pixbuf does not load large images properly in the inline image viewer in Pan, downloaded images are fine.  It seems to be because of a inconsistancy between Pan and gtk+2.12, (or maybe gtk+2.11 or higher).
 
There is a patch - if you go to the Pan website and check the mailing list_user archives for a thread entitled "Previews Gone Screwy", one of the posts has the patch attached.
 
The patch corrected the problem for me.
 
Cheers
Ogre

---

### Post by maulteez on 2007-10-31
I appreciate that ogregore. Fixed me right up! Thanks!

---

### Post by cycleger on 2007-12-02
Pardon the newbie question but how is the patch applied? This is the patch I found;
load-pixbuf-in-1024-byte-chunks.diff

---

### Post by kurraider on 2007-12-02
> **cycleger said:**
> Pardon the newbie question but how is the patch applied? This is the patch I found;
load-pixbuf-in-1024-byte-chunks.diff

cycleger:

You would need to apply the patch to the source and then compile the source.  Its a major pain.  I found the following post much more helpful:

[http://ubuntuforums.org/showthread.php?t=583865](http://ubuntuforums.org/showthread.php?t=583865)

Someone has already crated a .deb with the patch applied.

-kurraider

---

### Post by cycleger on 2007-12-03
Thanx for pointing me in the right direction kurraider,
Found and used that .deb, works as advertised. Looks like I get to use that patch anyway on a Debian/Sid install

---

