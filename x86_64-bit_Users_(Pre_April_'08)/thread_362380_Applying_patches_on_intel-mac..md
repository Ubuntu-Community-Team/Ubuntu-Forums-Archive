---
title: "Applying patches on intel-mac."
date: 2007-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by pwilcken on 2007-02-15
i'm trying to work out the kinks of running Edgy on my macbookpro.

i've followed all the tutorials as best i could, and as many as i could find.
but now i've resorted to asking a very newbie question, since i cant find my answer:

how do i install patches in ubuntu?

some pages i've found like to a page of pure text (the patch itself i'm assuming)
but what am i to do with it?

example: i'm trying to apply suggested patches from 
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)
dealing with the fans and trackpad.

any help would be greatly appreciated, and sorry if its a repeat, but i looked for so long
that this is my last resort.  (frustrated)

---

### Post by Bachstelze on 2007-02-15
Those are kernel patches, be warned that after applying them, you'll have to recompile your kernel.

Save the files in /usr/src, be sure you have the source tree for the relevant kernel in it and do :

```
sudo patch -p1 < filename.patch
```

---

### Post by bapoumba on 2007-02-15
edited out.

---

### Post by grazie on 2007-02-15
Why is an x86 machine post being moved to a PPC forum by a moderator?

pwilcken, Good advice there by HymnToLife.

EDIT:

Seems this post has had some difficulty in finding its rightful home :)

---

