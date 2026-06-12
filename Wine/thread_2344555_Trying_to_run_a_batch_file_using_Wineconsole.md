---
title: "Trying to run a batch file using Wineconsole"
date: 2016-11-26
forum: Wine
---

### Post by dokhanchi on 2016-11-26
Ok, so I am new to Ubuntu and I've just purchased and instance in Google's Compute that runs Ubuntu. Although I've had problems with using the SSH in there, I've just created a VM box that runs Ubuntu as well (NOT VPS).
I'm trying to run a "run.bat" and a "complier.bat". I've installed wineconsole to manage and run these lines, but I first have to redirect the Run.bat and Compiler.bat to javac.exe and it cannot find it.
In Windows the script is: 
```
"C:\Program Files\Java\jdk1.8.0_45\bin\javac.exe" -d bin -cp lib/*;src src\com\ruseps\GameServer.java
pause
``` This is for Complier.bat

```
@echo offtitle Ruse
"C:/Program Files/java/jdk1.8.0_45/bin/java.exe" -server -Xmx3024m -cp bin;lib/* com.ruseps.GameServer
pause
``` And this is for run.bat

Note, in Windows I just change the "C:/Program Files/java/jdk1.8.0_45/bin/java.exe" to my version of JDK. But in Ubuntu (which I've installed Oracles JDK 8) I redirect to "/usr/lib/jvm/java-8-oracle/bin/javac" but it cannot recognize the directory.
I've also tried "Z:\usr\lib\jvm\java-8-oracle\bin\javac.exe" , "Z:\usr\lib\jvm\java-8-oracle\bin\javac" and "/usr/lib/jvm/java-8-oracle/bin/javac.exe".

Please help!

---

### Post by howefield on 2016-11-26
Thread moved to the "*Wine*" forum.

---

### Post by ian-weisser on 2016-11-26
I do not understand why you are using wine to launch a Java application.
Ubuntu is perfectly capable of running Java without any assistance.

1) Uninstall whatever non-Ubuntu version of java.exe you installed. Completely remove it.
2) Install java properly: See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

3) Run a java application: $ /path/to/java [flags and options] /path/to/application.jar

A properly installed java won't need a path. If you navigate (cd) to the jar directory, then the jar won't need a path either.
Example using a Minecraft server:  $ java &#8211;Xmx1024M -jar minecraft_server.jar nogui

---

### Post by dokhanchi on 2016-11-26
I think my Oracle JDK is correct because here's how i installed it
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update

sudo apt-get install oracle-java8-installer


I think the problem is something else because the compiler and run are both batch files that only need to be directed to javac.exe

---

