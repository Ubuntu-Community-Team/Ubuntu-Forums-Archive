---
title: "Ibex/8.10 NVIDIA 8200M--CPU usage issues?"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by bfinan0 on 2008-12-13
I have a HP G60-120 laptop, about 4 hours old (so no preexisting problems whatsoever), and just installed 8.10.  Looking around the forum, I noticed that other people had assorted major problems with Ubuntu and NVIDIA graphics cards, but mine seems to be different.  At first, using the 173 driver, everything was EXTREMELY SLOW...I upgraded to the 177 available in restricted-drivers, and this somewhat solved the problem, but I still think it is rather strange that the CPU would be 0-100% idling.  Each core takes a turn at 100%, they switch over about every 0.7-1.5 seconds.  Video is slower than normal, Flash is nearly at a stop (1 fps at best).  Any idea what might be wrong, or is this normal?

---

### Post by bfinan0 on 2008-12-13
I removed compiz and installed 180-16 drivers, and they made performance a little less awful, but by no means good.  I still can't even watch a Youtube video in firefox, almost everything else seems to be working more or less as expected. CPU usage is still very high (30-50% idle) but no longer as absurd.  Might there be 3 or 4 (or 50) problems, of which I have only found 2?

---

### Post by iainfarrell on 2009-01-05
Looks like you're not alone. I had a look into this because I'm thinking of buying a similar model. This guy seems to think he's solved it.

[http://kubuntuforums.net/forums/index.php?topic=3100006.0](http://kubuntuforums.net/forums/index.php?topic=3100006.0)

---

### Post by yoasif on 2009-01-17
after tearing my hair out and even going as far as installing ubuntu-minimal, it seems the solution is to use the 173 driver. Even the 180.22 driver (downloaded from nvidia) exhibits extremely slow rendering in youtube, etc. 

use envy or the restricted hardware manager... i used envy, and it's working great.

---

### Post by bfinan0 on 2009-01-17
> **yoasif said:**
> after tearing my hair out and even going as far as installing ubuntu-minimal, it seems the solution is to use the 173 driver. Even the 180.22 driver (downloaded from nvidia) exhibits extremely slow rendering in youtube, etc. 

use envy or the restricted hardware manager... i used envy, and it's working great.

I actually figured out that the problem is not with NVIDIA at all...it's something with firefox or flash 11.  I have no problem watching 8.6GB HD movies, or, for that matter, downloaded Youtube videos, using 180.22 (both of which were sluggish with 173 and 177).

---

