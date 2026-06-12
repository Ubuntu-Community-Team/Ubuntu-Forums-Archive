---
title: "vlc 0.8.5 in universe"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by debian2003 on 2006-05-07
I have just compiled the vlc 0.8.5 on eMac G4, because I found only the 0.8.4 in the ubuntu universe packages. Now with the new compiled vlc I can play a movie like [http://insitu.lri.fr/~roussel/videos/metisse/metisse/metisse.mov](http://insitu.lri.fr/~roussel/videos/metisse/metisse/metisse.mov) (I could not played with 0.8.4).  Can I put my compiled deb package to universe section (to update the package). Can anyone tell how can I do that (I never tried)?

---

### Post by jaka on 2006-06-05
deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

gpg --keyserver subkeys.pgp.net --recv 81CACA84
gpg --export --armor 81CACA84  | sudo apt-key add -

---

### Post by elwood_j_blues on 2006-07-04
This helps a lot, thanks.

---

