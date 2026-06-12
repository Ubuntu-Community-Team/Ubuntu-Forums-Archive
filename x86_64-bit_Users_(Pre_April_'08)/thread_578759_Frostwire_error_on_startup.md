---
title: "Frostwire error on startup"
date: 2007-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ratchevs on 2007-10-17
I get this error when trying to run frostwire (just installed it, and sun java 6) from a terminal:

```

stefan@dilian-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b6fd10ca385, pid=6557, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid6557.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  6557 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)


```

any suggestions?

edit: using feisty

---

### Post by Kilz on 2007-10-17
> **ratchevs said:**
> I get this error when trying to run frostwire (just installed it, and sun java 6) from a terminal:

```

stefan@dilian-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b6fd10ca385, pid=6557, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid6557.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  6557 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)


```

any suggestions?

edit: using feisty

You might want to install ia32-java because its a 32bit java. The error looks to be because the 32bit frostwire is trying to use a 64bit java.

---

### Post by Marantz on 2007-12-25
[http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=java-gcj-compat](http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=java-gcj-compat)

Hmmmm

What can we do about this?

---

### Post by Kilz on 2007-12-25
> **Marantz said:**
> [http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=java-gcj-compat](http://qa.ubuntuwire.com/debcheck/debcheck.py?dist=gutsy&package=java-gcj-compat)

Hmmmm

What can we do about this?

Nothing, java-gcj-compat is not Sun Java. Frostwire may not work with it, Frostwire suggests you use Sun Java.

---

### Post by cv_zero on 2007-12-27
i get the same sigsegv fault with sun java...

---

### Post by PmDematagoda on 2007-12-27
If you are using Frostwire on Ubuntu X64 then you will need to use ia32Java.

---

### Post by rsambuca on 2007-12-27
> **cv_zero said:**
> i get the same sigsegv fault with sun java...

As kilz mentioned earlier, for frostwire you need to install the ia32 java.

---

### Post by Major_Kong on 2007-12-28
Before trying to use the ia32 java, do this:

in the console go to /usr/lib/frostwire, (the frostwire path) and type, 
"java -ea -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar"

Or:

> cd /usr/lib/frostwire
java -ea -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar


---

### Post by be4truth on 2008-02-20
That works for me on 64 bit with sun java. How can that be made permanent?

---

### Post by Kilbasar on 2008-04-06
> **be4truth said:**
> That works for me on 64 bit with sun java. How can that be made permanent?

stick it in a script. or, in copy-n'-paste form:

```
cd /usr/bin/
sudo mv frostwire frostwire.bak
sudo echo '#!/bin/sh' > frostwire
sudo echo 'cd /usr/lib/frostwire' >> frostwire
sudo echo 'java -ea -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar' >> frostwire
sudo chmod a+x frostwire
```

---

### Post by rrfx on 2008-04-23
With the RC of Hardy, I got the latest Frostwire (from frostwire-4.13.5.i586.deb) working fine with OpenJDK by commenting out/removing the "export AWT_TOOLKIT=MToolkit" lines from both of Frostwire's startup scripts:

```
sudo gedit /usr/lib/frostwire/runFrostwire.sh
sudo gedit /usr/bin/frostwire
```

This was done after setting OpenJDK as default:
```
sudo update-java-alternatives -s java-6-openjdk
```

---

### Post by augusto on 2008-04-26
Thanks rrfx! Worked for me too.

---

### Post by Driftech on 2008-05-29
Thank you!!

This hint saved me on Fedora 9 :)

---

### Post by fonsi2099 on 2008-05-29
Many thanks it works for me too, 
Hardy on Athlon 64bit
:guitar:

---

### Post by w00t1138 on 2008-06-06
Thanks!
Worked for me on 64bit Haron.:)

---

