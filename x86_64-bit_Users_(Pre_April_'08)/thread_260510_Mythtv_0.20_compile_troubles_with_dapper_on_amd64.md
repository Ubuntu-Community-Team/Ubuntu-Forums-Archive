---
title: "Mythtv 0.20 compile troubles with dapper on amd64?"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-09-18
I'm trying to install mythtv on my athlon64 ubuntu installation and while trying to compile the new plugins;
```
./configure --prefix=/usr/local/mythtv-0.20 --enable-transcode --enable-vcd
qmake mythplugins.pro 
make

```

after a few second's compiling:

```
:main.cpp:(.text+0x2ba8f): undefined reference to `av_open_input_file'
:main.cpp:(.text+0x2bd59): undefined reference to `av_find_stream_info'
:main.cpp:(.text+0x2bd78): undefined reference to `av_estimate_timings'
:main.cpp:(.text+0x2bd96): undefined reference to `dump_format'
:main.cpp:(.text+0x2c078): undefined reference to `avcodec_string'
:main.cpp:(.text+0x2c81e): undefined reference to `av_close_input_file'
:main.cpp:(.text+0x2d691): undefined reference to `av_close_input_file'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_crc04C11DB7'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `url_seek'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_find_encoder_by_name'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `img_resample_init'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_init'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_alloc_format_context'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `udp_get_file_handle'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_seek_frame'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `url_write'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_default_get_buffer'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_log_set_level'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_probe_input_format'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_freep'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `img_resample_close'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_decode_audio'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `codec_id_string'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `url_open'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_mallocz'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_crc'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `img_resample'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_malloc'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_encode_video'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_read_frame_flush'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_dup_packet'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `mm_support'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `codec_type_string'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `url_close'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_alloc_context'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `av_rescale'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_decode_subtitle'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_align_dimensions'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `url_read'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_default_release_buffer'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `a52_syncinfo'
/usr/local/mythtv-0.20/lib/libmythtv-0.20.so: undefined reference to `avcodec_register_all'
collect2: ld returned 1 exit status
make[2]: *** [mytharchivehelper] Error 1
make[2]: Leaving directory `/opt/src/mythplugins-0.20a/mytharchive/mytharchivehelper'
make[1]: *** [sub-mytharchivehelper] Error 2
make[1]: Leaving directory `/opt/src/mythplugins-0.20a/mytharchive'
make: *** [sub-mytharchive] Error 2

```

---

### Post by mjziegle on 2006-09-21
Mytharchive doesn't work.

Run .configure --mytharchive-disable or something like that

Use ./configure --help for the exact option.

---

### Post by paulwaite on 2006-09-23
FWIW here are a couple of include typos I had to fix  so that the plugins would compile. This was at 
revision 11277 today, on the 0.20-fixes branch. No doubt these will be corrected pretty soon anyway but it might help you in hte meantime.

Cheers,
paul.

Index: mytharchive/mytharchive/archiveutil.cpp
===================================================================
--- mytharchive/mytharchive/archiveutil.cpp     (revision 11276)
+++ mytharchive/mytharchive/archiveutil.cpp     (working copy)
@@ -10,7 +10,7 @@

 // myth
 #include <mythtv/mythcontext.h>
-#include <libmythtv/programinfo.h>
+#include <mythtv/libmythtv/programinfo.h>

 // mytharchive
 #include "archiveutil.h"
Index: mytharchive/mytharchivehelper/main.cpp
===================================================================
--- mytharchive/mytharchivehelper/main.cpp      (revision 11276)
+++ mytharchive/mytharchivehelper/main.cpp      (working copy)
@@ -19,7 +19,7 @@
 #include <mythtv/mythdbcon.h>
 #include <ffmpeg/avcodec.h>
 #include <ffmpeg/avformat.h>
-#include <libmythtv/programinfo.h>
+#include <mythtv/libmythtv/programinfo.h>

 // mytharchive headers
 #include "../mytharchive/archiveutil.h"

---

### Post by paulwaite on 2006-09-23
Forgot to add - try doing your configure explicitly setting --prefix= same prefix as you defined with the main mythtv install.

I got this compilation error when I didn't define --prefix and somehow it had become nullstring, which meant the compilation was looking in /include/mythtv for the <ffmpeg/avformat.h> include, instead of /usr/include/mythtv (--prefix=/usr in my case).

---

