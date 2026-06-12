---
title: "Cedega 5.1 - Sound Problem"
date: 2006-07-18
forum: Wine
---

### Post by BrokeBody on 2006-07-18
Everything was always working perfectly with Cedega 5.1, but suddenly and I don't know why, a sound problem came up. When I start any game, in the game there's a message: *Can not initialize base sound services. Sound is disabled.*. Each time I do the test, the OSS failes and it was never failing before. When I click on the *Failed* button there's a message: [I]The OSS Sound ystem does not appear to be working or avaliable. Please check your Linux distribution documentation on how to set up your sound card.  If your sound card is working in other applications please make sure that no other applications are using your sound card and that ARTS and ESD have been disabled.
[/I]

I don't know what happend. I just want everything to get back in normal, just like before - to have a sound in games when I'm playing them over Cedega 5.1.

---

### Post by gustavog on 2008-01-05
This is kinda old, and you probably solved this already. But i just had the same problem. So if anyone bumps into this thread later on here is the solution (at least for me it was, running Kubuntu 7.04):
All I had to do was kill the process artsd and everything went back to normal again.

See ya

---

