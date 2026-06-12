---
title: "Problem running jUploadr"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by igb on 2007-06-24
I have downloaded jUploadr and et the following error when I try to run it:

```
Starting JUploadr...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Exception in thread "main" java.lang.UnsatisfiedLinkError: /var/home/ian/devel/jUploadr-1.1.2-linuxGTK-i386/lib/libswt-pi-gtk-3232.so: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.dnd.Transfer.registerType(Transfer.java:135)
        at org.eclipse.swt.dnd.TextTransfer.<clinit>(TextTransfer.java:36)
        at org.scohen.juploadr.app.JUploadr.<init>(JUploadr.java:84)
        at org.scohen.juploadr.app.JUploadr.main(JUploadr.java:709)

```

The file exists and has permissions ian.usr. I chmodded lib to 755 in case the files needed to be executable, but that didn't work.

I have sun-java6-jre and ia32-sun-java6-bin  installed.

Any ideas?

Ian.

---

### Post by Kilz on 2007-06-24
> **igb said:**
> I have downloaded jUploadr and et the following error when I try to run it:

```
Starting JUploadr...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Exception in thread "main" java.lang.UnsatisfiedLinkError: /var/home/ian/devel/jUploadr-1.1.2-linuxGTK-i386/lib/libswt-pi-gtk-3232.so: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.dnd.Transfer.registerType(Transfer.java:135)
        at org.eclipse.swt.dnd.TextTransfer.<clinit>(TextTransfer.java:36)
        at org.scohen.juploadr.app.JUploadr.<init>(JUploadr.java:84)
        at org.scohen.juploadr.app.JUploadr.main(JUploadr.java:709)

```

The file exists and has permissions ian.usr. I chmodded lib to 755 in case the files needed to be executable, but that didn't work.

I have sun-java6-jre and ia32-sun-java6-bin  installed.

Any ideas?

Ian.

The error says it cant find "libgtk-x11-2.0.so.0". You say it exists, where did you find it?

---

