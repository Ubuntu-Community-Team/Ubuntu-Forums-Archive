---
title: "/usr/lib32"
date: 2009-04-07
forum: x86 64-bit Users
---

### Post by coloured on 2009-04-07
I'm after a little advise here, I have been trying to install the citrix client on my system... I was in the process of dealing with some lib issues because citrix doesn't release a 64 bit version of its client. I accidentally started copying everything from /usr/lib to /usr/lib32 and then realised what I was doing... anyway I ended up going into /usr/lib32 and deleting everything that was modified on todays date...
anyway I still can't get the citrix client installed after following everyone elses guides.
I am beginning to wonder whether I have deleted some stuff in /usr/lib32 that was actually required.
How do I check to ensure that /usr/lib32 actually houses everything it should? is there a way to rebuild this directory?

cheers
Jurgen

---

### Post by Yellow Pasque on 2009-04-07
I would suggest going into Synaptic and marking ia32-libs for reinstallation. I would also do a search for packages with lib32 in the name and mark any you have installed for reinstallation.

---

