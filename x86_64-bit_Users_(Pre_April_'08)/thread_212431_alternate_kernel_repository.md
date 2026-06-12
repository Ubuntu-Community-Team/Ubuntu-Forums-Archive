---
title: "alternate kernel repository?"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mysfitt on 2006-07-09
Hello all,

Long time user, first time poster. Don't hold it against me ;)

I've just loaded up a Opteron system with Dapper, and it was very painful to get a working system due to a SATA driver issue with the Marvell chipset (sata_mv). I finally got something going by attaching an old ata drive that i had lying around and installing to it. After doing extensive research, i've found that there's a much improved version of the driver in the 2.6.17 kernel. (as in, it might actually attach my disk!)

My question is: are there alternate repositories maintained by individuals for newer kernel versions than what comes with Dapper? I could always compile one from source, but would prefer a repo for maintainability.

TIA :)

---

### Post by RAOF on 2006-07-09
I've **tried** to make one, but although I can build the pacakages just fine, it's more difficult to actually turn them into a repository.  There's a different package building system involved for kernels, & I haven't quite worked it out :)

---

### Post by mysfitt on 2006-07-09
Well, if you've got a deb for 2.6.17 amd64, I'd certainly be happy to give it a try :D

Btw, it occured to me that backports might be a good place to look. Good idea or bad idea? In other words, do backports kernels tend to be unstable?

---

### Post by RAOF on 2006-07-09
> **mysfitt said:**
> Well, if you've got a deb for 2.6.17 amd64, I'd certainly be happy to give it a try :D

Btw, it occured to me that backports might be a good place to look. Good idea or bad idea? In other words, do backports kernels tend to be unstable?
Actually, I've got debs for 2.6.17-mm6 :).  I really just wanted to play with reiser4, kernel ntfs writing support.  And until recently, my DVB card wasn't supported in vanilla kernels :)

Get them from [raof.dyndns.org](raof.dyndns.org), if you want.

---

### Post by mysfitt on 2006-07-09
> **RAOF said:**
> Actually, I've got debs for 2.6.17-mm6 :).  I really just wanted to play with reiser4, kernel ntfs writing support.  And until recently, my DVB card wasn't supported in vanilla kernels :)

Get them from [raof.dyndns.org](raof.dyndns.org), if you want.

Many thanks. I'm downloading it now. I'll let you know how it works out.

---

