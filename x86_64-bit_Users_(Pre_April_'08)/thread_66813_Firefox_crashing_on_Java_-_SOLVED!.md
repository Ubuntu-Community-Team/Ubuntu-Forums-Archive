---
title: "Firefox crashing on Java - SOLVED!"
date: 2005-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by acariquara on 2005-09-18
My online banking site requires java to log in... after battling with sun-j2re's lack of a 64bit plugin for Firefox, I decided to try Blackdown java... great, only every single time I went to the site, Fx would crash and burn instantly.

Okay, Java is acting weird... let's run Fx from a terminal.

*** something about extensions datasource ***

fatal exception from java - could not find libXp.so.6

great...  ](*,) 

Synaptic describes libxp6 as an outdated X11 print library. Wouldn't harm trying to install it though. In fact, it just washed away my Java blues.

```
sudo apt-get install libxp6
```

also if you do not have Blackdown Java

```
sudo apt-get install blackdown-j2re1.4
sudo update-alternatives --config java
```

there should be a screen with some alternatives, and a prompt. Choose the number that refers to Blackdown Java (should be the last one), and press Enter.

---

### Post by patricia on 2005-09-19
Hey!

I´m having problems with java and firefox too. The error message that I get in the terminal is:

$firefox

Unexpected Signal : 11 occurred at PC=0x2A95DF3DAA
Function=(null)
Library=/usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
        at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
        at sun.plugin.navig.motif.AThread.JNIHandleLoop(Unknown Source)
        at sun.plugin.navig.motif.AThread.run(Unknown Source)

Dynamic libraries:
40000000-40003000 r-xp 00000000 03:05 18761                              /usr/lib/j2re1.4.2/bin/java_vm
40102000-40103000 rwxp 00002000 03:05 18761                              /usr/lib/j2re1.4.2/bin/java_vm
2a95556000-2a9556a000 r-xp 00000000 03:05 13090                          /lib/ld-2.3.2.so
2a9556a000-2a9556e000 rwxp 2a9556a000 00:00 0
2a9566a000-2a9566c000 rwxp 00014000 03:05 13090                          /lib/ld-2.3.2.so
2a9566c000-2a9567a000 r-xp 00000000 03:05 13244                          /lib/libpthread-0.60.so
2a9567a000-2a9576c000 ---p 0000e000 03:05 13244                          /lib/libpthread-0.60.so
2a9576c000-2a9577c000 rwxp 00000000 03:05 13244                          /lib/libpthread-0.60.so
2a9577c000-2a95780000 rwxp 2a9577c000 00:00 0
2a95780000-2a95783000 r-xp 00000000 03:05 13150                          /lib/libdl-2.3.2.so
2a95783000-2a95880000 ---p 00003000 03:05 13150                          /lib/libdl-2.3.2.so
2a95880000-2a95883000 rwxp 00000000 03:05 13150                          /lib/libdl-2.3.2.so
2a95883000-2a959a5000 r-xp 00000000 03:05 13106                          /lib/libc-2.3.2.so
2a959a5000-2a95a83000 ---p 00122000 03:05 13106                          /lib/libc-2.3.2.so
2a95a83000-2a95abe000 rwxp 00100000 03:05 13106                          /lib/libc-2.3.2.so
2a95abe000-2a95ac3000 rwxp 2a95abe000 00:00 0
2a95ac3000-2a96002000 r-xp 00000000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a96002000-2a960c3000 ---p 0053f000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a960c3000-2a9622f000 rwxp 00500000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a9622f000-2a96261000 rwxp 2a9622f000 00:00 0
2a96270000-2a96282000 r-xp 00000000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96282000-2a96370000 ---p 00012000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96370000-2a96384000 rwxp 00000000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96384000-2a96386000 rwxp 2a96384000 00:00 0
2a96386000-2a96409000 r-xp 00000000 03:05 13152                          /lib/libm-2.3.2.so
2a96409000-2a96486000 ---p 00083000 03:05 13152                          /lib/libm-2.3.2.so
2a96486000-2a9650c000 rwxp 00000000 03:05 13152                          /lib/libm-2.3.2.so
2a9650c000-2a96514000 r-xp 00000000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a96514000-2a9660c000 ---p 00008000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a9660c000-2a96616000 rwxp 00000000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a96616000-2a96617000 rwxp 2a96616000 00:00 0
2a96617000-2a9661b000 rwxs 00000000 03:05 91851                          /tmp/hsperfdata_patricia/8373
2a96626000-2a9662d000 r-xp 00000000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a9662d000-2a96726000 ---p 00007000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a96726000-2a9672e000 rwxp 00000000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a9672e000-2a96737000 r-xp 00000000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a96737000-2a9682e000 ---p 00009000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a9682e000-2a96838000 rwxp 00000000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a96838000-2a96841000 r-xp 00000000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96841000-2a96938000 ---p 00009000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96938000-2a96942000 rwxp 00000000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96942000-2a96954000 r-xp 00000000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96954000-2a96a42000 ---p 00012000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96a42000-2a96a56000 rwxp 00000000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96a56000-2a96a76000 r-xp 00000000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96a76000-2a96b56000 ---p 00020000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96b56000-2a96b7b000 rwxp 00000000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96b7b000-2a96b8c000 r-xp 00000000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96b8c000-2a96c7b000 ---p 00011000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96c7b000-2a96c8f000 rwxp 00000000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96c8f000-2a9837e000 r-xs 00000000 03:05 103335                         /usr/lib/j2re1.4.2/lib/rt.jar
2a9837e000-2a983c8000 rwxp 2a9837e000 00:00 0
2a983c8000-2a983de000 r-xs 00000000 03:05 103276                         /usr/lib/j2re1.4.2/lib/sunrsasign.jar
2a983de000-2a984b7000 r-xs 00000000 03:05 103244                         /usr/lib/j2re1.4.2/lib/jsse.jar
2a984b7000-2a984c8000 r-xs 00000000 03:05 103324                         /usr/lib/j2re1.4.2/lib/jce.jar
2a984c8000-2a98a57000 r-xs 00000000 03:05 103248                         /usr/lib/j2re1.4.2/lib/charsets.jar
2a98a57000-2a98c1b000 r-xs 00000000 03:05 103258                         /usr/lib/j2re1.4.2/lib/plugin.jar
2a98c1b000-2a98d1b000 rwxp 2a98c1b000 00:00 0
2a98d1b000-2ad8c1b000 rwxp 2a98d1b000 00:00 0
2ad8c1b000-2ad8c1f000 rwxp 2ad8c1b000 00:00 0
2ad8c1f000-2ad9c1b000 rwxp 2ad8c1f000 00:00 0
2ad9c1b000-2ad9c6a000 rwxp 2ad9c1b000 00:00 0
2ad9c70000-2ad9ea0000 rwxp 2ad9c70000 00:00 0
2ad9ea0000-2adb1c0000 rwxp 2ad9ea0000 00:00 0
2adb1c0000-2adb608000 rwxp 2adb1c0000 00:00 0
2adb608000-2addc70000 rwxp 2adb608000 00:00 0
2addc70000-2adec70000 rwxp 2addc70000 00:00 0
2adec70000-2ae1c70000 rwxp 2adec70000 00:00 0
2ae1c70000-2ae1c72000 rwxp 2ae1c70000 00:00 0
2ae1c72000-2ae1c7a000 rwxp 2ae1c72000 00:00 0
2ae1c7a000-2ae1c7d000 rwxp 2ae1c7a000 00:00 0
2ae1c7d000-2ae1c90000 rwxp 2ae1c7d000 00:00 0
2ae1c90000-2ae1c98000 rwxp 2ae1c90000 00:00 0
2ae1c98000-2ae1cb0000 rwxp 2ae1c98000 00:00 0
2ae1cb0000-2ae1cb4000 rwxp 2ae1cb0000 00:00 0
2ae1cb4000-2ae1cc7000 rwxp 2ae1cb4000 00:00 0
2ae1cc7000-2ae1cd0000 rwxp 2ae1cc7000 00:00 0
2ae1cd0000-2ae1ce8000 rwxp 2ae1cd0000 00:00 0
2ae1ce8000-2ae1e0a000 r-xp 00000000 03:05 18456                          /usr/lib/locale/locale-archive
2ae1e0a000-2ae1f0a000 rwxp 2ae1e0a000 00:00 0
2ae1f0a000-2ae1f0d000 r-xs 00000000 03:05 103177                         /usr/lib/j2re1.4.2/lib/ext/dnsns.jar
2ae1f0d000-2ae1f29000 r-xs 00000000 03:05 103178                         /usr/lib/j2re1.4.2/lib/ext/sunjce_provider.jar
2ae1f29000-2ae1f37000 r-xs 00000000 03:05 103179                         /usr/lib/j2re1.4.2/lib/ext/ldapsec.jar
2ae1f37000-2ae1ff2000 r-xs 00000000 03:05 103180                         /usr/lib/j2re1.4.2/lib/ext/localedata.jar
2ae2000000-2ae2021000 rwxp 2ae2000000 00:00 0
2ae2021000-2ae2100000 ---p 2ae2021000 00:00 0
2ae2100000-2ae21e3000 r-xp 00000000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae21e3000-2ae2200000 ---p 000e3000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae2200000-2ae2305000 rwxp 00000000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae2305000-2ae232a000 rwxp 2ae2305000 00:00 0
2ae232a000-2ae2382000 r-xp 00000000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae2382000-2ae242a000 ---p 00058000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae242a000-2ae2485000 rwxp 00000000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae2485000-2ae26ca000 r-xp 00000000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae26ca000-2ae2785000 ---p 00245000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae2785000-2ae2833000 rwxp 00200000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae2833000-2ae2834000 rwxp 2ae2833000 00:00 0
2ae2843000-2ae284b000 r-xp 00000000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae284b000-2ae2943000 ---p 00008000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae2943000-2ae294b000 rwxp 00000000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae294b000-2ae299e000 r-xp 00000000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae299e000-2ae2a4b000 ---p 00053000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae2a4b000-2ae2aab000 rwxp 00000000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae2aab000-2ae2aac000 rwxp 2ae2aab000 00:00 0
2ae2aac000-2ae2ab5000 r-xp 00000000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2ab5000-2ae2bac000 ---p 00009000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2bac000-2ae2bb6000 rwxp 00000000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2bb6000-2ae2bcb000 r-xp 00000000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2bcb000-2ae2cb6000 ---p 00015000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2cb6000-2ae2cce000 rwxp 00000000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2cce000-2ae2cd1000 rwxp 2ae2cce000 00:00 0
2ae2cd1000-2ae2cdf000 r-xp 00000000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2cdf000-2ae2dd1000 ---p 0000e000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2dd1000-2ae2de2000 rwxp 00000000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2de2000-2ae2de7000 r-xp 00000000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2de7000-2ae2ee2000 ---p 00005000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2ee2000-2ae2ee8000 rwxp 00000000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2ee8000-2ae2fb2000 r-xp 00000000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae2fb2000-2ae2fe8000 ---p 000ca000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae2fe8000-2ae30c6000 rwxp 00000000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae30c6000-2ae30d7000 r-xp 00000000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae30d7000-2ae31c6000 ---p 00011000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae31c6000-2ae31d9000 rwxp 00000000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae31d9000-2ae3201000 rwxp 2ae31d9000 00:00 0
2ae3201000-2ae329e000 r-xp 00000000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae329e000-2ae3301000 ---p 0009d000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae3301000-2ae33bc000 rwxp 00000000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae33bc000-2ae36cd000 rwxp 2ae33bc000 00:00 0
2ae36cd000-2ae36ce000 r-xp 00000000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae36ce000-2ae37cd000 ---p 00001000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae37cd000-2ae37ce000 rwxp 00000000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae37ce000-2ae37d7000 r-xp 00000000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae37d7000-2ae38ce000 ---p 00009000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae38ce000-2ae38d8000 rwxp 00000000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae38d8000-2ae38e0000 r-xp 00000000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae38e0000-2ae39d8000 ---p 00008000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae39d8000-2ae39e1000 rwxp 00000000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae39e1000-2ae39fd000 r-xp 00000000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae39fd000-2ae3ae1000 ---p 0001c000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae3ae1000-2ae3b02000 rwxp 00000000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae3b02000-2ae4002000 rwxp 2ae3b02000 00:00 0
2ae4002000-2ae4010000 r-xp 00000000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4010000-2ae4102000 ---p 0000e000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4102000-2ae4112000 rwxp 00000000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4112000-2ae4116000 r-xp 00000000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4116000-2ae4212000 ---p 00004000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4212000-2ae4216000 rwxp 00000000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4216000-2ae4225000 r-xp 00000000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4225000-2ae4316000 ---p 0000f000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4316000-2ae4328000 rwxp 00000000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4328000-2ae432a000 rwxp 2ae4328000 00:00 0
2ae432a000-2ae4343000 r-xp 00000000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae4343000-2ae442a000 ---p 00019000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae442a000-2ae4459000 rwxp 00000000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae446d000-2ae4478000 r-xs 00000000 03:05 124444                         /tmp/jar_cache42643.tmp (deleted)
2ae4478000-2ae4578000 rwxp 2ae4478000 00:00 0
7fbfe00000-7fbfe02000 rwxp 7fbfe00000 00:00 0
7fbfe02000-7fbfe05000 ---p 7fbfe02000 00:00 0
7fbffdb000-7fc0000000 rwxp 7fbffdb000 00:00 0
ffffffffff600000-ffffffffffe00000 ---p 00000000 00:00 0

Heap at VM Abort:
Heap
 def new generation   total 2048K, used 197K [0x0000002ad9c70000, 0x0000002ad9ea0000, 0x0000002adb1c0000)
  eden space 1856K,  10% used [0x0000002ad9c70000, 0x0000002ad9ca1600, 0x0000002ad9e40000)
  from space 192K,   0% used [0x0000002ad9e40000, 0x0000002ad9e40000, 0x0000002ad9e70000)
  to   space 192K,   0% used [0x0000002ad9e70000, 0x0000002ad9e70000, 0x0000002ad9ea0000)
 tenured generation   total 4384K, used 2629K [0x0000002adb1c0000, 0x0000002adb608000, 0x0000002addc70000)
   the space 4384K,  59% used [0x0000002adb1c0000, 0x0000002adb451428, 0x0000002adb451600, 0x0000002adb608000)
 compacting perm gen  total 16384K, used 13238K [0x0000002addc70000, 0x0000002adec70000, 0x0000002ae1c70000)
   the space 16384K,  80% used [0x0000002addc70000, 0x0000002ade95d930, 0x0000002ade95da00, 0x0000002adec70000)

Local Time = Mon Sep 19 20:31:20 2005
Elapsed Time = 34
#
# HotSpot Virtual Machine Error : 11
# Error ID : 4F530E43505002EF
# Please report this error at
# [http://www.blackdown.org/cgi-bin/jdk](http://www.blackdown.org/cgi-bin/jdk)
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid8373.log.
# Please refer to the file for further information.
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Sucesso

----------------------

.... be continued

---

### Post by patricia on 2005-09-19
.....

And the report file **hs_err_pid8373.log** is:


Unexpected Signal : 11 occurred at PC=0x2A95DF3DAA
Function=(null)
Library=/usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
	at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
	at sun.plugin.navig.motif.AThread.JNIHandleLoop(Unknown Source)
	at sun.plugin.navig.motif.AThread.run(Unknown Source)

Dynamic libraries:
40000000-40003000 r-xp 00000000 03:05 18761                              /usr/lib/j2re1.4.2/bin/java_vm
40102000-40103000 rwxp 00002000 03:05 18761                              /usr/lib/j2re1.4.2/bin/java_vm
2a95556000-2a9556a000 r-xp 00000000 03:05 13090                          /lib/ld-2.3.2.so
2a9556a000-2a9556f000 rwxp 2a9556a000 00:00 0 
2a9566a000-2a9566c000 rwxp 00014000 03:05 13090                          /lib/ld-2.3.2.so
2a9566c000-2a9567a000 r-xp 00000000 03:05 13244                          /lib/libpthread-0.60.so
2a9567a000-2a9576c000 ---p 0000e000 03:05 13244                          /lib/libpthread-0.60.so
2a9576c000-2a9577c000 rwxp 00000000 03:05 13244                          /lib/libpthread-0.60.so
2a9577c000-2a95780000 rwxp 2a9577c000 00:00 0 
2a95780000-2a95783000 r-xp 00000000 03:05 13150                          /lib/libdl-2.3.2.so
2a95783000-2a95880000 ---p 00003000 03:05 13150                          /lib/libdl-2.3.2.so
2a95880000-2a95883000 rwxp 00000000 03:05 13150                          /lib/libdl-2.3.2.so
2a95883000-2a959a5000 r-xp 00000000 03:05 13106                          /lib/libc-2.3.2.so
2a959a5000-2a95a83000 ---p 00122000 03:05 13106                          /lib/libc-2.3.2.so
2a95a83000-2a95abe000 rwxp 00100000 03:05 13106                          /lib/libc-2.3.2.so
2a95abe000-2a95ac3000 rwxp 2a95abe000 00:00 0 
2a95ac3000-2a96002000 r-xp 00000000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a96002000-2a960c3000 ---p 0053f000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a960c3000-2a9622f000 rwxp 00500000 03:05 103212                         /usr/lib/j2re1.4.2/lib/amd64/server/libjvm.so
2a9622f000-2a96261000 rwxp 2a9622f000 00:00 0 
2a96270000-2a96282000 r-xp 00000000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96282000-2a96370000 ---p 00012000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96370000-2a96384000 rwxp 00000000 03:05 13194                          /lib/libnsl-2.3.2.so
2a96384000-2a96386000 rwxp 2a96384000 00:00 0 
2a96386000-2a96409000 r-xp 00000000 03:05 13152                          /lib/libm-2.3.2.so
2a96409000-2a96486000 ---p 00083000 03:05 13152                          /lib/libm-2.3.2.so
2a96486000-2a9650c000 rwxp 00000000 03:05 13152                          /lib/libm-2.3.2.so
2a9650c000-2a96514000 r-xp 00000000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a96514000-2a9660c000 ---p 00008000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a9660c000-2a96616000 rwxp 00000000 03:05 103201                         /usr/lib/j2re1.4.2/lib/amd64/native_threads/libhpi.so
2a96616000-2a96617000 rwxp 2a96616000 00:00 0 
2a96617000-2a9661b000 rwxs 00000000 03:05 91851                          /tmp/hsperfdata_patricia/8373
2a96626000-2a9662d000 r-xp 00000000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a9662d000-2a96726000 ---p 00007000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a96726000-2a9672e000 rwxp 00000000 03:05 13199                          /lib/libnss_compat-2.3.2.so
2a9672e000-2a96737000 r-xp 00000000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a96737000-2a9682e000 ---p 00009000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a9682e000-2a96838000 rwxp 00000000 03:05 13224                          /lib/libnss_nis-2.3.2.so
2a96838000-2a96841000 r-xp 00000000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96841000-2a96938000 ---p 00009000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96938000-2a96942000 rwxp 00000000 03:05 13208                          /lib/libnss_files-2.3.2.so
2a96942000-2a96954000 r-xp 00000000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96954000-2a96a42000 ---p 00012000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96a42000-2a96a56000 rwxp 00000000 03:05 103194                         /usr/lib/j2re1.4.2/lib/amd64/libverify.so
2a96a56000-2a96a76000 r-xp 00000000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96a76000-2a96b56000 ---p 00020000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96b56000-2a96b7b000 rwxp 00000000 03:05 103206                         /usr/lib/j2re1.4.2/lib/amd64/libjava.so
2a96b7b000-2a96b8c000 r-xp 00000000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96b8c000-2a96c7b000 ---p 00011000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96c7b000-2a96c8f000 rwxp 00000000 03:05 103199                         /usr/lib/j2re1.4.2/lib/amd64/libzip.so
2a96c8f000-2a9837e000 r-xs 00000000 03:05 103335                         /usr/lib/j2re1.4.2/lib/rt.jar
2a9837e000-2a983c8000 rwxp 2a9837e000 00:00 0 
2a983c8000-2a983de000 r-xs 00000000 03:05 103276                         /usr/lib/j2re1.4.2/lib/sunrsasign.jar
2a983de000-2a984b7000 r-xs 00000000 03:05 103244                         /usr/lib/j2re1.4.2/lib/jsse.jar
2a984b7000-2a984c8000 r-xs 00000000 03:05 103324                         /usr/lib/j2re1.4.2/lib/jce.jar
2a984c8000-2a98a57000 r-xs 00000000 03:05 103248                         /usr/lib/j2re1.4.2/lib/charsets.jar
2a98a57000-2a98c1b000 r-xs 00000000 03:05 103258                         /usr/lib/j2re1.4.2/lib/plugin.jar
2a98c1b000-2a98d1b000 rwxp 2a98c1b000 00:00 0 
2a98d1b000-2ad8c1b000 rwxp 2a98d1b000 00:00 0 
2ad8c1b000-2ad8c1f000 rwxp 2ad8c1b000 00:00 0 
2ad8c1f000-2ad9c1b000 rwxp 2ad8c1f000 00:00 0 
2ad9c1b000-2ad9c6a000 rwxp 2ad9c1b000 00:00 0 
2ad9c70000-2ad9ea0000 rwxp 2ad9c70000 00:00 0 
2ad9ea0000-2adb1c0000 rwxp 2ad9ea0000 00:00 0 
2adb1c0000-2adb608000 rwxp 2adb1c0000 00:00 0 
2adb608000-2addc70000 rwxp 2adb608000 00:00 0 
2addc70000-2adec70000 rwxp 2addc70000 00:00 0 
2adec70000-2ae1c70000 rwxp 2adec70000 00:00 0 
2ae1c70000-2ae1c72000 rwxp 2ae1c70000 00:00 0 
2ae1c72000-2ae1c7a000 rwxp 2ae1c72000 00:00 0 
2ae1c7a000-2ae1c7d000 rwxp 2ae1c7a000 00:00 0 
2ae1c7d000-2ae1c90000 rwxp 2ae1c7d000 00:00 0 
2ae1c90000-2ae1c98000 rwxp 2ae1c90000 00:00 0 
2ae1c98000-2ae1cb0000 rwxp 2ae1c98000 00:00 0 
2ae1cb0000-2ae1cb4000 rwxp 2ae1cb0000 00:00 0 
2ae1cb4000-2ae1cc7000 rwxp 2ae1cb4000 00:00 0 
2ae1cc7000-2ae1cd0000 rwxp 2ae1cc7000 00:00 0 
2ae1cd0000-2ae1ce8000 rwxp 2ae1cd0000 00:00 0 
2ae1ce8000-2ae1e0a000 r-xp 00000000 03:05 18456                          /usr/lib/locale/locale-archive
2ae1e0a000-2ae1f0a000 rwxp 2ae1e0a000 00:00 0 
2ae1f0a000-2ae1f0d000 r-xs 00000000 03:05 103177                         /usr/lib/j2re1.4.2/lib/ext/dnsns.jar
2ae1f0d000-2ae1f29000 r-xs 00000000 03:05 103178                         /usr/lib/j2re1.4.2/lib/ext/sunjce_provider.jar
2ae1f29000-2ae1f37000 r-xs 00000000 03:05 103179                         /usr/lib/j2re1.4.2/lib/ext/ldapsec.jar
2ae1f37000-2ae1ff2000 r-xs 00000000 03:05 103180                         /usr/lib/j2re1.4.2/lib/ext/localedata.jar
2ae2000000-2ae2021000 rwxp 2ae2000000 00:00 0 
2ae2021000-2ae2100000 ---p 2ae2021000 00:00 0 
2ae2100000-2ae21e3000 r-xp 00000000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae21e3000-2ae2200000 ---p 000e3000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae2200000-2ae2305000 rwxp 00000000 03:05 103221                         /usr/lib/j2re1.4.2/lib/amd64/libawt.so
2ae2305000-2ae232a000 rwxp 2ae2305000 00:00 0 
2ae232a000-2ae2382000 r-xp 00000000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae2382000-2ae242a000 ---p 00058000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae242a000-2ae2485000 rwxp 00000000 03:05 103204                         /usr/lib/j2re1.4.2/lib/amd64/libmlib_image.so
2ae2485000-2ae26ca000 r-xp 00000000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae26ca000-2ae2785000 ---p 00245000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae2785000-2ae2833000 rwxp 00200000 03:05 103189                         /usr/lib/j2re1.4.2/lib/amd64/libXm.so.3
2ae2833000-2ae2834000 rwxp 2ae2833000 00:00 0 
2ae2843000-2ae284b000 r-xp 00000000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae284b000-2ae2943000 ---p 00008000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae2943000-2ae294b000 rwxp 00000000 03:05 25774                          /usr/X11R6/lib/libXp.so.6.2
2ae294b000-2ae299e000 r-xp 00000000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae299e000-2ae2a4b000 ---p 00053000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae2a4b000-2ae2aab000 rwxp 00000000 03:05 13209                          /usr/X11R6/lib/libXt.so.6.0
2ae2aab000-2ae2aac000 rwxp 2ae2aab000 00:00 0 
2ae2aac000-2ae2ab5000 r-xp 00000000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2ab5000-2ae2bac000 ---p 00009000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2bac000-2ae2bb6000 rwxp 00000000 03:05 101314                         /usr/X11R6/lib/libSM.so.6.0
2ae2bb6000-2ae2bcb000 r-xp 00000000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2bcb000-2ae2cb6000 ---p 00015000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2cb6000-2ae2cce000 rwxp 00000000 03:05 101288                         /usr/X11R6/lib/libICE.so.6.3
2ae2cce000-2ae2cd1000 rwxp 2ae2cce000 00:00 0 
2ae2cd1000-2ae2cdf000 r-xp 00000000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2cdf000-2ae2dd1000 ---p 0000e000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2dd1000-2ae2de2000 rwxp 00000000 03:05 25741                          /usr/X11R6/lib/libXext.so.6.4
2ae2de2000-2ae2de7000 r-xp 00000000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2de7000-2ae2ee2000 ---p 00005000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2ee2000-2ae2ee8000 rwxp 00000000 03:05 25828                          /usr/X11R6/lib/libXtst.so.6.1
2ae2ee8000-2ae2fb2000 r-xp 00000000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae2fb2000-2ae2fe8000 ---p 000ca000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae2fe8000-2ae30c6000 rwxp 00000000 03:05 25725                          /usr/X11R6/lib/libX11.so.6.2
2ae30c6000-2ae30d7000 r-xp 00000000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae30d7000-2ae31c6000 ---p 00011000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae31c6000-2ae31d9000 rwxp 00000000 03:05 103220                         /usr/lib/j2re1.4.2/lib/amd64/libjavaplugin_jni.so
2ae31d9000-2ae3201000 rwxp 2ae31d9000 00:00 0 
2ae3201000-2ae329e000 r-xp 00000000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae329e000-2ae3301000 ---p 0009d000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae3301000-2ae33bc000 rwxp 00000000 03:05 103197                         /usr/lib/j2re1.4.2/lib/amd64/libfontmanager.so
2ae33bc000-2ae36cd000 rwxp 2ae33bc000 00:00 0 
2ae36cd000-2ae36ce000 r-xp 00000000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae36ce000-2ae37cd000 ---p 00001000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae37cd000-2ae37ce000 rwxp 00000000 03:05 25721                          /usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2
2ae37ce000-2ae37d7000 r-xp 00000000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae37d7000-2ae38ce000 ---p 00009000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae38ce000-2ae38d8000 rwxp 00000000 03:05 32738                          /usr/lib/libXcursor.so.1.0.2
2ae38d8000-2ae38e0000 r-xp 00000000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae38e0000-2ae39d8000 ---p 00008000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae39d8000-2ae39e1000 rwxp 00000000 03:05 26241                          /usr/lib/libXrender.so.1.3.0
2ae39e1000-2ae39fd000 r-xp 00000000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae39fd000-2ae3ae1000 ---p 0001c000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae3ae1000-2ae3b02000 rwxp 00000000 03:05 18728                          /usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2
2ae3b02000-2ae4002000 rwxp 2ae3b02000 00:00 0 
2ae4002000-2ae4010000 r-xp 00000000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4010000-2ae4102000 ---p 0000e000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4102000-2ae4112000 rwxp 00000000 03:05 103190                         /usr/lib/j2re1.4.2/lib/amd64/libnet.so
2ae4112000-2ae4116000 r-xp 00000000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4116000-2ae4212000 ---p 00004000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4212000-2ae4216000 rwxp 00000000 03:05 13207                          /lib/libnss_dns-2.3.2.so
2ae4216000-2ae4225000 r-xp 00000000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4225000-2ae4316000 ---p 0000f000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4316000-2ae4328000 rwxp 00000000 03:05 13245                          /lib/libresolv-2.3.2.so
2ae4328000-2ae432a000 rwxp 2ae4328000 00:00 0 
2ae432a000-2ae4343000 r-xp 00000000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae4343000-2ae442a000 ---p 00019000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae442a000-2ae4459000 rwxp 00000000 03:05 103215                         /usr/lib/j2re1.4.2/lib/amd64/libdcpr.so
2ae446d000-2ae4478000 r-xs 00000000 03:05 124444                         /tmp/jar_cache42643.tmp (deleted)
2ae4478000-2ae4578000 rwxp 2ae4478000 00:00 0 
7fbfe00000-7fbfe02000 rwxp 7fbfe00000 00:00 0 
7fbfe02000-7fbfe05000 ---p 7fbfe02000 00:00 0 
7fbffdb000-7fc0000000 rwxp 7fbffdb000 00:00 0 
ffffffffff600000-ffffffffffe00000 ---p 00000000 00:00 0 

Heap at VM Abort:
Heap
 def new generation   total 2048K, used 197K [0x0000002ad9c70000, 0x0000002ad9ea0000, 0x0000002adb1c0000)
  eden space 1856K,  10% used [0x0000002ad9c70000, 0x0000002ad9ca1600, 0x0000002ad9e40000)
  from space 192K,   0% used [0x0000002ad9e40000, 0x0000002ad9e40000, 0x0000002ad9e70000)
  to   space 192K,   0% used [0x0000002ad9e70000, 0x0000002ad9e70000, 0x0000002ad9ea0000)
 tenured generation   total 4384K, used 2629K [0x0000002adb1c0000, 0x0000002adb608000, 0x0000002addc70000)
   the space 4384K,  59% used [0x0000002adb1c0000, 0x0000002adb451428, 0x0000002adb451600, 0x0000002adb608000)
 compacting perm gen  total 16384K, used 13238K [0x0000002addc70000, 0x0000002adec70000, 0x0000002ae1c70000)
   the space 16384K,  80% used [0x0000002addc70000, 0x0000002ade95d930, 0x0000002ade95da00, 0x0000002adec70000)

Local Time = Mon Sep 19 20:31:20 2005
Elapsed Time = 34
#
# HotSpot Virtual Machine Error : 11
# Error ID : 4F530E43505002EF
# Please report this error at
# [http://www.blackdown.org/cgi-bin/jdk](http://www.blackdown.org/cgi-bin/jdk)
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (Blackdown-1.4.2-02 mixed mode)
#

------------


Any ideia about whout can I do to fix it?


Thanks!


My bank account is: [www.bb.com.br](www.bb.com.br)

---

### Post by Swab on 2005-09-27
OK so I was getting the libXp.so.6 error: ```
Java process: caught exception from sun.plugin.navig.motif.Plugin.start Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/j2re1.4-blackdown/lib/amd64/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory Followed solution as posted above.
```
Followed solution posted above.  Now firefox crashes with only: ```
Segmentation fault
``` Any ideas?

---

### Post by oak on 2005-09-28
Hi, I've also got the same error, ie "Segmentation Fault". Has anyone made any headway on a solution?

---

### Post by mishranurag on 2006-01-26
I am also getting same kinds of error!
Should I leave firefox :(
Anurag

---

