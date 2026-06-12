---
title: "[SOLVED] how to frostwire with 64bit"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by tjwoosta on 2008-05-09
i am currently using limewire and all works fine, but i would like to switch over to frostwire

i downloaded the .deb from frostwire.com but frostwire still wont start

i am currently using java version "1.6.0_06"

here is the error i get when trying to start frostwire

```

tj@tj-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f709047d755, pid=26092, tid=1106626896
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid26092.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 26092 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

tj@tj-laptop:~$ 

```

any ideas on how i can make this work?

---

### Post by Exsecrabilus on 2008-05-09
Aww man I thought this was a guide to *making it work*.

I have the same problem. XD

---

### Post by old_geekster on 2008-05-10
Here is what I did to solve the problem:

sudo update-alternatives --config java

Here is the outcome of that command:

gene@Linuxbox-Ubuntu:~$ sudo update-alternatives --config java
[sudo] password for gene: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/ia32-java-6-sun/jre/bin/java' to provide 'java'.

As you can see, I chose "2".  This installs java 32-bit.  It is the only way that I could get "Frostwire" to function.  It is working better than ever.  All of the videos I have run on Youtube and other sites have also worked great.

By the way, you should install "ia32-libs", also.  This is the "ia32 shared libraries for use on amd64 and ia64 systems".

---

### Post by tjwoosta on 2008-05-10
> 
Here is what I did to solve the problem:


awesome, thanks man thats exactly what i was looking for.

i just got one queston though before i do this

will this replace java for everything, or just for frostwire?

i mean i want frostwire, but if i have to downgrade to 32 bit java for everything then i dont know if its worth it

also, do you know of any other good p2p clients that work with 64bit (besides limewire)

---

