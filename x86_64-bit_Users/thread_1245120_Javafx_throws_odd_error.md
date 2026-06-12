---
title: "Javafx throws odd error"
date: 2009-08-20
forum: x86 64-bit Users
---

### Post by eram on 2009-08-20
Ok, simply stated, javafx isn't working on my system. However, I don't even know if it's installed and just not working properly, or if it's not installed at all. Either way, I'm lost. :D

I'm running Ubuntu 9.04 64-bit, and I can develop/run normal java just fine, but when I try to go to [http://javafx.com/samples](http://javafx.com/samples) and run any of those, that blue ring just keeps spinning and nothing ever happens. When I enable debugging in java, I get the error message that is shown in my attached image. The text file behind the error window is what I get when I click Details.

So what do you think? Can you help me get this working? Thanks!

Edit: After trying another javafx app on another site, I'm suspicioning that javafx is not installed. But last I heard, javafx came packaged with the jre 6.10 and up. I'm running 6.14.

---

### Post by anthw27 on 2009-08-20
I Tested it and I got a Error on the digital signature, strange but I dont work with Java much either. I would see if theres any thing on the site worth reading in case their are dependencies, however having said that the 64bit Java is still in beta so their may be bugs.

Dont forget to check this sticky for more on java.

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by eram on 2009-08-21
Yeah, it very well could be due just to the fact that I'm running 64-bit. But at the same time, the standard java works just fine for me. For example, this app runs perfectly for me: [http://www.falstad.com/fourier/](http://www.falstad.com/fourier/)

Strange...

---

### Post by anthw27 on 2009-08-21
Might just be that site..bump

---

### Post by eram on 2009-08-22
You mean a problem with the javafx site? I don't think so because when I go to other non related sites and try to to run their javafx apps, they don't work either.

---

### Post by int2ag0n on 2009-10-25
When i had OpenJDK and firefox 3.0.14 the applets used to run (extremely slow however). After unistalling openjdk and started using sun's java6 64bit then every javafx/java applet complained that there isn't any suitable java installed to run the applets. Now i am using firefox 3.5.5pre(Shiretoko) with sun's java and  i always get exception (also in galeon and epiphany , so not a firefox problem as i thought at first) :

```
load: class com.sun.javafx.runtime.adapter.Applet not found.
java.lang.ClassNotFoundException: com.sun.javafx.runtime.adapter.Applet
	at sun.plugin2.applet.Plugin2ClassLoader$2.run(Plugin2ClassLoader.java:679)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.applet.Plugin2ClassLoader.findClassHelper(Plugin2ClassLoader.java:633)
	at sun.plugin2.applet.JNLP2ClassLoader.findClass(JNLP2ClassLoader.java:242)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:445)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.ClassNotFoundException: com.sun.javafx.runtime.adapter.Applet
```

The strange thing is that the same javafx applets i download from suns sample javafx apps site ([http://www.javafx.com/samples/](http://www.javafx.com/samples/)) and load them in Netbeans are running flawlessly (extremely fast) with the current configuration. 

Please respond if you came up with a solution.

---

