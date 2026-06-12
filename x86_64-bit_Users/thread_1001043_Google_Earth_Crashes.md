---
title: "Google Earth Crashes"
date: 2008-12-03
forum: x86 64-bit Users
---

### Post by arvevans on 2008-12-03
arv@arv-desktop:~$ nohup $HOME/bin/googleearth
nohup: ignoring input and appending output to `nohup.out'
arv@arv-desktop:~$ cat ./nohup.out
0000:   f0000001  00000300  f0000006  00000001
0010:   f000000b  00000000  f000000c  00278fd0
0020:   f000000d  00278fd0  f000000e  80200020
0030:   f0000002  00000000  f0000003  00000000
0040:   f0000004  00000000  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
Google Earth has caught signal 6.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb8009400]
  /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb717b248]
  /usr/lib/dri/unichrome_dri.so [0xad045303]
  /usr/lib/dri/unichrome_dri.so(viaFlushDmaLocked+0xe4) [0xad045494]
  /usr/lib/dri/unichrome_dri.so [0xad0466fe]
  /usr/lib/dri/unichrome_dri.so(viaWaitIdle+0x11a) [0xad046c5a]
  /usr/lib/dri/unichrome_dri.so [0xad046dbc]
  /usr/lib/dri/unichrome_dri.so(_mesa_Finish+0x41) [0xad068cc1]
  /home/arv/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext9flushDrawEv+0x16) [0xb4e92e86]
  /home/arv/google-earth/libevll.so(_ZN5earth4evll13VisualContext20determineRefreshRateEv+0x39) [0xb395ac19]
  /home/arv/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x872) [0xb395b902]
  /home/arv/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x8f) [0xb3b1bcaf]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x4f) [0xb683b12f]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xb2) [0xb6845e92]
  ./libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x90) [0xb73c32d0]
  ./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0xa86) [0xb78600d2]
  ./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0x1d3) [0xb782444b]
  ./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x132) [0xb782b03e]
  ./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x62) [0xb7e1deda]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0xf9) [0xb78627a9]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb7862507]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb78626a4]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb786268e]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb7862507]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb78626a4]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb786268e]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb786268e]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb786268e]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb786268e]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb7862710]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb7864d6b]
  ./libQtGui.so.4(_ZN7QWidget10showNormalEv+0x68) [0xb785b0f0]
  ./libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xc0f) [0xb73a3e4f]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application12setupMainWinERK7QStringb+0x2ab) [0xb73539ab]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x2f1) [0xb7357451]
  ./googleearth-bin(main+0x2ba) [0x8050bea]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7164685]
  ./googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/arv/.googleearth/crashlogs/crashlog-F428DA1F.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

arv@arv-desktop:~$ cat ./nohup.out

---

### Post by chongzi35 on 2008-12-03
Through conduit **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed for oil & gas pipeline service. Featured with double block and bleed function, the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is suitable for bi-directional flow isolation.

---

### Post by arvevans on 2008-12-14
It still crashes.

---

### Post by il-luzhin on 2008-12-31
just for the sake of the bump and not simply a 'me too', has anyone got any feedback on this one?

---

### Post by Kilz on 2008-12-31
Just a question, have either of you filed bug reports with the google earth project?

---

### Post by dcstar on 2009-01-01
People should use the **googleearth-package** package to obtain and package the latest GoogleEarth binary, at least then you know that it is a package built for your system and not from any other source.

---

### Post by dcstar on 2009-01-01
> **arvevans said:**
> arv@arv-desktop:~$ nohup $HOME/bin/googleearth
nohup: ignoring input and appending output to `nohup.out'
arv@arv-desktop:~$ cat ./nohup.out
0000:   f0000001  00000300  f0000006  00000001
0010:   f000000b  00000000  f000000c  00278fd0
0020:   f000000d  00278fd0  f000000e  80200020
0030:   f0000002  00000000  f0000003  00000000
0040:   f0000004  00000000  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
Google Earth has caught signal 6.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb8009400]
  /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb717b248]
  /usr/lib/dri/unichrome_dri.so [0xad045303]
  /usr/lib/dri/unichrome_dri.so(viaFlushDmaLocked+0xe4) [0xad045494]
  /usr/lib/dri/unichrome_dri.so [0xad0466fe]
  /usr/lib/dri/unichrome_dri.so(viaWaitIdle+0x11a) [0xad046c5a]
  /usr/lib/dri/unichrome_dri.so [0xad046dbc]
  /usr/lib/dri/**unichrome**_dri.so(_mesa_Finish+0x41) [0xad068cc1]
........

Ahh, last time I looked (a few years ago, now) there was not a working 3D Unichrome Ubuntu driver (only 2D), and GoogleEarth requires a working 3D system.

I used to have a S3 Unichrome video system, I gave up on it because of lack of Linux 3D support (a cheap Nvidia card solved everything back then).

---

### Post by athlonx2 on 2009-01-17
Hello..

i have problem installing google earth

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
setup.data/bin/Linux/amd64/setup.gtk: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

what dose that mean? please help me!

---

### Post by arvevans on 2009-01-24
Just to make sure it was not a hardware incompatibility, I temporarily installed SUSE on another hard drive.  Google Earth runs just fine on the same computer but running SUSE Linux.

Arv
_._

---

### Post by jespdj on 2009-01-24
@**athlonx2**: Try installing Google Earth from [Medibuntu](http://medibuntu.org/), so that you don't have to track down and install the necessary libraries yourself.

---

