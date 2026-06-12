---
title: "Azureus on Gutsy x64"
date: 2008-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by iSplicer on 2008-03-29
Hey all!

It just wont work. Starting it will just cause it to crash and exit. When I start from the terminal, this is what i get:

```
isplicer@PEGASUS-III:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b2bb7ee1e11, pid=7327, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/isplicer/.azureus/hs_err_pid7327.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
isplicer@PEGASUS-III:~$ 

```

Im sure its Java conflicting with my x64 system, can anyone please help? If I get past this problem, I would like to continue using Gutsy x64!

Thanks all!

---

### Post by iSplicer on 2008-03-29
No problem, the kind people at the IRC helped me fix this. I just removed "icedtea" from my system, and ran this command:

```
sudo apt-get install sun-java6-jre
```

---

### Post by chajuram on 2008-03-30
Wow! This solution worked great for me. Does this mean that I will be missing out on something that uses java-7? 

Thanks

Chajuram

---

### Post by Thelasko on 2008-03-31
Get rid of IcedTea you say?  I've spent forever trying to get IcedTea to install and it still doesn't work.  I'll have to try Sun Java.  I know it's not open source but, if it works...
:-$

---

### Post by Thelasko on 2008-04-01
That didn't work at all.  Sorry, Java is still broken on my machine.:(

---

### Post by SyberKowboy on 2008-04-02
I'm having the same issue. Installed IceTea hoping to get it working for the web and Azureus died on me. Uninstalled Icetea and reconfigured Java but no dice. Still not working. Any ideas?

---

### Post by prostar on 2008-04-03
You can have multiiple javas installed.  For me, the version of Azureus I have(2.5.0.4) needed java 6 from sun.  Start azureus in a terminal and see what it says as the first line (using Java-x.y.z).  If it's not the one you meant you can simply define a variable called "AZUREUS_JAVA" and set it to the one you need.  In my case:

```
export AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
azureus
```

FYI to see what version is used by most programs (default) use:
```
java -version
```

Good luck!

---

### Post by Thelasko on 2008-04-03
Unfortunately none of the versions of Java work for me.  It's quite frustrating.

---

### Post by prostar on 2008-04-03
Did the "AZUREUS_JAVA" variable actually change which version it was trying to use?  In the terminal you should see it say something about overriding java with the info from the variable.  Also can anything else use java?  Try limewire, or something else that would give java a descent test.  Someone that knows more about java should chime in, because I know it can get to be quite a mess.

---

### Post by Terminating.proprietary on 2008-04-07
> **prostar said:**
> You can have multiiple javas installed.  For me, the version of Azureus I have(2.5.0.4) needed java 6 from sun.  Start azureus in a terminal and see what it says as the first line (using Java-x.y.z).  If it's not the one you meant you can simply define a variable called "AZUREUS_JAVA" and set it to the one you need.  In my case:

```
export AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
azureus
```

FYI to see what versioJAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
azureusn is used by most programs (default) use:
```
java -version
```
JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
azureus
Good luck!

This is exactly what you type to define which java to use? with the azureus at the end???

This is what I have tried.... I have not yet got a message saying anything about the variable being changed
[CODE]brian@brian-laptop:~$ export AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
brian@brian-laptop:~$ AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
brian@brian-laptop:~$ sudo export AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java
sudo: export: command not found
brian@brian-laptop:~$ sudo AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/javasudo: AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java: command not found
brian@brian-laptop:~$ [CODE]
I will try typing it with azureus at the end

---

### Post by Terminating.proprietary on 2008-04-07
OK, I got it it had changed just no conformation, here is some confirmation
[CODE]brian@brian-laptop:~$ azureus
Java Runtime specified using AZUREUS_JAVA environment
Using Java: /usr/lib/jvm/java-6-sun/jre/bin/java
[CODE]

---

### Post by Terminating.proprietary on 2008-04-07
OK little issue.

[CODE]brian@brian-laptop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java[CODE}

As soon as I closed the terminal and tryed to open it via GUI it crashed so I went back and tried it in the terminal and guess what, it defaulted back to iced tea java. How do I change the variable permanently?

---

