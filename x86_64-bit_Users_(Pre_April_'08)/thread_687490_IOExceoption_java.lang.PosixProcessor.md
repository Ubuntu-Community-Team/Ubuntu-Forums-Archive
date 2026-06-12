---
title: "IOExceoption java.lang.PosixProcessor"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by rsearls on 2008-02-04
Getting the following stacktrace.   Any suggestion as to how to track down
the true cause of the failure?

NB6.0
Ubuntu 7.10
jdk1.6.0_03
   > java -version
           java version 1.5.0
          gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5unbuntu5)

============ stack trace =========================
Copying 1 file to /home/guest/x/jwt-client/dist/nbrun12962
Copying 1 file to /home/guest/x/jwt-client/dist/nbrun12962
Jad URL for OTA execution: [http://localhost:8082/servlet/org.netbeans.modules.mobility](http://localhost:8082/servlet/org.netbeans.modules.mobility)
.project.jam.JAMServlet/home/guest/x/jwt-client/dist//jwt-client.jad
Starting emulator in execution mode
java.io.IOException: java.io.IOException: No such file or directory
   at java.lang.PosixProcess.<init>(libgcj.so.81)
   at java.lang.Runtime.execInternal(libgcj.so.81)
   at java.lang.Runtime.exec(libgcj.so.81)
   at java.lang.Runtime.exec(libgcj.so.81)
   at com.sun.kvem.environment.JVM.run(Unknown Source)
   at com.sun.kvem.environment.EmulatorInvoker.runEmulatorOtherVM(Unknown Source)
   at com.sun.kvem.environment.EmulatorInvoker.runEmulator(Unknown Source)
   at com.sun.kvem.environment.ProfileEnvironment$KVMThread.runEmulator(Unknown Source
)
   at com.sun.kvem.environment.ProfileEnvironment$KVMThread.run(Unknown Source)
Caused by: java.io.IOException: No such file or directory
   at java.lang.PosixProcess.nativeSpawn(libgcj.so.81)
   at java.lang.PosixProcess.spawn(libgcj.so.81)
   at java.lang.PosixProcess$ProcessManager.run(libgcj.so.81)

---

### Post by prince_niceguy on 2008-02-20
which application are you tryig to run?

avoid using gcj instead use sun java from sun's website.

---

### Post by jespdj on 2008-02-20
According to the stack trace, you are running with GNU Java (libgcj). NetBeans and many other Java programs do not run well or at all on GNU Java. Make sure you are using Sun's Java. To make Sun Java the default on your system, run this:
```
update-alternatives --config java
```
and select Sun Java in the menu that appears.

---

