---
title: "Hi, I am trying to install matlab on ubuntu with wine and i got the following. help!"
date: 2013-06-02
forum: Wine
---

### Post by mike1250 on 2013-06-02
```
# 
# A fatal error has been detected by the Java Runtime Environment: 
# 
#  EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x0000000078bff2f2, pid=38, tid=39 
# 
# JRE version: 6.0_17-b04 
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.3-b01 mixed mode windows-amd64 ) 
# Problematic frame: 
# V  [jvm.dll+0x38f2f2] 
# 
# If you would like to submit a bug report, please visit: 
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp) 
# 
 
---------------  T H R E A D  --------------- 
 
Current thread (0x0000000000061000):  JavaThread "main" [_thread_in_Java, id=39, stack(0x0000000000140000,0x0000000000240000)] 
 
siginfo: ExceptionCode=0xc0000005, reading address 0x0000000000000008 
 
Registers: 
EAX=0x0000000000000004, EBX=0x0000000078a65cf0, ECX=0x00000000ffffffff, EDX=0x0000000000000003 
ESP=0x000000000022a630, EBP=0x0000000000061880, ESI=0x0000000029cb4d50, EDI=0x000000000022a870 
EIP=0x0000000078bff2f2, EFLAGS=0x0000000000010246 
 
Top of Stack: (sp=0x000000000022a630) 
0x000000000022a630:   000000000022a968 000000000022a801 
0x000000000022a640:   000000000022a6d0 000000000070f680 
0x000000000022a650:   0000000000061000 0000000078a6694d 
0x000000000022a660:   2020002020000000 0000000000000020 
0x000000000022a670:   ffffffffff000000 ffff00ffffffffff 
0x000000000022a680:   0000000000061000 0020202000202000 
0x000000000022a690:   0000000000061000 ffffffffffffff00 
0x000000000022a6a0:   0000000029cb4da0 0000000029cb4d90 
0x000000000022a6b0:   0000000029cb4d90 0000000029cb4da0 
0x000000000022a6c0:   0000000029cb4da0 00000000fffffffe 
0x000000000022a6d0:   0000000000000000 000000001e436bf8 
0x000000000022a6e0:   000000001e437158 000000001e437180 
0x000000000022a6f0:   000000000022a850 00000000788ccd5e 
0x000000000022a700:   0000000029cb4d88 0000000000000000 
0x000000000022a710:   0000000029cb4d88 000000001e437180 
0x000000000022a720:   0000000029cb4d78 000000001e437158  
 
Instructions: (pc=0x0000000078bff2f2) 
0x0000000078bff2e2:   4c 8b 4c 24 50 4c 8b c0 49 8b d2 49 8b cb ff d3 
0x0000000078bff2f2:   eb 00 48 83 c4 20 5b c3 cc cc cc cc cc cc 48 55  
 
 
Stack: [0x0000000000140000,0x0000000000240000],  sp=0x000000000022a630,  free space=937k 
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code) 
V  [jvm.dll+0x38f2f2] 
C  0x00000000000618b0 
 
 
---------------  P R O C E S S  --------------- 
 
Java Threads: ( => current thread ) 
  0x0000000029fb7800 JavaThread "AWT-Windows" daemon [_thread_in_native, id=63, stack(0x000000002abd0000,0x000000002acd0000)] 
  0x000000002a09b000 JavaThread "AWT-Shutdown" [_thread_blocked, id=62, stack(0x000000002aad0000,0x000000002abd0000)] 
  0x000000002a091000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=61, stack(0x000000002a9d0000,0x000000002aad0000)] 
  0x0000000029ffc800 JavaThread "com.google.inject.internal.Finalizer" daemon [_thread_blocked, id=60, stack(0x000000002a8c0000,0x000000002a9c0000)] 
  0x0000000029058000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=58, stack(0x00000000297e0000,0x00000000298e0000)] 
  0x0000000029055000 JavaThread "CompilerThread1" daemon [_thread_blocked, id=57, stack(0x00000000296e0000,0x00000000297e0000)] 
  0x0000000029053000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=56, stack(0x00000000295e0000,0x00000000296e0000)] 
  0x0000000029051000 JavaThread "Attach Listener" daemon [_thread_blocked, id=55, stack(0x00000000294e0000,0x00000000295e0000)] 
  0x000000002904f800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=54, stack(0x00000000293e0000,0x00000000294e0000)] 
  0x0000000000116800 JavaThread "Finalizer" daemon [_thread_blocked, id=53, stack(0x00000000292e0000,0x00000000293e0000)] 
  0x0000000029032800 JavaThread "Reference Handler" daemon [_thread_blocked, id=52, stack(0x00000000291e0000,0x00000000292e0000)] 
=>0x0000000000061000 JavaThread "main" [_thread_in_Java, id=39, stack(0x0000000000140000,0x0000000000240000)] 
 
Other Threads: 
  0x0000000000112800 VMThread [stack: 0x00000000290e0000,0x00000000291e0000] [id=51] 
  0x000000002905a800 WatcherThread [stack: 0x00000000298e0000,0x00000000299e0000] [id=59] 
 
VM state:synchronizing (normal execution) 
 
VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event]) 
[0x000000000005fcc0] Safepoint_lock - owner thread: 0x0000000000112800 
[0x000000000005fd50] Threads_lock - owner thread: 0x0000000000112800 
 
Heap 
 PSYoungGen      total 6656K, used 4066K [0x000000001e120000, 0x000000001e8c0000, 0x0000000028bc0000) 
  eden space 5696K, 56% used [0x000000001e120000,0x000000001e4409d0,0x000000001e6b0000) 
  from space 960K, 90% used [0x000000001e7b0000,0x000000001e888000,0x000000001e8a0000) 
  to   space 1024K, 0% used [0x000000001e6b0000,0x000000001e6b0000,0x000000001e7b0000) 
 PSOldGen        total 5312K, used 856K [0x0000000008bc0000, 0x00000000090f0000, 0x000000001e120000) 
  object space 5312K, 16% used [0x0000000008bc0000,0x0000000008c960a8,0x00000000090f0000) 
 PSPermGen       total 21248K, used 13497K [0x00000000037c0000, 0x0000000004c80000, 0x0000000008bc0000) 
  object space 21248K, 63% used [0x00000000037c0000,0x00000000044ee7f8,0x0000000004c80000) 
 
Dynamic libraries: 
0x0000000140000000 - 0x000000014004a000     Z:\home\user\Desktop\Matlab\bin\win64\setup.exe 
0x00007fcbf4880000 - 0x00007fcbf4b76000     C:\windows\system32\ntdll.dll 
0x000000007b820000 - 0x000000007bc69000     C:\windows\system32\KERNEL32.dll 
0x0000000180000000 - 0x00000001800b9000     Z:\home\user\Desktop\Matlab\bin\win64\java_launcher.dll 
0x00007fcbf31b0000 - 0x00007fcbf3430000     C:\windows\system32\shlwapi.dll 
0x00007fcbf2df0000 - 0x00007fcbf319b000     C:\windows\system32\user32.dll 
0x00007fcbf2ad0000 - 0x00007fcbf2dd5000     C:\windows\system32\gdi32.dll 
0x00007fcbf2840000 - 0x00007fcbf2ac0000     C:\windows\system32\advapi32.dll 
0x00007fcbf2620000 - 0x00007fcbf2832000     C:\windows\system32\version.dll 
0x00007fcbf21b0000 - 0x00007fcbf2617000     C:\windows\system32\shell32.dll 
0x00007fcbf1e70000 - 0x00007fcbf2196000     C:\windows\system32\comctl32.dll 
0x00007fcbf1700000 - 0x00007fcbf19b0000     C:\windows\system32\winex11.drv 
0x00007fcbf0330000 - 0x00007fcbf054f000     C:\windows\system32\imm32.dll 
0x00007fcbeeb70000 - 0x00007fcbeeda4000     C:\windows\system32\uxtheme.dll 
0x00007fcbee7c0000 - 0x00007fcbeeb53000     C:\windows\system32\ole32.dll 
0x00007fcbee500000 - 0x00007fcbee795000     C:\windows\system32\rpcrt4.dll 
0x0000000078870000 - 0x0000000078ecd000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\server\jvm.dll 
0x00007fcbee240000 - 0x00007fcbee4f1000     C:\windows\system32\winmm.dll 
0x00007fcbee010000 - 0x00007fcbee22f000     C:\windows\system32\msacm32.dll 
0x00007fcbedd60000 - 0x00007fcbee000000     C:\windows\system32\msvcrt.dll 
0x000000007a440000 - 0x000000007a44e000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\verify.dll 
0x000000007a070000 - 0x000000007a097000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\java.dll 
0x000000007a540000 - 0x000000007a54a000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\hpi.dll 
0x00007fcbedab0000 - 0x00007fcbedcb3000     C:\windows\system32\psapi.dll 
0x000000007a370000 - 0x000000007a382000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\zip.dll 
0x000000007a230000 - 0x000000007a247000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\net.dll 
0x00007fcbed870000 - 0x00007fcbedaa0000     C:\windows\system32\ws2_32.dll 
0x000000007a500000 - 0x000000007a50b000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\nio.dll 
0x0000000073150000 - 0x0000000073311000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\awt.dll 
0x00007fcbed620000 - 0x00007fcbed865000     C:\windows\system32\winspool.drv 
0x0000000075b90000 - 0x0000000075bfb000     Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\bin\fontmanager.dll 
0x00007fcbe6a90000 - 0x00007fcbe6cdb000     C:\windows\system32\d3d9.dll 
0x00007fcbe6700000 - 0x00007fcbe6a88000     C:\windows\system32\wined3d.dll 
 
VM Arguments: 
jvm_args: -Djava.ext.dirs=Z:\home\user\Desktop\Matlab\sys\java\jre\win64\jre\\lib\ext;Z:\home\user\Desktop\Matlab\java\jar;Z:\home\user\Desktop\Matlab\java\jarext;Z:\home\user\Desktop\Matlab\java\jarext\guice;Z:\home\user\Desktop\Matlab\java\jarext\axis2;Z:\home\user\Desktop\Matlab\java\jarext\webservices vfprintf -Xmx512m  
java_command: <unknown> 
Launcher Type: generic 
 
Environment Variables: 
PATH=Z:\home\user\Desktop\Matlab\bin\win64;C:\windows\system32;C:\windows;C:\windows\system32\wbem 
USERNAME=user 
SHELL=/bin/bash 
DISPLAY=:0.0 
OS=Windows_NT 
PROCESSOR_IDENTIFIER=AMD64 Family 6 Model 23 Stepping 10, GenuineIntel 
 
 
 
---------------  S Y S T E M  --------------- 
 
OS: Windows XP Build 2600 Service Pack 3 
 
CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 23 stepping 10, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3 
 
Memory: 4k page, physical 4048896k(3289928k free), swap 4194303k(4293774519k free) 
 
vm_info: Java HotSpot(TM) 64-Bit Server VM (14.3-b01) for windows-amd64 JRE (1.6.0_17-b04), built on Oct 11 2009 00:46:08 by "java_re" with MS VC++ 8.0 
 
time: Sun Jun  2 00:25:25 2013 
elapsed time: 4 seconds
```

---

### Post by QIII on 2013-06-02
Hi!  Welcome to the Forums!

Please enclose long streams of code in code tags by pressing the '#' button and placing your cursor between the tags.  That will avoid making people scroll a lot.

Thanks.

---

