---
title: "netbeans startup error in 64bit"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by rbprogrammer on 2008-03-17
ok, so basically i cannot run netbeans.  i installed netbeans from synaptic and all its sun-java-5-XX stuff that it needed.  but when i go to run netbeans i just get a blank gray screen.  and when i run from the terminal i do not get any output but still just that gray netbeans screen.

did a little googling and what not and found that i need to put this line in a few places:
```

export AWT_TOOLKIT=MToolkit

```
i tried that in:
[LIST]
[*]/etc/profile
[*]~/.bashrc
[*]/usr/share/netbeans/5.5/bin/netbeans  (or whatever that path to the script is)
[/LIST]

i tried all three places with the export thing, but when i run netbeans from the terminal i get this error output:
```

$ netbeans 

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at javax.swing.UIManager.initialize(UIManager.java:1262)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1245)
        at javax.swing.UIManager.getDefaults(UIManager.java:556)
        at javax.swing.filechooser.FileSystemView.getFileSystemView(FileSystemView.java:63)
        at org.openide.filesystems.FileUtil.<clinit>(FileUtil.java:64)
        at org.netbeans.core.startup.TopLogging.printSystemInfo(TopLogging.java:187)
        at org.netbeans.core.startup.TopLogging.<init>(TopLogging.java:112)
        at org.netbeans.core.startup.CLIOptions.initialize(CLIOptions.java:205)
        at org.netbeans.core.startup.Main.start(Main.java:292)
        at org.netbeans.core.startup.TopThreadGroup.run(TopThreadGroup.java:96)
        at java.lang.Thread.run(Thread.java:595)
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at javax.swing.UIManager.initialize(UIManager.java:1262)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1245)
        at javax.swing.UIManager.getDefaults(UIManager.java:556)
        at javax.swing.filechooser.FileSystemView.getFileSystemView(FileSystemView.java:63)
        at org.openide.filesystems.FileUtil.<clinit>(FileUtil.java:64)
        at org.netbeans.core.startup.TopLogging.printSystemInfo(TopLogging.java:187)
        at org.netbeans.core.startup.TopLogging.<init>(TopLogging.java:112)
        at org.netbeans.core.startup.CLIOptions.initialize(CLIOptions.java:205)
        at org.netbeans.core.startup.Main.start(Main.java:292)
        at org.netbeans.core.startup.TopThreadGroup.run(TopThreadGroup.java:96)
        at java.lang.Thread.run(Thread.java:595)

```

i know netbeans/java/(whatever it is) has issues with repainting its windows with compiz.  but i have the default installed compiz running.  no extra "goodies".  

whats going on? how do i get netbeans to run? putting the export line in the netbeans startup script worked in 32bit gutsy, but now i cannot get it to work in 64bit gutsy

---

### Post by clanky on 2008-03-20
I had the same problem when I tried to run netbeans with desktop effects enabled, there are answers out there if you do a forums search for netbeans.

There is code that can be entered to allow netbeans to run with desktop effects enabled, but I just switched off the advanced desktop effects and it ran fine.

---

