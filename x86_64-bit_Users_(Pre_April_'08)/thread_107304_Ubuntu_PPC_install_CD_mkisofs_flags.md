---
title: "Ubuntu PPC install CD mkisofs flags?"
date: 2005-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by fyhuang on 2005-12-22
Hello,

I'm trying to remaster a PPC CD for a friend (just to add some timeout flags for yaboot), and I would like to know the paramters that mkisofs was called with when creating the original Ubuntu PPC installation CD, or equivalent flags that would allow me to create a bootable, modified PPC installation CD.

Thanks!

[sorry moderators if this looks like a cross-post, I accidentally posted it first in the customization section - please delete that one]

---

### Post by gruepig on 2005-12-23
I haven't done this, and it looks like it might (or might not?) be more complicated than just using the right mkisofs flags, but these URLs might be of some help:

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo)
[http://metadistribution.org/blog/archive/2005/05/09/howto_build_a_livecdlivedvd_yo](http://metadistribution.org/blog/archive/2005/05/09/howto_build_a_livecdlivedvd_yo)
[http://lists.penguinppc.org/yaboot-users/2002/yaboot-users-200212/msg00001.html](http://lists.penguinppc.org/yaboot-users/2002/yaboot-users-200212/msg00001.html)

I'm curious to know how it goes.

(Idle speculation ... even if the CD isn't bootable, can you go into open firmware and then specify the path to the kernel or yaboot?)

---

### Post by fyhuang on 2005-12-23
Thanks for the links, using them I've managed to create a bootable CD now (at least bootable on PearPC, I dunno about a real Mac). I shall have to see how this works for my friend, because I'm unable to get past yaboot on PearPC (with either the original CD or my hacked one), so I can't tell if my CD will actually do anything after 'booting'...

Thanks again for the help!

---

