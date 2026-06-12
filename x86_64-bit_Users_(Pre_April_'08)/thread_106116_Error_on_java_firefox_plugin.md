---
title: "Error on java firefox plugin"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Al_maverick on 2005-12-19
I use Kubuntu and installed the blackdown java package.
When I try to use a java site, Firefox quits when I click on a java feature.

I get an error log in my home folder stating an undefined function in libjvm.so

Anyone have an idea what may be happening?

Also, I tried the java test in [www.java.com](www.java.com), and I only get a blank page on test 1.

---

### Post by omegamike on 2005-12-19
Hi, it sounds like you might need to delete the current plugin in your firefox plugins folder and make a new symbolic link from your java plugins folder to the firefox plugins folder. I will tell you how I did it, but your java might be installed into a different directory, so please make sure to put in *your* installation paths.

After locating both your mozilla plugins directory (mine is /usr/lib/mozilla-firefox/plugins) and your java plugin directory (mine is /usr/lib/j2re1.5-sun/plugin/i386/ns7), crank up a terminal:

#cd into your mozilla plugins directory:

cd /usr/lib/mozilla-firefox/plugins
sudo rm libjavaplugin_oji.so
sudo ln -s  /lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

The first path is the java plugin, the second is the firefox plugin directory.

That should make the link for you. I did it on my system about an hour ago. If you are using firefox 1.5, there is a good chance it is installed in /opt/firefox/plugins but try there or in /usr/lib just to be sure

---

### Post by Al_maverick on 2005-12-19
no luck. I have Firefox 1.0.7.
I tried this command: 
```
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/ 
```

I tried again and Firefox quit on me just like before. I get this log file on my home folder.

> Unexpected Signal : 11 occurred at PC=0x2AAAAB55BDAA
Function=(null)
Library=/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
	at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
	at sun.plugin.navig.motif.AThread.JNIHandleLoop(AThread.java:35)
	at sun.plugin.navig.motif.AThread.run(AThread.java:27)

Dynamic libraries:
40000000-40003000 r-xp 00000000 08:03 488718                             /usr/lib/j2se/1.4/jre/bin/java_vm
40102000-40103000 rwxp 00002000 08:03 488718                             /usr/lib/j2se/1.4/jre/bin/java_vm
40103000-4018f000 rwxp 40103000 00:00 0                                  [heap]
2aaaaaaab000-2aaaaaac1000 r-xp 00000000 08:03 1368211                    /lib/ld-2.3.5.so
2aaaaaac1000-2aaaaaac4000 rwxp 2aaaaaac1000 00:00 0 
2aaaaaac4000-2aaaaaae0000 r-xs 00000000 08:03 835886                     /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
2aaaaaae0000-2aaaaaae3000 r-xs 00000000 08:03 835885                     /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
2aaaaaae3000-2aaaaab9f000 r-xs 00000000 08:03 835888                     /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
2aaaaab9f000-2aaaaabad000 r-xs 00000000 08:03 835887                     /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
2aaaaabc1000-2aaaaabc2000 rwxp 00016000 08:03 1368211                    /lib/ld-2.3.5.so
2aaaaabc2000-2aaaaabc5000 r-xp 00000000 08:03 65508                      /usr/lib/libartsdsp.so.0.0.0
2aaaaabc5000-2aaaaacc4000 ---p 00003000 08:03 65508                      /usr/lib/libartsdsp.so.0.0.0
2aaaaacc4000-2aaaaacc5000 rwxp 00002000 08:03 65508                      /usr/lib/libartsdsp.so.0.0.0
2aaaaacc5000-2aaaaaccb000 r-xp 00000000 08:03 788919                     /usr/lib/libartsc.so.0.0.0
2aaaaaccb000-2aaaaadca000 ---p 00006000 08:03 788919                     /usr/lib/libartsc.so.0.0.0
2aaaaadca000-2aaaaadcb000 rwxp 00005000 08:03 788919                     /usr/lib/libartsc.so.0.0.0
2aaaaaddb000-2aaaaadeb000 r-xp 00000000 08:03 1368230                    /lib/libpthread-2.3.5.so
2aaaaadeb000-2aaaaaeeb000 ---p 00010000 08:03 1368230                    /lib/libpthread-2.3.5.so
2aaaaaeeb000-2aaaaaeec000 rwxp 00010000 08:03 1368230                    /lib/libpthread-2.3.5.so
2aaaaaeec000-2aaaaaef0000 rwxp 2aaaaaeec000 00:00 0 
2aaaaaef0000-2aaaaaef2000 r-xp 00000000 08:03 1368219                    /lib/libdl-2.3.5.so
2aaaaaef2000-2aaaaaff1000 ---p 00002000 08:03 1368219                    /lib/libdl-2.3.5.so
2aaaaaff1000-2aaaaaff2000 rwxp 00001000 08:03 1368219                    /lib/libdl-2.3.5.so
2aaaaaff2000-2aaaaaff3000 rwxp 2aaaaaff2000 00:00 0 
2aaaaaff3000-2aaaab121000 r-xp 00000000 08:03 1368217                    /lib/libc-2.3.5.so
2aaaab121000-2aaaab220000 ---p 0012e000 08:03 1368217                    /lib/libc-2.3.5.so
2aaaab220000-2aaaab226000 rwxp 0012d000 08:03 1368217                    /lib/libc-2.3.5.so
2aaaab226000-2aaaab22b000 rwxp 2aaaab226000 00:00 0 
2aaaab22b000-2aaaab76a000 r-xp 00000000 08:03 932758                     /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2aaaab76a000-2aaaab86b000 ---p 0053f000 08:03 932758                     /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2aaaab86b000-2aaaab997000 rwxp 00540000 08:03 932758                     /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2aaaab997000-2aaaab9c9000 rwxp 2aaaab997000 00:00 0 
2aaaab9d9000-2aaaab9ed000 r-xp 00000000 08:03 1368222                    /lib/libnsl-2.3.5.so
2aaaab9ed000-2aaaabaed000 ---p 00014000 08:03 1368222                    /lib/libnsl-2.3.5.so
2aaaabaed000-2aaaabaee000 rwxp 00014000 08:03 1368222                    /lib/libnsl-2.3.5.so
2aaaabaee000-2aaaabaf0000 rwxp 2aaaabaee000 00:00 0 
2aaaabaf0000-2aaaabb75000 r-xp 00000000 08:03 1368220                    /lib/libm-2.3.5.so
2aaaabb75000-2aaaabc74000 ---p 00085000 08:03 1368220                    /lib/libm-2.3.5.so
2aaaabc74000-2aaaabc75000 rwxp 00084000 08:03 1368220                    /lib/libm-2.3.5.so
2aaaabc75000-2aaaabc7d000 r-xp 00000000 08:03 880436                     /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2aaaabc7d000-2aaaabd7d000 ---p 00008000 08:03 880436                     /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2aaaabd7d000-2aaaabd7f000 rwxp 00008000 08:03 880436                     /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2aaaabd7f000-2aaaabd80000 rwxp 2aaaabd7f000 00:00 0 
2aaaabd80000-2aaaabd84000 rwxs 00000000 08:03 765637                     /tmp/hsperfdata_al/20258
2aaaabd90000-2aaaabd98000 r-xp 00000000 08:03 1368223                    /lib/libnss_compat-2.3.5.so
2aaaabd98000-2aaaabe98000 ---p 00008000 08:03 1368223                    /lib/libnss_compat-2.3.5.so
2aaaabe98000-2aaaabe99000 rwxp 00008000 08:03 1368223                    /lib/libnss_compat-2.3.5.so
2aaaabe99000-2aaaabea2000 r-xp 00000000 08:03 1368227                    /lib/libnss_nis-2.3.5.so
2aaaabea2000-2aaaabfa2000 ---p 00009000 08:03 1368227                    /lib/libnss_nis-2.3.5.so
2aaaabfa2000-2aaaabfa3000 rwxp 00009000 08:03 1368227                    /lib/libnss_nis-2.3.5.so
2aaaabfa3000-2aaaabfae000 r-xp 00000000 08:03 1368225                    /lib/libnss_files-2.3.5.so
2aaaabfae000-2aaaac0ad000 ---p 0000b000 08:03 1368225                    /lib/libnss_files-2.3.5.so
2aaaac0ad000-2aaaac0ae000 rwxp 0000a000 08:03 1368225                    /lib/libnss_files-2.3.5.so
2aaaac0ae000-2aaaac0c0000 r-xp 00000000 08:03 963533                     /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2aaaac0c0000-2aaaac1bf000 ---p 00012000 08:03 963533                     /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2aaaac1bf000-2aaaac1c2000 rwxp 00011000 08:03 963533                     /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2aaaac1c2000-2aaaac1e2000 r-xp 00000000 08:03 963545                     /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2aaaac1e2000-2aaaac2e2000 ---p 00020000 08:03 963545                     /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2aaaac2e2000-2aaaac2e7000 rwxp 00020000 08:03 963545                     /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2aaaac2e7000-2aaaac2f8000 r-xp 00000000 08:03 963539                     /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2aaaac2f8000-2aaaac3f7000 ---p 00011000 08:03 963539                     /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2aaaac3f7000-2aaaac3fb000 rwxp 00010000 08:03 963539                     /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2aaaac3fb000-2aaaadda7000 r-xs 00000000 08:03 505148                     /usr/lib/j2se/1.4/jre/lib/rt.jar
2aaaadda7000-2aaaaddf1000 rwxp 2aaaadda7000 00:00 0 
2aaaaddf1000-2aaaade07000 r-xs 00000000 08:03 505144                     /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
2aaaade07000-2aaaadee4000 r-xs 00000000 08:03 472355                     /usr/lib/j2se/1.4/jre/lib/jsse.jar
2aaaadee4000-2aaaadef5000 r-xs 00000000 08:03 505146                     /usr/lib/j2se/1.4/jre/lib/jce.jar
2aaaadef5000-2aaaae495000 r-xs 00000000 08:03 472357                     /usr/lib/j2se/1.4/jre/lib/charsets.jar
2aaaae495000-2aaaae677000 r-xs 00000000 08:03 505143                     /usr/lib/j2se/1.4/jre/lib/plugin.jar
2aaaae677000-2aaaae777000 rwxp 2aaaae677000 00:00 0 
2aaaae777000-2aaaee677000 rwxp 2aaaae777000 00:00 0 
2aaaee677000-2aaaee67b000 rwxp 2aaaee677000 00:00 0 
2aaaee67b000-2aaaef677000 rwxp 2aaaee67b000 00:00 0 
2aaaef677000-2aaaef6c6000 rwxp 2aaaef677000 00:00 0 
2aaaef6d0000-2aaaef8d0000 rwxp 2aaaef6d0000 00:00 0 
2aaaef8d0000-2aaaf0c20000 rwxp 2aaaef8d0000 00:00 0 
2aaaf0c20000-2aaaf0f0b000 rwxp 2aaaf0c20000 00:00 0 
2aaaf0f0b000-2aaaf36d0000 rwxp 2aaaf0f0b000 00:00 0 
2aaaf36d0000-2aaaf46d0000 rwxp 2aaaf36d0000 00:00 0 
2aaaf46d0000-2aaaf76d0000 rwxp 2aaaf46d0000 00:00 0 
2aaaf76d0000-2aaaf76d1000 rwxp 2aaaf76d0000 00:00 0 
2aaaf76d1000-2aaaf76da000 rwxp 2aaaf76d1000 00:00 0 
2aaaf76da000-2aaaf76dd000 rwxp 2aaaf76da000 00:00 0 
2aaaf76dd000-2aaaf76f0000 rwxp 2aaaf76dd000 00:00 0 
2aaaf76f0000-2aaaf76f8000 rwxp 2aaaf76f0000 00:00 0 
2aaaf76f8000-2aaaf7710000 rwxp 2aaaf76f8000 00:00 0 
2aaaf7710000-2aaaf7713000 rwxp 2aaaf7710000 00:00 0 
2aaaf7713000-2aaaf7727000 rwxp 2aaaf7713000 00:00 0 
2aaaf7727000-2aaaf7730000 rwxp 2aaaf7727000 00:00 0 
2aaaf7730000-2aaaf7748000 rwxp 2aaaf7730000 00:00 0 
2aaaf7748000-2aaaf78d8000 r-xp 00000000 08:03 799771                     /usr/lib/locale/locale-archive
2aaaf78d8000-2aaaf79d8000 rwxp 2aaaf78d8000 00:00 0 
2aaaf79d8000-2aaaf7abb000 r-xp 00000000 08:03 965271                     /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaf7abb000-2aaaf7bbc000 ---p 000e3000 08:03 965271                     /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaf7bbc000-2aaaf7bdd000 rwxp 000e4000 08:03 965271                     /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaf7bdd000-2aaaf7c02000 rwxp 2aaaf7bdd000 00:00 0 
2aaaf7c02000-2aaaf7c5a000 r-xp 00000000 08:03 963542                     /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaf7c5a000-2aaaf7d5a000 ---p 00058000 08:03 963542                     /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaf7d5a000-2aaaf7d5d000 rwxp 00058000 08:03 963542                     /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaf7d5d000-2aaaf7fa2000 r-xp 00000000 08:03 868337                     /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaf7fa2000-2aaaf80a1000 ---p 00245000 08:03 868337                     /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaf80a1000-2aaaf810b000 rwxp 00244000 08:03 868337                     /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaf810b000-2aaaf810c000 rwxp 2aaaf810b000 00:00 0 
2aaaf810c000-2aaaf8114000 r-xp 00000000 08:03 65959                      /usr/lib/libXp.so.6.2.1
2aaaf8114000-2aaaf8213000 ---p 00008000 08:03 65959                      /usr/lib/libXp.so.6.2.1
2aaaf8213000-2aaaf8214000 rwxp 00007000 08:03 65959                      /usr/lib/libXp.so.6.2.1
2aaaf8214000-2aaaf826f000 r-xp 00000000 08:03 65187                      /usr/lib/libXt.so.6.0.0
2aaaf826f000-2aaaf836e000 ---p 0005b000 08:03 65187                      /usr/lib/libXt.so.6.0.0
2aaaf836e000-2aaaf8374000 rwxp 0005a000 08:03 65187                      /usr/lib/libXt.so.6.0.0
2aaaf8374000-2aaaf8375000 rwxp 2aaaf8374000 00:00 0 
2aaaf8375000-2aaaf837c000 r-xp 00000000 08:03 65175                      /usr/lib/libSM.so.6.0.1
2aaaf837c000-2aaaf847c000 ---p 00007000 08:03 65175                      /usr/lib/libSM.so.6.0.1
2aaaf847c000-2aaaf847d000 rwxp 00007000 08:03 65175                      /usr/lib/libSM.so.6.0.1
2aaaf847d000-2aaaf8495000 r-xp 00000000 08:03 65163                      /usr/lib/libICE.so.6.4.1
2aaaf8495000-2aaaf8594000 ---p 00018000 08:03 65163                      /usr/lib/libICE.so.6.4.1
2aaaf8594000-2aaaf8596000 rwxp 00017000 08:03 65163                      /usr/lib/libICE.so.6.4.1
2aaaf8596000-2aaaf8599000 rwxp 2aaaf8596000 00:00 0 
2aaaf8599000-2aaaf85a9000 r-xp 00000000 08:03 65185                      /usr/lib/libXext.so.6.4.1
2aaaf85a9000-2aaaf86a9000 ---p 00010000 08:03 65185                      /usr/lib/libXext.so.6.4.1
2aaaf86a9000-2aaaf86aa000 rwxp 00010000 08:03 65185                      /usr/lib/libXext.so.6.4.1
2aaaf86aa000-2aaaf86af000 r-xp 00000000 08:03 65733                      /usr/lib/libXtst.so.6.0.1
2aaaf86af000-2aaaf87af000 ---p 00005000 08:03 65733                      /usr/lib/libXtst.so.6.0.1
2aaaf87af000-2aaaf87b0000 rwxp 00005000 08:03 65733                      /usr/lib/libXtst.so.6.0.1
2aaaf87b0000-2aaaf8885000 r-xp 00000000 08:03 65183                      /usr/lib/libX11.so.6.2.0
2aaaf8885000-2aaaf8985000 ---p 000d5000 08:03 65183                      /usr/lib/libX11.so.6.2.0
2aaaf8985000-2aaaf8989000 rwxp 000d5000 08:03 65183                      /usr/lib/libX11.so.6.2.0
2aaaf8989000-2aaaf898a000 rwxp 2aaaf8989000 00:00 0 
2aaaf898a000-2aaaf898c000 r-xp 00000000 08:03 65179                      /usr/lib/libXau.so.6.0.0
2aaaf898c000-2aaaf8a8c000 ---p 00002000 08:03 65179                      /usr/lib/libXau.so.6.0.0
2aaaf8a8c000-2aaaf8a8d000 rwxp 00002000 08:03 65179                      /usr/lib/libXau.so.6.0.0
2aaaf8a8d000-2aaaf8a90000 r-xp 00000000 08:03 65181                      /usr/lib/libXdmcp.so.6.0.0
2aaaf8a90000-2aaaf8b8f000 ---p 00003000 08:03 65181                      /usr/lib/libXdmcp.so.6.0.0
2aaaf8b8f000-2aaaf8b90000 rwxp 00002000 08:03 65181                      /usr/lib/libXdmcp.so.6.0.0
2aaaf8b90000-2aaaf8ba1000 r-xp 00000000 08:03 965270                     /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaf8ba1000-2aaaf8ca0000 ---p 00011000 08:03 965270                     /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaf8ca0000-2aaaf8ca3000 rwxp 00010000 08:03 965270                     /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaf8ca3000-2aaaf8ccb000 rwxp 2aaaf8ca3000 00:00 0 
2aaaf8ccb000-2aaaf8d68000 r-xp 00000000 08:03 963537                     /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaf8d68000-2aaaf8e67000 ---p 0009d000 08:03 963537                     /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaf8e67000-2aaaf8e86000 rwxp 0009c000 08:03 963537                     /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaf8e86000-2aaaf9397000 rwxp 2aaaf8e86000 00:00 0 
2aaaf9397000-2aaaf93c6000 rwxs 00000000 00:07 86540292                   /SYSV00000000 (deleted)
2aaaf93c6000-2aaaf93f5000 rwxs 00000000 00:07 86573062                   /SYSV00000000 (deleted)
2aaaf93f5000-2aaaf93f7000 rwxp 2aaaf93f5000 00:00 0 
2aaaf943f000-2aaaf953f000 rwxp 2aaaf943f000 00:00 0 
2aaaf953f000-2aaaf9540000 r-xp 00000000 08:03 834422                     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
2aaaf9540000-2aaaf963f000 ---p 00001000 08:03 834422                     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
2aaaf963f000-2aaaf9640000 rwxp 00000000 08:03 834422                     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
2aaaf9640000-2aaaf964a000 r-xp 00000000 08:03 65264                      /usr/lib/libXcursor.so.1.0.2
2aaaf964a000-2aaaf9749000 ---p 0000a000 08:03 65264                      /usr/lib/libXcursor.so.1.0.2
2aaaf9749000-2aaaf974a000 rwxp 00009000 08:03 65264                      /usr/lib/libXcursor.so.1.0.2
2aaaf974a000-2aaaf9753000 r-xp 00000000 08:03 65262                      /usr/lib/libXrender.so.1.3.0
2aaaf9753000-2aaaf9852000 ---p 00009000 08:03 65262                      /usr/lib/libXrender.so.1.3.0
2aaaf9852000-2aaaf9853000 rwxp 00008000 08:03 65262                      /usr/lib/libXrender.so.1.3.0
2aaaf9853000-2aaaf9858000 r-xp 00000000 08:03 65260                      /usr/lib/libXfixes.so.3.0.0
2aaaf9858000-2aaaf9957000 ---p 00005000 08:03 65260                      /usr/lib/libXfixes.so.3.0.0
2aaaf9957000-2aaaf9958000 rwxp 00004000 08:03 65260                      /usr/lib/libXfixes.so.3.0.0
2aaaf9958000-2aaaf9976000 r-xp 00000000 08:03 834420                     /usr/lib/X11/locale/common/ximcp.so.2.0.0
2aaaf9976000-2aaaf9a75000 ---p 0001e000 08:03 834420                     /usr/lib/X11/locale/common/ximcp.so.2.0.0
2aaaf9a75000-2aaaf9a78000 rwxp 0001d000 08:03 834420                     /usr/lib/X11/locale/common/ximcp.so.2.0.0
2aaaf9ae5000-2aaaf9ce5000 rwxp 2aaaf9ae5000 00:00 0 
2aaaf9ce5000-2aaaf9cf3000 r-xp 00000000 08:03 963521                     /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaf9cf3000-2aaaf9df2000 ---p 0000e000 08:03 963521                     /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaf9df2000-2aaaf9df5000 rwxp 0000d000 08:03 963521                     /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaf9e05000-2aaaf9e09000 r-xp 00000000 08:03 1368224                    /lib/libnss_dns-2.3.5.so
2aaaf9e09000-2aaaf9f08000 ---p 00004000 08:03 1368224                    /lib/libnss_dns-2.3.5.so
2aaaf9f08000-2aaaf9f09000 rwxp 00003000 08:03 1368224                    /lib/libnss_dns-2.3.5.so
2aaaf9f09000-2aaaf9f1a000 r-xp 00000000 08:03 1368231                    /lib/libresolv-2.3.5.so
2aaaf9f1a000-2aaafa01a000 ---p 00011000 08:03 1368231                    /lib/libresolv-2.3.5.so
2aaafa01a000-2aaafa01b000 rwxp 00011000 08:03 1368231                    /lib/libresolv-2.3.5.so
2aaafa01b000-2aaafa01e000 rwxp 2aaafa01b000 00:00 0 
2aaafa01e000-2aaafa037000 r-xp 00000000 08:03 965265                     /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaafa037000-2aaafa136000 ---p 00019000 08:03 965265                     /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaafa136000-2aaafa14d000 rwxp 00018000 08:03 965265                     /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaafa17c000-2aaafa183000 r-xs 00000000 08:03 1417132                    /home/al/.java/deployment/cache/javapi/v1.0/jar/CSIM.jar-25643c8b-46974fd4.zip
2aaafa183000-2aaafa283000 rwxp 2aaafa183000 00:00 0 
2aaafa31a000-2aaafa41a000 rwxp 2aaafa31a000 00:00 0 
7fffffd70000-7fffffd72000 rwxp 7fffffd70000 00:00 0 
7fffffd72000-7fffffd75000 ---p 7fffffd72000 00:00 0 
7ffffff4c000-7ffffff71000 rwxp 7ffffff4c000 00:00 0                      [stack]
ffffffffff600000-ffffffffffe00000 ---p 00000000 00:00 0                  [vdso]

Heap at VM Abort:
Heap
 def new generation   total 1856K, used 1506K [0x00002aaaef6d0000, 0x00002aaaef8d0000, 0x00002aaaf0c20000)
  eden space 1664K,  79% used [0x00002aaaef6d0000, 0x00002aaaef818b98, 0x00002aaaef870000)
  from space 192K, 100% used [0x00002aaaef8a0000, 0x00002aaaef8d0000, 0x00002aaaef8d0000)
  to   space 192K,   0% used [0x00002aaaef870000, 0x00002aaaef870000, 0x00002aaaef8a0000)
 tenured generation   total 2988K, used 2389K [0x00002aaaf0c20000, 0x00002aaaf0f0b000, 0x00002aaaf36d0000)
   the space 2988K,  79% used [0x00002aaaf0c20000, 0x00002aaaf0e754e8, 0x00002aaaf0e75600, 0x00002aaaf0f0b000)
 compacting perm gen  total 16384K, used 11295K [0x00002aaaf36d0000, 0x00002aaaf46d0000, 0x00002aaaf76d0000)
   the space 16384K,  68% used [0x00002aaaf36d0000, 0x00002aaaf41d7f30, 0x00002aaaf41d8000, 0x00002aaaf46d0000)

Local Time = Tue Dec 20 01:45:45 2005
Elapsed Time = 129053
#
# HotSpot Virtual Machine Error : 11
# Error ID : 4F530E43505002EF
# Please report this error at
# [http://www.blackdown.org/cgi-bin/jdk](http://www.blackdown.org/cgi-bin/jdk)
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (Blackdown-1.4.2-02 mixed mode)
#

---

### Post by George666 on 2005-12-27
I get pretty much the same results as maverick, when I try to access my banks website.

Signal 11 is a segmentation fault, so it seems like a bug in the blackdown JVM.

It doesn't seem to be possible to report a bug on the blackdown website.

But there seems to be a new version out, I'm gonna try that and see what it gives.

---

### Post by Al_maverick on 2006-01-02
Did you try the new version? Any luck?

---

