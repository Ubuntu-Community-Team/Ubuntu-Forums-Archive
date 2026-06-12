---
title: "Different Java versions on a 64bit PC?"
date: 2007-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Palmstroem on 2007-02-14
Hi all,

I am running Edgy on an amd64 PC. I installed the 32bit firefox and java version following [Kilz' Howto]("http://www.ubuntuforums.org/showthread.php?p=1174435")  and it works. I also installed the latest Sun Java binary (jre-1_5_0_11-linux-i586.bin) following the [hod139 Howto]("http://ubuntuforums.org/showthread.php?t=201378").

However, I get this:

:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

And the Matlab command "ver" reports

>> ver
-------------------------------------------------------------------------------------
MATLAB Version 7.3.0.298 (R2006b)
MATLAB License Number: xxxxxx
Operating System: Linux 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64
Java VM Version: Java 1.5.0_04 with Sun Microsystems Inc. Java HotSpot(TM) 64-Bit Server VM mixed mode

So it appears I have many different java versions on my system. Any help?

---

### Post by Kilz on 2007-02-14
> **Palmstroem said:**
> Hi all,

I am running Edgy on an amd64 PC. I installed the 32bit firefox and java version following [Kilz' Howto]("http://www.ubuntuforums.org/showthread.php?p=1174435")  and it works. I also installed the latest Sun Java binary (jre-1_5_0_11-linux-i586.bin) following the [hod139 Howto]("http://ubuntuforums.org/showthread.php?t=201378").

However, I get this:

:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

And the Matlab command "ver" reports

>> ver
-------------------------------------------------------------------------------------
MATLAB Version 7.3.0.298 (R2006b)
MATLAB License Number: xxxxxx
Operating System: Linux 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64
Java VM Version: Java 1.5.0_04 with Sun Microsystems Inc. Java HotSpot(TM) 64-Bit Server VM mixed mode

So it appears I have many different java versions on my system. Any help?

Is it causing any problems? If not I would just leave it alone.

---

### Post by saneone on 2007-02-14
> **Kilz said:**
> Is it causing any problems? If not I would just leave it alone.

I have two different versions of Java installed on my system. 32 bit for Firefox32 and 64 bit for Azureus i.e. 
It seems that there are no troubles with it, but u must remember to install different versions of Java to different directories...
For example i have /opt/jre1.5.0_11_x64 and /opt/jre1.5.0_11 dirs and everything`s fine...

---

### Post by Kilz on 2007-02-14
> **saneone said:**
> I have two different versions of Java installed on my system. 32 bit for Firefox32 and 64 bit for Azureus i.e. 
It seems that there are no troubles with it, but u must remember to install different versions of Java to different directories...
For example i have /opt/jre1.5.0_11_x64 and /opt/jre1.5.0_11 dirs and everything`s fine...

I also have 2 different versions installed. Thats why I asked if the original poster was having any problems.

---

### Post by Palmstroem on 2007-02-15
Thanks Kilz and saneone for the quick reply!

Although Firefox and Matlab both work fine with my "multi-java-config", another program (Comsol Multiphysics) crashes after the last update! Could have quite a number of reasons, of course (one candidate is the ATI driver ati-driver-installer-8.33.6.x86.x86_64.run). But the graphics runs fine with Matlab.

In my system I found at least three java versions:

$ /usr/local/sys/java/jre/glnxa64/jre1.5.0/bin/java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_04-b05, mixed mode)

$ /usr/lib/jvm/java-1.5.0-sun/jre/bin/java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

$ /usr/local/java32/bin/java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Server VM (build 1.5.0_11-b03, mixed mode)

Probably some more :)  It seems to me that some commercial programs are just installing "their own" java version as well. How do I get rid of the old versions & clean up my system? What about all the symbolic links? Why should I put java into /opt ?

Thanks again for all comments!

---

### Post by Kilz on 2007-02-15
> **Palmstroem said:**
> Thanks Kilz and saneone for the quick reply!

Although Firefox and Matlab both work fine with my "multi-java-config", another program (Comsol Multiphysics) crashes after the last update! Could have quite a number of reasons, of course (one candidate is the ATI driver ati-driver-installer-8.33.6.x86.x86_64.run). But the graphics runs fine with Matlab.

In my system I found at least three java versions:

$ /usr/local/sys/java/jre/glnxa64/jre1.5.0/bin/java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_04-b05, mixed mode)

$ /usr/lib/jvm/java-1.5.0-sun/jre/bin/java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

$ /usr/local/java32/bin/java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Server VM (build 1.5.0_11-b03, mixed mode)

Probably some more :)  It seems to me that some commercial programs are just installing "their own" java version as well. How do I get rid of the old versions & clean up my system? What about all the symbolic links? Why should I put java into /opt ?

Thanks again for all comments!

Unless you are sure thats the reason that program is crashing. I would just leave a few multiple java installs alone. Its more work than its worth and you could do all the work for nothing.

---

### Post by Palmstroem on 2007-02-15
Kilz, you are right, the Comsol crash is not a java problem. When I boot into the previous kernel the program works OK. However, fglrxinfo returns:
[INDENT]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)[/INDENT]

so the Mesa software rederer is used. However, with the new kernel and the proprietary ATI driver graphics is much faster and did not crash with Matlab or other programs so far.

Any ideas? By the way, I have to admit, I'm getting a bit "lost in installation/configuration space":confused: 

My fault, I know, since I am installing proprietary software :)

---

### Post by s_spiff on 2007-02-15
finally! I've been thinking I was the only one who had 2 Java installations. Thanks.

---

### Post by Kilz on 2007-02-15
> **Palmstroem said:**
> Kilz, you are right, the Comsol crash is not a java problem. When I boot into the previous kernel the program works OK. However, fglrxinfo returns:
[INDENT]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)[/INDENT]

so the Mesa software rederer is used. However, with the new kernel and the proprietary ATI driver graphics is much faster and did not crash with Matlab or other programs so far.

Any ideas? By the way, I have to admit, I'm getting a bit "lost in installation/configuration space":confused: 

My fault, I know, since I am installing proprietary software :)

Every time the kernel upgrades a number (sometimes updates fix minor bugs that dont increese the number) you have to update the kernel module for ATI. The following commands should do it.


```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

---

