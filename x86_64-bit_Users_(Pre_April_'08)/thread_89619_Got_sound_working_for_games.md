---
title: "Got sound working for games"
date: 2005-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ryba on 2005-11-13
Well I couldn't find an answer to this question but I have seen lots of people asking it. It really was quite simple.

The problem is that some random games just don't have sound. Other games do. For instance, UT2k3 did not have sound but Heroes of Might and Magic did. They both used SDL and openAL and the same version of the libs so why the no sound?

Answer ended up being a lot simplier then I thought. Those games are missing some dependency libraries. In the case of UT2k3 it was missing the libsmpeg-0.4.so.0 library. So I should have just copied that file over from a working game but I didn't think of that one at first. Instead what I did was google search for a debian package that had the 32bit version of libsmpeg, extracted it to the /tmp folder (dpkg -x package-name.deb /tmp) and then manually copied over that file to the ut2003/System folder. Voila instant success :)

If that does not work for you do an (ldd ut2003/System/openal.so) and then see what it cannot find. Then just make sure everything it cannot find is in the ut2003/System folder with read permissions. That is how I tracked down the missing library to make the stuff work finally :)

---

