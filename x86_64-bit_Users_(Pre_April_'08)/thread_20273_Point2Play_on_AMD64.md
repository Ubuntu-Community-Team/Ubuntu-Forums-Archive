---
title: "Point2Play on AMD64"
date: 2005-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kemotaha on 2005-03-15
Anyone able to DL the new version of Cedega with point2play in AMD 64?

---

### Post by Mike Douglas on 2005-03-16
I ran into a corrupted file error when trying to update Cedega through Point2Play on my AMD64, but a quick fix is to chroot into a 32-bit setup and run the update through there.

---

### Post by dmatrix on 2005-03-16
This can be done now without a 32bit chroot on Hoary.

Follow these instructions:

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot)

---

### Post by dmatrix on 2005-03-16
Sorry I forgot to mention that I had no problems downloading the new version in point2play. But I did have to update the proper winex3 file with lib32 stuff as noted in the wiki article. Before I updated the proper winex3 file with lib32 stuff it just kept crashing.

---

### Post by Kemotaha on 2005-03-16
I had it done without the chroot environment.  I think my problem was not changing the variables.  I had forgotten about that part.  I has been a while.  If you make those changes are you able to download Cedega from with in P2P?

---

### Post by Kemotaha on 2005-03-16
The variables didn't do it.  I did find the problem though.

You have to use the point2play-small version.  The full version has libraries built in that don't work.

Works find now. :)

---

### Post by rj3 on 2005-03-19
Point2Play /Cedega working fine on AMD 64/K8V SE / nVidia 5700  /SuSE 9.2 ,

---

