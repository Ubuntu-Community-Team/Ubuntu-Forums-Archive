---
title: "Java Problems ..."
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by wannabelinuxconvert on 2006-01-16
Hi,

I used the wiki page [https://wiki.ubuntu.com/JavaPPC]("https://wiki.ubuntu.com/JavaPPC") to install the PowerPC version of the Java 1.5 SDK and everything went fine, except for after the installation when typing JAVA in the terminal I got the 'Command not found' error ... so to sort this out I added the line ```
java='/opt/ibm-java2-ppc-50/bin/java'
``` into my .bashrc file and now I get the correct output. And when I do ```
Java -showversion
``` I get the following 
```
Java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build pxp32dev-20050923b)
IBM J9SE VM (build 2.3, J2RE 1.5.0 IBM J9 2.3 Linux ppc-32 j9vmxp3223-20050915a (JIT enabled)
J9VM - 20050914_03248_bHdSMR
JIT  - 20050914_1758_r8
GC   - 20050907_AB)
JCL  - 20050915
```

Followed by the rest of the help file ... so it looks as if everything went okay with the installation. 

My problem is that I then downloaded Eclipse and JEdit but neither will run. When I click on the apps in the app menu, the taskbar entry appears in the taskbar (*with either 'starting eclipse' or just 'jEdit' depending on which was clicked*) as you'd expect, but only for a few seconds and then it disappears with no error ... and if I try running the jar's from the terminal, it thinks for a while, and then just returns to the prompt, again with no output or error messages !?

I know the JAVA installation is running okay because I also installed the Firefox Plugin, but this consumes a whopping 500mb of memory, and doesn't end when you close Firefox so I've since removed it - but tested it against the Java Installation Test on [http://www.java.com]("http://www.java.com") and everything ran fine.

Any ideas !?

Cheers

Mic

---

### Post by Rob_Frohne on 2006-01-18
Hi, I don't have any answers for you, but I went to download the tarball from IBM and I can't find it anywhere now. I wonder if they pulled it because Apple is now going with Intel?

 Can anyone tell me where I might be able to download it now? 

Thanks, Rob:(

---

### Post by felix_stegerman on 2006-01-20
[QUOTE=Rob_Frohne]... I went to download the tarball from IBM and I can't find it anywhere now. I wonder if they pulled it because Apple is now going with Intel? Can anyone tell me where I might be able to download it now?[/QUOTE]

It's still at [http://www-128.ibm.com/developerworks/java/jdk/linux/download.html](http://www-128.ibm.com/developerworks/java/jdk/linux/download.html).


Felix

---

### Post by Rob_Frohne on 2006-01-23
You are right.  I didn't realize I needed the i or p series software.

Thanks,

Rob

---

