---
title: "regnum x86_64 error"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by allorder on 2007-10-20
In feisty I had no problem with regnum now in 7.10 I got this error:

allorder@ubuntu:~/regnum$ ./rolauncher 
*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x0000000000b30970 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b02df460b0a]
/lib/libc.so.6(cfree+0x8c)[0x2b02df4646fc]
./rolauncher[0x530ebf]
./rolauncher[0x531404]
./rolauncher[0x431b81]
./rolauncher[0x41e1f9]
./rolauncher[0x428e22]
./rolauncher[0x4bcb16]
./rolauncher[0x4bcc57]
./rolauncher[0x41b9da]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b02df40cb44]
./rolauncher(__gxx_personality_v0+0x3e2)[0x41b79a]
======= Memory map: ========
00400000-00872000 r-xp 00000000 03:01 3850242                            /home/allorder/regnum/rolauncher
00971000-009b3000 rw-p 00471000 03:01 3850242                            /home/allorder/regnum/rolauncher
009b3000-00c70000 rw-p 009b3000 00:00 0                                  [heap]
40002000-40004000 rwxp 00000000 00:0e 2853                               /dev/zero
40004000-40005000 ---p 40004000 00:00 0 
40005000-40805000 rwxp 40005000 00:00 0 
2aaaaaaab000-2aaaaab1f000 rw-p 2aaaaaaab000 00:00 0 
2aaaaab1f000-2aaaaab5e000 r--p 00000000 03:01 9012038                    /usr/lib/locale/en_CA.utf8/LC_CTYPE
2aaaaab5e000-2aaaaab65000 r--s 00000000 03:01 8979750                    /usr/lib/gconv/gconv-modules.cache
2aaaaab65000-2aaaaab67000 r-xp 00000000 03:01 8979746                    /usr/lib/gconv/UTF-32.so
2aaaaab67000-2aaaaad66000 ---p 00002000 03:01 8979746                    /usr/lib/gconv/UTF-32.so
2aaaaad66000-2aaaaad68000 rw-p 00001000 03:01 8979746                    /usr/lib/gconv/UTF-32.so
2aaaaad68000-2aaaaad69000 r--p 00000000 03:01 9012039                    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
2aaaaad69000-2aaaaad6a000 r--p 00000000 03:01 9012040                    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
2aaaaad6a000-2aaaaad6b000 r--p 00000000 03:01 9012045                    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
2aaaaad6b000-2aaaaad6c000 r--p 00000000 03:01 9012036                    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
2aaaaad6c000-2aaaaad6d000 r--p 00000000 03:01 9012042                    /usr/lib/locale/en_CA.utf8/LC_NAME
2aaaaad6d000-2aaaaad6e000 r--p 00000000 03:01 9012044                    /usr/lib/locale/en_CA.utf8/LC_PAPER
2aaaaad6e000-2aaaaad6f000 r--p 00000000 03:01 9012047                    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2aaaaad6f000-2aaaaad70000 r--p 00000000 03:01 9012041                    /usr/lib/locale/en_CA.utf8/LC_MONETARY
2aaaaad70000-2aaaaae50000 r--p 00000000 03:01 9012037                    /usr/lib/locale/en_CA.utf8/LC_COLLATE
2aaaaae50000-2aaaaae51000 r--p 00000000 03:01 9012046                    /usr/lib/locale/en_CA.utf8/LC_TIME
2aaaaae51000-2aaaaae52000 r--p 00000000 03:01 9012043                    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
2aaaaae52000-2aaaaae62000 r--p 00000000 03:01 9339864                    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo
2aaaaae70000-2aaaaae78000 r-xp 00000000 03:01 9994323                    /lib/libnss_compat-2.6.1.so
2aaaaae78000-2aaaab077000 ---p 00008000 03:01 9994323                    /lib/libnss_compat-2.6.1.so
2aaaab077000-2aaaab079000 rw-p 00007000 03:01 9994323                    /lib/libnss_compat-2.6.1.so
2aaaab079000-2aaaab08f000 r-xp 00000000 03:01 9994321                    /lib/libnsl-2.6.1.so
2aaaab08f000-2aaaab28e000 ---p 00016000 03:01 9994321                    /lib/libnsl-2.6.1.so
2aaaab28e000-2aaaab290000 rw-p 00015000 03:01 9994321                    /lib/libnsl-2.6.1.so
2aaaab290000-2aaaab292000 rw-p 2aaaab290000 00:00 0 
2aaaab292000-2aaaab29c000 r-xp 00000000 03:01 9994337                    /lib/libnss_nis-2.6.1.so
2aaaab29c000-2aaaab49b000 ---p 0000a000 03:01 9994337                    /lib/libnss_nis-2.6.1.so
2aaaab49b000-2aaaab49d000 rw-p 00009000 03:01 9994337                    /lib/libnss_nis-2.6.1.so
2aaaab49d000-2aaaab4a7000 r-xp 00000000 03:01 9994327                    /lib/libnss_files-2.6.1.so
2aaaab4a7000-2aaaab6a6000 ---p 0000a000 03:01 9994327                    /lib/libnss_files-2.6.1.so
2aaaab6a6000-2aaaab6a8000 rw-p 00009Aborted (core dumped)

any ideas ? :confused:

---

