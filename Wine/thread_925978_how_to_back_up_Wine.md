---
title: "how to back up Wine?"
date: 2008-09-21
forum: Wine
---

### Post by Meow27 on 2008-09-21
i dont want to get into details. but can someone explain to me hwo i can make a backup of Wine so i can restore it when it gets screwed up.

ive tried to copy the wine folder elsewhere (which doesnt work out well)

ive tried compressing it but that ends up in disaster wherever i go 

and now im here.. does anyone know of a simple way to make a backup of everything in wine (thats located in the home folder of course)

(i prefer to have the ability of compressing it as well)

---

### Post by asdfoo on 2008-09-21
> **Meow27 said:**
> i dont want to get into details. but can someone explain to me hwo i can make a backup of Wine so i can restore it when it gets screwed up.

ive tried to copy the wine folder elsewhere (which doesnt work out well)

ive tried compressing it but that ends up in disaster wherever i go 

and now im here.. does anyone know of a simple way to make a backup of everything in wine (thats located in the home folder of course)

(i prefer to have the ability of compressing it as well)

Assuming you're using the default prefix:

tar cfz ~/wine-Mon-22-Sept-2008.tar.gz ~/.wine

---

