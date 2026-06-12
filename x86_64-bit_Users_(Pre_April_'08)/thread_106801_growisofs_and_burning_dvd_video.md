---
title: "growisofs and burning dvd video"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by c2483 on 2005-12-21
I burnt 1 dvd video (video_ts/audio_ts) using 
growisofs  -Z /dev/hdc  -V WC -dvd-video -speed=1 /home/charles/Desktop/dvd 
and it burned so I could watch on my standalone dvd player even

however i tried to burn another copy later and i get
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

i tried different disc
i tried restarting
i tried enabling dma
what could the problem be

---

### Post by bonzodog on 2005-12-23
(theorising) -could it be that the first one you burnt was unprotected, and so burnt fine, but you then attempted to burn a protected DVD audio and video_ts?

---

### Post by paganini on 2006-01-07
I've seen cases where this happens because your DVD struct is not correct. A common problem is to have filenames in lowercase (such as "video_ts" instead of "VIDEO_TS") and so on. Perhaps, that's your case?

-- Paga

---

