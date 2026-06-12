---
title: "Installing Hearthstone under Wine in Ubuntu 13.10"
date: 2013-12-13
forum: Wine
---

### Post by Ertai87 on 2013-12-13
As the title says, I'm attempting to install Hearthstone under Wine in Ubuntu 13.10.  As far as I know, Wine is up to date, as is my OS (last updated 2 days ago).  Here's the Blizzard help page for the error I'm getting:

[https://us.battle.net/support/en/article/BLZBNTBTS00007](https://us.battle.net/support/en/article/BLZBNTBTS00007)

I Googled for it but couldn't come up with anything reasonable.  I went to the WineHQ page and disabled that thing they said to disable, but that didn't work.  Does anyone know anything about this?  I really want to play Hearthstone T_T

The other thing is that my comp is very old and doesn't meet minimum specs, but I wanted to see how bad running it below minimum specs is; if it runs reasonably I'll play it anyway.  However, it might be the case that it just won't let me install if I don't meet minimum specs.  Can someone confirm/deny/give me a solution for this?

Thanks.

---

### Post by mörgæs on 2013-12-13
> **Ertai87 said:**
>  Can someone confirm/deny/give me a solution for this?


No, as you have not posted a complete hardware description.

---

### Post by Ertai87 on 2013-12-13
OK.  What would you like me to provide?  I have a Dell Inspiron 6400 with, I believe, 1GB of RAM.  Not sure what else you want.

---

### Post by Ertai87 on 2013-12-13
Nevermind.  Turns out the problem was that the main repo has Wine 1.4 and I needed a newer version of Wine.  It worked after upgrading to Wine 1.6.  Can someone add Wine 1.6 to the main repo to help others with this problem?

---

### Post by cRaZyBisCuiT on 2013-12-14
Due to the release model of Ubuntu, no newer versions are added to the main repo after the initial release. Only new distributions ship in new versions. Apart from that you just got bug fixes.

---

### Post by philinux on 2013-12-14
> **cRaZyBisCuiT said:**
> Due to the release model of Ubuntu, no newer versions are added to the main repo after the initial release. Only new distributions ship in new versions. Apart from that you just got bug fixes.

That's what the backports repos are for and also firefox gets regular updates. Wine would be a backports category.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Toz on 2013-12-14
*Moved to the **Wine** subforum.*

---

