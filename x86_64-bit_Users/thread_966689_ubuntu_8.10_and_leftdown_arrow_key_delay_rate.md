---
title: "ubuntu 8.10 and left/down arrow key delay rate"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by dafi on 2008-11-01
I've a **very strange** problem under Intrepid Ibex, the left and down arrow keys don't respect the delay rate set from keyboard panel.

I've set a very fast rate and all keys respect it when I press a key and hold it pressed.
The left/down arrow keys instead have a long delay.

My env
Linux dafihome 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

I've installed nVidia driver 177.80 from nVidia web site.

[COLOR="Red"]EDIT:[/COLOR] using xev I've seen after pressing left/down key to see next event processed pass 499 ms, other keys are about 2/3 ms

Any idea?

---

### Post by awreneau on 2008-11-03
Same problem here.

IBM T42
2.6.27-7-generic

---

