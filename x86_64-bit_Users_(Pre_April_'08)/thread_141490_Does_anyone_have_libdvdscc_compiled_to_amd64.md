---
title: "Does anyone have libdvdscc compiled to amd64 ?"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by tim67 on 2006-03-08
it seems that i cant compile it. doesanyone have binaries for it / compilation instructions ? agan, bootstrap & configure work ok, but during make I'l get this
error:

ffmpeg.c:49:44: error: libpostproc/postprocess.h: No such file or directory

and then

make[6]: *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[6]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/timo67/libdvdscc_sources/vlc-trunk'
make: *** [all] Error 2

-timo

---

