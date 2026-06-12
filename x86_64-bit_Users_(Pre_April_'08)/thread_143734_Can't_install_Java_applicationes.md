---
title: "Can't install Java applicationes"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by z3r0x on 2006-03-13
I can't install any Java applicationes.

> 
unix@ubuntu:~/Desktop/ZendStudio-3_5_2$ ./ZendStudio-3_5_2.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.24171/Linux/resource/jre/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX) 


I installed the libxp6 package but it won't work. Does anybody know how to solve this problem? 

Thanks,

---

### Post by gord on 2006-03-13
sounds like you need the sun JRE

[this website](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java) should sort you out :)

---

### Post by z3r0x on 2006-03-13
I already installed java. The j2re1.4 and j2sdk1.4 package. This is the output of Java -version

```

unix@ubuntu:~/Desktop$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

```

---

### Post by hod139 on 2006-03-13
do you have the build-essential package installed?

---

### Post by knalle on 2006-03-13
[QUOTE=z3r0x]I already installed java. The j2re1.4 and j2sdk1.4 package. This is the output of Java -version

```

unix@ubuntu:~/Desktop$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

```[/QUOTE]

you got the blackdown version of the jdk, try the sun kit, or try to run the jvm in -classic mode


 Now go to Sun's website [http://java.sun.com/](http://java.sun.com/) and select the java jdk or jre that you want.

This example uses J2jsdk-1.4.2 but you can use any J2sdk. Run similar commands from the terminal:

First install the required packages:

sudo apt-get install fakeroot java-package java-common

Create the Deb file for the install:

fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i586.bin

Install The deb file

sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb

Now make Sun's java the default by running this command and selecting it.

sudo update-alternatives --config java

you can now check your java sdk with:

java -version

java version "1.4.2_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_10-b03)
Java HotSpot(TM) Client VM (build 1.4.2_10-b03, mixed mode)

Happy Hacking!

---

### Post by z3r0x on 2006-03-15
Hi thanks for helping me. But it wont work

```

unix@ubuntu:~/Desktop$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)

```

any other ideas?

> 
Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.21068/Linux/resource/jre/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1473)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1389)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:832)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:507)
        at com.zerog.ia.installer.Main.c(Unknown Source)
        at com.zerog.ia.installer.Main.main(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at com.zerog.lax.LAX.launch(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
GUI-
unix@ubuntu:~/Desktop$


---

### Post by hod139 on 2006-03-15
Looks like you are missing libXp.so.6.  Looks like you can install that lib by installing the libxp6 package.  Interestingly, there is also a libxp-java package, maybe that package will help too.

---

### Post by z3r0x on 2006-03-15
I've already installed the libxp-java package and libXp.so.6 is also located on my harddisk

> 
unix@ubuntu:~$ sudo find / -name libXp.so.6
/usr/lib/libXp.so.6
/usr/X11R6/lib/libXp.so.6


---

### Post by WhiteZ on 2006-11-14
Same problem here on 32 bit installation on AMD 64 

# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

Errors are the same:
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/home/tmp/install.dir.23265/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory


I have all of the above mentioned packages installed.

---

### Post by kuja on 2006-11-14
Is this program 32-bit or 64-bit?  If it's 32-bit you may need to install 32-bit libraries to make it run.
If so then libXp.so.6, as well as many other things, is provided by the ia32-libs package.

---

### Post by RAOF on 2006-11-14
Ugh.  What a stupid way to write an installer for a Java program.  It seems to have it's own copy of the Java runtime, which is 32bit, so it's like taking all the cross-platform advantages of Java and then saying "nah, let's make sure it only ever runs on IA32".

kuja's advice is probably what'll fix stuff for you.  You'll just need 32bit versions of all those libraries mentioned.

---

### Post by ktroxe on 2006-11-16
I've ubuntu 32 bits installed in a computer with a 32 bits processor and I take the same error:

-------------------------------------------------------------------------
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
------------------------------------------------------------------------

---

### Post by kuja on 2006-11-16
You need to install libc6 - ```
sudo apt-get install libc6
```

---

### Post by daru on 2006-11-20
vi into the installer bin file, and comment the line holding:
> export LD_ASSUME_KERNEL...
And enjoy

Any GPLed replacements for Zend Studio ?

---

