---
title: "Which kernel to use on a server with 2 x 64-Bit Xeon processors?"
date: 2006-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by maoo on 2006-06-15
Which kernel should I use on a server with 2 x 64-Bit Xeon processors [this machine is a router and a server (BGP, ip-forwarding, 4 NICs, LAMP, no GUI, etc.), but it has Xeon processors]:
**linux-image-2.6.15-xx-amd64-server** or **linux-image-2.6.15-xx-amd64-xeon** ?

What are the main differences between these kernel-images?

Thanks.

---

### Post by JoWilly on 2006-06-15
The amd64 kernel is optimized for the generic amd64 arch, whereas the xeon kernel is optimized for EM64T.

I didn't take a precise look at the server kernel so I can't talk much about it, but I would guess that you most probably won't need any features that are not available in the xeon kernel.

So, go with the xeon kernel as it is made for your cpu (EM64T).

---

