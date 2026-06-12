---
title: "wine+DoW+multiple isos"
date: 2008-01-08
forum: Wine
---

### Post by hOmerscousin on 2008-01-08
Hey everyone,

I am trying to install Dawn of War 40K, Winehq says they can get through installation and give it a silver rating. I have created iso's for the three cd's and I am using Gmount to mount them.

I created /media/iso as the mount point and set that mount point as a drive in wine (Z: /media/iso). The install starts but when  I wine eject -a and try to unmount the iso Gmount refuses to unmount it.

Once I killed wine, Gmount unmounted the iso without a problem. I am  using wine verision: 0.9.46. I really would prefer not to burn the images... Any suggestions???

---

### Post by Stormspireiv on 2008-01-26
Unfortunately, the only way I know to get that to work is burn the CDs.  Wine eject doesn't seem to like mounted iso files.  I know for a fact that it will work if you burn the discs and use wine eject (I too was in the same boat when I couldn't find my DoW original discs but had iso files of them).

---

