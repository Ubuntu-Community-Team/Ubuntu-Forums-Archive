---
title: "-m64 does not work in gutsy g."
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by flappinski on 2008-03-10
Hello,
since I provided a small c++ - program for 32bit and for 64bit machines, I just compiled both binaries on the 32it machine. Once with the argument -m64. This worked very nicely in feisty fawn.
But since I upgraded to gutsy gibbon I get this error. I tried many synaptic installations, but still get it, even when installing a new gutsy gibbon - system.
Is there a workaround or should I just go back to my beloved feisty fawn ( and what do I have to do for this?

/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status


thanks a lot,
Stephan

---

