---
title: "Updates in Ubuntu 6.10 keep popping up"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by pokechu on 2007-07-19
I keep getting these pop-up saying that the new updates are available. But I did a sudo apt-get update and sudo apt-get upgrade, but I get the following error or maybe whatever message. 

The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic


How should I fix it? Thanks. If there's another thread on this, I'm sorry I haven't done much work to search for it and please do provide the link there. Sorry for the inconvenience caused. Thanks for help!

---

### Post by Sayers on 2007-07-19
I think it's possibly trying to fix a package OR telling you 7.04 is out. 

Why don't you update?

---

### Post by deanjm1963 on 2007-07-19
try doing a sudo apt-get dist-upgrade - it will upgrade those kernels for you.

---

### Post by Kilz on 2007-07-19
> **deanjm1963 said:**
> try doing a sudo apt-get dist-upgrade - it will upgrade those kernels for you.

It may also try and upgrade you to Edgy. I dont know if thats what the orignal poster wants since there is actualy less support time for Edgy. Dapper goes to 2009 on the desktop, Edgy has 6-8 months.

---

### Post by Kilz on 2007-07-19
> **pokechu said:**
> I keep getting these pop-up saying that the new updates are available. But I did a sudo apt-get update and sudo apt-get upgrade, but I get the following error or maybe whatever message. 

The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic


How should I fix it? Thanks. If there's another thread on this, I'm sorry I haven't done much work to search for it and please do provide the link there. Sorry for the inconvenience caused. Thanks for help!

Are you using the generic kernel, or are you using one of the alternates? What Im thinking is that there is some required package that isnt avilable yet. Wait a day or so to see. You can also try 

```
sudo apt-get install -f
```

---

### Post by ghandi69_ on 2007-07-19
> **Kilz said:**
> It may also try and upgrade you to Edgy. I dont know if thats what the orignal poster wants since there is actualy less support time for Edgy. Dapper goes to 2009 on the desktop, Edgy has 6-8 months.


I am pretty certain that 6.10 is edgy... and 6.06 is Dapper.

I was under the impression that edgy is no longer even supported?

I would suggest for the OP to go ahead and update to feisty.

---

### Post by deanjm1963 on 2007-07-19
the user is already using edgy. apt-get dist-upgrade would only upgrade to the next release if you were to edit your sources.list, e.g. change edgy to feisty.

the only "manual" way I could update my kernels a few days ago was to "dist-upgrade". the standard "upgrade" left the kernels behind.

---

### Post by Kilz on 2007-07-19
> **deanjm1963 said:**
> the user is already using edgy. apt-get dist-upgrade would only upgrade to the next release if you were to edit your sources.list, e.g. change edgy to feisty.

the only "manual" way I could update my kernels a few days ago was to "dist-upgrade". the standard "upgrade" left the kernels behind.

ya, misread that. If its a choice between Edgy and Feisty, go to Feisty.

---

### Post by pokechu on 2007-07-25
Thanks people for giving all the support, I think I kinda know what i should do then. Thanks everyone of you.

---

