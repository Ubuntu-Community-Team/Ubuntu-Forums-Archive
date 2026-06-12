---
title: "Transcode Error in Kubuntu Edgy 64bit Core 2 Duo"
date: 2007-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by prince_niceguy on 2007-02-22
i am having kubuntu edgy 64 bit on my intel core 2 duo 1.66GHz system. When I try to transcode a movie I get the following error.

Job 'Transcode - title #3, chapter #1' failed with error message:
Job 'Transcode video - title #3, chapter #1, pass 2' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/prince/dvdrip/seinfeld/tmp' && cd /home/prince/dvdrip/seinfeld/tmp && mkdir -p /home/prince/dvdrip/seinfeld/avi/003 && execflow -n 19 transcode -H 10 -a 0 -T 3,1,1 -x dvd -i /media/USBCurrent/Azureus/seinfelds4d1 -w 1000,50 -b 160 -s 4 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 25 -Y 6,4,4,4 -Z 504x378 -R 2 -y xvid,ogg -m /home/prince/dvdrip/seinfeld/avi/003/seinfeld-003-C001-00.ogm -o /home/prince/dvdrip/seinfeld/avi/003/seinfeld-003-C001.ogm --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(dvd_reader.c) DVD title 3/17: 7 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 00:45:04.08 2705 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 673652 to 673665
(dvd_reader.c) [Chapter 02] 00:00:41.520 , block from 673652 to 673665
(dvd_reader.c) [Chapter 03] 00:12:58.920 , block from 673652 to 673665
(dvd_reader.c) [Chapter 04] 00:22:16.080 , block from 673652 to 673665
(dvd_reader.c) [Chapter 05] 00:31:03.240 , block from 673652 to 673665
(dvd_reader.c) [Chapter 06] 00:44:19.800 , block from 673652 to 673665
(dvd_reader.c) [Chapter 07] 00:45:03.160 , block from 673652 to 673665
tc_memcpy: using amd64 for memcpy
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[export_xvid4.so] v0.0.5 (2003-12-05) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /media/USBCurrent/Azureus/seinfelds4d1 (ok)
[transcode] V: import format | MPEG-2 DVD PAL (V=dvd|A=dvd)
[transcode] V: AV demux/sync | (1) sync AV at initial MPEG sequence
[transcode] V: import frame | 720x576 1.25:1 encoded @ 4:3
[transcode] V: zoom | 504x378 1.33:1 (Lanczos3)
[transcode] V: clip frame (->) | 496x368
[transcode] V: bits/pixel | 0.219
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: multi-pass | (mode=2) reading data (pass2) from divx4.log
[transcode] V: Y'CbCr | YV12/I420
[transcode] A: import format | 0x2000 AC3 [48000,16,2]
[transcode] A: export format | 0x55 MPEG layer-3 [48000,16,2] 160 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: language | en
[transcode] A: bytes per frame | 7680 (7680.000000)
[transcode] A: adjustment | 0@1000
[transcode] A: rescale stream | 4.000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: video buffer | 10 @ 720x576
[filter_smartyuv.so] options=threshold=10:Blend=1:diffmode=2:highq=1
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[import_dvd.so] tccat -T 3,1,1 -i "/media/USBCurrent/Azureus/seinfelds4d1" -t dvd -d 0 -L | tcdemux -a 0 -x ac3 -S 0 -M 1 -d 0 | tcextract -t vob -x ac3 -a 0 -d 0 | tcdecode -x ac3 -d 0 -s 1.000000,1.000000,1.000000 -A 1
[import_dvd.so] tccat -T 3,1,1 -i "/media/USBCurrent/Azureus/seinfelds4d1" -t dvd -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[import_dvd.so] delaying DVD access by 3 second(s)
.tc_memcpy: using amd64 for memcpy
..tc_memcpy: using amd64 for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
[export_xvid4.so] Reading configuration from './xvid4.cfg'
[export_xvid4.so] Reading config section 'features' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'quantizer' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'cbr' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'vbr' from './xvid4.cfg'
[export_ogg.so] oggenc -r -B 16 -C 2 -b 160 -R 48000 -Q -o "/home/prince/dvdrip/seinfeld/avi/003/seinfeld-003-C001-00.ogm" -
Illegal instruction

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
Please help....

---

### Post by kuja on 2007-02-22
Well, it certainly looks like it could be some sort of bug in the export_ogg.so to me, but hard to be sure eh? Try experimenting with different audio options, for a test you could try just passing through the AC3 or something, or perhaps MP3. That would rule out the possibility of the problem being anywhere else, not sure where to go from there.

---

### Post by prince_niceguy on 2007-02-22
I tried using mp3 earlier but it was giving error some illegal instruction. not sure what is the error. haven't tried out the ac3 option... will check that and post it back...

thanks for the suggestion Kuja!!! :)

---

### Post by prince_niceguy on 2007-02-23
i tried out ac3... but it seems it is a transcode error... 

Job 'Transcode - title #3, chapter #1' failed with error message:
Job 'Transcode video - title #3, chapter #1, pass 2' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/prince/dvdrip/seinfeld/tmp' && cd /home/prince/dvdrip/seinfeld/tmp && mkdir -p /home/prince/dvdrip/seinfeld/avi/003 && execflow -n 19 transcode -H 10 -a 0 -T 3,1,1 -x dvd -i /media/USBCurrent/Azureus/seinfelds4d1 -w 1000,50 -A -N 0x2000 -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 25 -Y 6,4,4,4 -Z 504x378 -R 2 -y xvid -m /home/prince/dvdrip/seinfeld/avi/003/seinfeld-003-C001-00.ogm -o /home/prince/dvdrip/seinfeld/avi/003/seinfeld-003-C001.ogm --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(dvd_reader.c) DVD title 3/17: 7 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 00:45:04.08  2705 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 673652 to 673665
(dvd_reader.c) [Chapter 02] 00:00:41.520 , block from 673652 to 673665
(dvd_reader.c) [Chapter 03] 00:12:58.920 , block from 673652 to 673665
(dvd_reader.c) [Chapter 04] 00:22:16.080 , block from 673652 to 673665
(dvd_reader.c) [Chapter 05] 00:31:03.240 , block from 673652 to 673665
(dvd_reader.c) [Chapter 06] 00:44:19.800 , block from 673652 to 673665
(dvd_reader.c) [Chapter 07] 00:45:03.160 , block from 673652 to 673665
tc_memcpy: using amd64 for memcpy
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_xvid4.so] v0.0.5 (2003-12-05) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /media/USBCurrent/Azureus/seinfelds4d1 (ok)
[transcode] V: import format    | MPEG-2 DVD PAL (V=dvd|A=dvd)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 4:3
[transcode] V: zoom             | 504x378  1.33:1 (Lanczos3)
[transcode] V: clip frame (->)  | 496x368
[transcode] V: bits/pixel       | 0.219
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: multi-pass       | (mode=2) reading data (pass2) from divx4.log
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x2000  AC3          [48000,16,2]    0 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: language         | en
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: video buffer     | 10 @ 720x576
[filter_smartyuv.so] options=threshold=10:Blend=1:diffmode=2:highq=1
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[import_dvd.so] tccat -T 3,1,1 -i "/media/USBCurrent/Azureus/seinfelds4d1" -t dvd -d 0 -L | tcdemux -a 0 -x ac3 -S 0 -M 1 -d 0 | tcextract -t vob -x ac3 -a 0 -d 0 | tcextract -t raw -x ac3 -d 0
[import_dvd.so] tccat -T 3,1,1 -i "/media/USBCurrent/Azureus/seinfelds4d1" -t dvd -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[import_dvd.so] delaying DVD access by 3 second(s)
.tc_memcpy: using amd64 for memcpy
tc_memcpy: using amd64 for memcpy
..(ac3scan.c) AC3 frame 128 (160) bytes | bitrate 32 kBits/s | depsize 7680 | rbytes 160.000000
tc_memcpy: using amd64 for memcpy
[export_xvid4.so] Reading configuration from './xvid4.cfg'
[export_xvid4.so] Reading config section 'features' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'quantizer' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'cbr' from './xvid4.cfg'
[export_xvid4.so] Reading config section 'vbr' from './xvid4.cfg'
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
Illegal instruction

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------

---

### Post by prince_niceguy on 2007-04-18
now it works with the transcode 1.0 release... no issues so far after the upgrade to feisty..

---

