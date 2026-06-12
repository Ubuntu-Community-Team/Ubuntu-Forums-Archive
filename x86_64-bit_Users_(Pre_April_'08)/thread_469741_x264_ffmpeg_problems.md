---
title: "x264 ffmpeg problems"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by chronosoft on 2007-06-10
Hi there, i'm trying to encode a video with x264, but for some reason (though i have compiled and installed videolan's x264) ffmpeg ./configure script is not picking up x264 even though i specified ./configure --enable-libx264 --enable-gpl i just get

ERROR: x264 not found

**note, when i tried to compile x264 with mp4 output support, i got a whole lot of "muxers.c:774: error:" errors and could not compile x264, but without it, it compiled.

---

### Post by pay on 2007-06-10
Type```
x264 --help 
```and make sure that x264 is installed properly. If it says command not found then it isn't.

---

### Post by chronosoft on 2007-06-10
As i said before with when i ./configure --enable-mp4-output it doesn't compile (and i just don't know why) e.g.  the make with this configuration enabled

> rm -f .depend
( echo -n "`dirname common/mc.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/csp.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/csp.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/mc-c.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/i386/mc-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/predict-c.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/i386/predict-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  matroska.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname muxers.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  muxers.c -MM -g0 ) 1>> .depend;
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o x264.o x264.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o matroska.o matroska.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o muxers.o muxers.c
muxers.c:43:27: error: gpac/isomedia.h: No such file or directory
muxers.c:554: error: expected specifier-qualifier-list before ‘GF_ISOFile’
muxers.c:568: error: expected ‘)’ before ‘*’ token
muxers.c: In function ‘close_file_mp4’:
muxers.c:620: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:621: warning: implicit declaration of function ‘gf_odf_avc_cfg_del’
muxers.c:621: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:623: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:625: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:626: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:628: warning: implicit declaration of function ‘gf_isom_sample_del’
muxers.c:628: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:631: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:633: warning: implicit declaration of function ‘recompute_bitrate_mp4’
muxers.c:633: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:633: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:634: warning: implicit declaration of function ‘gf_isom_set_pl_indication’
muxers.c:634: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:634: error: ‘GF_ISOM_PL_VISUAL’ undeclared (first use in this function)
muxers.c:634: error: (Each undeclared identifier is reported only once
muxers.c:634: error: for each function it appears in.)
muxers.c:635: warning: implicit declaration of function ‘gf_isom_set_storage_mode’
muxers.c:635: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:635: error: ‘GF_ISOM_STORE_FLAT’ undeclared (first use in this function)
muxers.c:636: warning: implicit declaration of function ‘gf_isom_close’
muxers.c:636: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c: In function ‘open_file_mp4’:
muxers.c:654: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:654: warning: implicit declaration of function ‘gf_isom_open’
muxers.c:654: error: ‘GF_ISOM_OPEN_WRITE’ undeclared (first use in this function)
muxers.c:656: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:656: warning: implicit declaration of function ‘gf_isom_sample_new’
muxers.c:662: warning: implicit declaration of function ‘gf_isom_set_brand_info’
muxers.c:662: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:662: error: ‘GF_ISOM_BRAND_AVC1’ undeclared (first use in this function)
muxers.c: In function ‘set_param_mp4’:
muxers.c:674: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:674: warning: implicit declaration of function ‘gf_isom_new_track’
muxers.c:674: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:674: error: ‘GF_ISOM_MEDIA_VISUAL’ undeclared (first use in this function)
muxers.c:677: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:677: warning: implicit declaration of function ‘gf_odf_avc_cfg_new’
muxers.c:678: warning: implicit declaration of function ‘gf_isom_avc_config_new’
muxers.c:678: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:678: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:678: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:679: error: ‘mp4_t’ has no member named ‘i_descidx’
muxers.c:681: warning: implicit declaration of function ‘gf_isom_set_track_enabled’
muxers.c:681: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:681: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:683: warning: implicit declaration of function ‘gf_isom_set_visual_info’
muxers.c:683: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:683: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:683: error: ‘mp4_t’ has no member named ‘i_descidx’
muxers.c:686: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:687: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:690: error: ‘mp4_t’ has no member named ‘i_time_res’
muxers.c:691: error: ‘mp4_t’ has no member named ‘i_time_inc’
muxers.c:692: error: ‘mp4_t’ has no member named ‘i_init_delay’
muxers.c:693: error: ‘mp4_t’ has no member named ‘i_init_delay’
muxers.c:693: error: ‘mp4_t’ has no member named ‘i_time_inc’
muxers.c:695: error: ‘mp4_t’ has no member named ‘i_init_delay’
muxers.c:695: error: ‘mp4_t’ has no member named ‘i_time_res’
muxers.c: In function ‘write_nalu_mp4’:
muxers.c:704: error: ‘GF_AVCConfigSlot’ undeclared (first use in this function)
muxers.c:704: error: ‘p_slot’ undeclared (first use in this function)
muxers.c:712: error: ‘mp4_t’ has no member named ‘b_sps’
muxers.c:714: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:715: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:716: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:717: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:718: error: expected expression before ‘)’ token
muxers.c:722: warning: implicit declaration of function ‘gf_list_add’
muxers.c:722: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:724: error: ‘mp4_t’ has no member named ‘b_sps’
muxers.c:730: error: ‘mp4_t’ has no member named ‘b_pps’
muxers.c:732: error: expected expression before ‘)’ token
muxers.c:736: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:738: error: ‘mp4_t’ has no member named ‘b_pps’
muxers.c:739: error: ‘mp4_t’ has no member named ‘b_sps’
muxers.c:740: warning: implicit declaration of function ‘gf_isom_avc_config_update’
muxers.c:740: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:740: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:740: error: ‘mp4_t’ has no member named ‘p_config’
muxers.c:749: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:749: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:750: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:750: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:751: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:751: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:752: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:752: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:753: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:753: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:754: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c: In function ‘set_eop_mp4’:
muxers.c:764: error: ‘mp4_t’ has no member named ‘i_numframe’
muxers.c:764: error: ‘mp4_t’ has no member named ‘i_time_inc’
muxers.c:766: error: ‘mp4_t’ has no member named ‘i_init_delay’
muxers.c:768: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:769: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:770: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:771: warning: implicit declaration of function ‘gf_isom_add_sample’
muxers.c:771: error: ‘mp4_t’ has no member named ‘p_file’
muxers.c:771: error: ‘mp4_t’ has no member named ‘i_track’
muxers.c:771: error: ‘mp4_t’ has no member named ‘i_descidx’
muxers.c:771: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:773: error: ‘mp4_t’ has no member named ‘p_sample’
muxers.c:774: error: ‘mp4_t’ has no member named ‘i_numframe’
make: *** [muxers.o] Error 1

but, if i compile without the "--enable-mp4-output" it compiles cleanly e.g. [B]./configure 
sudo make (compiles cleanly here)
sudo make install
(sudo make install output)[/B]
> install -d /usr/local/bin /usr/local/include
install -d /usr/local/lib /usr/local/lib/pkgconfig
install -m 644 x264.h /usr/local/include
install -m 644 libx264.a /usr/local/lib
install -m 644 x264.pc /usr/local/lib/pkgconfig
install x264 /usr/local/bin
ranlib /usr/local/lib/libx264.a

now having x264 installed without mp4 output support, and trying to compile ffmpeg (SVN) with x264 support e.g. **./configure --enable-libx264 --enable-gpl**
I get this
> ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-devel@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.


---

### Post by chronosoft on 2007-06-12
:( no ideas?

---

### Post by pay on 2007-06-12
Try using a slightly older snapshot. [ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20070325-2245.tar.bz2](ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20070325-2245.tar.bz2) 
This has the same rev number than the latest svn checkout so I'm guessing that theres not a whole lot differnt.

---

### Post by TheMono on 2007-06-12
As I recall it is something to do with pthreads... At least, I think it was that that did it for me. Try adding 

--enable-pthreads 

as the first flag when configuring... 

I may be on the complete wrong track with my memory failing me though.

---

### Post by danny.hajicek on 2007-06-14
Here's what I did to make it work (I think. I'm encoding something right now so I'll see.)

I downloaded the gpac source package and copied the /gpac/include/gpac directory into x264 source directory so directory x264... contained a folder called gpac with some headers and such.

I configured with mp4 support and then ran make.

I got an error about missing lgpac_static and make died.

I ran the command:

 gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -lgpac -s

(I just took "_static" out of it)

Then I ran sudo make install.

So far, so good :-)

---

### Post by agikthomas on 2008-05-10
Hey, 

Make sure you built x264 with the "--enable-shared" option and that you
ran (as root) /sbin/ldconfig immediately after your "make install".

Then go back to the ffmpeg source tree, "make distclean" and start
again.


This should work.:guitar:

---

