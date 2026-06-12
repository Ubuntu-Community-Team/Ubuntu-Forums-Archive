---
title: "Realplayer Videos in 7.04"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by hiruzzolo on 2007-05-26
Hi.. I have a problem in ubuntu 7.04 64bit.. I can't watch realplayer movies.. I hear the sound but the video doesn't work neither in realplayer(32bit) nor in mplayer/totem(64bit).. I copy you the errors from terminal:

This one is for realplayer:
realplay I\ Simpson\ -\ 09x01\ -\ Citt&#65533;\ di\ New\ York\ contro\ Homer\ \[4F22\]\ -\ by\ DrHibbert.rm

(realplay.bin:23186): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(realplay.bin:23186): Gtk-WARNING **: Invalid input string

(realplay.bin:23186): GLib-WARNING **: Invalid UTF-8 passed to g_io_channel_write_chars().

** (realplay.bin:23186): WARNING **: Invalid byte sequence in conversion input

** (realplay.bin:23186): CRITICAL **: file mainapp.cpp: line 1433 (void hxwindow_save_preferences(HXMainWindow*, GIOChannel*)): assertion `result' failed

-----------------------------------------------------------------------------
This one is for mplayer:

Playing I Simpson - 09x01 - Citt&#65533; di New York contro Homer [4F22] - by DrHibbert.rm.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
Stream mimetype: logical-fileinfo
VIDEO:  [RV30]  368x284  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Citt&#65533; di New York contro Homer - 4F22
 author: Dr Hibbert Multimedia
 copyright: 20th Century Fox
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/win32/drvc.so: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/win32/drv3.so.6.0: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec drv3.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Could not open required DirectShow codec drv33260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30335652.
Read DOCS/HTML/en/codecs.html!

What could it be?

---

### Post by hiruzzolo on 2007-05-30
I solved the problem installing the AUD-DVD codecs from the automatix for amd64..Now I can play Realplayer videos at least in mplayer!

---

