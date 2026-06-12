---
title: "Java problems"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by amirseg on 2007-12-07
Hi,
I am using Ubuntu 7.10 64 bit on AMD athlon, and my problem (as you can all guess...) is runing java applets.
Some work, some not... I got a certain program that I use (an emulator for the univercity) which use java, and it works just fine on 32bit Ubuntu and wundows, but for some reason does not on the 64bit.
The link to download the software is [http://www1.idc.ac.il/tecs/software/tecs-software-suite-2.5.zip](http://www1.idc.ac.il/tecs/software/tecs-software-suite-2.5.zip)

and as you can see when opening it the are files which are .sh for linux.
What hapen is that runing each one of them just open a white window and thats it.

If it help. I add the version of my installed java:

[I]amirseg@amirseg-PC:~$ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
[/I]

I hope you could help me.

Amir

---

### Post by Kilz on 2007-12-07
> **amirseg said:**
> Hi,
I am using Ubuntu 7.10 64 bit on AMD athlon, and my problem (as you can all guess...) is runing java applets.
Some work, some not... I got a certain program that I use (an emulator for the univercity) which use java, and it works just fine on 32bit Ubuntu and wundows, but for some reason does not on the 64bit.
The link to download the software is [http://www1.idc.ac.il/tecs/software/tecs-software-suite-2.5.zip](http://www1.idc.ac.il/tecs/software/tecs-software-suite-2.5.zip)

and as you can see when opening it the are files which are .sh for linux.
What hapen is that runing each one of them just open a white window and thats it.

If it help. I add the version of my installed java:

[I]amirseg@amirseg-PC:~$ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
[/I]

I hope you could help me.

Amir

First off, there is no sun java for 64bit Ubuntu or linux in general. Java 7 (currently under development) will have a 64bit plugin, but thats months away. There are a few plugins that are open source java like the icedtea and Blackdown in the repositories. But they dont work on every site. But there is a solution if they dont work for you ( it looks like you have tried them) .[Click here for my 32bit browser and plugins script.]("http://ubuntuforums.org/showthread.php?p=1174435") It will install 32bit firefox , java, flash, and mplayer plugins.

---

### Post by amirseg on 2007-12-08
Hi.
Thanks for the answer, but I could not understand if it can solve my problem. The apps I am runing are not in the broser but "stand-alone".

will that solve the "white-screen" problem? anyone know why it happen? is there any log file I can open after running them to se what happened?

Amir

---

### Post by sjatkins on 2007-12-27
> **Kilz said:**
> First off, there is no sun java for 64bit Ubuntu or linux in general. Java 7 (currently under development) will have a 64bit plugin, but thats months away. There are a few plugins that are open source java like the icedtea and Blackdown in the repositories. But they dont work on every site. But there is a solution if they dont work for you ( it looks like you have tried them) .[Click here for my 32bit browser and plugins script.]("http://ubuntuforums.org/showthread.php?p=1174435") It will install 32bit firefox , java, flash, and mplayer plugins.

That is not so any longer as I just downloaded one today for linux amd64.  In any case there have been recurring white screen and other problem with java under compiz and beryl for some time now.  People are being told to have a nice window manager or run java apps but not both.  This is completely unacceptable and a huge turd in the ubuntu linux punch bowl.  Is this being addressed with full seriousness?  It certainly should be.   AFAIK the source for java is now out so a real fix of these problems should be possible.

---

### Post by kingkoopa on 2007-12-28
Java 1.5 was Java 5, right? I'm really in no position to give advice (I'm still working on my wireless issue in the Gutsy x64 live CD lol) but I would suggest that you try downloading and installing Java 6, the latest version of Java. You can get it at [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by Kilz on 2007-12-28
> **sjatkins said:**
> That is not so any longer as I just downloaded one today for linux amd64.  In any case there have been recurring white screen and other problem with java under compiz and beryl for some time now.  People are being told to have a nice window manager or run java apps but not both.  This is completely unacceptable and a huge turd in the ubuntu linux punch bowl.  Is this being addressed with full seriousness?  It certainly should be.   AFAIK the source for java is now out so a real fix of these problems should be possible.

You have not downloaded a 64bit version of **Sun** java. Please reread my post you quoted. You may have some java plugin. My guess would be icedtea ( a gcj-compat plugin) that is not made by Sun and has problems on some sites, or Blackdown ( an ancient plugin thats even worse). The next version of Sun Java (7), which is in development will have a real Sun Java plugin. Its not out right now.
The original poster said they tried a gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5) the gcj-compat plugin. That it didnt work, so I gave them an option of installing a real 32bit Sun Java plugin that may work for them.

> **kingkoopa said:**
> Java 1.5 was Java 5, right? I'm really in no position to give advice (I'm still working on my wireless issue in the Gutsy x64 live CD lol) but I would suggest that you try downloading and installing Java 6, the latest version of Java. You can get it at [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Sun Java 6 does not have a 64bit plugin. Java 7, still under development will have a 64bit plugin.

---

### Post by kingkoopa on 2007-12-28
But what he's trying to run isn't an applet (which is just a Java class embedded in a Web page IIRC), it's a stand-alone Java application (or Java program). Lookee here, the CPU emulator runs in its own window. So I don't think the Java browser plug-in is needed. The readme file itself says that all that is needed is the JRE, or the JDK (which includes the JRE) if you're also going to do Java programming.

---

### Post by Kilz on 2007-12-28
> **kingkoopa said:**
> But what he's trying to run isn't an applet (which is just a Java class embedded in a Web page IIRC), it's a stand-alone Java application (or Java program). Lookee here, the CPU emulator runs in its own window. So I don't think the Java browser plug-in is needed. The readme file itself says that all that is needed is the JRE, or the JDK (which includes the JRE) if you're also going to do Java programming.

Ok, if all he wants is just to run a applet on his computer, not one in a web page it may be possible.  But imho most people who need java will most likely also need the browser plugin.

---

