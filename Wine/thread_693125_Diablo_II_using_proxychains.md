---
title: "Diablo II using proxychains"
date: 2008-02-10
forum: Wine
---

### Post by band-aid on 2008-02-10
I am trying to play diablo II, but my school requires that all connections be routed through a proxy server. This means that I have to use proxy chains. Everything appears to be working fine. I do

```


proxychains wine ./Game.exe


```

from inside the diablo II directory and the game launches. When I click battle.net the connecting box pops up for a split second then closes and the terminal reports that a successful connection has been made from my proxy to Bnets servers. It appears that the connection is closing and kicking me back to the menu. Any help?

---

### Post by Ferrat on 2008-02-11
have you tried jumping another leap to a extra proxy for ex. one you got at home or similar, it could be that the school proxy doesn't like Bnet or that Bnet doesn't like something about your schools proxy. 

Just guessing here but that's my first guess and best way to try it is to use another proxy that you know is "clean" and can connect to Bnet.

---

### Post by Gunman1982 on 2008-04-28
Try using tsocks instead of proxychains (needs a socks proxy though)

---

