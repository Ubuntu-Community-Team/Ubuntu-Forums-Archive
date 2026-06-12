---
title: "installing Java makes OpenOffice unstable"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Oliver W. on 2007-02-13
Hello community!

First off: I have searched and found the [ guide]("https://help.ubuntu.com/community/Java") detailing how to install Java on Ubuntu. I followed its instructions (installing JDK) and it worked near perfectly.

Near.

When I try to finish the installation up with
 sudo update-java-alternatives -s java-1.5.0-sun
I get the following output:

Using `/usr/lib/jvm/java-1.5.0-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry' .
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

Note the last few lines. They're all related to amd64.

Anyway, I didn't think anything of it at first (it might be related to Firefox-plugins, I don't know though I've checked the howto by Kilz as well (currently trying to fix another problem before I try FF32-bit)).
I was anxious to see if OpenOffice would be using the JRE by default now, so I start Writer, go to Tools > Options and select "Java" under "OpenOffice.org". When I get there, the program becomes unresponsive and I have to kill it.

Anyone know what's up with that? Or what those last errormessages mean?

Thanks!

---

### Post by Kilz on 2007-02-13
> **Oliver W. said:**
> Hello community!

First off: I have searched and found the [ guide]("https://help.ubuntu.com/community/Java") detailing how to install Java on Ubuntu. I followed its instructions (installing JDK) and it worked near perfectly.

Near.

When I try to finish the installation up with
 sudo update-java-alternatives -s java-1.5.0-sun
I get the following output:

Using `/usr/lib/jvm/java-1.5.0-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry' .
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1 .5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

Note the last few lines. They're all related to amd64.

Anyway, I didn't think anything of it at first (it might be related to Firefox-plugins, I don't know though I've checked the howto by Kilz as well (currently trying to fix another problem before I try FF32-bit)).
I was anxious to see if OpenOffice would be using the JRE by default now, so I start Writer, go to Tools > Options and select "Java" under "OpenOffice.org". When I get there, the program becomes unresponsive and I have to kill it.

Anyone know what's up with that? Or what those last errormessages mean?

Thanks!

The error messages are for the browser plugin.

---

### Post by phossal on 2007-02-13
Why would you install Java using a package? Why not download it directly from SUN?

---

### Post by Oliver W. on 2007-02-13
> **phossal said:**
> Why would you install Java using a package? Why not download it directly from SUN?Because it is the suggested way of doing things. That and the reason that many beginners complain when they try to do it by downloading directly from the website: they are either directed to 32-bit versions or have heaploads of trouble trying to install it. The more positive posts are always praising the ubuntu wiki.

Thanks Kilz to clarify that. But do you have any idea why OpenOffice becomes unresponsive when accessing the Java-options?
Also, do I have a guarantee that JDK (and JRE) were successfully installed? I could check it with Eclipse perhaps (though I don't know where to look).

---

### Post by John Jason Jordan on 2007-02-13
> **Oliver W. said:**
>  ... I was anxious to see if OpenOffice would be using the JRE by default now, so I start Writer, go to Tools > Options and select "Java" under "OpenOffice.org". When I get there, the program becomes unresponsive and I have to kill it.
I note you are using Dapper. When I had Dapper with OOo 2.0.2 I had the same problem. However, I think you need to be really, really patient. I discovered one day that if I just left it alone eventually OOo would display the Java that I had installed. For some reason it takes OOo 2.02 a long time to find the Java. Try it again and go get a cup of coffee while it thinks about it.

I have since upgraded to Edgy and the upgrade also installed OOo 2.0.4. I note that OOo now finds the Java much faster, although you still have to wait a few moments before it appears.

---

### Post by Oliver W. on 2007-02-13
> **John Jason Jordan said:**
> I note you are using Dapper. When I had Dapper with OOo 2.0.2 I had the same problem. However, I think you need to be really, really patient. I discovered one day that if I just left it alone eventually OOo would display the Java that I had installed. For some reason it takes OOo 2.02 a long time to find the Java. Try it again and go get a cup of coffee while it thinks about it.

I have since upgraded to Edgy and the upgrade also installed OOo 2.0.4. I note that OOo now finds the Java much faster, although you still have to wait a few moments before it appears.
I love these forums. :)
 Remember kids, patience is a virtue.

Thanks John Jason Jordan, waiting quite a bit longer (several minutes) showed me the options. However, here's the strange part: it still uses the Free Software Foundation JRE version 1.4.2 and gives me an error message when I try to add 
/usr/lib/jvm/java-1.5.0-sun/jre

Here's the error message:
The folder you selected does not contain a Java runtime environment.
Please select a different folder.

Here's what's in that folder:
bin        lib      man     THIRDPARTYLICENSEREADME.txt
COPYRIGHT  LICENSE  README  Welcome.html

My local Ubuntu-mentor (every beginner should have one :) ) doesn't even know.

---

### Post by phossal on 2007-02-13
I feel like a parent trying to give a kid some subtle advice, so he or she would take it, consider it his  or her own idea, and run with it. Of course, the typical reaction is a complete dismissal at best, and a rebuke for being out of touch at worst. A package automates some steps, but it doesn't release you from the personal responsibility (especially when it doesn't work) of administrating your system. The configuration has to be done by *someone.* I'm willing to contribute, if you think I might be valuable.

---

### Post by Oliver W. on 2007-02-13
Phossal, the reason I dismissed your idea is because I like the way the packages integrate with the desktop. However, I'm not an ignorant lout and will gladly try an alternative if the first option does not succeed (as is my case).

I've just read your howto and will try it (with 64 bit packages, unlike your howto). However I'm rather reluctant, because I not only have Eclipse pre-installed with Synaptic, but BlueJ ("by hand") as well (and Maple10 of which the user interface is written in Java too) and am worried it might mess things up. I'm also asking myself if the Update Manager will also update the JDK (and JRE...) automatically when a new version comes out.

I also wonder: what have I been downloading with Synaptic then? The JDK (with its dependencies) took quite a while to download and all this is for nothing? I just don't get why it won't work with Synaptic.

As you can see, I still have a lot of questions and am very interested in any answers you can provide :)

---

### Post by phossal on 2007-02-13
What is the output to each of the following commands:
```
java -version
sudo update-alternatives --display java
ls -l $(type -path -all java)
```

Maybe post the output?

---

### Post by Oliver W. on 2007-02-14
Thanks for helping me. I really appreciate it.

```
oliver@cinnamoon:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)


oliver@cinnamoon:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1041
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/jre/bin/java.


oliver@cinnamoon:~$ ls -l $(type -path -all java)
lrwxrwxrwx 1 root root 22 2006-09-16 13:40 /usr/bin/java -> /etc/alternatives/java
lrwxrwxrwx 1 root root 22 2006-09-16 13:40 /usr/bin/X11/java -> /etc/alternatives/java
```
(added linebreaks to increase the readability)


That's the output of the given commands.

---

