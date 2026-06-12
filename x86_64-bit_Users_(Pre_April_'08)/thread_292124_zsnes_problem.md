---
title: "zsnes problem"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by flapane on 2006-11-03
flapane@a64:~$ zsnes

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest verion.
Please report crashes to [email]zsnes-devel@lists.sourceforge.ne[/email].

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free sotware,
and you are welcome to redistribute it under certain condtions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** zsnes: munmap_chunk(): invalid poiter: 0xffffded3 ***
======= Backtrace: =========
/lib32/libc.so.6(__libc_free+0x18a)[0x5585a70a]
zsnes[0x80dd746]
/lib32/libc.so.6(__libc_start_main+0xdc)[0x558088cc]
zsnes(__gxx_personality_v0+0xcd)[0x804b9f1]
======= Memory map: ========
08048000-082f7000 r-xp 00000000 08:03 516473                            /usr/bin/zsnes
082f7000-0834a000 rwxp 002ae000 08:03 516473                            /usr/bin/zsnes
0834a000-085d7000 rwxp 0834a000 00:00 0                                 [heap]
55555000-55570000 r-xp 00000000 08:03 274317                            /lib32/ld-2.4.so
55570000-55572000 rwxp 0001b000 08:03 274317                            /lib32/ld-2.4.so
55572000-55574000 rwxp 55572000 00:00 0
55574000-55576000 rwxp 00000000 00:0d 2387                              /dev/zero
55576000-55577000 rwxp 55576000 00:00 0
55585000-55598000 r-xp 00000000 08:03 209698                            /usr/lib32/libz.so.1.2.3
55598000-55599000 rwxp 00012000 08:03 209698                            /usr/lib32/libz.so.1.2.3
55599000-555fb000 r-xp 00000000 08:03 210614                            /usr/lib32/libSDL-1.2.so.0
555fb000-555fd000 rwxp 00062000 08:03 210614                            /usr/lib32/libSDL-1.2.so.0
555fd000-55627000 rwxp 555fd000 00:00 0
55627000-55636000 r-xp 00000000 08:03 276556                            /lib32/libpthread-2.4.so
55636000-55638000 rwxp 0000f000 08:03 276556                            /lib32/libpthread-2.4.so
55638000-5563b000 rwxp 55638000 00:00 0
5563b000-5565d000 r-xp 00000000 08:03 210182                            /usr/lib32/libpng12.so.0.1.2.8
5565d000-5565e000 rwxp 00021000 08:03 210182                            /usr/lib32/libpng12.so.0.1.2.8
5565e000-556c9000 r-xp 00000000 08:03 217115                            /usr/lib32/libGL.so.1.0.8774
556c9000-556e2000 rwxp 0006b000 08:03 217115                            /usr/lib32/libGL.so.1.0.8774
556e2000-556e3000 rwxp 556e2000 00:00 0
556e3000-557b7000 r-xp 00000000 08:03 209722                            /usr/lib32/libstdc++.so.6.0.8
557b7000-557ba000 r-xp 000d4000 08:03 209722                            /usr/lib32/libstdc++.so.6.0.8
557ba000-557bc000 rwxp 000d7000 08:03 209722                            /usr/lib32/libstdc++.so.6.0.8
557bc000-557c2000 rwxp 557bc000 00:00 0
557c2000-557e6000 r-xp 00000000 08:03 276254                            /lib32/libm-2.4.so
557e6000-557e8000 rwxp 00023000 08:03 276254                            /lib32/libm-2.4.so
557e8000-557f2000 r-xp 00000000 08:03 209949                            /usr/lib32/libgcc_s.so.1
557f2000-557f3000 rwxp 00009000 08:03 209949                            /usr/lib32/libgcc_s.so.1
557f3000-55920000 r-xp 00000000 08:03 275590                            /lib32/libc-2.4.so
55920000-55922000 r-xp 0012c000 08:03 275590                            /lib32/libc-2.4.so
55922000-55924000 rwxp 0012e000 08:03 275590                            /lib32/libc-2.4.so
55924000-55928000 rwxp 55924000 00:00 0
55928000-559d8000 r-xp 00000000 08:03 210602                            /usr/lib32/libasound.so.2.0.0
559d8000-559dd000 rwxp 000af000 08:03 210602                            /usr/lib32/libasound.so.2.0.0
559dd000-559e2000 r-xp 00000000 08:03 210597                            /usr/lib32/libartsc.so.0.0.0
559e2000-559e3000 rwxp 00004000 08:03 210597                            /usr/lib32/libartsc.so.0.0.0
559e3000-559e6000 r-xp 00000000 08:03 210173                            /usr/lib32/libgmodule-2.0.sAborted


what to do?

---

