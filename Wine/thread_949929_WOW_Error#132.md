---
title: "WOW Error#132"
date: 2008-10-16
forum: Wine
---

### Post by elias832 on 2008-10-16
I know a lot of threads are out there regarding this error. I tried almost everything and kept getting the error, so i wanted to post what had fixed my issue; maybe thats the case with a lot of Ubuntu users as well.


All you have to do after you install WOW in Wine is to copy this: 

SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"



and paste it in the config.wtf and the should do it.

---

