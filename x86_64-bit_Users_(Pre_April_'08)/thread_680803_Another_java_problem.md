---
title: "Another java problem"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Freek07 on 2008-01-28
64bit ubuntu 7.10, I've installed icedtea plugin and instead of java applets, I get grey boxes. I've tried anything I could think of, without success.

Java and javascript ARE enabled in firefox!

**Firefox version:**
root@Grandis:/usr/lib/firefox/plugins# dpkg -l | grep firefox
ii  firefox                                    2.0.0.11+2nobinonly-0ubuntu0.7.10 lightweight web browser based on Mozilla


**I've got java:**

root@Grandis:/usr/lib/firefox/plugins# dpkg -l | grep java
ii  icedtea-java7-bin                          7~b21-1.4+20071007-0ubuntu6       Java runtime based on OpenJDK
ii  icedtea-java7-jre                          7~b21-1.4+20071007-0ubuntu6       Java runtime based on OpenJDK
ii  icedtea-java7-plugin                       7~b21-1.4+20071007-0ubuntu6       Java plugin based on OpenJDK and gcjwebplugi
ii  java-common                                0.26ubuntu1                       Base of all Java packages
ii  libhsqldb-java                             1.8.0.8-1ubuntu1                  Java SQL database engine
ii  libjaxp1.3-java                            1.3.03-5                          Java XML parser and transformer APIs (DOM, S
ii  libjline-java                              0.9.5-3ubuntu2                    Java library for handling console input
ii  libservlet2.4-java                         5.0.30-6ubuntu1                   Servlet 2.4 and JSP 2.0 Java library.
ii  libxalan2-java                             2.7.0-4                           XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                            2.8.1-2                           Validating XML parser for Java with DOM leve
ii  openoffice.org-java-common                 1:2.3.0-1ubuntu5.3                OpenOffice.org office suite Java support arc
root@Grandis:/usr/lib/firefox/plugins# cd

**Java -version returns:**
root@Grandis:/usr/lib/firefox/plugins# java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
root@Grandis:/usr/lib/firefox/plugins# 

**Firefox detects plugin:**

GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes

Any ideas?

---

### Post by Freek07 on 2008-01-28
I've found I get crash files in my home dir.
It seems java crashes.
There's one of the dumps, hope it helps:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b235c06fe11, pid=20632, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609400):  JavaThread "main" [_thread_in_vm, id=20638, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609400, RBX=0x0000000000609400, RCX=0x0000000000609400, RDX=0x00002b235ac14280
RSP=0x00000000400fe260, RBP=0x00000000400fe290, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd80783, R11=0x00002b235bfdf2f0
R12=0xf816744000002ab3, R13=0x0000000000609400, R14=0x00000000400fe330, R15=0x00002b235c4756c0
RIP=0x00002b235c06fe11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe260)
0x00000000400fe260:   00000000400fe380 00002aaaaef44fd0
0x00000000400fe270:   0000000000000101 00002aaaaef44fd0
0x00000000400fe280:   00000000400fe330 0000000000609400
0x00000000400fe290:   00000000400fe300 00002aaaabd807b0
0x00000000400fe2a0:   0000000000b19c20 0000000000b19c40
0x00000000400fe2b0:   0000000000b19c48 0000000000b19c48
0x00000000400fe2c0:   00000000400fe2c0 0000000000000000
0x00000000400fe2d0:   00000000400fe330 00002aaaaef48a48
0x00000000400fe2e0:   0000000000000000 00002aaaaef44fd0
0x00000000400fe2f0:   0000000000000000 00000000400fe320
0x00000000400fe300:   00000000400fe380 00002aaaabd74342
0x00000000400fe310:   0000000000000000 00002aaaabd7ccee
0x00000000400fe320:   f816744000002ab3 0000000000b19c28
0x00000000400fe330:   00002aaae2a490c0 00000000000000ff
0x00000000400fe340:   00000000400fe340 00002aaaaf508287
0x00000000400fe350:   00000000400fe398 00002aaaaf50b750
0x00000000400fe360:   0000000000000000 00002aaaaf5082a0
0x00000000400fe370:   00000000400fe320 00000000400fe390
0x00000000400fe380:   00000000400fe3e0 00002aaaabd742b8
0x00000000400fe390:   f816744000002ab3 00002aaaabd741e9
0x00000000400fe3a0:   00000000400fe3a0 00002aaaaf50835c
0x00000000400fe3b0:   00000000400fe400 00002aaaaf50b750
0x00000000400fe3c0:   0000000000000000 00002aaaaf508380
0x00000000400fe3d0:   00000000400fe390 00000000400fe3f0
0x00000000400fe3e0:   00000000400fe448 00002aaaabd742b8
0x00000000400fe3f0:   0000000000000009 f816744000002aaa
0x00000000400fe400:   0000000000000000 00000000400fe408
0x00000000400fe410:   00002aaaaf4db311 00000000400fe4d8
0x00000000400fe420:   00002aaaaf4e2528 0000000000000000
0x00000000400fe430:   00002aaaaf4db5a0 00000000400fe3f0
0x00000000400fe440:   00000000400fe4e0 00000000400fe520
0x00000000400fe450:   00002aaaabd7411a 0000000000000000 

Instructions: (pc=0x00002b235c06fe11)
0x00002b235c06fe01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002b235c06fe11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

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
  0x00002aaaf8110400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=20659, stack(0x0000000040d0d000,0x0000000040e0e000)]
  0x00002aaaf8021c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=20652, stack(0x0000000040b0b000,0x0000000040c0c000)]
  0x00002aaaf801f000 JavaThread "CompilerThread1" daemon [_thread_blocked, id=20651, stack(0x0000000040a0a000,0x0000000040b0b000)]
  0x00002aaaf801d000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=20650, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00002aaaf801b800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=20649, stack(0x0000000040808000,0x0000000040909000)]
  0x000000000067f000 JavaThread "Finalizer" daemon [_thread_blocked, id=20646, stack(0x0000000040707000,0x0000000040808000)]
  0x000000000067d800 JavaThread "Reference Handler" daemon [_thread_blocked, id=20645, stack(0x0000000040606000,0x0000000040707000)]
=>0x0000000000609400 JavaThread "main" [_thread_in_vm, id=20638, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000677c00 VMThread [stack: 0x0000000040505000,0x0000000040606000] [id=20644]
  0x00002aaaf8024400 WatcherThread [stack: 0x0000000040c0c000,0x0000000040d0d000] [id=20653]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 18496K, used 3175K [0x00002aaae2a40000, 0x00002aaae3ee0000, 0x00002aaaf7440000)
  eden space 15872K, 20% used [0x00002aaae2a40000,0x00002aaae2d59f10,0x00002aaae39c0000)
  from space 2624K, 0% used [0x00002aaae3c50000,0x00002aaae3c50000,0x00002aaae3ee0000)
  to   space 2624K, 0% used [0x00002aaae39c0000,0x00002aaae39c0000,0x00002aaae3c50000)
 PSOldGen        total 42240K, used 0K [0x00002aaab9640000, 0x00002aaabbf80000, 0x00002aaae2a40000)
  object space 42240K, 0% used [0x00002aaab9640000,0x00002aaab9640000,0x00002aaabbf80000)
 PSPermGen       total 21248K, used 6961K [0x00002aaaaee40000, 0x00002aaab0300000, 0x00002aaab9640000)
  object space 21248K, 32% used [0x00002aaaaee40000,0x00002aaaaf50c460,0x00002aaab0300000)

Dynamic libraries:
00400000-00401000 r-xp 00000000 08:02 167168                             /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00600000-00601000 rw-p 00000000 08:02 167168                             /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00601000-00b7c000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40203000 ---p 40202000 00:00 0 
40203000-40303000 rwxp 40203000 00:00 0 
40303000-40304000 ---p 40303000 00:00 0 
40304000-40404000 rwxp 40304000 00:00 0 
40404000-40405000 ---p 40404000 00:00 0 
40405000-40505000 rwxp 40405000 00:00 0 
40505000-40506000 ---p 40505000 00:00 0 
40506000-40606000 rwxp 40506000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-4080b000 ---p 40808000 00:00 0 
4080b000-40909000 rwxp 4080b000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
40a0a000-40a0d000 ---p 40a0a000 00:00 0 
40a0d000-40b0b000 rwxp 40a0d000 00:00 0 
40b0b000-40b0e000 ---p 40b0b000 00:00 0 
40b0e000-40c0c000 rwxp 40b0e000 00:00 0 
40c0c000-40c0d000 ---p 40c0c000 00:00 0 
40c0d000-40d0d000 rwxp 40c0d000 00:00 0 
40d0d000-40d10000 ---p 40d0d000 00:00 0 
40d10000-40e0e000 rwxp 40d10000 00:00 0 
2aaaaaac0000-2aaaaaac8000 r-xp 00000000 08:02 10672                      /lib/librt-2.6.1.so
2aaaaaac8000-2aaaaacc7000 ---p 00008000 08:02 10672                      /lib/librt-2.6.1.so
2aaaaacc7000-2aaaaacc9000 rw-p 00007000 08:02 10672                      /lib/librt-2.6.1.so
2aaaaacc9000-2aaaaacca000 r--p 2aaaaacc9000 00:00 0 
2aaaaacca000-2aaaaaccb000 rw-p 2aaaaacca000 00:00 0 
2aaaaaccb000-2aaaaacd3000 r-xp 00000000 08:02 167160                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd3000-2aaaaaed2000 ---p 00008000 08:02 167160                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed2000-2aaaaaed4000 rw-p 00007000 08:02 167160                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed4000-2aaaaaedc000 rw-s 00000000 08:02 177274                     /tmp/hsperfdata_may/20632
2aaaaaee7000-2aaaaaefd000 r-xp 00000000 08:02 10662                      /lib/libnsl-2.6.1.so
2aaaaaefd000-2aaaab0fc000 ---p 00016000 08:02 10662                      /lib/libnsl-2.6.1.so
2aaaab0fc000-2aaaab0fe000 rw-p 00015000 08:02 10662                      /lib/libnsl-2.6.1.so
2aaaab0fe000-2aaaab100000 rw-p 2aaaab0fe000 00:00 0 
2aaaab100000-2aaaab108000 r-xp 00000000 08:02 10663                      /lib/libnss_compat-2.6.1.so
2aaaab108000-2aaaab307000 ---p 00008000 08:02 10663                      /lib/libnss_compat-2.6.1.so
2aaaab307000-2aaaab309000 rw-p 00007000 08:02 10663                      /lib/libnss_compat-2.6.1.so
2aaaab309000-2aaaab313000 r-xp 00000000 08:02 10667                      /lib/libnss_nis-2.6.1.so
2aaaab313000-2aaaab512000 ---p 0000a000 08:02 10667                      /lib/libnss_nis-2.6.1.so
2aaaab512000-2aaaab514000 rw-p 00009000 08:02 10667                      /lib/libnss_nis-2.6.1.so
2aaaab514000-2aaaab51e000 r-xp 00000000 08:02 10665                      /lib/libnss_files-2.6.1.so
2aaaab51e000-2aaaab71d000 ---p 0000a000 08:02 10665                      /lib/libnss_files-2.6.1.so
2aaaab71d000-2aaaab71f000 rw-p 00009000 08:02 10665                      /lib/libnss_files-2.6.1.so
2aaaab71f000-2aaaab72d000 r-xp 00000000 08:02 167157                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab72d000-2aaaab92c000 ---p 0000e000 08:02 167157                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92c000-2aaaab92e000 rw-p 0000d000 08:02 167157                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92e000-2aaaab95c000 r-xp 00000000 08:02 167138                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab95c000-2aaaabb5b000 ---p 0002e000 08:02 167138                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5b000-2aaaabb5f000 rw-p 0002d000 08:02 167138                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5f000-2aaaabb6f000 r-xp 00000000 08:02 167158                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb6f000-2aaaabd6f000 ---p 00010000 08:02 167158                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6f000-2aaaabd71000 rw-p 00010000 08:02 167158                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd71000-2aaaabfe1000 rwxp 2aaaabd71000 00:00 0 
2aaaabfe1000-2aaaaed71000 rwxp 2aaaabfe1000 00:00 0 
2aaaaed71000-2aaaaed7b000 rwxp 2aaaaed71000 00:00 0 
2aaaaed7b000-2aaaaee31000 rwxp 2aaaaed7b000 00:00 0 
2aaaaee40000-2aaab0300000 rwxp 2aaaaee40000 00:00 0 
2aaab0300000-2aaab9640000 rwxp 2aaab0300000 00:00 0 
2aaab9640000-2aaabbf80000 rwxp 2aaab9640000 00:00 0 
2aaabbf80000-2aaae2a40000 rwxp 2aaabbf80000 00:00 0 
2aaae2a40000-2aaae3ee0000 rwxp 2aaae2a40000 00:00 0 
2aaae3ee0000-2aaaf7440000 rwxp 2aaae3ee0000 00:00 0 
2aaaf7440000-2aaaf744b000 rwxp 2aaaf7440000 00:00 0 
2aaaf744b000-2aaaf7494000 rwxp 2aaaf744b000 00:00 0 
2aaaf7494000-2aaaf74a9000 rwxp 2aaaf7494000 00:00 0 
2aaaf74a9000-2aaaf75de000 rwxp 2aaaf74a9000 00:00 0 
2aaaf75de000-2aaaf75e9000 rwxp 2aaaf75de000 00:00 0 
2aaaf75e9000-2aaaf7683000 rwxp 2aaaf75e9000 00:00 0 
2aaaf7683000-2aaaf7699000 rwxp 2aaaf7683000 00:00 0 
2aaaf7699000-2aaaf77ce000 rwxp 2aaaf7699000 00:00 0 
2aaaf77ce000-2aaaf77d9000 rwxp 2aaaf77ce000 00:00 0 
2aaaf77d9000-2aaaf7822000 rwxp 2aaaf77d9000 00:00 0 
2aaaf7822000-2aaaf784a000 rw-p 2aaaf7822000 00:00 0 
2aaaf784a000-2aaaf79c4000 r--s 035c6000 08:02 161204                     /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaaf79c4000-2aaaf7a99000 rw-p 2aaaf79c4000 00:00 0 
2aaaf7a99000-2aaaf7ad8000 r--p 00000000 08:02 10556                      /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaaf7ad8000-2aaaf7adf000 r--s 00000000 08:02 2250                       /usr/lib/gconv/gconv-modules.cache
2aaaf7adf000-2aaaf7b7d000 r-xp 00000000 08:02 167127                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaaf7b7d000-2aaaf7d7c000 ---p 0009e000 08:02 167127                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaaf7d7c000-2aaaf7d88000 rw-p 0009d000 08:02 167127                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaaf7d88000-2aaaf7dac000 rw-p 2aaaf7d88000 00:00 0 
2aaaf7dac000-2aaaf7df4000 r-xp 00000000 08:02 167165                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaaf7df4000-2aaaf7ff4000 ---p 00048000 08:02 167165                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaaf7ff4000-2aaaf7ff7000 rw-p 00048000 08:02 167165                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaaf7ff7000-2aaaf7ff9000 rw-p 2aaaf7ff7000 00:00 0 
2aaaf8000000-2aaaf81a1000 rw-p 2aaaf8000000 00:00 0 
2aaaf81a1000-2aaafc000000 ---p 2aaaf81a1000 00:00 0 
2aaafc000000-2aaafc009000 r--s 00065000 08:02 161182                     /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaafc013000-2aaafc015000 r-xp 00000000 08:02 7075                       /usr/lib/libXinerama.so.1.0.0
2aaafc015000-2aaafc214000 ---p 00002000 08:02 7075                       /usr/lib/libXinerama.so.1.0.0
2aaafc214000-2aaafc215000 rw-p 00001000 08:02 7075                       /usr/lib/libXinerama.so.1.0.0
2aaafc215000-2aaafc226000 r-xp 00000000 08:02 7065                       /usr/lib/libXext.so.6.4.0
2aaafc226000-2aaafc425000 ---p 00011000 08:02 7065                       /usr/lib/libXext.so.6.4.0
2aaafc425000-2aaafc426000 rw-p 00010000 08:02 7065                       /usr/lib/libXext.so.6.4.0
2aaafc426000-2aaafc42b000 r-xp 00000000 08:02 7093                       /usr/lib/libXtst.so.6.1.0
2aaafc42b000-2aaafc62b000 ---p 00005000 08:02 7093                       /usr/lib/libXtst.so.6.1.0
2aaafc62b000-2aaafc62c000 rw-p 00005000 08:02 7093                       /usr/lib/libXtst.so.6.1.0
2aaafc62c000-2aaafc634000 r-xp 00000000 08:02 7073                       /usr/lib/libXi.so.6.0.0
2aaafc634000-2aaafc834000 ---p 00008000 08:02 7073                       /usr/lib/libXi.so.6.0.0
2aaafc834000-2aaafc835000 rw-p 00008000 08:02 7073                       /usr/lib/libXi.so.6.0.0
2aaafc835000-2aaafc87b000 r-xp 00000000 08:02 167130                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaafc87b000-2aaafca7a000 ---p 00046000 08:02 167130                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaafca7a000-2aaafca7e000 rw-p 00045000 08:02 167130                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaafca7e000-2aaafca8e000 rw-p 2aaafca7e000 00:00 0 
2aaafcaa1000-2aaafcb1b000 r-xp 00000000 08:02 7266                       /usr/lib/libfreetype.so.6.3.16
2aaafcb1b000-2aaafcd1b000 ---p 0007a000 08:02 7266                       /usr/lib/libfreetype.so.6.3.16
2aaafcd1b000-2aaafcd20000 rw-p 0007a000 08:02 7266                       /usr/lib/libfreetype.so.6.3.16
2aaafcd20000-2aaafcd2d000 r-xp 00000000 08:02 2177                       /lib/libgcc_s.so.1
2aaafcd2d000-2aaafcf2d000 ---p 0000d000 08:02 2177                       /lib/libgcc_s.so.1
2aaafcf2d000-2aaafcf2e000 rw-p 0000d000 08:02 2177                       /lib/libgcc_s.so.1
2aaafcf2e000-2aaafcf44000 r-xp 00000000 08:02 7826                       /usr/lib/libz.so.1.2.3.3
2aaafcf44000-2aaafd144000 ---p 00016000 08:02 7826                       /usr/lib/libz.so.1.2.3.3
2aaafd144000-2aaafd145000 rw-p 00016000 08:02 7826                       /usr/lib/libz.so.1.2.3.3
2aaafd145000-2aaafd14c000 r--s 00000000 08:02 171741                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaafd14c000-2aaafd151000 r--s 00000000 08:02 76832                      /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaafd151000-2aaafd157000 r--s 00000000 08:02 171744                     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaafd157000-2aaafd15d000 r--s 000f6000 08:02 161203                     /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaafd38d000-2aaafd392000 r--s 00000000 08:02 76834                      /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaafd392000-2aaafd393000 r--s 00000000 08:02 76835                      /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaafd393000-2aaafd39b000 r--s 00000000 08:02 76836                      /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaafd39b000-2aaafd3a1000 r--s 00000000 08:02 171747                     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaafd3a1000-2aaafd3a2000 r--s 00000000 08:02 77390                      /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaafd3a2000-2aaafd3a3000 r--s 00000000 08:02 171748                     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaafd3a3000-2aaafd3a4000 r--s 00000000 08:02 77391                      /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaafd3a4000-2aaafd3a7000 r--s 00000000 08:02 83890                      /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaafd3a7000-2aaafd3aa000 r--s 00000000 08:02 83892                      /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaafd3aa000-2aaafd3b0000 r--s 00000000 08:02 83894                      /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaafd3b0000-2aaafd3b7000 r--s 00000000 08:02 83896                      /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaafd3b7000-2aaafd3b8000 r--s 00000000 08:02 88330                      /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaafd3b8000-2aaafd3ba000 r--s 00000000 08:02 88331                      /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaafd3ba000-2aaafd3bb000 r--s 00000000 08:02 88332                      /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaafd3bb000-2aaafd3bd000 r--s 00000000 08:02 88333                      /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaafd3bd000-2aaafd3c6000 r--s 00000000 08:02 171749                     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaafd3c6000-2aaafd3ca000 r--s 00000000 08:02 88335                      /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaafd3ca000-2aaafd3cd000 r--s 00000000 08:02 171752                     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaafd3cd000-2aaafd3ce000 r--s 00000000 08:02 171753                     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaafd3ce000-2aaafd3cf000 r--s 00000000 08:02 88337                      /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaafd3cf000-2aaafd3d0000 r--s 00000000 08:02 88338                      /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaafd3d0000-2aaafd3d2000 r--s 00000000 08:02 5134                       /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaafd3d2000-2aaafd3d6000 r--s 00000000 08:02 73617                      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaafd3d6000-2aaafd3dd000 r--s 00000000 08:02 73618                      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaafd3dd000-2aaafd3e0000 r--s 00000000 08:02 73619                      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaafd3e0000-2aaafd3ff000 r--s 00000000 08:02 171974                     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaafd3ff000-2aaafd400000 r--s 00000000 08:02 73620                      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaafd400000-2aaafd408000 r--s 00000000 08:02 73621                      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaafd408000-2aaafd413000 r--s 00000000 08:02 73622                      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaafd413000-2aaafd416000 r--s 00000000 08:02 73623                      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaafd416000-2aaafd419000 r--s 00000000 08:02 73624                      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaafd419000-2aaafd41b000 r--s 00000000 08:02 73625                      /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaafd41b000-2aaafd41f000 r--s 00000000 08:02 73721                      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaafd41f000-2aaafd420000 r--s 00000000 08:02 73723                      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaafd420000-2aaafd421000 r--s 00000000 08:02 73724                      /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaafd421000-2aaafd426000 r--s 00000000 08:02 74382                      /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaafd426000-2aaafd429000 r--s 00000000 08:02 74383                      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaafd429000-2aaafd431000 r--s 00000000 08:02 74390                      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaafd59d000-2aaafd5a4000 r--s 00000000 08:02 171741                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaafd5a4000-2aaafd5a9000 r--s 00000000 08:02 76832                      /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaafd5a9000-2aaafd5af000 r--s 00000000 08:02 171744                     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaafd5af000-2aaafd5b4000 r--s 00000000 08:02 76834                      /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaafd5b4000-2aaafd5b5000 r--s 00000000 08:02 76835                      /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaafd5b5000-2aaafd5bd000 r--s 00000000 08:02 76836                      /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaafd5bd000-2aaafd5c3000 r--s 00000000 08:02 171747                     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaafd5c3000-2aaafd5c4000 r--s 00000000 08:02 77390                      /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaafd5c4000-2aaafd5c5000 r--s 00000000 08:02 171748                     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaafd5c5000-2aaafd5c6000 r--s 00000000 08:02 77391                      /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaafd5c6000-2aaafd5c9000 r--s 00000000 08:02 83890                      /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaafd5c9000-2aaafd5cc000 r--s 00000000 08:02 83892                      /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaafd5cc000-2aaafd5d2000 r--s 00000000 08:02 83894                      /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaafd5d2000-2aaafd5d9000 r--s 00000000 08:02 83896                      /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaafd5d9000-2aaafd5da000 r--s 00000000 08:02 88330                      /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaafd5da000-2aaafd5dc000 r--s 00000000 08:02 88331                      /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaafd5dc000-2aaafd5dd000 r--s 00000000 08:02 88332                      /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaafd5dd000-2aaafd5df000 r--s 00000000 08:02 88333                      /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaafd5df000-2aaafd5e8000 r--s 00000000 08:02 171749                     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaafd5e8000-2aaafd5ec000 r--s 00000000 08:02 88335                      /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaafd5ec000-2aaafd5ef000 r--s 00000000 08:02 171752                     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaafd5ef000-2aaafd5f0000 r--s 00000000 08:02 171753                     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaafd5f0000-2aaafd5f1000 r--s 00000000 08:02 88337                      /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaafd5f1000-2aaafd5f2000 r--s 00000000 08:02 88338                      /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaafd5f2000-2aaafd5f4000 r--s 00000000 08:02 5134                       /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaafd5f4000-2aaafd5f8000 r--s 00000000 08:02 73617                      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaafd5f8000-2aaafd5ff000 r--s 00000000 08:02 73618                      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaafd5ff000-2aaafd602000 r--s 00000000 08:02 73619                      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaafd602000-2aaafd621000 r--s 00000000 08:02 171974                     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaafd621000-2aaafd622000 r--s 00000000 08:02 73620                      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaafd622000-2aaafd62a000 r--s 00000000 08:02 73621                      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaafd62a000-2aaafd635000 r--s 00000000 08:02 73622                      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaafd635000-2aaafd638000 r--s 00000000 08:02 73623                      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaafd638000-2aaafd63b000 r--s 00000000 08:02 73624                      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaafd63b000-2aaafd63d000 r--s 00000000 08:02 73625                      /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaafd63d000-2aaafd641000 r--s 00000000 08:02 73721                      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaafd641000-2aaafd642000 r--s 00000000 08:02 73723                      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaafd642000-2aaafd643000 r--s 00000000 08:02 73724                      /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaafd643000-2aaafd648000 r--s 00000000 08:02 74382                      /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaafd648000-2aaafd64b000 r--s 00000000 08:02 74383                      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaafd64b000-2aaafd653000 r--s 00000000 08:02 74390                      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaafd653000-2aaafd682000 r-xp 00000000 08:02 167147                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaafd682000-2aaafd881000 ---p 0002f000 08:02 167147                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaafd881000-2aaafd883000 rw-p 0002e000 08:02 167147                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaafd883000-2aaafd885000 rw-p 2aaafd883000 00:00 0 
2b235a7e0000-2b235a7fd000 r-xp 00000000 08:02 10653                      /lib/ld-2.6.1.so
2b235a7fd000-2b235a800000 rw-p 2b235a7fd000 00:00 0 
2b235a9fc000-2b235a9fe000 rw-p 0001c000 08:02 10653                      /lib/ld-2.6.1.so
2b235a9fe000-2b235aa14000 r-xp 00000000 08:02 10670                      /lib/libpthread-2.6.1.so
2b235aa14000-2b235ac13000 ---p 00016000 08:02 10670                      /lib/libpthread-2.6.1.so
2b235ac13000-2b235ac15000 rw-p 00015000 08:02 10670                      /lib/libpthread-2.6.1.so
2b235ac15000-2b235ac19000 rw-p 2b235ac15000 00:00 0 
2b235ac19000-2b235ad23000 r-xp 00000000 08:02 7044                       /usr/lib/libX11.so.6.2.0
2b235ad23000-2b235af23000 ---p 0010a000 08:02 7044                       /usr/lib/libX11.so.6.2.0
2b235af23000-2b235af2a000 rw-p 0010a000 08:02 7044                       /usr/lib/libX11.so.6.2.0
2b235af2a000-2b235af3a000 r-xp 00000000 08:02 167125                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b235af3a000-2b235b13a000 ---p 00010000 08:02 167125                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b235b13a000-2b235b13c000 rw-p 00010000 08:02 167125                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b235b13c000-2b235b13d000 rw-p 2b235b13c000 00:00 0 
2b235b13d000-2b235b13f000 r-xp 00000000 08:02 10659                      /lib/libdl-2.6.1.so
2b235b13f000-2b235b33f000 ---p 00002000 08:02 10659                      /lib/libdl-2.6.1.so
2b235b33f000-2b235b341000 rw-p 00002000 08:02 10659                      /lib/libdl-2.6.1.so
2b235b341000-2b235b493000 r-xp 00000000 08:02 10656                      /lib/libc-2.6.1.so
2b235b493000-2b235b692000 ---p 00152000 08:02 10656                      /lib/libc-2.6.1.so
2b235b692000-2b235b695000 r--p 00151000 08:02 10656                      /lib/libc-2.6.1.so
2b235b695000-2b235b697000 rw-p 00154000 08:02 10656                      /lib/libc-2.6.1.so
2b235b697000-2b235b69c000 rw-p 2b235b697000 00:00 0 
2b235b69c000-2b235b69e000 r-xp 00000000 08:02 7050                       /usr/lib/libXau.so.6.0.0
2b235b69e000-2b235b89d000 ---p 00002000 08:02 7050                       /usr/lib/libXau.so.6.0.0
2b235b89d000-2b235b89e000 rw-p 00001000 08:02 7050                       /usr/lib/libXau.so.6.0.0
2b235b89e000-2b235b89f000 rw-p 2b235b89e000 00:00 0 
2b235b89f000-2b235b8a4000 r-xp 00000000 08:02 7061                       /usr/lib/libXdmcp.so.6.0.0
2b235b8a4000-2b235baa3000 ---p 00005000 08:02 7061                       /usr/lib/libXdmcp.so.6.0.0
2b235baa3000-2b235baa4000 rw-p 00004000 08:02 7061                       /usr/lib/libXdmcp.so.6.0.0
2b235baa4000-2b235baa6000 rw-p 2b235baa4000 00:00 0 
2b235baa6000-2b235c1ee000 r-xp 00000000 08:02 167162                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b235c1ee000-2b235c3ee000 ---p 00748000 08:02 167162                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b235c3ee000-2b235c468000 rw-p 00748000 08:02 167162                     /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b235c468000-2b235c4a2000 rw-p 2b235c468000 00:00 0 
2b235c4b5000-2b235c535000 r-xp 00000000 08:02 10660                      /lib/libm-2.6.1.so
2b235c535000-2b235c734000 ---p 00080000 08:02 10660                      /lib/libm-2.6.1.so
2b235c734000-2b235c736000 rw-p 0007f000 08:02 10660                      /lib/libm-2.6.1.so
7fff502b4000-7fff502c7000 rwxp 7fff502b4000 00:00 0                      [stack]
7fff502c7000-7fff502ca000 rw-p 7fff502c7000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Dapplication.home=/usr/lib/jvm/java-7-icedtea/jre 
java_command: sun.applet.PluginMain /home/may/.gcjwebplugin/gcj-instance-20619-0-plugin-to-appletviewer /home/may/.gcjwebplugin/gcj-instance-20619-0-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=may
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
rlimit: STACK 8192k, CORE 0k, NPROC 38912, NOFILE 1024, AS infinity
load average:0.14 0.17 0.18

CPU:total 4 (4 cores per cpu, 1 threads per core) family 6 model 15 stepping 11, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 4054168k(51752k free), swap 3903784k(3903564k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Mon Jan 28 15:52:10 2008
elapsed time: 0 seconds

---

### Post by rtalcott on 2008-01-28
I have the same problem....any suggestions would be appreciated
rt

---

### Post by Kilz on 2008-01-28
Icedtea isnt perfect. It is an open source project to build a free java. It doesnt work on all sites, and can crash when it doesnt work. The good news is that when Sun Java 7 is released it will have a 64bit plugin. But it is still under development, and has not even released a beta plugin.
You can [install a 32bit firefox/java/flash]("http://ubuntuforums.org/showthread.php?p=1174435") setup to your 64bit install if you really need java to work. It uses the sun java6 plugin.

---

### Post by Freek07 on 2008-01-28
well, it does not work on any site for me...ok, so I'm f*cked unless I go 32-bit. Just great :)

---

### Post by TWFJR on 2008-01-28
I am having similar problems.  So what is Ubuntu doing to resolve this problem.  Java chat rooms don't work.  Pogo.com games online don't work.  I would like to know what the future of 64 bit java is with Ubuntu.

---

