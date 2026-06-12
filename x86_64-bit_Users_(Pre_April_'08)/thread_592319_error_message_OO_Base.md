---
title: "error message OO Base"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by malbaugh on 2007-10-26
I get this error message using OO Base. The JRE 1.7 fails. JRE 1.6 works.
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aebebe05e11, pid=7215, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609000):  JavaThread "main" [_thread_in_vm, id=7217, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609000, RBX=0x0000000000609000, RCX=0x0000000000609000, RDX=0x00002aebeb0c4280
RSP=0x00000000400fe8a0, RBP=0x00000000400fe8d0, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd80743, R11=0x00002aebebd752f0
R12=0x00818ee000000009, R13=0x0000000000609000, R14=0x00000000400fe970, R15=0x00002aebec20b6c0
RIP=0x00002aebebe05e11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe8a0)
0x00000000400fe8a0:   00000000400fe9c0 00002aaad8944fd0
0x00000000400fe8b0:   0000000000000101 00002aaad8944fd0
0x00000000400fe8c0:   00000000400fe970 0000000000609000
0x00000000400fe8d0:   00000000400fe940 00002aaaabd80770
0x00000000400fe8e0:   0000000000655a78 0000000000655a98
0x00000000400fe8f0:   0000000000655aa0 0000000000655aa0
0x00000000400fe900:   00000000400fe900 0000000000000000
0x00000000400fe910:   00000000400fe970 00002aaad8948a48
0x00000000400fe920:   0000000000000000 00002aaad8944fd0
0x00000000400fe930:   0000000000000000 00000000400fe960
0x00000000400fe940:   00000000400fe9c0 00002aaaabd74342
0x00000000400fe950:   0000000000000000 00002aaaabd7ccce
0x00000000400fe960:   00818ee000000009 0000000000655a80
0x00000000400fe970:   00002aaaaf093e10 00000000000000ff
0x00000000400fe980:   00000000400fe980 00002aaad8e83597
0x00000000400fe990:   00000000400fe9d8 00002aaad8e86a60
0x00000000400fe9a0:   0000000000000000 00002aaad8e835b0
0x00000000400fe9b0:   00000000400fe960 00000000400fe9d0
0x00000000400fe9c0:   00000000400fea20 00002aaaabd742b8
0x00000000400fe9d0:   00818ee000000009 00002aaaabd741e9
0x00000000400fe9e0:   00000000400fe9e0 00002aaad8e8366c
0x00000000400fe9f0:   00000000400fea40 00002aaad8e86a60
0x00000000400fea00:   0000000000000000 00002aaad8e83690
0x00000000400fea10:   00000000400fe9d0 00000000400fea30
0x00000000400fea20:   00000000400fea88 00002aaaabd742b8
0x00000000400fea30:   0000000000000009 00818ee000000000
0x00000000400fea40:   0000000000000000 00000000400fea48
0x00000000400fea50:   00002aaad8b78f59 00000000400feb18
0x00000000400fea60:   00002aaad8b969e0 0000000000000000
0x00000000400fea70:   00002aaad8b791e8 00000000400fea30
0x00000000400fea80:   00000000400feb20 00000000400feb60
0x00000000400fea90:   00002aaaabd7411a 0000000000000000 

Instructions: (pc=0x00002aebebe05e11)
0x00002aebebe05e01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002aebebe05e11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

Stack: [0x0000000040000000,0x0000000040101000],  sp=0x00000000400fe8a0,  free space=1018k
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
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0000000000689400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=7226, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00000000006a7400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=7224, stack(0x0000000040707000,0x0000000040808000)]
  0x00000000006a4c00 JavaThread "CompilerThread1" daemon [_thread_blocked, id=7223, stack(0x0000000040606000,0x0000000040707000)]
  0x00000000006a1000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=7222, stack(0x0000000040505000,0x0000000040606000)]
  0x000000000069f800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=7221, stack(0x0000000040404000,0x0000000040505000)]
  0x0000000000678000 JavaThread "Finalizer" daemon [_thread_blocked, id=7220, stack(0x0000000040303000,0x0000000040404000)]
  0x0000000000676400 JavaThread "Reference Handler" daemon [_thread_blocked, id=7219, stack(0x0000000040202000,0x0000000040303000)]
=>0x0000000000609000 JavaThread "main" [_thread_in_vm, id=7217, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000670c00 VMThread [stack: 0x0000000040101000,0x0000000040202000] [id=7218]
  0x00000000006a9800 WatcherThread [stack: 0x0000000040808000,0x0000000040909000] [id=7225]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 2368K, used 1187K [0x00002aaaaee40000, 0x00002aaaaf0d0000, 0x00002aaabcc40000)
  eden space 2112K,  44% used [0x00002aaaaee40000, 0x00002aaaaef28ec8, 0x00002aaaaf050000)
  from space 256K,  99% used [0x00002aaaaf090000, 0x00002aaaaf0cfff8, 0x00002aaaaf0d0000)
  to   space 256K,   0% used [0x00002aaaaf050000, 0x00002aaaaf050000, 0x00002aaaaf090000)
 tenured generation   total 5312K, used 455K [0x00002aaabcc40000, 0x00002aaabd170000, 0x00002aaad8840000)
   the space 5312K,   8% used [0x00002aaabcc40000, 0x00002aaabccb1c48, 0x00002aaabccb1e00, 0x00002aaabd170000)
 compacting perm gen  total 21248K, used 6429K [0x00002aaad8840000, 0x00002aaad9d00000, 0x00002aaae3040000)
   the space 21248K,  30% used [0x00002aaad8840000, 0x00002aaad8e87770, 0x00002aaad8e87800, 0x00002aaad9d00000)
No shared spaces configured.

Dynamic libraries:
00400000-00401000 r-xp 00000000 03:01 900046                             /usr/lib/jvm/java-7-icedtea/jre/bin/java
00600000-00601000 rw-p 00000000 03:01 900046                             /usr/lib/jvm/java-7-icedtea/jre/bin/java
00601000-00b6c000 rw-p 00601000 00:00 0                                  [heap]
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
2aaaaaaab000-2aaaaaab4000 r--s 00065000 03:01 883168                     /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaaaaac0000-2aaaaaac8000 r-xp 00000000 03:01 2191521                    /lib/librt-2.6.1.so
2aaaaaac8000-2aaaaacc7000 ---p 00008000 03:01 2191521                    /lib/librt-2.6.1.so
2aaaaacc7000-2aaaaacc9000 rw-p 00007000 03:01 2191521                    /lib/librt-2.6.1.so
2aaaaacc9000-2aaaaacca000 r--p 2aaaaacc9000 00:00 0 
2aaaaacca000-2aaaaaccb000 rwxp 2aaaaacca000 00:00 0 
2aaaaaccb000-2aaaaacd3000 r-xp 00000000 03:01 900042                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd3000-2aaaaaed2000 ---p 00008000 03:01 900042                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed2000-2aaaaaed4000 rw-p 00007000 03:01 900042                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed4000-2aaaaaedc000 rw-s 00000000 03:01 1815135                    /tmp/hsperfdata_malbaugh/7215
2aaaaaee7000-2aaaaaefd000 r-xp 00000000 03:01 2191511                    /lib/libnsl-2.6.1.so
2aaaaaefd000-2aaaab0fc000 ---p 00016000 03:01 2191511                    /lib/libnsl-2.6.1.so
2aaaab0fc000-2aaaab0fe000 rw-p 00015000 03:01 2191511                    /lib/libnsl-2.6.1.so
2aaaab0fe000-2aaaab100000 rw-p 2aaaab0fe000 00:00 0 
2aaaab100000-2aaaab108000 r-xp 00000000 03:01 2191512                    /lib/libnss_compat-2.6.1.so
2aaaab108000-2aaaab307000 ---p 00008000 03:01 2191512                    /lib/libnss_compat-2.6.1.so
2aaaab307000-2aaaab309000 rw-p 00007000 03:01 2191512                    /lib/libnss_compat-2.6.1.so
2aaaab309000-2aaaab313000 r-xp 00000000 03:01 2191516                    /lib/libnss_nis-2.6.1.so
2aaaab313000-2aaaab512000 ---p 0000a000 03:01 2191516                    /lib/libnss_nis-2.6.1.so
2aaaab512000-2aaaab514000 rw-p 00009000 03:01 2191516                    /lib/libnss_nis-2.6.1.so
2aaaab514000-2aaaab51e000 r-xp 00000000 03:01 2191514                    /lib/libnss_files-2.6.1.so
2aaaab51e000-2aaaab71d000 ---p 0000a000 03:01 2191514                    /lib/libnss_files-2.6.1.so
2aaaab71d000-2aaaab71f000 rw-p 00009000 03:01 2191514                    /lib/libnss_files-2.6.1.so
2aaaab71f000-2aaaab72d000 r-xp 00000000 03:01 900040                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab72d000-2aaaab92c000 ---p 0000e000 03:01 900040                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92c000-2aaaab92e000 rw-p 0000d000 03:01 900040                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92e000-2aaaab95c000 r-xp 00000000 03:01 900021                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab95c000-2aaaabb5b000 ---p 0002e000 03:01 900021                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5b000-2aaaabb5f000 rw-p 0002d000 03:01 900021                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5f000-2aaaabb6f000 r-xp 00000000 03:01 900041                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb6f000-2aaaabd6f000 ---p 00010000 03:01 900041                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6f000-2aaaabd71000 rw-p 00010000 03:01 900041                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd71000-2aaaabfe1000 rwxp 2aaaabd71000 00:00 0 
2aaaabfe1000-2aaaaed71000 rwxp 2aaaabfe1000 00:00 0 
2aaaaed71000-2aaaaed7b000 rwxp 2aaaaed71000 00:00 0 
2aaaaed7b000-2aaaaee31000 rwxp 2aaaaed7b000 00:00 0 
2aaaaee40000-2aaaaf0d0000 rwxp 2aaaaee40000 00:00 0 
2aaaaf0d0000-2aaabcc40000 rwxp 2aaaaf0d0000 00:00 0 
2aaabcc40000-2aaabd170000 rwxp 2aaabcc40000 00:00 0 
2aaabd170000-2aaad8840000 rwxp 2aaabd170000 00:00 0 
2aaad8840000-2aaad9d00000 rwxp 2aaad8840000 00:00 0 
2aaad9d00000-2aaae3040000 rwxp 2aaad9d00000 00:00 0 
2aaae3040000-2aaae3042000 rwxp 2aaae3040000 00:00 0 
2aaae3042000-2aaae30af000 rwxp 2aaae3042000 00:00 0 
2aaae30af000-2aaae30b2000 rwxp 2aaae30af000 00:00 0 
2aaae30b2000-2aaae318d000 rwxp 2aaae30b2000 00:00 0 
2aaae318d000-2aaae3198000 rwxp 2aaae318d000 00:00 0 
2aaae3198000-2aaae31e1000 rwxp 2aaae3198000 00:00 0 
2aaae31e1000-2aaae31e5000 rwxp 2aaae31e1000 00:00 0 
2aaae31e5000-2aaae32c1000 rwxp 2aaae31e5000 00:00 0 
2aaae32c1000-2aaae32cc000 rwxp 2aaae32c1000 00:00 0 
2aaae32cc000-2aaae3316000 rwxp 2aaae32cc000 00:00 0 
2aaae3316000-2aaae333e000 rw-p 2aaae3316000 00:00 0 
2aaae333e000-2aaae34b8000 r--s 035c6000 03:01 883185                     /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaae34b8000-2aaae34e8000 rw-p 2aaae34b8000 00:00 0 
2aaae34e8000-2aaae3527000 r--p 00000000 03:01 556954                     /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaae3527000-2aaae352e000 r--s 00000000 03:01 524831                     /usr/lib/gconv/gconv-modules.cache
2aaae352e000-2aaae35cc000 r-xp 00000000 03:01 900010                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae35cc000-2aaae37cb000 ---p 0009e000 03:01 900010                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37cb000-2aaae37d7000 rw-p 0009d000 03:01 900010                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37d7000-2aaae37fb000 rw-p 2aaae37d7000 00:00 0 
2aaae37fb000-2aaae3843000 r-xp 00000000 03:01 900045                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3843000-2aaae3a43000 ---p 00048000 03:01 900045                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a43000-2aaae3a46000 rw-p 00048000 03:01 900045                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a46000-2aaae3a48000 rw-p 2aaae3a46000 00:00 0 
2aaae3a48000-2aaae3a4b000 r--s 00000000 03:01 2339541                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae3a4b000-2aaae3a50000 r--s 00000000 03:01 2339663                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae3a50000-2aaae3a52000 r--s 00000000 03:01 2339664                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae3a5b000-2aaae3a5d000 r-xp 00000000 03:01 1455446                    /usr/lib/libXinerama.so.1.0.0
2aaae3a5d000-2aaae3c5c000 ---p 00002000 03:01 1455446                    /usr/lib/libXinerama.so.1.0.0
2aaae3c5c000-2aaae3c5d000 rw-p 00001000 03:01 1455446                    /usr/lib/libXinerama.so.1.0.0
2aaae3c5d000-2aaae3c6e000 r-xp 00000000 03:01 1455414                    /usr/lib/libXext.so.6.4.0
2aaae3c6e000-2aaae3e6d000 ---p 00011000 03:01 1455414                    /usr/lib/libXext.so.6.4.0
2aaae3e6d000-2aaae3e6e000 rw-p 00010000 03:01 1455414                    /usr/lib/libXext.so.6.4.0
2aaae3e6e000-2aaae3f78000 r-xp 00000000 03:01 1455390                    /usr/lib/libX11.so.6.2.0
2aaae3f78000-2aaae4178000 ---p 0010a000 03:01 1455390                    /usr/lib/libX11.so.6.2.0
2aaae4178000-2aaae417f000 rw-p 0010a000 03:01 1455390                    /usr/lib/libX11.so.6.2.0
2aaae417f000-2aaae4184000 r-xp 00000000 03:01 491671                     /usr/lib/libXtst.so.6.1.0
2aaae4184000-2aaae4384000 ---p 00005000 03:01 491671                     /usr/lib/libXtst.so.6.1.0
2aaae4384000-2aaae4385000 rw-p 00005000 03:01 491671                     /usr/lib/libXtst.so.6.1.0
2aaae4385000-2aaae438d000 r-xp 00000000 03:01 1455444                    /usr/lib/libXi.so.6.0.0
2aaae438d000-2aaae458d000 ---p 00008000 03:01 1455444                    /usr/lib/libXi.so.6.0.0
2aaae458d000-2aaae458e000 rw-p 00008000 03:01 1455444                    /usr/lib/libXi.so.6.0.0
2aaae458e000-2aaae4590000 r-xp 00000000 03:01 490585                     /usr/lib/libXau.so.6.0.0
2aaae4590000-2aaae478f000 ---p 00002000 03:01 490585                     /usr/lib/libXau.so.6.0.0
2aaae478f000-2aaae4790000 rw-p 00001000 03:01 490585                     /usr/lib/libXau.so.6.0.0
2aaae4790000-2aaae4795000 r-xp 00000000 03:01 491148                     /usr/lib/libXdmcp.so.6.0.0
2aaae4795000-2aaae4994000 ---p 00005000 03:01 491148                     /usr/lib/libXdmcp.so.6.0.0
2aaae4994000-2aaae4995000 rw-p 00004000 03:01 491148                     /usr/lib/libXdmcp.so.6.0.0
2aaae4995000-2aaae49db000 r-xp 00000000 03:01 900013                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae49db000-2aaae4bda000 ---p 00046000 03:01 900013                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae4bda000-2aaae4bde000 rw-p 00045000 03:01 900013                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae4bde000-2aaae4bee000 rw-p 2aaae4bde000 00:00 0 
2aaae4bee000-2aaae4bf9000 r--s 00000000 03:01 2339669                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae4bf9000-2aaae4bfa000 r--s 00000000 03:01 2339671                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae4c01000-2aaae4c7b000 r-xp 00000000 03:01 1455384                    /usr/lib/libfreetype.so.6.3.16
2aaae4c7b000-2aaae4e7b000 ---p 0007a000 03:01 1455384                    /usr/lib/libfreetype.so.6.3.16
2aaae4e7b000-2aaae4e80000 rw-p 0007a000 03:01 1455384                    /usr/lib/libfreetype.so.6.3.16
2aaae4e80000-2aaae4e8d000 r-xp 00000000 03:01 2191189                    /lib/libgcc_s.so.1
2aaae4e8d000-2aaae508d000 ---p 0000d000 03:01 2191189                    /lib/libgcc_s.so.1
2aaae508d000-2aaae508e000 rw-p 0000d000 03:01 2191189                    /lib/libgcc_s.so.1
2aaae508e000-2aaae50a4000 r-xp 00000000 03:01 1455381                    /usr/lib/libz.so.1.2.3.3
2aaae50a4000-2aaae52a4000 ---p 00016000 03:01 1455381                    /usr/lib/libz.so.1.2.3.3
2aaae52a4000-2aaae52a5000 rw-p 00016000 03:01 1455381                    /usr/lib/libz.so.1.2.3.3
2aaae56fd000-2aaae5705000 r--s 00000000 03:01 2339676                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae5705000-2aaae570a000 r--s 00000000 03:01 2339678                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae570a000-2aaae570c000 r--s 00000000 03:01 2339680                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae570c000-2aaae570d000 r--s 00000000 03:01 2339682                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae570d000-2aaae5711000 r--s 00000000 03:01 2339683                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae5711000-2aaae5714000 r--s 00000000 03:01 2339687                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae5714000-2aaae571a000 r--s 00000000 03:01 2339689                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae571a000-2aaae5721000 r--s 00000000 03:01 2339695                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae5721000-2aaae5722000 r--s 00000000 03:01 2339696                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae5722000-2aaae5725000 r--s 00000000 03:01 2339697                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae5725000-2aaae5726000 r--s 00000000 03:01 2339702                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae5726000-2aaae5729000 r--s 00000000 03:01 2339715                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae5729000-2aaae5730000 r--s 00000000 03:01 2339731                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae5730000-2aaae5734000 r--s 00000000 03:01 2339737                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae5734000-2aaae5735000 r--s 00000000 03:01 2339235                    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaae5735000-2aaae5736000 r--s 00000000 03:01 2339750                    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaae5736000-2aaae5737000 r--s 00000000 03:01 2339751                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae5737000-2aaae5741000 r--s 00000000 03:01 2339569                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae5741000-2aaae5746000 r--s 00000000 03:01 2339593                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae5746000-2aaae574a000 r--s 00000000 03:01 2339594                    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaae574a000-2aaae5751000 r--s 00000000 03:01 2339595                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae5751000-2aaae5754000 r--s 00000000 03:01 2339596                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae5754000-2aaae5755000 r--s 00000000 03:01 2339597                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae5755000-2aaae575d000 r--s 00000000 03:01 2339602                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae575d000-2aaae5768000 r--s 00000000 03:01 2339604                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae5768000-2aaae576a000 r--s 00000000 03:01 2339605                    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaae576a000-2aaae576d000 r--s 00000000 03:01 2339606                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae576d000-2aaae5775000 r--s 00000000 03:01 2339607                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae5775000-2aaae5778000 r--s 00000000 03:01 2339610                    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaae5778000-2aaae577a000 r--s 00000000 03:01 2339613                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae577a000-2aaae577c000 r--s 00000000 03:01 2339614                    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaae577c000-2aaae5780000 r--s 00000000 03:01 2339615                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae5780000-2aaae5782000 r--s 00000000 03:01 2339620                    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaae5782000-2aaae5783000 r--s 00000000 03:01 2339623                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae5783000-2aaae5784000 r--s 00000000 03:01 2339624                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae5784000-2aaae5789000 r--s 00000000 03:01 2339626                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae5789000-2aaae578a000 r--s 00000000 03:01 2339637                    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaae578a000-2aaae578b000 r--s 00000000 03:01 2339639                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaae578b000-2aaae578e000 r--s 00000000 03:01 2339645                    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaae578e000-2aaae578f000 r--s 00000000 03:01 2339649                    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaae578f000-2aaae5792000 r--s 00000000 03:01 2339650                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae5792000-2aaae579a000 r--s 00000000 03:01 2339655                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae579a000-2aaae579d000 r--s 00000000 03:01 2339541                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae579d000-2aaae57a2000 r--s 00000000 03:01 2339663                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae57a2000-2aaae57a4000 r--s 00000000 03:01 2339664                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae57a4000-2aaae57aa000 r--s 000f6000 03:01 883184                     /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaae57aa000-2aaae57d9000 r-xp 00000000 03:01 900030                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae57d9000-2aaae59d8000 ---p 0002f000 03:01 900030                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae59d8000-2aaae59da000 rw-p 0002e000 03:01 900030                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae59da000-2aaae59dc000 rw-p 2aaae59da000 00:00 0 
2aaae5c05000-2aaae5c10000 r--s 00000000 03:01 2339669                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae5c10000-2aaae5c11000 r--s 00000000 03:01 2339671                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae5c11000-2aaae5c19000 r--s 00000000 03:01 2339676                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae5c19000-2aaae5c1e000 r--s 00000000 03:01 2339678                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae5c1e000-2aaae5c20000 r--s 00000000 03:01 2339680                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae5c20000-2aaae5c21000 r--s 00000000 03:01 2339682                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae5c21000-2aaae5c25000 r--s 00000000 03:01 2339683                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae5c25000-2aaae5c28000 r--s 00000000 03:01 2339687                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae5c28000-2aaae5c2e000 r--s 00000000 03:01 2339689                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae5c2e000-2aaae5c35000 r--s 00000000 03:01 2339695                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae5c35000-2aaae5c36000 r--s 00000000 03:01 2339696                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae5c36000-2aaae5c39000 r--s 00000000 03:01 2339697                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae5c39000-2aaae5c3a000 r--s 00000000 03:01 2339702                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae5c3a000-2aaae5c3d000 r--s 00000000 03:01 2339715                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae5c3d000-2aaae5c44000 r--s 00000000 03:01 2339731                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae5c44000-2aaae5c48000 r--s 00000000 03:01 2339737                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae5c48000-2aaae5c49000 r--s 00000000 03:01 2339235                    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaae5c49000-2aaae5c4a000 r--s 00000000 03:01 2339750                    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaae5c4a000-2aaae5c4b000 r--s 00000000 03:01 2339751                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae5c4b000-2aaae5c55000 r--s 00000000 03:01 2339569                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae5c55000-2aaae5c5a000 r--s 00000000 03:01 2339593                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae5c5a000-2aaae5c5e000 r--s 00000000 03:01 2339594                    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaae5c5e000-2aaae5c65000 r--s 00000000 03:01 2339595                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae5c65000-2aaae5c68000 r--s 00000000 03:01 2339596                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae5c68000-2aaae5c69000 r--s 00000000 03:01 2339597                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae5c69000-2aaae5c71000 r--s 00000000 03:01 2339602                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae5c71000-2aaae5c7c000 r--s 00000000 03:01 2339604                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae5c7c000-2aaae5c7e000 r--s 00000000 03:01 2339605                    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaae5c7e000-2aaae5c81000 r--s 00000000 03:01 2339606                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae5c81000-2aaae5c89000 r--s 00000000 03:01 2339607                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae5c89000-2aaae5c8c000 r--s 00000000 03:01 2339610                    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaae5c8c000-2aaae5c8e000 r--s 00000000 03:01 2339613                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae5c8e000-2aaae5c90000 r--s 00000000 03:01 2339614                    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaae5c90000-2aaae5c94000 r--s 00000000 03:01 2339615                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae5c94000-2aaae5c96000 r--s 00000000 03:01 2339620                    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaae5c96000-2aaae5c97000 r--s 00000000 03:01 2339623                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae5c97000-2aaae5c98000 r--s 00000000 03:01 2339624                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae5c98000-2aaae5c9d000 r--s 00000000 03:01 2339626                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae5c9d000-2aaae5c9e000 r--s 00000000 03:01 2339637                    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaae5c9e000-2aaae5c9f000 r--s 00000000 03:01 2339639                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaae5c9f000-2aaae5ca2000 r--s 00000000 03:01 2339645                    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaae5ca2000-2aaae5ca3000 r--s 00000000 03:01 2339649                    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaae5ca3000-2aaae5ca6000 r--s 00000000 03:01 2339650                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae5ca6000-2aaae5cae000 r--s 00000000 03:01 2339655                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae8000000-2aaae8021000 rw-p 2aaae8000000 00:00 0 
2aaae8021000-2aaaec000000 ---p 2aaae8021000 00:00 0 
2aebeac90000-2aebeacad000 r-xp 00000000 03:01 2191502                    /lib/ld-2.6.1.so
2aebeacad000-2aebeacb0000 rw-p 2aebeacad000 00:00 0 
2aebeaeac000-2aebeaeae000 rw-p 0001c000 03:01 2191502                    /lib/ld-2.6.1.so
2aebeaeae000-2aebeaec4000 r-xp 00000000 03:01 2191519                    /lib/libpthread-2.6.1.so
2aebeaec4000-2aebeb0c3000 ---p 00016000 03:01 2191519                    /lib/libpthread-2.6.1.so
2aebeb0c3000-2aebeb0c5000 rw-p 00015000 03:01 2191519                    /lib/libpthread-2.6.1.so
2aebeb0c5000-2aebeb0c9000 rw-p 2aebeb0c5000 00:00 0 
2aebeb0c9000-2aebeb0d9000 r-xp 00000000 03:01 900008                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2aebeb0d9000-2aebeb2d9000 ---p 00010000 03:01 900008                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2aebeb2d9000-2aebeb2db000 rw-p 00010000 03:01 900008                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2aebeb2db000-2aebeb2dd000 r-xp 00000000 03:01 2191508                    /lib/libdl-2.6.1.so
2aebeb2dd000-2aebeb4dd000 ---p 00002000 03:01 2191508                    /lib/libdl-2.6.1.so
2aebeb4dd000-2aebeb4df000 rw-p 00002000 03:01 2191508                    /lib/libdl-2.6.1.so
2aebeb4df000-2aebeb4e0000 rw-p 2aebeb4df000 00:00 0 
2aebeb4e0000-2aebeb632000 r-xp 00000000 03:01 2191505                    /lib/libc-2.6.1.so
2aebeb632000-2aebeb831000 ---p 00152000 03:01 2191505                    /lib/libc-2.6.1.so
2aebeb831000-2aebeb834000 r--p 00151000 03:01 2191505                    /lib/libc-2.6.1.so
2aebeb834000-2aebeb836000 rw-p 00154000 03:01 2191505                    /lib/libc-2.6.1.so
2aebeb836000-2aebeb83c000 rw-p 2aebeb836000 00:00 0 
2aebeb83c000-2aebebf84000 r-xp 00000000 03:01 900043                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2aebebf84000-2aebec184000 ---p 00748000 03:01 900043                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2aebec184000-2aebec1fe000 rw-p 00748000 03:01 900043                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2aebec1fe000-2aebec238000 rw-p 2aebec1fe000 00:00 0 
2aebec24b000-2aebec2cb000 r-xp 00000000 03:01 2191509                    /lib/libm-2.6.1.so
2aebec2cb000-2aebec4ca000 ---p 00080000 03:01 2191509                    /lib/libm-2.6.1.so
2aebec4ca000-2aebec4cc000 rw-p 0007f000 03:01 2191509                    /lib/libm-2.6.1.so
7fffbfe05000-7fffbfe1a000 rwxp 7fffbfe05000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
java_command: JREProperties
Launcher Type: SUN_STANDARD

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
PATH=/usr/lib/openoffice/program:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=malbaugh
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server:/usr/lib/jvm/java-7-icedtea/jre/lib/amd64:/usr/lib/jvm/java-7-icedtea/jre/../lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/client:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/native_threads:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64:/usr/lib/openoffice/program
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

uname:Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 4094, NOFILE 1024, AS infinity
load average:0.30 0.19 0.19

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 79 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 512196k(6572k free), swap 891568k(853220k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Thu Oct 25 09:20:09 2007
elapsed time: 2 seconds

---

