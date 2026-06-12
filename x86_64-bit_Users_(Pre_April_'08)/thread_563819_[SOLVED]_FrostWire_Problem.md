---
title: "[SOLVED] FrostWire Problem"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by master_kernel on 2007-09-30
I get this problem when running FrostWire 4.13.3 in 64-bit Ubuntu with Sun Java 5 and 6 Runtime Environments installed. I think it's a library problem, but I don't know which one.

> Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b2b6ae60e25, pid=7406, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid7406.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7406 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)


---

### Post by Kilz on 2007-09-30
It was trying to use java 6. Frostwire doesnt like java 6 if I remember right.

---

### Post by master_kernel on 2007-09-30
> **Kilz said:**
> It was trying to use java 6. Frostwire doesnt like java 6 if I remember right.
So if I use Java 5 I'll be OK?

---

### Post by santiagoward2000 on 2007-09-30
> **Kilz said:**
> It was trying to use java 6. Frostwire doesnt like java 6 if I remember right.

I'm using FrostWire with java6 and have no problems...

---

### Post by master_kernel on 2007-09-30
> **master_kernel said:**
> So if I use Java 5 I'll be OK?
UPDATE: It worked! I used the ia32 version of sun-java5 though. I haven't tested it with the 64-bit version. Thanks Kilz!

---

### Post by master_kernel on 2007-09-30
> **santiagoward2000 said:**
> I'm using FrostWire with java6 and have no problems...
I'm using Gutsy 64-bit with the latest version of Frostwire (4.13.3).

---

### Post by santiagoward2000 on 2007-09-30
> **master_kernel said:**
> I'm using Gutsy 64-bit with the latest version of Frostwire (4.13.3).

Mmm... I don't know about that. I'm using Xubuntu Feisty on a standard laptop. Personally, I had no problems with java6 and FrostWire (better thank thank my lucky star :KS )

---

### Post by Nameless_one on 2007-09-30
I think Frostwire is built for i386 and it requires a java to match that. It did the exact same thing on my system, but I applied a very dirty hack and it worked - I edited /etc/bin/frostwire and called a i386 java executable directly instead of just 'java' which calls the standard, 1.6 java. That did it. 

@master_kernel
Provided that my way is dirty and messy, and could prove buggy, I wonder how you used the x86 java 1.5 :) Pray tell.

---

### Post by master_kernel on 2007-10-01
> **Nameless_one said:**
> I think Frostwire is built for i386 and it requires a java to match that. It did the exact same thing on my system, but I applied a very dirty hack and it worked - I edited /etc/bin/frostwire and called a i386 java executable directly instead of just 'java' which calls the standard, 1.6 java. That did it. 

@master_kernel
Provided that my way is dirty and messy, and could prove buggy, I wonder how you used the x86 java 1.5 :) Pray tell.
I just installed the 32-bit version of java and updated the java config:
NOTE: I noticed that it is just the 64-bit version of Java that does not work, and that the ia32 version of Java 5 or 6 does work.

```
sudo apt-get install ia32-sun-java6-bin
```
```
sudo update-alternatives --config java
```
Then choose the ia32 version of Java 6.
**EDIT:** I am using the latest version of Frostwire from their website for Ubuntu (4.13.3).


master_kernel

---

### Post by hagar_am on 2007-10-03
> **master_kernel said:**
> I just installed the 32-bit version of java and updated the java config:
NOTE: I noticed that it is just the 64-bit version of Java that does not work, and that the ia32 version of Java 5 or 6 does work.

```
sudo apt-get install ia32-sun-java6-bin
```
```
sudo update-alternatives --config java
```
Then choose the ia32 version of Java 6.
**EDIT:** I am using the latest version of Frostwire from their website for Ubuntu (4.13.3).


master_kernel

thx, thats help a lot:)

---

### Post by mwacky on 2007-10-06
> I just installed the 32-bit version of java and updated the java config:
NOTE: I noticed that it is just the 64-bit version of Java that does not work, and that the ia32 version of Java 5 or 6 does work.

Code:

sudo apt-get install ia32-sun-java6-bin

Code:

sudo update-alternatives --config java

Then choose the ia32 version of Java 6.


Thanks, Worked Awesome!!

---

### Post by old_geekster on 2007-11-06
> **mwacky said:**
> Thanks, Worked Awesome!!

Thanks from here, also!  Frostwire works fine with "ia32" in Gutsy 64-bit.:)  However, I have attempted every cure for the JRE 64-bit and it will not run; heck, it won't even start.:confused:

---

### Post by Cluc TK423 on 2007-11-22
I've had the same issues with FrostWire and the 64-bit JRE.

Thanks for the simple solution!

---

### Post by checho4 on 2007-12-16
I have Kubuntu Gutsy 64bit and FrostWire works well with Java IcedTea 7.

---

### Post by Major_Kong on 2007-12-17
Problem with Frostwire 4.13.4 :

> Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: Ficheiro ou directoria inexistente
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: Ficheiro ou directoria inexistente
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

Any ideas ?


EDIT: The program is fine. "Manually" starting the program works.
Some problem with the starter script or the java6 package... Can't decide...

---

### Post by Major_Kong on 2007-12-17
I decided, it's a problem with the sun-java 6 package.

---

### Post by rsambuca on 2007-12-17
What do you mean "Manually" starting it works.  Manually starting what?

---

### Post by Major_Kong on 2007-12-17
Using the console, and typing the correct command.

In my case (in the frostwire directory) :

 > 
'/usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java' -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar

Apparently the frostwire script doesn't find the java bin. Which is probably related to the way the sun-java6-bin package was made.

---

### Post by rsambuca on 2007-12-18
> **Major_Kong said:**
> Using the console, and typing the correct command.

In my case (in the frostwire directory) :

 

Apparently the frostwire script doesn't find the java bin. Which is probably related to the way the sun-java6-bin package was made.

Wow!  That is quite the command.  So does this command allow you to run Frostwire without the ia32 java?

---

### Post by Major_Kong on 2007-12-18
Yes, but i'm using the 4.13.4 version, i never tried 4.13.3 so it may be unrelated to the earlier problem.

As i said, the problem i found seems (at least to me) to be more related to the way the sun-java6 packages of ubuntu were made than with frostwire.

E.g.: If i type 'java' in the console, i get this:

> A aplicação 'java' poderá ser encontrada nos seguintes pacotes (it says java can be found in the following packages) :
 * j2re1.4
 * kaffe
 * cacao
 * java-gcj-compat
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Tente: sudo apt-get install <pacote selecionado>
bash: java: command not found


So, i think a link to the java bin, or a script to java is never created in the first place...

---

### Post by damvcoool on 2007-12-21
I am using Java7 (icedtea) and it does load but it never connects :S and i know is not firewall issue because it works with Java6 32bit.

any suggestions for IcedTea? any modification anywhere. i dont like combining 32 and 64 apps.

---

### Post by wolffkrieger on 2008-01-04
> **master_kernel said:**
> I just installed the 32-bit version of java and updated the java config:
NOTE: I noticed that it is just the 64-bit version of Java that does not work, and that the ia32 version of Java 5 or 6 does work.

```
sudo apt-get install ia32-sun-java6-bin
```
```
sudo update-alternatives --config java
```
Then choose the ia32 version of Java 6.
**EDIT:** I am using the latest version of Frostwire from their website for Ubuntu (4.13.3).


master_kernel

Thanks a lot!!! This really helped.

---

### Post by Major_Kong on 2008-01-07
> **Major_Kong said:**
> Using the console, and typing the correct command.

In my case (in the frostwire directory) :

>  '/usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java' -ea -Dorg.apache.commons.logging.Log=org.apache.commons .logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar

Apparently the frostwire script doesn't find the java bin. Which is probably related to the way the sun-java6-bin package was made.

This also works with other users, right ?

---

### Post by Azraelthe7th on 2008-01-29
> **Major_Kong said:**
> This also works with other users, right ?

I wouldn't even know where to put it.  Care to explain?

---

