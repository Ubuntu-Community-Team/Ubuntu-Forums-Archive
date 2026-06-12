---
title: "OpenOffice.org crashes after ubuntu upgrade"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikerobinson on 2007-05-21
After upgrading from edgy to feisty openoffice.org crashes on me. I can open up the main window by running `soffice` but when I try to open a file or create a new file or even open up one of the other programs directly (e.g. writer) the program crashes. It used to work fine when I had edgy.

Here is the backtrace:
```
mike@mike:~$ gdb /usr/lib/openoffice/program/soffice.bin
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(gdb) run
Starting program: /usr/lib/openoffice/program/soffice.bin
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47809388140832 (LWP 8868)]
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
warning: Lowest section in /usr/lib/libicudata.so.36 is .hash at 0000000000000120
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
Qt: gdb: -nograb added to command-line options.
         Use the -dograb option to enforce grabbing.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 1082132800 (LWP 8872)]
(no debugging symbols found)
[New Thread 1090525504 (LWP 8873)]
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 1098918208 (LWP 8874)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

(process:8868): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
(no debugging symbols found)
[New Thread 1107310912 (LWP 8875)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 1115703616 (LWP 8876)]
(no debugging symbols found)
(no debugging symbols found)
[Thread 1115703616 (LWP 8876) exited]
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

(process:8868): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:8868): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x00000000006ea620 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b7b77e0bb23]
/lib/libc.so.6(cfree+0x8c)[0x2b7b77e0f26c]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x17)[0x44b737]
/usr/lib/libscim-1.0.so.8[0x2aaab8cee789]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x45)[0x2aaab8cef435]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x30)[0x2aaab8cea910]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x24c)[0x2aaab896543c]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31c)[0x2aaab8966f2c]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x5b)[0x2aaab8960cab]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x32)[0x2b7b7ecb82b0]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x7f)[0x2b7b7ecb7e73]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xbd)[0x2aaab810d7b7]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x3a)[0x2aaab810d94c]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x25)[0x2aaab810db57]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xa4)[0x2b7b7ecb7e98]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x7b)[0x2b7b7ea1ef13]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x15)[0x2b7b7ea1f1cb]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x19)[0x2b7b7eb94f03]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x73)[0x2b7b7eb5ef2d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x5d)[0x2b7b7eb59545]
/usr/lib/libqt-mt.so.3(_ZN9QComboBoxC1EbP7QWidgetPKc+0x2b1)[0x2b7b7eb5e9b7]
/usr/lib/openoffice/program/libvclplug_kde680lx.so[0x2b7b7d9dce49]
/usr/lib/openoffice/program/libvclplug_kde680lx.so[0x2b7b7d9dee45]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11SalGraphics22GetNativeControlRegionEjjRK6RegionjRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x168)[0x2b7b73ce8758]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN6Window22GetNativeControlRegionEjjRK6RegionjRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x112)[0x2b7b73da0a22]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN8ComboBox6ResizeEv+0x1a9)[0x2b7b73db3079]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b7b73d89119]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN6Window4ShowEht+0xd6)[0x2b7b73d8b4a6]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae76df8d]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae771d9f]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae77205a]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae781493]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae780f1d]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae732288]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae8bd437]
/usr/lib/openoffice/program/libsfx680lx.so(_ZN13SfxDispatcher7ExecuteEttP10SfxItemSetS1_t+0x1ea)[0x2aaaae8beaaa]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae8daad4]
/usr/lib/openoffice/program/libsfx680lx.so[0x2aaaae8db539]
/usr/lib/openoffice/program/libfwk680lx.so[0x2aaaaf95fff1]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b7b73d9bab1]
/usr/lib/openoffice/program/libvclplug_gen680lx.so(_ZN10SalDisplay21DispatchInternalEventEv+0xba)[0x2b7b7f2fe09a]
/usr/lib/openoffice/program/libvclplug_gen680lx.so(_ZN13SalX11Display5YieldEv+0x19)[0x2b7b7f2fe0c9]
/usr/lib/openoffice/program/libvclplug_gen680lx.so[0x2b7b7f2fdea7]
/usr/lib/openoffice/program/libvclplug_gen680lx.so(_ZN7SalXLib5YieldEbb+0x4e0)[0x2b7b7f2f7890]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11Application5YieldEb+0x3e)[0x2b7b73bb786e]
/usr/lib/openoffice/program/libvcl680lx.so(_ZN11Application7ExecuteEv+0x27)[0x2b7b73bb7947]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x14d3)[0x427bd3]
/usr/lib/openoffice/program/libvcl680lx.so[0x2b7b73bbd344]
/usr/lib/openoffice/program/libvcl680lx.so(_Z6SVMainv+0x25)[0x2b7b73bbd435]
/usr/lib/openoffice/program/soffice.bin(main+0x3f)[0x41c10f]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b7b77db98e4]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x41bfa9]
======= Memory map: ========
00400000-00459000 r-xp 00000000 08:03 440891                             /usr/lib/openoffice/program/soffice.bin
00659000-0065b000 rw-p 00059000 08:03 440891                             /usr/lib/openoffice/program/soffice.bin
0065b000-00df3000 rw-p 0065b000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0
40001000-40801000 rwxp 40001000 00:00 0
40801000-40802000 ---p 40801000 00:00 0
40802000-41002000 rwxp 40802000 00:00 0
41002000-41003000 ---p 41002000 00:00 0
41003000-41803000 rwxp 41003000 00:00 0
41803000-41804000 ---p 41803000 00:00 0
41804000-42004000 rwxp 41804000 00:00 0
42004000-42005000 ---p 42004000 00:00 0
42005000-42805000 rwxp 42005000 00:00 0
2aaaaaac5000-2aaaaaada000 r-xp 00000000 08:03 441377                     /usr/lib/openoffice/program/uriproc.uno.so
2aaaaaada000-2aaaaacd9000 ---p 00015000 08:03 441377                     /usr/lib/openoffice/program/uriproc.uno.so
2aaaaacd9000-2aaaaacdc000 rw-p 00014000 08:03 441377                     /usr/lib/openoffice/program/uriproc.uno.so
2aaaaacdc000-2aaaaad14000 r-xp 00000000 08:03 441254                     /usr/lib/openoffice/program/libspl680lx.so
2aaaaad14000-2aaaaaf14000 ---p 00038000 08:03 441254                     /usr/lib/openoffice/program/libspl680lx.so
2aaaaaf14000-2aaaaaf18000 rw-p 00038000 08:03 441254                     /usr/lib/openoffice/program/libspl680lx.so
2aaaaaf18000-2aaaaaf7b000 r-xp 00000000 08:03 441339                     /usr/lib/openoffice/program/libpackage2.so
2aaaaaf7b000-2aaaab17b000 ---p 00063000 08:03 441339                     /usr/lib/openoffice/program/libpackage2.so
2aaaab17b000-2aaaab181000 rw-p 00063000 08:03 441339                     /usr/lib/openoffice/program/libpackage2.so
2aaaab181000-2aaaab1a5000 r-xp 00000000 08:03 441011                     /usr/lib/openoffice/program/libfwl680lx.so
2aaaab1a5000-2aaaab3a5000 ---p 00024000 08:03 441011                     /usr/lib/openoffice/program/libfwl680lx.so
2aaaab3a5000-2aaaab3a7000 rw-p 00024000 08:03 441011                     /usr/lib/openoffice/program/libfwl680lx.so
2aaaab3a7000-2aaaab3e5000 r-xp 00000000 08:03 441008                     /usr/lib/openoffice/program/libfwi680lx.so
2aaaab3e5000-2aaaab5e4000 ---p 0003e000 08:03 441008                     /usr/lib/openoffice/program/libfwi680lx.so
2aaaab5e4000-2aaaab5e7000 rw-p 0003d000 08:03 441008                     /usr/lib/openoffice/program/libfwi680lx.so
2aaaab5e7000-2aaaab5fa000 r-xp 00000000 08:03 441309                     /usr/lib/openoffice/program/libfileacc.so
2aaaab5fa000-2aaaab7fa000 ---p 00013000 08:03 441309                     /usr/lib/openoffice/program/libfileacc.so
2aaaab7fa000-2aaaab7fc000 rw-p 00013000 08:03 441309                     /usr/lib/openoffice/program/libfileacc.so
2aaaab859000-2aaaab89b000 r-xp 00000000 08:03 441367                     /usr/lib/openoffice/program/libucb1.so
2aaaab89b000-2aaaaba9a000 ---p 00042000 08:03 441367                     /usr/lib/openoffice/program/libucb1.so
2aaaaba9a000-2aaaaba9f000 rw-p 00041000 08:03 441367                     /usr/lib/openoffice/program/libucb1.so
2aaaaba9f000-2aaaabac6000 r-xp 00000000 08:03 440675                     /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaabac6000-2aaaabcc5000 ---p 00027000 08:03 440675                     /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaabcc5000-2aaaabcc8000 rw-p 00026000 08:03 440675                     /usr/lib/openoffice/program/ucpgvfs1.uno.so
2aaaabce2000-2aaaabd44000 r-xp 00000000 08:03 359564                     /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaabd44000-2aaaabf44000 ---p 00062000 08:03 359564                     /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaabf44000-2aaaabf49000 rw-p 00062000 08:03 359564                     /usr/lib/libgnomevfs-2.so.0.1800.1
2aaaabf49000-2aaaabf82000 r-xp 00000000 08:03 359880                     /usr/lib/libgconf-2.so.4.1.2
2aaaabf82000-2aaaac181000 ---p 00039000 08:03 359880                     /usr/lib/libgconf-2.so.4.1.2
2aaaac181000-2aaaac186000 rw-p 00038000 08:03 359880                     /usr/lib/libgconf-2.so.4.1.2
2aaaac186000-2aaaac1e2000 r-xp 00000000 08:03 360111                     /usr/lib/libORBit-2.so.0.1.0
2aaaac1e2000-2aaaac3e1000 ---p 0005c000 08:03 360111                     /usr/lib/libORBit-2.so.0.1.0
2aaaac3e1000-2aaaac3f4000 rw-p 0005b000 08:03 360111                     /usr/lib/libORBit-2.so.0.1.0
2aaaac3f4000-2aaaac3f8000 r-xp 00000000 08:03 2203449                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaaac3f8000-2aaaac5f7000 ---p 00004000 08:03 2203449                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaaac5f7000-2aaaac5f8000 rw-p 00003000 08:03 2203449                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaaac5f8000-2aaaac616000 r-xp 00000000 08:03 2203472                    /usr/lib/libdbus-glib-1.so.2.1.0
2aaaac616000-2aaaac816000 ---p 0001e000 08:03 2203472                    /usr/lib/libdbus-glib-1.so.2.1.0
2aaaac816000-2aaaac818000 rw-p 0001e000 08:03 2203472                    /usr/lib/libdbus-glib-1.so.2.
Program received signal SIGABRT, Aborted.
[Switching to Thread 47809388140832 (LWP 8868)]
0x00002b7b77dcccab in raise () from /lib/libc.so.6
(gdb)                        
```

Anyone have any idea what's wrong and how I can fix it? I installed koffice, but it doesn't compare.

Thanks

---

### Post by mikerobinson on 2007-05-21
Actually more specifically, I'm on Kubuntu 7.04 x86_64. Sorry I forgot to mention this.

---

### Post by John Jason Jordan on 2007-05-21
> **mikerobinson said:**
> Actually more specifically, I'm on Kubuntu 7.04 x86_64. Sorry I forgot to mention this.
Have you tried a "complete removal" and then an "install" (not a single-step "reinstall") using Synaptic? A "complete removal" will remove all of OOo's configurations, but not your personal settings. Your personal settings are in an .openoffice.org2 folder (note the dot) in your home folder.

I haven't had any problem with OOo since upgrading to Feisty, but back in Edgy it was a constant battle. At one point I did a complete removal and then did a search for files on "openoffice." I found pages of files and folders that had "openoffice" in them, even though I had just done a "complete removal." I nuked everything except my personal preferences in ~/.openoffice.org2, and that folder I renamed ".openoffice.org2.old," just to keep it from being used. (OOo will create a new preferences folder for you the first time it is launched.) That cleared up a lot of issues.

---

### Post by mikerobinson on 2007-05-22
Thanks a lot for the help. That got it working, sorta. I am still getting a HUGE amount of errors to the console and the icons aren't showing up. I'll do a little more fooling around and see what's going on.

---

### Post by mikerobinson on 2007-05-22
Ok, I did a bit more fooling around and I can get everything to work as long as openoffice.org-gtk and openoffice.org-kde are not installed. If I install either of these, the program crashes upon startup. However, I still get all those errors in the console:

```
mike@mike:~$ ooffice -writer

(process:10918): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:10918): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:10918): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:10918): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:10918): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:10918): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:10918): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:10918): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

---

