---
title: "Gutsy + flash + swiftweasel"
date: 2007-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by PurposeOfReason on 2007-10-10
I've switched to gutsy becasue I'm highly impatient and because quite a few things are a lot easier. Flash for example, install through synaptic and it worked. At least it did with firefox, but not swiftweasel. How would I go about moving the flash plugin to the swiftweasel folder?

---

### Post by Kilz on 2007-10-11
> **PurposeOfReason said:**
> I've switched to gutsy becasue I'm highly impatient and because quite a few things are a lot easier. Flash for example, install through synaptic and it worked. At least it did with firefox, but not swiftweasel. How would I go about moving the flash plugin to the swiftweasel folder?

What version of Swiftweasel are you running? Dose swiftweasel see other plugins? What is the result of 

ls -al /usr/lib/mozilla/plugins

---

### Post by PurposeOfReason on 2007-10-11
That was the problem I guess because I just got the newest version and now flash works. But like before, if I try to edit settings (right click customize or mess with tab mix plus), I get the following. I'm using gutsy if it matters.

```

shawn@desktop:~$ swiftweasel 
esd: no process killed
the settings directory exists
*** glibc detected *** /usr/local/swiftweasel/swiftweasel-bin: free(): invalid pointer: 0x000000000386d110 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b514f02fb0a]
/lib/libc.so.6(cfree+0x8c)[0x2b514f0336fc]
/usr/local/swiftweasel/swiftweasel-bin[0x68a7e6]
/usr/local/swiftweasel/swiftweasel-bin[0x68cbf1]
/usr/local/swiftweasel/swiftweasel-bin[0x689919]
/usr/local/swiftweasel/swiftweasel-bin[0x7071d2]
/usr/local/swiftweasel/swiftweasel-bin[0x707f06]
/usr/local/swiftweasel/swiftweasel-bin[0x74a3a7]
/usr/local/swiftweasel/swiftweasel-bin[0x8560bb]
/usr/local/swiftweasel/swiftweasel-bin[0x8561ef]
/usr/local/swiftweasel/swiftweasel-bin[0x8566c6]
/usr/local/swiftweasel/swiftweasel-bin[0x85603c]
/usr/local/swiftweasel/swiftweasel-bin[0x722b1c]
/usr/local/swiftweasel/swiftweasel-bin[0x97bde3]
/usr/local/swiftweasel/swiftweasel-bin[0x97e2d7]
/usr/local/swiftweasel/swiftweasel-bin[0x98370e]
/usr/local/swiftweasel/swiftweasel-bin[0x984dc2]
/usr/local/swiftweasel/swiftweasel-bin[0x985bc8]
/usr/local/swiftweasel/swiftweasel-bin[0x97ce1c]
/usr/local/swiftweasel/swiftweasel-bin[0x6dd4fb]
/usr/local/swiftweasel/swiftweasel-bin[0x6d48b8]
/usr/local/swiftweasel/swiftweasel-bin[0x6d7572]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5d)[0x2b514a35e15d]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b514c91b99a]
/usr/lib/libgobject-2.0.so.0[0x2b514c92b6b8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x607)[0x2b514c92c8c7]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b514c92ccc3]
/usr/lib/libgtk-x11-2.0.so.0[0x2b514a4640ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x425)[0x2b514a358645]
/usr/lib/libgdk-x11-2.0.so.0[0x2b514a8188da]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xa5)[0x2b514a818f15]
/usr/lib/libgdk-x11-2.0.so.0[0x2b514a818f69]
/usr/lib/libgdk-x11-2.0.so.0[0x2b514a80031e]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2b514cd87fd3]
/usr/lib/libglib-2.0.so.0[0x2b514cd8b2dd]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2b514cd8b5ea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2b514a358883]
/usr/local/swiftweasel/swiftweasel-bin[0x6dcbe0]
/usr/local/swiftweasel/swiftweasel-bin[0xcaa80e]
/usr/local/swiftweasel/swiftweasel-bin[0x44994a]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b514efdbb44]
/usr/local/swiftweasel/swiftweasel-bin[0x445d4a]
======= Memory map: ========
00400000-01306000 r-xp 00000000 08:01 6029644                            /usr/local/swiftweasel/swiftweasel-bin
01406000-0142b000 rw-p 00f06000 08:01 6029644                            /usr/local/swiftweasel/swiftweasel-bin
0142b000-0447a000 rw-p 0142b000 00:00 0                                  [heap]
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
42805000-42806000 ---p 42805000 00:00 0 
42806000-43006000 rwxp 42806000 00:00 0 
43006000-43007000 ---p 43006000 00:00 0 
43007000-43807000 rwxp 43007000 00:00 0 
43807000-43808000 ---p 43807000 00:00 0 
43808000-44008000 rwxp 43808000 00:00 0 
44008000-44009000 ---p 44008000 00:00 0 
44009000-44809000 rwxp 44009000 00:00 0 
44809000-4480a000 ---p 44809000 00:00 0 
4480a000-4500a000 rwxp 4480a000 00:00 0 
4600c000-4600d000 ---p 4600c000 00:00 0 
4600d000-4680d000 rwxp 4600d000 00:00 0 
4680d000-4680e000 ---p 4680d000 00:00 0 
4680e000-4700e000 rwxp 4680e000 00:00 0 
2aaaaaab1000-2aaaaaab8000 r--s 00000000 08:01 2474049                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaaaab8000-2aaaaaabd000 r--s 00000000 08:01 2474425                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaaaabf000-2aaaaaaf8000 r-xp 00000000 08:01 5932862                    /usr/lib/libgconf-2.so.4.1.2
2aaaaaaf8000-2aaaaacf8000 ---p 00039000 08:01 5932862                    /usr/l

```

---

