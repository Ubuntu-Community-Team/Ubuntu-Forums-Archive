---
title: "AMD64 and libdvdcss"
date: 2006-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joshua on 2006-12-20
This is really frustrating me.  If I were to:

Install libdvdread3,
Run the script and install libdvdcss2,
Ensure that my DVD player is set to the proper region,
and Install totem-xine

Can anyone think of a reason that totem would still complain that I'm trying to play an encrypted DVD without libdvdcss?

Or if I were to try easyubuntu after all of that, why wouldn't the DVD playing options be listed and fix eveything so that I can play DVDs?

---

### Post by Joshua on 2006-12-20
I forgot to mention that totem will play the federal warnings about copying and stuff that come at the beginning of movies, but then it will give me that error:

> The source seems encrypted and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?

I don't have any DVDs that aren't encrypted, but it looks like Totem would play them because it will play those warnings.

---

### Post by Azakus on 2006-12-21
Try VLC instead (I've always hated Totem). It has given better results for DVDs in my experience.

---

### Post by tszanon on 2006-12-21
> **Joshua said:**
> Run the script and install libdvdcss2
Where did you get the package from? The one I use is for Debian and works flawlessly.
Maybe the package is the one frustating your DVD experience?

---

### Post by Azakus on 2006-12-21
If you want, I built an AMD64 package for libdvdcss2. I'll attach it and you see if you want to use it.

---

### Post by Joshua on 2006-12-21
Well originally, I just updated my repositories with universe and multiverse, then installed libdvdread3, and then ran the script that comes with it.  So the script installed libdvdcss2 from whereever that script goes.  Then I tried the easyubuntu stuff but couldn't find the option for it in the tabs.  Then I installed xine-ui to see if maybe it was totem that was causing the problem, but it still didn't work.  Then I downloaded the source for libdvdcss2 from a PLF source, I think.  It looked like it compiled and installed fine, but it still wouldn't work.  And I think that source had a more recent version than the packages that I used.

I'll try VLC and the package from Azakus when I get home.  Thanks for the help.

---

### Post by Joshua on 2006-12-23
Ok, I tried VLC and the AMD64 package that was posted, but it still isn't working.  Is there any reason that the video programs may just not be associated with the decryption program properly?

---

### Post by Azakus on 2006-12-23
Whoa. I noticed in your sig that you are using Hoary. That package I made was for Edgy, so I'm pretty sure it wont work. Try this script (it will build one for you).
```
wget http://download.videolan.org/pub/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.bz2
tar -xjf libdvdcss-1.2.9.tar.bz2
cd ./libdvdcss-1.2.9
sudo aptitude install build-essential checkinstall automake1.9
./configure --prefix=/usr
make
sudo checkinstall

```

---

### Post by BIGtrouble77 on 2006-12-23
I would highly recommend upgrading hoary to at least dapper.  The improvements to gnome have been pretty substantial.  It's much faster with some critical new features.  I also had tons of issues with DVD playback in hoary.  Getting fluid playback was such a bitch.

---

### Post by Azakus on 2006-12-23
> **BIGtrouble77 said:**
> I would highly recommend upgrading hoary to at least dapper.  The improvements to gnome have been pretty substantial.  It's much faster with some critical new features.  I also had tons of issues with DVD playback in hoary.  Getting fluid playback was such a bitch.

I agree. Dapper is at least still directly supported, not just through backports. An upgrade to Dapper (or Edgy) would probably alleviate this problem.

---

### Post by Joshua on 2006-12-25
Uh-oh... Sorry for the confusion.  That's an old signature, and I've been on vacation so I haven't been able to check this very often.  I'm using Edgy on an Averatec 2370.  It's nVidia geforce go 6100 graphics with an AMD64 x2 processor.

---

### Post by Joshua on 2006-12-28
This is what happens when I run xine:

```
joshua@Mossy:/media/cdrom$ sudo xine
This is xine (X11 gui) - a free video player v0.99.4.
(c) 2000-2004 The xine Team.
joshua@Mossy:/media/cdrom$ sudo xine
This is xine (X11 gui) - a free video player v0.99.4.
(c) 2000-2004 The xine Team.
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000003fa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000074a
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000082a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000840
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000008b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000017e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00001851
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000025fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00002600
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002620
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00002690
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0000ec72
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0008d5a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0008d5f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0009c2c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003c7cb7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003d4abb
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 3
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


```

---

### Post by Joshua on 2006-12-28
Sorry, I posted too soon.  Also, I figured out that I can get "verbose" info from xine.  Does this info give anyone any insight into why I can't watch the DVD?

```

joshua@Mossy:/media/cdrom$ sudo xine --verbose
Password:
This is xine (X11 gui) - a free video player v0.99.4.
(c) 2000-2004 The xine Team.
Built with xine library 1.1.1 (1.1.1)
Found xine library version: 1.1.2 (1.1.2).
   Plateform informations:
   ----------------------
        system name     : Linux
        node name       : Mossy
        release         : 2.6.17-10-generic
        version         : #2 SMP Tue Dec 5 21:16:35 UTC 2006
        machine         : x86_64
   CPU Informations:
   ----------------
        processor       : 0
        vendor_id       : AuthenticAMD
        cpu family      : 15
        model           : 72
        model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
        stepping        : 2
        cpu MHz         : 800.000
        cache size      : 256 KB
        physical id     : 0
        siblings        : 2
        core id         : 0
        cpu cores       : 2
        fpu             : yes
        fpu_exception   : yes
        cpuid level     : 1
        wp              : yes
        flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
        bogomips        : 1609.54
        TLB size        : 1024 4K pages
        clflush size    : 64
        cache_alignment : 64
        address sizes   : 40 bits physical, 48 bits virtual
        power management: ts fid vid ttp tm stc
        processor       : 1
        vendor_id       : AuthenticAMD
        cpu family      : 15
        model           : 72
        model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
        stepping        : 2
        cpu MHz         : 800.000
        cache size      : 256 KB
        physical id     : 0
        siblings        : 2
        core id         : 1
        cpu cores       : 2
        fpu             : yes
        fpu_exception   : yes
        cpuid level     : 1
        wp              : yes
        flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
        bogomips        : 1609.54
        TLB size        : 1024 4K pages
        clflush size    : 64
        cache_alignment : 64
        address sizes   : 40 bits physical, 48 bits virtual
        power management: ts fid vid ttp tm stc
   -------
   Display Name:          :0.0,
   XServer Vendor:        The X.Org Foundation,
   Protocol Version:      11, Revision: 0,
   Available Screen(s):   1,
   Default screen number: 0,
   Using screen:          0,
   Depth:                 24,
   XShmQueryVersion:      1.1,
-[ xiTK version 0.10.7 [XFT] ]-[ WM type: (EWMH) Metacity {Metacity} ]-
Display is not using Xinerama.
load_plugins: skipping unreadable plugin directory /root/.xine/plugins.
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_arts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_real_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.1.2/xineplug_decode_mad.so found
main: probing <dxr3> video output plugin
video_out_dxr3: Failed to open control device /dev/em8300-0 (No such file or directory)
main: probing <aadxr3> video output plugin
main: probing <xv> video output plugin
video_out_xv: using Xv port 275 from adaptor NV17 Video Texture for hardware colorspace conversion and scaling.
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
main: probing <alsa> audio output plugin
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) (5.1-channel not enabled in xine config) (a/52 and DTS pass-through not enabled in xine config)
video_out_xv: VO_PROP_ASPECT_RATIO(0)
gui_xine_open_and_play():
        mrl: 'file:/usr/share/xine/skins/xine-ui_logo.mpv',
        sub 'NONE',
        start_pos 0, start_time 0, av_offset 0, spu_offset 0.
xine: found input plugin  : file input plugin
ebml: invalid EBML ID size (0x0) at position 1
ebml: invalid master element
xine: found demuxer plugin: Elementary MPEG stream demux plugin
av_offset=0 pts
spu_offset=0 pts
video_out: throwing away image with pts 56030 because it's too old (diff : 10009).
video_out: throwing away image with pts 59030 because it's too old (diff : 7009).
video_out: throwing away image with pts 62030 because it's too old (diff : 4009).
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
gui_xine_open_and_play():
        mrl: 'dvd:/',
        sub 'NONE',
        start_pos 0, start_time 0, av_offset 0, spu_offset 0.
xine: found input plugin  : DVD Navigator
libdvdnav: Using dvdnav version 1.1.2 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdcss debug: opening target `/dev/dvd'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: cracking disc key 72:9b:1d:1f:03
libdvdcss debug: initializing the big table
libdvdcss debug: cracked disc key is 6a:66:8e:1e:78
libdvdcss debug: using CSS key cache dir: /root/.dvdcss//ROCKYHORROR-2000081715270600-6a668e1e78/
libdvdcss debug: cannot open /dev/rdvd (No such file or directory)
libdvdcss error: failed to open raw device, but continuing
libdvdnav: DVD Title: ROCKYHORROR
libdvdnav: DVD Serial Number: 29117EC3
libdvdnav: DVD Title (Alternative): ROCKYHORROR
libdvdnav: Unable to find map file '/home/joshua/.dvdnav/ROCKYHORROR.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000003fa
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000074a
libdvdcss debug: title key found in cache ca:a3:db:03:0c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000082a
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000840
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000008b0
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000017e1
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00001851
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000025fb
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00002600
libdvdcss debug: title key found in cache ca:a3:db:03:1f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002620
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00002690
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0000ec72
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0008d5a5
libdvdcss debug: title key found in cache ca:a3:db:03:29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0008d5f1
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0009c2c1
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003c7cb7
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003d4abb
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
xine: found demuxer plugin: DVD/VOB demux plugin
av_offset=0 pts
spu_offset=0 pts
audio_decoder: error, unknown buffer type: 02000000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
libdvdnav: Suspected RCE Region Protection!!!
audio_decoder: error, unknown buffer type: 02000000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
video_out: throwing away image with pts 971444 because it's too old (diff : 18425).
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
audio_decoder: error, unknown buffer type: 02000000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
libdvdcss error: no key but found encrypted block
libdvdcss error: no key but found encrypted block
demux_mpeg_block: warning: PES header indicates that this stream may be encrypted (encryption mode 1)

---------------------- (ERROR) ----------------------
The source seems encrypted, and can't be read.
Your DVD is probably crypted. According to your country laws, you can or can't install/use libdvdcss to be able to read this disc, which you bought. (Media stream scrambled/encrypted)
------------------ (END OF ERROR) -------------------


---------------------- (ERROR) ----------------------
The source seems encrypted, and can't be read.
Your DVD is probably crypted. According to your country laws, you can or can't install/use libdvdcss to be able to read this disc, which you bought. (Media stream scrambled/encrypted)
------------------ (END OF ERROR) -------------------

gui_xine_open_and_play():
        mrl: 'file:/usr/share/xine/skins/xine-ui_logo.mpv',
        sub 'NONE',
        start_pos 0, start_time 0, av_offset 0, spu_offset 0.
xine: found input plugin  : file input plugin
ebml: invalid EBML ID size (0x0) at position 1
ebml: invalid master element
xine: found demuxer plugin: Elementary MPEG stream demux plugin
av_offset=0 pts
spu_offset=0 pts


```

---

### Post by Joshua on 2006-12-29
Well, last night I went into Synaptic and uninstalled (for complete removal) all the programs related to DVD playback that I could think of:

libdvdcss2
libdvdread3
libdvdnav
xine-ui
totem-xine

I think that's all of them, but there were some dependencies that also got removed automatically.  Then, I went back and resinstalled all of them at the same time.  This means that I used the libdvdcss2 that is in the PLF repository rather than whatever the script in libdvdread3 will get me.

Anyway, STILL NO LUCK!

I would just erase the partition and start from scratch with a brand new Ubuntu install, but that would take a lot of time because of some of the hardware in the laptop.  So I don't want to do it unless I'm sure it will work.  Or maybe I should just go to 32-bit.  It seems like people have fewer problems with it...

---

### Post by janfsd on 2006-12-29
Maybe you should try with Mplayer, for me that's the best player.

---

### Post by Grugs on 2007-02-24
When trying to play a dvd with mplayer, with or without the above deb package installed, I get:

```
Error opening/initializing the selected video_out (-vo) device.
```

Is that related?

---

### Post by John.Michael.Kane on 2007-02-24
What worked for me was installing libdvdread3,and totem-xine.

Run sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by cvmirage on 2007-02-28
I am having the exact same issue. I have installed everything related to libdvd
(
libdvdcss2
libdvdread3
libdvdnav
xine-ui
totem-xine
)

It is still not working. I have tried reinstalling all libdvd packages, it still does not work. It loads the dvd just fine (including menus), but once it passes the fbi warning and trys to play the dvd,  I get the same error as above. My guess is that it is an issue with the 64 bit libdvdcss2 or libdvdread3 is not triggering / finding libdvdcss2 like its suppose to once the dvd starts. 

Please only reply if you use the AMD64 arch.

---

### Post by Lonthong on 2007-02-28
Hi, I suggest you uninstall every DVD related things & try the following that worked for me:

Enable universe & multiverse
sudo apt-get install totem-xine libxine-extracodecs
sudo apt-get install debhelper build-essential fakeroot

DVD subtitle
sudo apt-get install liba52-0.7.4-dev libdvdread-dev libdvdnav-dev
sudo /usr/share/doc/libdvdread3/install-css.sh

Totem-xine will now autoplay DVD but not VCD, to autoplay vcd:
terminal: gconf-editor
configuration editor: desktop - gnome - volume_manager
check autoplay vcd
autoplay vcd command = totem vcd://

Totem-xine cannot play wmv9 files, for this I have to install mplayer
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 ia32-libs-openoffice.org
wget [http://www.people.virginia.edu/~drf8...060501.tar.bz2](http://www.people.virginia.edu/~drf8...060501.tar.bz2)
tar -jxvf essential-20060501.tar.bz2
sudo mkdir /usr/lib/win32
sudo cp essential-20060501/* /usr/lib/win32/
sudo apt-get install mplayer
sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer

> **Grugs said:**
> When trying to play a dvd with mplayer, with or without the above deb package installed, I get:

```
Error opening/initializing the selected video_out (-vo) device.
```

Is that related?

Right after installing mplayer I also faced that same problem. You should change yr video output device
Issue the following command to get a list of available video output drivers:
mplayer -vo help
select  a video driver (for me was a trial and error) and add it to your configuration file:
vo = selected_vo to ~/.mplayer/config  and/or
vo_driver = selected_vo to ~/.mplayer/gui.conf. 

Hope this solution will work for you

---

### Post by John.Michael.Kane on 2007-02-28
Those still having issue with this please see post three [http://www.ubuntuforums.org/showthread.php?t=369361&highlight=libdvdread3](http://www.ubuntuforums.org/showthread.php?t=369361&highlight=libdvdread3)

---

### Post by cvmirage on 2007-03-01
I downloaded and installed the official nvidia drivers for my 6800 card and dvd playback is now working.

---

### Post by Corbelius on 2007-03-01
[http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/libdvdcss2_1.2.9-1ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/edgy-janvitus/main-amd64/libdvdcss2_1.2.9-1ubuntu1~janvitus_amd64.deb)

:)

---

### Post by canre on 2008-05-29
> **lonthong said:**
> words


Ty!!

---

