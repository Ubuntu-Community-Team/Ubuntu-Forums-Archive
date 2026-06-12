---
title: "WoW 3.02"
date: 2008-10-18
forum: Wine
---

### Post by Jarico on 2008-10-18
Hey everyone, I'm fairly new to Ubuntu, and a idiot in basically everything. I decided to reinstall WoW on my linux comp after my Windows laptop committed suicide. I have Ubuntu 8.04 and Wine 1.0, and I decided to take the easy route and do an internet download of the game. It took awhile but it finally patched itself up to 3.02. The Problem is when I fired it up and once I got to the login screen everything looked like a slider puzzle of pentagons. I was able to login and get to the character screen but once I hot enter world the game crashed on the loading screen. I would very much appreciate help, very basic help if possible...

---

### Post by gjoellee on 2008-10-18
install WINE 1.1.6 and try again, have you enabled opengl?

---

### Post by ooobuntooo on 2008-10-18
> **gjoellee said:**
> install WINE 1.1.6 and try again, have you enabled opengl?

isn't wine 1.1.5 better?

---

### Post by gjoellee on 2008-10-18
> **ooobuntooo said:**
> isn't wine 1.1.5 better?
  well WINE 1.1.6 is the latest version, but sometimes an older version can be better. JUst test it if you wonder ;)

---

### Post by Jarico on 2008-10-18
> **gjoellee said:**
> install WINE 1.1.6 and try again, have you enabled opengl?

Just updated and restarted, same problem. I don't believe I have enabled opengl though, I'll have to look into that.

---

### Post by Jarico on 2008-10-18
Well I fired up WoW in the terminal with enable opengl, still the same. So I tried to login again and it crashed...Again...Heres what happen in my terminal...

```
 fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
of Warcraft\WoW.exe: ../../src/xcb_io.c:453: _XRead: Assertion `dpy->xcb->reply_consumed + size <= dpy->xcb->reply_length' failed.
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ce0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ce081e]
#2 /usr/lib/libX11.so.6 [0x7ea38518]
#3 /usr/lib/libX11.so.6(XSetSubwindowMode+0x1d) [0x7ea1524d]
#4 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_ExtEscape+0x2ba) [0x7e1c8e4a]
#5 /usr/bin/../lib/wine/gdi32.dll.so(ExtEscape+0x50) [0x7ec3ced0]
#6 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_GetDC+0x15a) [0x7e1e2e3a]
#7 /usr/bin/../lib/wine/user32.dll.so [0x7ed44157]
#8 /usr/bin/../lib/wine/user32.dll.so(GetDCEx+0x21b) [0x7ed4440b]
#9 /usr/bin/../lib/wine/user32.dll.so(GetDC+0x5c) [0x7ed4493c]
#10 /usr/bin/../lib/wine/user32.dll.so(GetDialogBaseUnits+0x3d) [0x7ecfec2d]
#11 /usr/bin/../lib/wine/user32.dll.so [0x7ed0021a]
#12 /usr/bin/../lib/wine/user32.dll.so(DialogBoxIndirectParamAorW+0x39) [0x7ed02ed9]
#13 /usr/bin/../lib/wine/user32.dll.so(DialogBoxIndirectParamW+0x41) [0x7ed02f41]
#14 /usr/bin/../lib/wine/user32.dll.so(MessageBoxIndirectW+0x96) [0x7ed3f446]
#15 /usr/bin/../lib/wine/user32.dll.so(MessageBoxIndirectA+0xac) [0x7ed3f5dc]
#16 /usr/bin/../lib/wine/user32.dll.so(MessageBoxExA+0x5f) [0x7ed3f6df]
#17 /usr/bin/../lib/wine/user32.dll.so(MessageBoxA+0x3a) [0x7ed3f72a]
#18 [0x6a37d7]
#19 [0x6a3abc]
of Warcraft\WoW.exe: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
wine: Assertion failed at address 0xb7fb4410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xb7fb4410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7fb4410 ESP:0039ec70 EBP:0039ec8c EFLAGS:00200206(   - 00      - -IP1)
 EAX:00000000 EBX:0000189f ECX:0000189f EDX:00000006
 ESI:0000189f EDI:b7e33ff4
Stack dump:
0x0039ec70:  0039ec8c 00000006 0000189f b7d14085
0x0039ec80:  b7e33ff4 0039ed2c b7ce46b0 0039edb8
0x0039ec90:  b7d15a01 00000006 0039ed2c 00000000
0x0039eca0:  7c300010 7c301250 b7e33ff4 00000000
0x0039ecb0:  7c300010 7c300000 b7d56cad 7c300010
0x0039ecc0:  00000084 b7e33ff4 00000084 7c3013e0
Backtrace:
=>1 0xb7fb4410 (0x0039ec8c)
  2 0xb7d15a01 abort+0x101() in libc.so.6 (0x0039edb8)
  3 0xb7d0d10e __assert_fail+0xee() in libc.so.6 (0x0039edfc)
  4 0x7ea38a02 _XRead+0xd2() in libx11.so.6 (0x0039ee2c)
  5 0x7e9c6734 in libgl.so.1 (+0x47734) (0x0039ee6c)
  6 0x7e8d59e0 in wined3d (+0xa59e0) (0x0039eeec)
  7 0x7e8df5d2 in wined3d (+0xaf5d2) (0x0039efec)
  8 0x7e8dc01f in wined3d (+0xac01f) (0x0039f04c)
  9 0x7e94731e in d3d9 (+0x1731e) (0x0039f08c)
  10 0x005ea7d4 in wow (+0x1ea7d4) (0x0039f104)
  11 0x005ea965 in wow (+0x1ea965) (0x0039f118)
  12 0x005cec4c in wow (+0x1cec4c) (0x0039f124)
  13 0x005cc294 in wow (+0x1cc294) (0x0039f148)
  14 0x00452fa7 in wow (+0x52fa7) (0x0039f644)
  15 0x00453187 in wow (+0x53187) (0x0039f658)
  16 0x00454e50 in wow (+0x54e50) (0x0039f674)
  17 0x00455502 in wow (+0x55502) (0x0039f688)
  18 0x00451721 in wow (+0x51721) (0x0039f714)
  19 0x00451869 in wow (+0x51869) (0x0039f720)
  20 0x0057f785 in wow (+0x17f785) (0x0039f758)
  21 0x0057fb01 in wow (+0x17fb01) (0x0039f870)
  22 0x004b2d14 in wow (+0xb2d14) (0x0039f938)
  23 0x00404fd9 in wow (+0x4fd9) (0x0039f94c)
  24 0x004729b0 in wow (+0x729b0) (0x0039fda4)
  25 0x00427ba9 in wow (+0x27ba9) (0x0039fdd4)
  26 0x004250b1 in wow (+0x250b1) (0x0039fdf4)
  27 0x00426488 in wow (+0x26488) (0x0039fe54)
  28 0x00426591 in wow (+0x26591) (0x0039fe6c)
  29 0x00406b28 in wow (+0x6b28) (0x0039ff08)
  30 0x7b877b77 in kernel32 (+0x57b77) (0x0039ffe8)
0xb7fb4410: popl	%ebp
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000- 138e000	Export          wow
PE	10000000-10069000	Deferred        divxdecoder
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c42f000-7c499000	Deferred        msvcrt<elf>
  \-PE	7c440000-7c499000	\               msvcrt
ELF	7c499000-7c4e5000	Deferred        dbghelp<elf>
  \-PE	7c4a0000-7c4e5000	\               dbghelp
ELF	7d95d000-7d963000	Deferred        libnss_dns.so.2
ELF	7daef000-7db04000	Deferred        psapi<elf>
  \-PE	7daf0000-7db04000	\               psapi
ELF	7db04000-7db4e000	Deferred        dsound<elf>
  \-PE	7db10000-7db4e000	\               dsound
ELF	7dfc5000-7dff8000	Deferred        uxtheme<elf>
  \-PE	7dfd0000-7dff8000	\               uxtheme
ELF	7e020000-7e034000	Deferred        midimap<elf>
  \-PE	7e030000-7e034000	\               midimap
ELF	7e034000-7e04b000	Deferred        msacm32<elf>
  \-PE	7e040000-7e04b000	\               msacm32
ELF	7e04b000-7e10e000	Deferred        libasound.so.2
ELF	7e11d000-7e152000	Deferred        winealsa<elf>
  \-PE	7e130000-7e152000	\               winealsa
ELF	7e152000-7e15b000	Deferred        libxcursor.so.1
ELF	7e15b000-7e160000	Deferred        libxfixes.so.3
ELF	7e160000-7e166000	Deferred        libxrandr.so.2
ELF	7e166000-7e16e000	Deferred        libxrender.so.1
ELF	7e16e000-7e173000	Deferred        libxxf86vm.so.1
ELF	7e17c000-7e17f000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e182000-7e21a000	Deferred        winex11<elf>
  \-PE	7e190000-7e21a000	\               winex11
ELF	7e254000-7e275000	Deferred        libexpat.so.1
ELF	7e275000-7e29f000	Deferred        libfontconfig.so.1
ELF	7e2a0000-7e2a3000	Deferred        libxcomposite.so.1
ELF	7e2ae000-7e2c3000	Deferred        libz.so.1
ELF	7e2c3000-7e330000	Deferred        libfreetype.so.6
ELF	7e330000-7e343000	Deferred        libresolv.so.2
ELF	7e343000-7e362000	Deferred        iphlpapi<elf>
  \-PE	7e350000-7e362000	\               iphlpapi
ELF	7e362000-7e3c7000	Deferred        rpcrt4<elf>
  \-PE	7e370000-7e3c7000	\               rpcrt4
ELF	7e3c7000-7e4d0000	Deferred        ole32<elf>
  \-PE	7e3e0000-7e4d0000	\               ole32
ELF	7e4d0000-7e4f7000	Deferred        msacm32<elf>
  \-PE	7e4e0000-7e4f7000	\               msacm32
ELF	7e4f7000-7e523000	Deferred        ws2_32<elf>
  \-PE	7e500000-7e523000	\               ws2_32
ELF	7e523000-7e5e4000	Deferred        comctl32<elf>
  \-PE	7e530000-7e5e4000	\               comctl32
ELF	7e5e4000-7e6fe000	Deferred        shell32<elf>
  \-PE	7e5f0000-7e6fe000	\               shell32
ELF	7e6fe000-7e758000	Deferred        shlwapi<elf>
  \-PE	7e710000-7e758000	\               shlwapi
ELF	7e758000-7e77a000	Deferred        mpr<elf>
  \-PE	7e760000-7e77a000	\               mpr
ELF	7e77a000-7e7c9000	Deferred        wininet<elf>
  \-PE	7e780000-7e7c9000	\               wininet
ELF	7e7c9000-7e7e9000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7e9000	\               imm32
ELF	7e7e9000-7e7fd000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e7fd000	\               lz32
ELF	7e7fd000-7e816000	Deferred        version<elf>
  \-PE	7e800000-7e816000	\               version
ELF	7e816000-7e927000	Export          wined3d<elf>
  \-PE	7e830000-7e927000	\               wined3d
ELF	7e927000-7e957000	Export          d3d9<elf>
  \-PE	7e930000-7e957000	\               d3d9
ELF	7e957000-7e95c000	Deferred        libxdmcp.so.6
ELF	7e95c000-7e967000	Deferred        libgcc_s.so.1
ELF	7e967000-7e97f000	Deferred        libxcb.so.1
ELF	7e97f000-7e9f9000	Export          libgl.so.1
ELF	7e9f9000-7eae0000	Export          libx11.so.6
ELF	7eae0000-7eaee000	Deferred        libxext.so.6
ELF	7eaee000-7eb06000	Deferred        libice.so.6
ELF	7eb06000-7eb0e000	Deferred        libsm.so.6
ELF	7eb0e000-7eb11000	Deferred        libxinerama.so.1
ELF	7eb1d000-7ebb2000	Deferred        opengl32<elf>
  \-PE	7eb30000-7ebb2000	\               opengl32
ELF	7ebb2000-7ec06000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec06000	\               advapi32
ELF	7ec06000-7eca4000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca4000	\               gdi32
ELF	7eca4000-7eded000	Deferred        user32<elf>
  \-PE	7ecc0000-7eded000	\               user32
ELF	7eded000-7ee7f000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee7f000	\               winmm
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff4000-7eff7000	Deferred        libxau.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7ce0000-b7ce2000	Deferred        libxcb-xlib.so.0
ELF	b7ce5000-b7ce9000	Deferred        libdl.so.2
ELF	b7ce9000-b7e38000	Export          libc.so.6
ELF	b7e39000-b7e51000	Deferred        libpthread.so.0
ELF	b7e60000-b7f96000	Deferred        libwine.so.1
ELF	b7f98000-b7fb4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
	00000030    2
	0000002f   15
	0000002e    0
	0000002d    0
	0000002c    0
	00000028    0
	00000027    1
	00000026    0
	00000025    1
	00000024    0
	00000023    0
	00000022    0
	00000021    0
	00000020    2
	0000001f   15
	0000001e    2
	0000001d   15
	0000001c   15
	0000001b    0
	0000001a    0
	00000019    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
00000032 
	00000033    0
Backtrace:
=>1 0xb7fb4410 (0x0039ec8c)
  2 0xb7d15a01 abort+0x101() in libc.so.6 (0x0039edb8)
  3 0xb7d0d10e __assert_fail+0xee() in libc.so.6 (0x0039edfc)
  4 0x7ea38a02 _XRead+0xd2() in libx11.so.6 (0x0039ee2c)
  5 0x7e9c6734 in libgl.so.1 (+0x47734) (0x0039ee6c)
  6 0x7e8d59e0 in wined3d (+0xa59e0) (0x0039eeec)
  7 0x7e8df5d2 in wined3d (+0xaf5d2) (0x0039efec)
  8 0x7e8dc01f in wined3d (+0xac01f) (0x0039f04c)
  9 0x7e94731e in d3d9 (+0x1731e) (0x0039f08c)
  10 0x005ea7d4 in wow (+0x1ea7d4) (0x0039f104)
  11 0x005ea965 in wow (+0x1ea965) (0x0039f118)
  12 0x005cec4c in wow (+0x1cec4c) (0x0039f124)
  13 0x005cc294 in wow (+0x1cc294) (0x0039f148)
  14 0x00452fa7 in wow (+0x52fa7) (0x0039f644)
  15 0x00453187 in wow (+0x53187) (0x0039f658)
  16 0x00454e50 in wow (+0x54e50) (0x0039f674)
  17 0x00455502 in wow (+0x55502) (0x0039f688)
  18 0x00451721 in wow (+0x51721) (0x0039f714)
  19 0x00451869 in wow (+0x51869) (0x0039f720)
  20 0x0057f785 in wow (+0x17f785) (0x0039f758)
  21 0x0057fb01 in wow (+0x17fb01) (0x0039f870)
  22 0x004b2d14 in wow (+0xb2d14) (0x0039f938)
  23 0x00404fd9 in wow (+0x4fd9) (0x0039f94c)
  24 0x004729b0 in wow (+0x729b0) (0x0039fda4)
  25 0x00427ba9 in wow (+0x27ba9) (0x0039fdd4)
  26 0x004250b1 in wow (+0x250b1) (0x0039fdf4)
  27 0x00426488 in wow (+0x26488) (0x0039fe54)
  28 0x00426591 in wow (+0x26591) (0x0039fe6c)
  29 0x00406b28 in wow (+0x6b28) (0x0039ff08)
  30 0x7b877b77 in kernel32 (+0x57b77) (0x0039ffe8)
Aborted
```

Any ideas?

---

### Post by Flynn555 on 2008-10-18
partition your hard drive...install xp and play wow on that. :D

---

### Post by Jarico on 2008-10-18
> **Flynn555 said:**
> partition your hard drive...install xp and play wow on that. :D

know any site that can tell me HOW? You confuse me...Very, very much. Are you saying to partition my hard drive and then install XP from a copy of Windows, (Which I don't have) Or by Partitioning I can install XP? Remember, I'm an idiot.

---

### Post by Flynn555 on 2008-10-18
i havent had hardly any luck with games like that on ubuntu...and 
i was just implying that it is probably best to play your games on xp.


thats what i do...i have my windows machine for games and then my ubuntu box for everything else. ;)

---

### Post by Jarico on 2008-10-18
> **Flynn555 said:**
> i havent had hardly any luck with games like that on ubuntu...and 
i was just implying that it is probably best to play your games on xp.


thats what i do...i have my windows machine for games and then my ubuntu box for everything else. ;)

Yes, I do believe that is best, though can you please tell me what I should do? And how I can do that? (I don't have any copies of Windows)

---

### Post by Flynn555 on 2008-10-18
well if you are going to try to run WoW, it probably isnt going to happen on gnome.  gnome was always buggy with games( at least for me) so i would download fluxbox (more lightweight window manager) but be prepared to use terminal alot! not much of a gui.  

from what i have experienced with games and ubuntu this is the best enviroment.  although i have never tryed to play wow on it, it works fine with half life/counterstrike/wolfenstien etc.

but for what its worth games and ubuntu have always been to much trouble for what their worth :(

---

### Post by Jarico on 2008-10-18
> **Flynn555 said:**
> well if you are going to try to run WoW, it probably isnt going to happen on gnome.  gnome was always buggy with games( at least for me) so i would download fluxbox (more lightweight window manager) but be prepared to use terminal alot! not much of a gui.  

from what i have experienced with games and ubuntu this is the best enviroment.  although i have never tryed to play wow on it, it works fine with half life/counterstrike/wolfenstien etc.

but for what its worth games and ubuntu have always been to much trouble for what their worth :(

You're not helping...

---

### Post by Flynn555 on 2008-10-18
sorry man...im just stating the facts.  if you want to play a **windows** based game...its probably best to play it on **windows**

i wish you the best of luck.

---

### Post by UltimaDude on 2008-10-18
You really aren't helping, I've ran WoW 3.0.2 on Ubuntu fine on my wow folder copied from external.

I have two pictures:
[http://krigo.man-ma.de/wine/lol.png](http://krigo.man-ma.de/wine/lol.png)
[http://krigo.man-ma.de/wine/Not%20happy.png](http://krigo.man-ma.de/wine/Not%20happy.png)

This is on Wine 1.1.6 by the way.

---

### Post by Flynn555 on 2008-10-18
> **Jarico said:**
> Well I fired up WoW in the terminal with enable opengl, still the same. So I tried to login again and it crashed...Again...Heres what happen in my terminal...

```
 fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 266
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
of Warcraft\WoW.exe: ../../src/xcb_io.c:453: _XRead: Assertion `dpy->xcb->reply_consumed + size <= dpy->xcb->reply_length' failed.
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ce0767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ce081e]
#2 /usr/lib/libX11.so.6 [0x7ea38518]
#3 /usr/lib/libX11.so.6(XSetSubwindowMode+0x1d) [0x7ea1524d]
#4 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_ExtEscape+0x2ba) [0x7e1c8e4a]
#5 /usr/bin/../lib/wine/gdi32.dll.so(ExtEscape+0x50) [0x7ec3ced0]
#6 /usr/bin/../lib/wine/winex11.drv.so(X11DRV_GetDC+0x15a) [0x7e1e2e3a]
#7 /usr/bin/../lib/wine/user32.dll.so [0x7ed44157]
#8 /usr/bin/../lib/wine/user32.dll.so(GetDCEx+0x21b) [0x7ed4440b]
#9 /usr/bin/../lib/wine/user32.dll.so(GetDC+0x5c) [0x7ed4493c]
#10 /usr/bin/../lib/wine/user32.dll.so(GetDialogBaseUnits+0x3d) [0x7ecfec2d]
#11 /usr/bin/../lib/wine/user32.dll.so [0x7ed0021a]
#12 /usr/bin/../lib/wine/user32.dll.so(DialogBoxIndirectParamAorW+0x39) [0x7ed02ed9]
#13 /usr/bin/../lib/wine/user32.dll.so(DialogBoxIndirectParamW+0x41) [0x7ed02f41]
#14 /usr/bin/../lib/wine/user32.dll.so(MessageBoxIndirectW+0x96) [0x7ed3f446]
#15 /usr/bin/../lib/wine/user32.dll.so(MessageBoxIndirectA+0xac) [0x7ed3f5dc]
#16 /usr/bin/../lib/wine/user32.dll.so(MessageBoxExA+0x5f) [0x7ed3f6df]
#17 /usr/bin/../lib/wine/user32.dll.so(MessageBoxA+0x3a) [0x7ed3f72a]
#18 [0x6a37d7]
#19 [0x6a3abc]
of Warcraft\WoW.exe: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
wine: Assertion failed at address 0xb7fb4410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xb7fb4410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7fb4410 ESP:0039ec70 EBP:0039ec8c EFLAGS:00200206(   - 00      - -IP1)
 EAX:00000000 EBX:0000189f ECX:0000189f EDX:00000006
 ESI:0000189f EDI:b7e33ff4
Stack dump:
0x0039ec70:  0039ec8c 00000006 0000189f b7d14085
0x0039ec80:  b7e33ff4 0039ed2c b7ce46b0 0039edb8
0x0039ec90:  b7d15a01 00000006 0039ed2c 00000000
0x0039eca0:  7c300010 7c301250 b7e33ff4 00000000
0x0039ecb0:  7c300010 7c300000 b7d56cad 7c300010
0x0039ecc0:  00000084 b7e33ff4 00000084 7c3013e0
Backtrace:
=>1 0xb7fb4410 (0x0039ec8c)
  2 0xb7d15a01 abort+0x101() in libc.so.6 (0x0039edb8)
  3 0xb7d0d10e __assert_fail+0xee() in libc.so.6 (0x0039edfc)
  4 0x7ea38a02 _XRead+0xd2() in libx11.so.6 (0x0039ee2c)
  5 0x7e9c6734 in libgl.so.1 (+0x47734) (0x0039ee6c)
  6 0x7e8d59e0 in wined3d (+0xa59e0) (0x0039eeec)
  7 0x7e8df5d2 in wined3d (+0xaf5d2) (0x0039efec)
  8 0x7e8dc01f in wined3d (+0xac01f) (0x0039f04c)
  9 0x7e94731e in d3d9 (+0x1731e) (0x0039f08c)
  10 0x005ea7d4 in wow (+0x1ea7d4) (0x0039f104)
  11 0x005ea965 in wow (+0x1ea965) (0x0039f118)
  12 0x005cec4c in wow (+0x1cec4c) (0x0039f124)
  13 0x005cc294 in wow (+0x1cc294) (0x0039f148)
  14 0x00452fa7 in wow (+0x52fa7) (0x0039f644)
  15 0x00453187 in wow (+0x53187) (0x0039f658)
  16 0x00454e50 in wow (+0x54e50) (0x0039f674)
  17 0x00455502 in wow (+0x55502) (0x0039f688)
  18 0x00451721 in wow (+0x51721) (0x0039f714)
  19 0x00451869 in wow (+0x51869) (0x0039f720)
  20 0x0057f785 in wow (+0x17f785) (0x0039f758)
  21 0x0057fb01 in wow (+0x17fb01) (0x0039f870)
  22 0x004b2d14 in wow (+0xb2d14) (0x0039f938)
  23 0x00404fd9 in wow (+0x4fd9) (0x0039f94c)
  24 0x004729b0 in wow (+0x729b0) (0x0039fda4)
  25 0x00427ba9 in wow (+0x27ba9) (0x0039fdd4)
  26 0x004250b1 in wow (+0x250b1) (0x0039fdf4)
  27 0x00426488 in wow (+0x26488) (0x0039fe54)
  28 0x00426591 in wow (+0x26591) (0x0039fe6c)
  29 0x00406b28 in wow (+0x6b28) (0x0039ff08)
  30 0x7b877b77 in kernel32 (+0x57b77) (0x0039ffe8)
0xb7fb4410: popl	%ebp
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000- 138e000	Export          wow
PE	10000000-10069000	Deferred        divxdecoder
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c42f000-7c499000	Deferred        msvcrt<elf>
  \-PE	7c440000-7c499000	\               msvcrt
ELF	7c499000-7c4e5000	Deferred        dbghelp<elf>
  \-PE	7c4a0000-7c4e5000	\               dbghelp
ELF	7d95d000-7d963000	Deferred        libnss_dns.so.2
ELF	7daef000-7db04000	Deferred        psapi<elf>
  \-PE	7daf0000-7db04000	\               psapi
ELF	7db04000-7db4e000	Deferred        dsound<elf>
  \-PE	7db10000-7db4e000	\               dsound
ELF	7dfc5000-7dff8000	Deferred        uxtheme<elf>
  \-PE	7dfd0000-7dff8000	\               uxtheme
ELF	7e020000-7e034000	Deferred        midimap<elf>
  \-PE	7e030000-7e034000	\               midimap
ELF	7e034000-7e04b000	Deferred        msacm32<elf>
  \-PE	7e040000-7e04b000	\               msacm32
ELF	7e04b000-7e10e000	Deferred        libasound.so.2
ELF	7e11d000-7e152000	Deferred        winealsa<elf>
  \-PE	7e130000-7e152000	\               winealsa
ELF	7e152000-7e15b000	Deferred        libxcursor.so.1
ELF	7e15b000-7e160000	Deferred        libxfixes.so.3
ELF	7e160000-7e166000	Deferred        libxrandr.so.2
ELF	7e166000-7e16e000	Deferred        libxrender.so.1
ELF	7e16e000-7e173000	Deferred        libxxf86vm.so.1
ELF	7e17c000-7e17f000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e182000-7e21a000	Deferred        winex11<elf>
  \-PE	7e190000-7e21a000	\               winex11
ELF	7e254000-7e275000	Deferred        libexpat.so.1
ELF	7e275000-7e29f000	Deferred        libfontconfig.so.1
ELF	7e2a0000-7e2a3000	Deferred        libxcomposite.so.1
ELF	7e2ae000-7e2c3000	Deferred        libz.so.1
ELF	7e2c3000-7e330000	Deferred        libfreetype.so.6
ELF	7e330000-7e343000	Deferred        libresolv.so.2
ELF	7e343000-7e362000	Deferred        iphlpapi<elf>
  \-PE	7e350000-7e362000	\               iphlpapi
ELF	7e362000-7e3c7000	Deferred        rpcrt4<elf>
  \-PE	7e370000-7e3c7000	\               rpcrt4
ELF	7e3c7000-7e4d0000	Deferred        ole32<elf>
  \-PE	7e3e0000-7e4d0000	\               ole32
ELF	7e4d0000-7e4f7000	Deferred        msacm32<elf>
  \-PE	7e4e0000-7e4f7000	\               msacm32
ELF	7e4f7000-7e523000	Deferred        ws2_32<elf>
  \-PE	7e500000-7e523000	\               ws2_32
ELF	7e523000-7e5e4000	Deferred        comctl32<elf>
  \-PE	7e530000-7e5e4000	\               comctl32
ELF	7e5e4000-7e6fe000	Deferred        shell32<elf>
  \-PE	7e5f0000-7e6fe000	\               shell32
ELF	7e6fe000-7e758000	Deferred        shlwapi<elf>
  \-PE	7e710000-7e758000	\               shlwapi
ELF	7e758000-7e77a000	Deferred        mpr<elf>
  \-PE	7e760000-7e77a000	\               mpr
ELF	7e77a000-7e7c9000	Deferred        wininet<elf>
  \-PE	7e780000-7e7c9000	\               wininet
ELF	7e7c9000-7e7e9000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7e9000	\               imm32
ELF	7e7e9000-7e7fd000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e7fd000	\               lz32
ELF	7e7fd000-7e816000	Deferred        version<elf>
  \-PE	7e800000-7e816000	\               version
ELF	7e816000-7e927000	Export          wined3d<elf>
  \-PE	7e830000-7e927000	\               wined3d
ELF	7e927000-7e957000	Export          d3d9<elf>
  \-PE	7e930000-7e957000	\               d3d9
ELF	7e957000-7e95c000	Deferred        libxdmcp.so.6
ELF	7e95c000-7e967000	Deferred        libgcc_s.so.1
ELF	7e967000-7e97f000	Deferred        libxcb.so.1
ELF	7e97f000-7e9f9000	Export          libgl.so.1
ELF	7e9f9000-7eae0000	Export          libx11.so.6
ELF	7eae0000-7eaee000	Deferred        libxext.so.6
ELF	7eaee000-7eb06000	Deferred        libice.so.6
ELF	7eb06000-7eb0e000	Deferred        libsm.so.6
ELF	7eb0e000-7eb11000	Deferred        libxinerama.so.1
ELF	7eb1d000-7ebb2000	Deferred        opengl32<elf>
  \-PE	7eb30000-7ebb2000	\               opengl32
ELF	7ebb2000-7ec06000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec06000	\               advapi32
ELF	7ec06000-7eca4000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca4000	\               gdi32
ELF	7eca4000-7eded000	Deferred        user32<elf>
  \-PE	7ecc0000-7eded000	\               user32
ELF	7eded000-7ee7f000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee7f000	\               winmm
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff4000-7eff7000	Deferred        libxau.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7ce0000-b7ce2000	Deferred        libxcb-xlib.so.0
ELF	b7ce5000-b7ce9000	Deferred        libdl.so.2
ELF	b7ce9000-b7e38000	Export          libc.so.6
ELF	b7e39000-b7e51000	Deferred        libpthread.so.0
ELF	b7e60000-b7f96000	Deferred        libwine.so.1
ELF	b7f98000-b7fb4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
	00000030    2
	0000002f   15
	0000002e    0
	0000002d    0
	0000002c    0
	00000028    0
	00000027    1
	00000026    0
	00000025    1
	00000024    0
	00000023    0
	00000022    0
	00000021    0
	00000020    2
	0000001f   15
	0000001e    2
	0000001d   15
	0000001c   15
	0000001b    0
	0000001a    0
	00000019    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
00000032 
	00000033    0
Backtrace:
=>1 0xb7fb4410 (0x0039ec8c)
  2 0xb7d15a01 abort+0x101() in libc.so.6 (0x0039edb8)
  3 0xb7d0d10e __assert_fail+0xee() in libc.so.6 (0x0039edfc)
  4 0x7ea38a02 _XRead+0xd2() in libx11.so.6 (0x0039ee2c)
  5 0x7e9c6734 in libgl.so.1 (+0x47734) (0x0039ee6c)
  6 0x7e8d59e0 in wined3d (+0xa59e0) (0x0039eeec)
  7 0x7e8df5d2 in wined3d (+0xaf5d2) (0x0039efec)
  8 0x7e8dc01f in wined3d (+0xac01f) (0x0039f04c)
  9 0x7e94731e in d3d9 (+0x1731e) (0x0039f08c)
  10 0x005ea7d4 in wow (+0x1ea7d4) (0x0039f104)
  11 0x005ea965 in wow (+0x1ea965) (0x0039f118)
  12 0x005cec4c in wow (+0x1cec4c) (0x0039f124)
  13 0x005cc294 in wow (+0x1cc294) (0x0039f148)
  14 0x00452fa7 in wow (+0x52fa7) (0x0039f644)
  15 0x00453187 in wow (+0x53187) (0x0039f658)
  16 0x00454e50 in wow (+0x54e50) (0x0039f674)
  17 0x00455502 in wow (+0x55502) (0x0039f688)
  18 0x00451721 in wow (+0x51721) (0x0039f714)
  19 0x00451869 in wow (+0x51869) (0x0039f720)
  20 0x0057f785 in wow (+0x17f785) (0x0039f758)
  21 0x0057fb01 in wow (+0x17fb01) (0x0039f870)
  22 0x004b2d14 in wow (+0xb2d14) (0x0039f938)
  23 0x00404fd9 in wow (+0x4fd9) (0x0039f94c)
  24 0x004729b0 in wow (+0x729b0) (0x0039fda4)
  25 0x00427ba9 in wow (+0x27ba9) (0x0039fdd4)
  26 0x004250b1 in wow (+0x250b1) (0x0039fdf4)
  27 0x00426488 in wow (+0x26488) (0x0039fe54)
  28 0x00426591 in wow (+0x26591) (0x0039fe6c)
  29 0x00406b28 in wow (+0x6b28) (0x0039ff08)
  30 0x7b877b77 in kernel32 (+0x57b77) (0x0039ffe8)
Aborted
```

Any ideas?

well if you are using an ati card...this might be of some help
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#ATI%20enter%20game%20world%20crash](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#ATI%20enter%20game%20world%20crash)

---

### Post by MasterNetra on 2008-10-18
Well he would have to re-install grub if he installs xp after Ubuntu.

Jarico it might be better to back up whatever stuff you want to keep on Ubuntu then just install XP over everything then afterward you can use Ubuntu Live CD's Gnome Partition Editor to yank HD space from XP...or just leave some space when setting up XP's partition for installation... ANy who to install XP just put your XP cd in your drive and restart the computer. when booting the computer will give you a option to boot from XP cd and there you can install it.

*(Of course if you don't mind re-installing grub then go ahead and install XP...might have to use Ubuntu Live CD to yank some space from Ubuntu if its hogging all of it. though. And look for "Super Grub" and burn it to CD so you can restore grub.)*

Of course thats if you want to go with the duel boot option in regards to this :)

---

### Post by Rody on 2008-10-19
actualy it kinda looks like you need to install video drivers. or enable video drivers. There are a lot of guides to run games and wow on ubuntu or linux in general. A web search might help out.

 Wow runs just fine in ubuntu with just a bit of frame rate loss.
Just because other people can't seem to get it running don't get discourged the guy telling you to install windows probebly works for microsoft.

rody

---

### Post by go_lanche on 2008-10-19
First thing's first, whenever you have WoW / Warcraft + Wine + Ubuntu questions the first and foremost place for information **in the entire universe** is this thread: 

[URL="http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine"]http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine
[/URL]

It has helped *thousands* of people play WoW on Ubuntu, and many of them (myself included) don't know jack about Linux. 

It contains links for detailed troubleshooting methods for tons of problems, big and small.

Most importantly, the person (Sammi) who wrote the how to and is a genious at WoW in Ubuntu is really cool and will often work with your specific issue just to help you out. 

Second thing's second: Rody is right, don't get discouraged by the Micro$oft marketing department, when you first start out with Ubuntu you will face a few challenges, but they are not even close to impossible and this is particular challenge is a good way to learn a lot of useful stuff. 

Finally, always remember: Most of the people who really know their way around Ubuntu and are helping you on these forums were once lowly noobs like yourself, with a little detective work you can always fix whatever issues you are experiencing and then someday pass the torch of noob-hood on to someone else when you explain to them how to do something cool.

---

