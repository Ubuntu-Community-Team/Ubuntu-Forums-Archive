---
title: "More Java problems"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thelasko on 2008-02-18
Fortunately for me I don't use Java much, but it doesn't work on my machine.  This lovely file appears in my home folder every time I try to use it.  I blanked out my username with ***** for security purposes. (not that it matters)

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b690d059e11, pid=16066, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609400):  JavaThread "main" [_thread_in_vm, id=16067, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609400, RBX=0x0000000000609400, RCX=0x0000000000609400, RDX=0x00002b690bbfe280
RSP=0x00000000400fe260, RBP=0x00000000400fe290, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd7c783, R11=0x00002b690cfc92f0
R12=0xec0a5c7000002ab3, R13=0x0000000000609400, R14=0x00000000400fe330, R15=0x00002b690d45f6c0
RIP=0x00002b690d059e11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe260)
0x00000000400fe260:   00000000400fe380 00002aaad8934fd0
0x00000000400fe270:   0000000000000101 00002aaad8934fd0
0x00000000400fe280:   00000000400fe330 0000000000609400
0x00000000400fe290:   00000000400fe300 00002aaaabd7c7b0
0x00000000400fe2a0:   00002aaae8083968 00002aaae8083988
0x00000000400fe2b0:   00002aaae8083990 00002aaae8083990
0x00000000400fe2c0:   00000000400fe2c0 0000000000000000
0x00000000400fe2d0:   00000000400fe330 00002aaad8938a48
0x00000000400fe2e0:   0000000000000000 00002aaad8934fd0
0x00000000400fe2f0:   0000000000000000 00000000400fe320
0x00000000400fe300:   00000000400fe380 00002aaaabd70342
0x00000000400fe310:   0000000000000000 00002aaaabd78cee
0x00000000400fe320:   ec0a5c7000002ab3 00002aaae8083970
0x00000000400fe330:   00002aaabccac260 00000000000000ff
0x00000000400fe340:   00000000400fe340 00002aaad8ef920f
0x00000000400fe350:   00000000400fe398 00002aaad8efc6d8
0x00000000400fe360:   0000000000000000 00002aaad8ef9228
0x00000000400fe370:   00000000400fe320 00000000400fe390
0x00000000400fe380:   00000000400fe3e0 00002aaaabd702b8
0x00000000400fe390:   ec0a5c7000002ab3 00002aaaabd701e9
0x00000000400fe3a0:   00000000400fe3a0 00002aaad8ef92e4
0x00000000400fe3b0:   00000000400fe400 00002aaad8efc6d8
0x00000000400fe3c0:   0000000000000000 00002aaad8ef9308
0x00000000400fe3d0:   00000000400fe390 00000000400fe3f0
0x00000000400fe3e0:   00000000400fe448 00002aaaabd702b8
0x00000000400fe3f0:   0000000000000009 ec0a5c7000002aaa
0x00000000400fe400:   0000000000000000 00000000400fe408
0x00000000400fe410:   00002aaad8ecc299 00000000400fe4d8
0x00000000400fe420:   00002aaad8ed34b0 0000000000000000
0x00000000400fe430:   00002aaad8ecc528 00000000400fe3f0
0x00000000400fe440:   00000000400fe4e0 00000000400fe520
0x00000000400fe450:   00002aaaabd7011a 0000000000000000 

Instructions: (pc=0x00002b690d059e11)
0x00002b690d059e01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002b690d059e11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

Stack: [0x0000000040000000,0x0000000040101000],  sp=0x00000000400fe260,  free space=1016k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x5c9e11]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x30ec06]
V  [libjvm.so+0x30fe0d]
V  [libjvm.so+0x3102f1]
V  [libjvm.so+0x389aaa]
V  [libjvm.so+0x3943fa]
C  [libjava.so+0x1242d]  Java_java_lang_Class_forName0+0x15d
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x39b888]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x33b231]
V  [libjvm.so+0x3583d5]
C  [libjli.so+0x3abd]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00002aaaec041800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=16084, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00000000006a7400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=16082, stack(0x0000000040707000,0x0000000040808000)]
  0x00000000006a5400 JavaThread "CompilerThread1" daemon [_thread_blocked, id=16081, stack(0x0000000040606000,0x0000000040707000)]
  0x00000000006a1400 JavaThread "CompilerThread0" daemon [_thread_blocked, id=16080, stack(0x0000000040505000,0x0000000040606000)]
  0x000000000069fc00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=16079, stack(0x0000000040404000,0x0000000040505000)]
  0x0000000000678000 JavaThread "Finalizer" daemon [_thread_blocked, id=16073, stack(0x0000000040303000,0x0000000040404000)]
  0x0000000000676400 JavaThread "Reference Handler" daemon [_thread_blocked, id=16072, stack(0x0000000040202000,0x0000000040303000)]
=>0x0000000000609400 JavaThread "main" [_thread_in_vm, id=16067, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000670c00 VMThread [stack: 0x0000000040101000,0x0000000040202000] [id=16071]
  0x00000000006a9c00 WatcherThread [stack: 0x0000000040808000,0x0000000040909000] [id=16083]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 2368K, used 658K [0x00002aaaaee30000, 0x00002aaaaf0c0000, 0x00002aaabcc30000)
  eden space 2112K,  19% used [0x00002aaaaee30000, 0x00002aaaaee94ba0, 0x00002aaaaf040000)
  from space 256K,  99% used [0x00002aaaaf040000, 0x00002aaaaf07fff0, 0x00002aaaaf080000)
  to   space 256K,   0% used [0x00002aaaaf080000, 0x00002aaaaf080000, 0x00002aaaaf0c0000)
 tenured generation   total 5312K, used 1083K [0x00002aaabcc30000, 0x00002aaabd160000, 0x00002aaad8830000)
   the space 5312K,  20% used [0x00002aaabcc30000, 0x00002aaabcd3ec00, 0x00002aaabcd3ec00, 0x00002aaabd160000)
 compacting perm gen  total 21248K, used 6964K [0x00002aaad8830000, 0x00002aaad9cf0000, 0x00002aaae3030000)
   the space 21248K,  32% used [0x00002aaad8830000, 0x00002aaad8efd3e8, 0x00002aaad8efd400, 0x00002aaad9cf0000)
No shared spaces configured.

Dynamic libraries:
00400000-00401000 r-xp 00000000 08:05 1818694                            /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00600000-00601000 rw-p 00000000 08:05 1818694                            /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00601000-00cbf000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40205000 ---p 40202000 00:00 0 
40205000-40303000 rwxp 40205000 00:00 0 
40303000-40306000 ---p 40303000 00:00 0 
40306000-40404000 rwxp 40306000 00:00 0 
40404000-40407000 ---p 40404000 00:00 0 
40407000-40505000 rwxp 40407000 00:00 0 
40505000-40508000 ---p 40505000 00:00 0 
40508000-40606000 rwxp 40508000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-40809000 ---p 40808000 00:00 0 
40809000-40909000 rwxp 40809000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
2aaaaaabe000-2aaaaaac6000 r-xp 00000000 08:05 1308764                    /lib/librt-2.6.1.so
2aaaaaac6000-2aaaaacc5000 ---p 00008000 08:05 1308764                    /lib/librt-2.6.1.so
2aaaaacc5000-2aaaaacc7000 rw-p 00007000 08:05 1308764                    /lib/librt-2.6.1.so
2aaaaacc7000-2aaaaacc8000 r--p 2aaaaacc7000 00:00 0 
2aaaaacc8000-2aaaaacc9000 rwxp 2aaaaacc8000 00:00 0 
2aaaaacc9000-2aaaaacd1000 r-xp 00000000 08:05 1818684                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd1000-2aaaaaed0000 ---p 00008000 08:05 1818684                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed0000-2aaaaaed2000 rw-p 00007000 08:05 1818684                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed2000-2aaaaaeda000 rw-s 00000000 08:05 1291842                    /tmp/hsperfdata_****/16066
2aaaaaee3000-2aaaaaef9000 r-xp 00000000 08:05 1308754                    /lib/libnsl-2.6.1.so
2aaaaaef9000-2aaaab0f8000 ---p 00016000 08:05 1308754                    /lib/libnsl-2.6.1.so
2aaaab0f8000-2aaaab0fa000 rw-p 00015000 08:05 1308754                    /lib/libnsl-2.6.1.so
2aaaab0fa000-2aaaab0fc000 rw-p 2aaaab0fa000 00:00 0 
2aaaab0fc000-2aaaab104000 r-xp 00000000 08:05 1308755                    /lib/libnss_compat-2.6.1.so
2aaaab104000-2aaaab303000 ---p 00008000 08:05 1308755                    /lib/libnss_compat-2.6.1.so
2aaaab303000-2aaaab305000 rw-p 00007000 08:05 1308755                    /lib/libnss_compat-2.6.1.so
2aaaab305000-2aaaab30f000 r-xp 00000000 08:05 1308759                    /lib/libnss_nis-2.6.1.so
2aaaab30f000-2aaaab50e000 ---p 0000a000 08:05 1308759                    /lib/libnss_nis-2.6.1.so
2aaaab50e000-2aaaab510000 rw-p 00009000 08:05 1308759                    /lib/libnss_nis-2.6.1.so
2aaaab510000-2aaaab51a000 r-xp 00000000 08:05 1308757                    /lib/libnss_files-2.6.1.so
2aaaab51a000-2aaaab719000 ---p 0000a000 08:05 1308757                    /lib/libnss_files-2.6.1.so
2aaaab719000-2aaaab71b000 rw-p 00009000 08:05 1308757                    /lib/libnss_files-2.6.1.so
2aaaab71b000-2aaaab729000 r-xp 00000000 08:05 1767313                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab729000-2aaaab928000 ---p 0000e000 08:05 1767313                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab928000-2aaaab92a000 rw-p 0000d000 08:05 1767313                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92a000-2aaaab958000 r-xp 00000000 08:05 1766503                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab958000-2aaaabb57000 ---p 0002e000 08:05 1766503                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb57000-2aaaabb5b000 rw-p 0002d000 08:05 1766503                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5b000-2aaaabb6b000 r-xp 00000000 08:05 1767314                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb6b000-2aaaabd6b000 ---p 00010000 08:05 1767314                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6b000-2aaaabd6d000 rw-p 00010000 08:05 1767314                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6d000-2aaaabfdd000 rwxp 2aaaabd6d000 00:00 0 
2aaaabfdd000-2aaaaed6d000 rwxp 2aaaabfdd000 00:00 0 
2aaaaed6d000-2aaaaed77000 rwxp 2aaaaed6d000 00:00 0 
2aaaaed77000-2aaaaee2d000 rwxp 2aaaaed77000 00:00 0 
2aaaaee30000-2aaaaf0c0000 rwxp 2aaaaee30000 00:00 0 
2aaaaf0c0000-2aaabcc30000 rwxp 2aaaaf0c0000 00:00 0 
2aaabcc30000-2aaabd160000 rwxp 2aaabcc30000 00:00 0 
2aaabd160000-2aaad8830000 rwxp 2aaabd160000 00:00 0 
2aaad8830000-2aaad9cf0000 rwxp 2aaad8830000 00:00 0 
2aaad9cf0000-2aaae3030000 rwxp 2aaad9cf0000 00:00 0 
2aaae3030000-2aaae3032000 rwxp 2aaae3030000 00:00 0 
2aaae3032000-2aaae309f000 rwxp 2aaae3032000 00:00 0 
2aaae309f000-2aaae30a2000 rwxp 2aaae309f000 00:00 0 
2aaae30a2000-2aaae317d000 rwxp 2aaae30a2000 00:00 0 
2aaae317d000-2aaae3188000 rwxp 2aaae317d000 00:00 0 
2aaae3188000-2aaae31d1000 rwxp 2aaae3188000 00:00 0 
2aaae31d1000-2aaae31d5000 rwxp 2aaae31d1000 00:00 0 
2aaae31d5000-2aaae32b1000 rwxp 2aaae31d5000 00:00 0 
2aaae32b1000-2aaae32bc000 rwxp 2aaae32b1000 00:00 0 
2aaae32bc000-2aaae3306000 rwxp 2aaae32bc000 00:00 0 
2aaae3306000-2aaae332e000 rw-p 2aaae3306000 00:00 0 
2aaae332e000-2aaae34a8000 r--s 035c6000 08:05 1767348                    /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaae34a8000-2aaae34d8000 rw-p 2aaae34a8000 00:00 0 
2aaae34d8000-2aaae3517000 r--p 00000000 08:05 1767039                    /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaae3517000-2aaae351e000 r--s 00000000 08:05 1717517                    /usr/lib/gconv/gconv-modules.cache
2aaae351e000-2aaae35bc000 r-xp 00000000 08:05 1766182                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae35bc000-2aaae37bb000 ---p 0009e000 08:05 1766182                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37bb000-2aaae37c7000 rw-p 0009d000 08:05 1766182                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37c7000-2aaae37eb000 rw-p 2aaae37c7000 00:00 0 
2aaae37eb000-2aaae3833000 r-xp 00000000 08:05 1818689                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3833000-2aaae3a33000 ---p 00048000 08:05 1818689                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a33000-2aaae3a36000 rw-p 00048000 08:05 1818689                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a36000-2aaae3a38000 rw-p 2aaae3a36000 00:00 0 
2aaae3a38000-2aaae3a41000 r--s 00065000 08:05 1818787                    /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaae3a49000-2aaae3a4b000 r-xp 00000000 08:05 1701949                    /usr/lib/libXinerama.so.1.0.0
2aaae3a4b000-2aaae3c4a000 ---p 00002000 08:05 1701949                    /usr/lib/libXinerama.so.1.0.0
2aaae3c4a000-2aaae3c4b000 rw-p 00001000 08:05 1701949                    /usr/lib/libXinerama.so.1.0.0
2aaae3c4b000-2aaae3c5c000 r-xp 00000000 08:05 1701939                    /usr/lib/libXext.so.6.4.0
2aaae3c5c000-2aaae3e5b000 ---p 00011000 08:05 1701939                    /usr/lib/libXext.so.6.4.0
2aaae3e5b000-2aaae3e5c000 rw-p 00010000 08:05 1701939                    /usr/lib/libXext.so.6.4.0
2aaae3e5c000-2aaae3e61000 r-xp 00000000 08:05 1701967                    /usr/lib/libXtst.so.6.1.0
2aaae3e61000-2aaae4061000 ---p 00005000 08:05 1701967                    /usr/lib/libXtst.so.6.1.0
2aaae4061000-2aaae4062000 rw-p 00005000 08:05 1701967                    /usr/lib/libXtst.so.6.1.0
2aaae4062000-2aaae406a000 r-xp 00000000 08:05 1701947                    /usr/lib/libXi.so.6.0.0
2aaae406a000-2aaae426a000 ---p 00008000 08:05 1701947                    /usr/lib/libXi.so.6.0.0
2aaae426a000-2aaae426b000 rw-p 00008000 08:05 1701947                    /usr/lib/libXi.so.6.0.0
2aaae426b000-2aaae426d000 r--s 00000000 08:05 1424791                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86-64.cache-2
2aaae426d000-2aaae4274000 r--s 00000000 08:05 1426026                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae4274000-2aaae4279000 r--s 00000000 08:05 1426052                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae4279000-2aaae427f000 r--s 000f6000 08:05 1767347                    /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaae427f000-2aaae42ae000 r-xp 00000000 08:05 1767303                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae42ae000-2aaae44ad000 ---p 0002f000 08:05 1767303                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae44ad000-2aaae44af000 rw-p 0002e000 08:05 1767303                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae44af000-2aaae44b1000 rw-p 2aaae44af000 00:00 0 
2aaae44b1000-2aaae44bb000 r--s 00000000 08:05 1426054                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae44bb000-2aaae44c9000 r--s 00000000 08:05 1426056                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae44c9000-2aaae44cb000 r--s 00000000 08:05 1426117                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae44cb000-2aaae44d3000 r--s 00000000 08:05 1426123                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae44d3000-2aaae44d9000 r--s 00000000 08:05 1426128                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae44d9000-2aaae44da000 r--s 00000000 08:05 1426157                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae44da000-2aaae44dc000 r--s 00000000 08:05 1426159                    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaae44dc000-2aaae44dd000 r--s 00000000 08:05 1426160                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae44dd000-2aaae44e0000 r--s 00000000 08:05 1426161                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae44e0000-2aaae44e9000 r--s 00000000 08:05 1426162                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae44e9000-2aaae44f1000 r--s 00000000 08:05 1426164                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae44f1000-2aaae44f8000 r--s 00000000 08:05 1426165                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae44f8000-2aaae44f9000 r--s 00000000 08:05 1426182                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae44f9000-2aaae44fb000 r--s 00000000 08:05 1426184                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae44fb000-2aaae44fc000 r--s 00000000 08:05 1426186                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae44fc000-2aaae44ff000 r--s 00000000 08:05 1426187                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae44ff000-2aaae4509000 r--s 00000000 08:05 1426195                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae4509000-2aaae450e000 r--s 00000000 08:05 1426218                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae450e000-2aaae4511000 r--s 00000000 08:05 1426220                    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaae4511000-2aaae4512000 r--s 00000000 08:05 1426221                    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaae4512000-2aaae4513000 r--s 00000000 08:05 1426222                    /var/cache/fontconfig/aa6caf9eb4374966b8da29da8547f4f4-x86-64.cache-2
2aaae4513000-2aaae4514000 r--s 00000000 08:05 1426336                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae4514000-2aaae4515000 r--s 00000000 08:05 1426337                    /var/cache/fontconfig/c6c650a19da23b8ee5782aefc5f28033-x86-64.cache-2
2aaae4515000-2aaae4516000 r--s 00000000 08:05 1426376                    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaae4516000-2aaae4520000 r--s 00000000 08:05 1424784                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae4520000-2aaae4524000 r--s 00000000 08:05 1424800                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae4524000-2aaae452a000 r--s 00000000 08:05 1424995                    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86-64.cache-2
2aaae452a000-2aaae452c000 r--s 00000000 08:05 1425010                    /var/cache/fontconfig/ae26c1aac6606cb24499bf89ff8f20df-x86-64.cache-2
2aaae452c000-2aaae4533000 r--s 00000000 08:05 1425011                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae4533000-2aaae4536000 r--s 00000000 08:05 1425012                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae4536000-2aaae453a000 r--s 00000000 08:05 1425013                    /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-x86-64.cache-2
2aaae453a000-2aaae4559000 r--s 00000000 08:05 1425014                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaae4559000-2aaae455a000 r--s 00000000 08:05 1425069                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae455a000-2aaae455b000 r--s 00000000 08:05 1425075                    /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86-64.cache-2
2aaae455b000-2aaae4563000 r--s 00000000 08:05 1425113                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae4563000-2aaae456e000 r--s 00000000 08:05 1425114                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae456e000-2aaae4571000 r--s 00000000 08:05 1425115                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae4571000-2aaae4579000 r--s 00000000 08:05 1425116                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae4579000-2aaae457b000 r--s 00000000 08:05 1425117                    /var/cache/fontconfig/5a86461592e14be7c82e45729474f230-x86-64.cache-2
2aaae457b000-2aaae457c000 r--s 00000000 08:05 1425124                    /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86-64.cache-2
2aaae457c000-2aaae457e000 r--s 00000000 08:05 1425245                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae457e000-2aaae4582000 r--s 00000000 08:05 1425447                    /var/cache/fontconfig/f680583fed5bdc90d95a16af47e16528-x86-64.cache-2
2aaae4582000-2aaae4583000 r--s 00000000 08:05 1425448                    /var/cache/fontconfig/7ee55724f82591cb35c3d9771e9e69ed-x86-64.cache-2
2aaae4583000-2aaae4587000 r--s 00000000 08:05 1425451                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae4587000-2aaae4588000 r--s 00000000 08:05 1425487                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae4588000-2aaae45b1000 r--s 00000000 08:05 1425608                    /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86-64.cache-2
2aaae45b1000-2aaae45d9000 r--s 00000000 08:05 1425609                    /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86-64.cache-2
2aaae45d9000-2aaae45fe000 r--s 00000000 08:05 1425610                    /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86-64.cache-2
2aaae45fe000-2aaae45ff000 r--s 00000000 08:05 1425612                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae45ff000-2aaae4604000 r--s 00000000 08:05 1425661                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae4604000-2aaae4605000 r--s 00000000 08:05 1425663                    /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86-64.cache-2
2aaae4605000-2aaae4607000 r--s 00000000 08:05 1425688                    /var/cache/fontconfig/1b70ff56935fd37e75520e134628df26-x86-64.cache-2
2aaae4607000-2aaae4608000 r--s 00000000 08:05 1425689                    /var/cache/fontconfig/79b7902a698c37d747b157374a08587f-x86-64.cache-2
2aaae4608000-2aaae460c000 r--s 00000000 08:05 1426017                    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86-64.cache-2
2aaae460c000-2aaae460f000 r--s 00000000 08:05 1426018                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae460f000-2aaae4617000 r--s 00000000 08:05 1426020                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae4617000-2aaae4619000 r--s 00000000 08:05 1426022                    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86-64.cache-2
2aaae4619000-2aaae461d000 r--s 00000000 08:05 1426023                    /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86-64.cache-2
2aaae46c3000-2aaae46c5000 r--s 00000000 08:05 1424791                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86-64.cache-2
2aaae46c5000-2aaae46cc000 r--s 00000000 08:05 1426026                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae46cc000-2aaae46d1000 r--s 00000000 08:05 1426052                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae46d1000-2aaae46db000 r--s 00000000 08:05 1426054                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae46db000-2aaae46e9000 r--s 00000000 08:05 1426056                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae46e9000-2aaae46eb000 r--s 00000000 08:05 1426117                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae46eb000-2aaae46f3000 r--s 00000000 08:05 1426123                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae46f3000-2aaae46f9000 r--s 00000000 08:05 1426128                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae46f9000-2aaae46fa000 r--s 00000000 08:05 1426157                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae46fa000-2aaae46fc000 r--s 00000000 08:05 1426159                    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaae46fc000-2aaae46fd000 r--s 00000000 08:05 1426160                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae46fd000-2aaae4700000 r--s 00000000 08:05 1426161                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae4700000-2aaae4709000 r--s 00000000 08:05 1426162                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae4709000-2aaae4711000 r--s 00000000 08:05 1426164                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae4711000-2aaae4718000 r--s 00000000 08:05 1426165                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae4718000-2aaae4719000 r--s 00000000 08:05 1426182                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae4719000-2aaae471b000 r--s 00000000 08:05 1426184                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae471b000-2aaae471c000 r--s 00000000 08:05 1426186                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae471c000-2aaae471f000 r--s 00000000 08:05 1426187                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae471f000-2aaae4729000 r--s 00000000 08:05 1426195                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae4729000-2aaae472e000 r--s 00000000 08:05 1426218                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae472e000-2aaae4731000 r--s 00000000 08:05 1426220                    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaae4731000-2aaae4732000 r--s 00000000 08:05 1426221                    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaae4732000-2aaae4733000 r--s 00000000 08:05 1426222                    /var/cache/fontconfig/aa6caf9eb4374966b8da29da8547f4f4-x86-64.cache-2
2aaae4733000-2aaae4734000 r--s 00000000 08:05 1426336                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae4734000-2aaae4735000 r--s 00000000 08:05 1426337                    /var/cache/fontconfig/c6c650a19da23b8ee5782aefc5f28033-x86-64.cache-2
2aaae4735000-2aaae4736000 r--s 00000000 08:05 1426376                    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaae4736000-2aaae4740000 r--s 00000000 08:05 1424784                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae4740000-2aaae4744000 r--s 00000000 08:05 1424800                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae4744000-2aaae474a000 r--s 00000000 08:05 1424995                    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86-64.cache-2
2aaae474a000-2aaae474c000 r--s 00000000 08:05 1425010                    /var/cache/fontconfig/ae26c1aac6606cb24499bf89ff8f20df-x86-64.cache-2
2aaae474c000-2aaae4753000 r--s 00000000 08:05 1425011                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae4753000-2aaae4756000 r--s 00000000 08:05 1425012                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae4756000-2aaae475a000 r--s 00000000 08:05 1425013                    /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-x86-64.cache-2
2aaae475a000-2aaae4779000 r--s 00000000 08:05 1425014                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaae4779000-2aaae477a000 r--s 00000000 08:05 1425069                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae477a000-2aaae477b000 r--s 00000000 08:05 1425075                    /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86-64.cache-2
2aaae477b000-2aaae4783000 r--s 00000000 08:05 1425113                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae4783000-2aaae478e000 r--s 00000000 08:05 1425114                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae478e000-2aaae4791000 r--s 00000000 08:05 1425115                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae4791000-2aaae4799000 r--s 00000000 08:05 1425116                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae4799000-2aaae479b000 r--s 00000000 08:05 1425117                    /var/cache/fontconfig/5a86461592e14be7c82e45729474f230-x86-64.cache-2
2aaae479b000-2aaae479c000 r--s 00000000 08:05 1425124                    /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86-64.cache-2
2aaae479c000-2aaae479e000 r--s 00000000 08:05 1425245                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae479e000-2aaae47a2000 r--s 00000000 08:05 1425447                    /var/cache/fontconfig/f680583fed5bdc90d95a16af47e16528-x86-64.cache-2
2aaae47a2000-2aaae47a3000 r--s 00000000 08:05 1425448                    /var/cache/fontconfig/7ee55724f82591cb35c3d9771e9e69ed-x86-64.cache-2
2aaae47a3000-2aaae47a7000 r--s 00000000 08:05 1425451                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae47a7000-2aaae47a8000 r--s 00000000 08:05 1425487                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae47a8000-2aaae47d1000 r--s 00000000 08:05 1425608                    /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86-64.cache-2
2aaae47d1000-2aaae47f9000 r--s 00000000 08:05 1425609                    /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86-64.cache-2
2aaae47f9000-2aaae481e000 r--s 00000000 08:05 1425610                    /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86-64.cache-2
2aaae481e000-2aaae481f000 r--s 00000000 08:05 1425612                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae481f000-2aaae4824000 r--s 00000000 08:05 1425661                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae4824000-2aaae4825000 r--s 00000000 08:05 1425663                    /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86-64.cache-2
2aaae4825000-2aaae4827000 r--s 00000000 08:05 1425688                    /var/cache/fontconfig/1b70ff56935fd37e75520e134628df26-x86-64.cache-2
2aaae4827000-2aaae4828000 r--s 00000000 08:05 1425689                    /var/cache/fontconfig/79b7902a698c37d747b157374a08587f-x86-64.cache-2
2aaae4828000-2aaae482c000 r--s 00000000 08:05 1426017                    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86-64.cache-2
2aaae482c000-2aaae482f000 r--s 00000000 08:05 1426018                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae482f000-2aaae4837000 r--s 00000000 08:05 1426020                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae4837000-2aaae4839000 r--s 00000000 08:05 1426022                    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86-64.cache-2
2aaae4839000-2aaae483d000 r--s 00000000 08:05 1426023                    /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86-64.cache-2
2aaae8000000-2aaae8205000 rw-p 2aaae8000000 00:00 0 
2aaae8205000-2aaaec000000 ---p 2aaae8205000 00:00 0 
2aaaec000000-2aaaec137000 rw-p 2aaaec000000 00:00 0 
2aaaec137000-2aaaf0000000 ---p 2aaaec137000 00:00 0 
2aaaf0000000-2aaaf0046000 r-xp 00000000 08:05 1766188                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaaf0046000-2aaaf0245000 ---p 00046000 08:05 1766188                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaaf0245000-2aaaf0249000 rw-p 00045000 08:05 1766188                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaaf0249000-2aaaf0259000 rw-p 2aaaf0249000 00:00 0 
2aaaf026a000-2aaaf02e4000 r-xp 00000000 08:05 1702140                    /usr/lib/libfreetype.so.6.3.16
2aaaf02e4000-2aaaf04e4000 ---p 0007a000 08:05 1702140                    /usr/lib/libfreetype.so.6.3.16
2aaaf04e4000-2aaaf04e9000 rw-p 0007a000 08:05 1702140                    /usr/lib/libfreetype.so.6.3.16
2aaaf04e9000-2aaaf04f6000 r-xp 00000000 08:05 1308226                    /lib/libgcc_s.so.1
2aaaf04f6000-2aaaf06f6000 ---p 0000d000 08:05 1308226                    /lib/libgcc_s.so.1
2aaaf06f6000-2aaaf06f7000 rw-p 0000d000 08:05 1308226                    /lib/libgcc_s.so.1
2aaaf06f7000-2aaaf070d000 r-xp 00000000 08:05 1702700                    /usr/lib/libz.so.1.2.3.3
2aaaf070d000-2aaaf090d000 ---p 00016000 08:05 1702700                    /usr/lib/libz.so.1.2.3.3
2aaaf090d000-2aaaf090e000 rw-p 00016000 08:05 1702700                    /usr/lib/libz.so.1.2.3.3
2b690b7ca000-2b690b7e7000 r-xp 00000000 08:05 1308172                    /lib/ld-2.6.1.so
2b690b7e7000-2b690b7ea000 rw-p 2b690b7e7000 00:00 0 
2b690b9e6000-2b690b9e8000 rw-p 0001c000 08:05 1308172                    /lib/ld-2.6.1.so
2b690b9e8000-2b690b9fe000 r-xp 00000000 08:05 1308762                    /lib/libpthread-2.6.1.so
2b690b9fe000-2b690bbfd000 ---p 00016000 08:05 1308762                    /lib/libpthread-2.6.1.so
2b690bbfd000-2b690bbff000 rw-p 00015000 08:05 1308762                    /lib/libpthread-2.6.1.so
2b690bbff000-2b690bc03000 rw-p 2b690bbff000 00:00 0 
2b690bc03000-2b690bd0d000 r-xp 00000000 08:05 1701918                    /usr/lib/libX11.so.6.2.0
2b690bd0d000-2b690bf0d000 ---p 0010a000 08:05 1701918                    /usr/lib/libX11.so.6.2.0
2b690bf0d000-2b690bf14000 rw-p 0010a000 08:05 1701918                    /usr/lib/libX11.so.6.2.0
2b690bf14000-2b690bf24000 r-xp 00000000 08:05 1766178                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b690bf24000-2b690c124000 ---p 00010000 08:05 1766178                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b690c124000-2b690c126000 rw-p 00010000 08:05 1766178                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b690c126000-2b690c127000 rw-p 2b690c126000 00:00 0 
2b690c127000-2b690c129000 r-xp 00000000 08:05 1308751                    /lib/libdl-2.6.1.so
2b690c129000-2b690c329000 ---p 00002000 08:05 1308751                    /lib/libdl-2.6.1.so
2b690c329000-2b690c32b000 rw-p 00002000 08:05 1308751                    /lib/libdl-2.6.1.so
2b690c32b000-2b690c47d000 r-xp 00000000 08:05 1308673                    /lib/libc-2.6.1.so
2b690c47d000-2b690c67c000 ---p 00152000 08:05 1308673                    /lib/libc-2.6.1.so
2b690c67c000-2b690c67f000 r--p 00151000 08:05 1308673                    /lib/libc-2.6.1.so
2b690c67f000-2b690c681000 rw-p 00154000 08:05 1308673                    /lib/libc-2.6.1.so
2b690c681000-2b690c686000 rw-p 2b690c681000 00:00 0 
2b690c686000-2b690c688000 r-xp 00000000 08:05 1701924                    /usr/lib/libXau.so.6.0.0
2b690c688000-2b690c887000 ---p 00002000 08:05 1701924                    /usr/lib/libXau.so.6.0.0
2b690c887000-2b690c888000 rw-p 00001000 08:05 1701924                    /usr/lib/libXau.so.6.0.0
2b690c888000-2b690c889000 rw-p 2b690c888000 00:00 0 
2b690c889000-2b690c88e000 r-xp 00000000 08:05 1701935                    /usr/lib/libXdmcp.so.6.0.0
2b690c88e000-2b690ca8d000 ---p 00005000 08:05 1701935                    /usr/lib/libXdmcp.so.6.0.0
2b690ca8d000-2b690ca8e000 rw-p 00004000 08:05 1701935                    /usr/lib/libXdmcp.so.6.0.0
2b690ca8e000-2b690ca90000 rw-p 2b690ca8e000 00:00 0 
2b690ca90000-2b690d1d8000 r-xp 00000000 08:05 1818686                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b690d1d8000-2b690d3d8000 ---p 00748000 08:05 1818686                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b690d3d8000-2b690d452000 rw-p 00748000 08:05 1818686                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b690d452000-2b690d48c000 rw-p 2b690d452000 00:00 0 
2b690d49d000-2b690d51d000 r-xp 00000000 08:05 1308752                    /lib/libm-2.6.1.so
2b690d51d000-2b690d71c000 ---p 00080000 08:05 1308752                    /lib/libm-2.6.1.so
2b690d71c000-2b690d71e000 rw-p 0007f000 08:05 1308752                    /lib/libm-2.6.1.so
7fff9f2cb000-7fff9f2df000 rwxp 7fff9f2cb000 00:00 0                      [stack]
7fff9f2df000-7fff9f2e0000 rw-p 7fff9f2df000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Dapplication.home=/usr/lib/jvm/java-7-icedtea/jre 
java_command: sun.applet.PluginMain /home/*****/.gcjwebplugin/gcj-instance-6624-1-plugin-to-appletviewer /home/*****/.gcjwebplugin/gcj-instance-6624-1-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=****
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server:/usr/lib/jvm/java-7-icedtea/jre/lib/amd64:/usr/lib/jvm/java-7-icedtea/jre/../lib/amd64:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mre/mre
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4ccc50], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 8114, NOFILE 1024, AS infinity
load average:0.22 0.21 0.11

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 1019468k(381676k free), swap 1309256k(976700k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Mon Jan 21 12:04:39 2008
elapsed time: 0 seconds
```

I tried to read[ the other page]("http://ubuntuforums.org/showthread.php?t=580792") about fixing Java but it was entirely too long.  From what I gathered those solutions didn't work for me.  Most of the repositories didn't work and the ones that did didn't fix the problem.  Please only reply if you have a suggestion to fix this.  Let's try to keep it short and to the point.

Thanks in advance

---

### Post by jespdj on 2008-02-19
Is there a special reason why you need to use IcedTea Java, which is a kind of development version for the next version of Sun Java (version 7)? Since IcedTea is more or less beta software, you can expect there to be bugs.

One reason for people who run 64-bit systems to use IcedTea instead of Sun Java 6 is because the 64-bit version of Sun Java 6 does not include a Java browser plug-in, so you can't run Java applets in your 64-bit browser.

If you don't need to run applets, just use Sun Java 6, which is more stable than IcedTea.

---

### Post by Rog-Mahal on 2008-02-29
I have the exact same error, and am limited in my options because I want a browser plugin and I also use azureus (or i did until this java error made it crash every time it starts). Is there another option that will solve this problem?

---

### Post by Thelasko on 2008-03-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/177514](https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/177514) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It sounds like it's completely broken.  [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/177514") says there is a fix in the pipeline.

---

