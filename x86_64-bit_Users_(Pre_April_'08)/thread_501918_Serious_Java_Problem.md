---
title: "Serious Java Problem"
date: 2007-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Goliath! on 2007-07-15
I have a Java problem on my Dell Inspiron 1501 AMD64 laptop with Ubuntu 7.04.  Please see post [http://ubuntuforums.org/showthread.php?t=501095]("http://ubuntuforums.org/showthread.php?t=501095")

I'm afraid people may ignore my original post because I have it a very flippant title ("Where O Where has my Java Gone?").  I'm really **_*very*_** sorry to cross-post this, but I can't find a way to change the title so people might take me seriously.  (I've learned my lesson: no more  funny business.)

Thanks for any help you might be able to offer!!

---

### Post by Kilz on 2007-07-15
> **Goliath! said:**
> I have a Java problem on my Dell Inspiron 1501 AMD64 laptop with Ubuntu 7.04.  Please see post [http://ubuntuforums.org/showthread.php?t=501095]("http://ubuntuforums.org/showthread.php?t=501095")

I'm afraid people may ignore my original post because I have it a very flippant title ("Where O Where has my Java Gone?").  I'm really **_*very*_** sorry to cross-post this, but I can't find a way to change the title so people might take me seriously.  (I've learned my lesson: no more  funny business.)

Thanks for any help you might be able to offer!!

Ok, I read the post. If you have flock 32 installed by my script you should have java installed if you chose it. Just a few questions, where is java not working? What application dose not see java? Also are you running the 32bit or 64bit version of Feisty?

---

### Post by kuja on 2007-07-15
Try running "sudo apt-get install --reinstall sun-java5-jre". Afterwards, run "sudo update-alternatives --config  java"
Additionally, just incase it still doesn't like it, add the following to the bottom of your ~/.bashrc file:
```
PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/:$PATH
export PATH
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/
export JAVA_HOME
```

Be sure to double check that that path is correct - it may not be, but I reckoned it was a good guess :popcorn:

Afterwards, log out before running the program.

---

### Post by redDEADresolve on 2007-07-16
dude your main problem is using a 64 bit version of ubuntu. Is there any reason your not using a 32 bit version?

---

### Post by Kilz on 2007-07-16
> **redDEADresolve said:**
> dude your main problem is using a 64 bit version of ubuntu. Is there any reason your not using a 32 bit version?

Maybe he doesn't believe the FUD about the 64bit version that even well wishing people who don't know any better keep repeating.

---

### Post by Goliath! on 2007-07-16
Kilz, thanks for your response.  Yes, I'm running Flock32 (installed with your script).  Java works in Flock: if I go to java.com and click on the "Do I have Java" link it tells me:
> Verified Java Version
Congratulations!
You have the recommended Java installed (Version 6 Update 2).  

But when I check the Java version in a terminal I get:
> john@xan2:~$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

As I said in my post, the app I want to run is Freemind.  When I try to run it, it tells me:
> john@xan2:~$ freemind
ERROR:   Your Java virtual machine is neither Sun nor Blackdown,
         =======================================
         FREEMIND WILL MOST PROBABLY *NOT* WORK,
         =======================================
         define JAVACMD, JAVA_BINDIR, JAVA_HOME or PATH in order
         to point to such a VM. See the manpage of freemind(1) for details.

I've posted this question to the Freemind forum; no response yet.

***Note: There is a known bug that Freemind does not work with Java6.  This is what started me down this path: I had Java6 installed & working.  Then I stumbled on the bug with Freemind and Java6 and I started trying to install a different version of Java.***

I'm running 64 bit Feisty.

Thanks for any help!

---

### Post by Goliath! on 2007-07-16
redDEADresolve, thanks for your message.  I'm using Feisty 64 because I specifically want to experiement and learn about the 64 bit version.  Maybe I'll even be able to help debug some problems.

I've read your 1501 blog and I really appreciate all the great info.  I read your posts on 64-bit, but as I said, I really wanted to try it out.  We'll need to get a 64-bit version working eventually; better now than later :)

---

### Post by Goliath! on 2007-07-16
Hi Kuja, thanks for your reply.

I tried your suggestion, but still no joy.

I did the sudo apt-get install --reinstall sun-java5-jre and sudo update-alternatives --config java.  Then here's what I got:
> john@xan2:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
john@xan2:~$ PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin:$PATH
john@xan2:~$ export PATH
john@xan2:~$ echo $JAVA_HOME

john@xan2:~$ JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
john@xan2:~$ export JAVA_HOME
john@xan2:~$ echo $JAVA_HOME
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
john@xan2:~$ java -version
Error: could not open `/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64/jvm.cfg'

jvm.cfg exists in that directory, but it's a symbolic link pointing to /etc/java-1.5.0-sun/jvm.cfg and that file doesn't exist.  The only thing in that directory is:
> john@xan2:/etc/java-1.5.0-sun$ ls -al
total 20
drwxr-xr-x   3 root root  4096 2007-07-14 20:38 .
drwxr-xr-x 121 john john 12288 2007-07-16 21:10 ..
drwxr-xr-x   2 root root  4096 2007-07-14 20:38 security

The only jvm.cfg files I have are:
> john@xan2:/etc/java-1.5.0-sun$ find / -name jvm.cfg -print 2>/dev/null
/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64/jvm.cfg
/usr/lib/j2se/1.4/jre/lib/amd64/jvm.cfg
/usr/lib/j2se/1.4/jre/lib/i386/jvm.cfg
/usr/local/java32/lib/i386/jvm.cfg
/home/john/.Trash/j2re1.4.2/lib/amd64/jvm.cfg

Like I said, I got a bit carried away uninstalling/reinstalling various versions - that's why there are so many different leftovers.

Any ideas?

---

### Post by Kilz on 2007-07-17
I think there is maybe a symlink missing, or messed up please post the results of 

```
ls -la /usr/lib/jvm
```

---

### Post by Goliath! on 2007-07-17
Here's that:
j> ohn@xan2:~$ ls -la /usr/lib/jvm
total 76
drwxr-xr-x   3 root root  4096 2007-07-14 20:38 .
drwxr-xr-x 146 john john 61440 2007-07-15 16:10 ..
lrwxrwxrwx   1 root root    23 2007-07-14 20:38 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.11
drwxr-xr-x   6 root root  4096 2007-07-14 20:38 java-1.5.0-sun-1.5.0.11
-rw-r--r--   1 root root  2153 2007-04-03 11:34 .java-1.5.0-sun.jinfo

None of those links are broken, but as I said before I'm missing jvm.cfg:
> john@xan2:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64$ ls -al | more
total 4668
drwxr-xr-x  7 root root   4096 2007-07-14 20:38 .
drwxr-xr-x 14 root root   4096 2007-07-16 21:02 ..
-rwxr-xr-x  1 root root  23784 2006-12-15 03:09 awt_robot
-rwxr-xr-x  1 root root   6696 2006-12-15 03:08 gtkhelper
drwxr-xr-x  2 root root   4096 2007-07-14 20:38 headless
lrwxrwxrwx  1 root root     27 2007-07-14 20:38 jvm.cfg -> /etc/java-1.5.0-sun/j
vm.cfg
-rw-r--r--  1 root root 542584 2006-12-15 03:08 libawt.so
-rw-r--r--  1 root root 443304 2006-12-15 03:12 libcmm.so
-rw-r--r--  1 root root 199600 2006-12-15 03:06 libdcpr.so
< . . .  more . . . >

That link to jvm.cfg is broken, and I don't have a java5 jvm.cfg anywhere on my machine.
:confused:

---

### Post by Kilz on 2007-07-17
> **Goliath! said:**
> Here's that:
j

None of those links are broken, but as I said before I'm missing jvm.cfg:


That link to jvm.cfg is broken, and I don't have a java5 jvm.cfg anywhere on my machine.
:confused:

I think the easiest way to make sure java5 is installed [is to just go here]("http://packages.ubuntu.com/feisty/libs/sun-java5-jre") and [get this one also]("http://packages.ubuntu.com/feisty/libs/sun-java5-bin") , download the deb, then click on them, let Gdebi reinstall them. Cant hurt to try it. That should also install the config file you are missing.

---

### Post by Goliath! on 2007-07-17
I did exactly as you said: downloaded the 2 .deb files and run them.  Still the same problem.

So I decided to try to try to uninstall everything and try the .deb files again.  Using Synaptic I removed java-common, sun-java5-bin, sun-java5-jre, and j2re1.4.  I searched for everything containing java or jre.  There were a lot of packages of java code used by other apps - I left all those.

Then I went thru the file system at the terminal and deleted everything that looked like java rte or java bin files.  I left stuff like /var/lib/dpkg/info/sun-java6-bin.list and /var/cache/apt/archives/sun-java5-jre_1.5.0-11-1ubuntu2_all.deb (they seem like reference files, not Java itself).

Then I rebooted.  When it came up I greped  ps aux for java and jre just to make sure nothing was running.

THen I re-downloaded those 2 debs (bin and jre) from ubuntu packages and re-run them.  When I go the terminal I get:
> john@xan2:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

NOTE: When I re-ran the .debs I looked at the terminal log and there was a message that the license had already been accepted.  Therefore I must have not cleaned out everything!!!

I looked on sun.java.com and their forums.  Didn't find anything helpful.

I really appreciate your help.  Any other suggestions?

---

### Post by Goliath! on 2007-07-17
By the way, the bin deb had the option of either i386 or amd64.  I chose amd64.  Is that correct?

---

### Post by Kilz on 2007-07-17
> **Goliath! said:**
> I did exactly as you said: downloaded the 2 .deb files and run them.  Still the same problem.

So I decided to try to try to uninstall everything and try the .deb files again.  Using Synaptic I removed java-common, sun-java5-bin, sun-java5-jre, and j2re1.4.  I searched for everything containing java or jre.  There were a lot of packages of java code used by other apps - I left all those.

**Then I went thru the file system at the terminal and deleted everything that looked like java rte or java bin files.  I left stuff like /var/lib/dpkg/info/sun-java6-bin.list and /var/cache/apt/archives/sun-java5-jre_1.5.0-11-1ubuntu2_all.deb (they seem like reference files, not Java itself).**

Then I rebooted.  When it came up I greped  ps aux for java and jre just to make sure nothing was running.

THen I re-downloaded those 2 debs (bin and jre) from ubuntu packages and re-run them.  When I go the terminal I get:


NOTE: When I re-ran the .debs I looked at the terminal log and there was a message that the license had already been accepted.  Therefore I must have not cleaned out everything!!!

I looked on sun.java.com and their forums.  Didn't find anything helpful.

I really appreciate your help.  Any other suggestions?

Just for future reference. It is much safer to uninstall packages with Synaptic/apt, than just deleting files, that way you get everything that was installed.
Im not really sure what to do next.

---

### Post by Goliath! on 2007-07-18
Well, I solved that problem!!

I went into Synaptic and uninstalled gij and gij-4.1.  Now when I check my version I get:
> john@xanadu:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

Hooray!

However, now I notice that OpenOffice is broken.  When I try to start the Writer, it paints about half the window and then stops completely.  I have to force-quit it.

How can I reinstall OO.o on AMD64?

Thanks!!

---

### Post by Kilz on 2007-07-18
> **Goliath! said:**
> Well, I solved that problem!!

I went into Synaptic and uninstalled gij and gij-4.1.  Now when I check my version I get:


Hooray!

However, now I notice that OpenOffice is broken.  When I try to start the Writer, it paints about half the window and then stops completely.  I have to force-quit it.

How can I reinstall OO.o on AMD64?

Thanks!!

Synaptic will let you reinstall it.  :)

---

### Post by Mr_bleu on 2007-07-18
> **redDEADresolve said:**
> dude your main problem is using a 64 bit version of ubuntu. Is there any reason your not using a 32 bit version?

I agree w/ kilz.  No need to bash 64bit Ubuntu.  If you don't like 64bit, read elsewhere.  You're not helping matters.

---

### Post by Goliath! on 2007-07-18
OK, my machine is all better now!!

When I tried to run OO.o from the terminal, I got:
> john@xan2:~$ ooffice -writer 

(process:7682): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7682): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:7682): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7682): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:7682): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7682): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
john@xanadu:~$ 
(process:7682): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7682): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

Even when I uninstalled and re-installed thru Synaptic, I had the same problem.

I did some googling and searching of forums.  I found out errors like this can be caused by a couple of things:
- problems with the spellchecker libhunspell
- some kind of corruption that can be fixed by deleting your ~/.openoffice2 folder.

So I uninstalled all openoffice stuff from Synaptic.  I found that it left ~/.openoffice2 as well as /etc/openoffice and /usr/lib/openoffice/program.  So I removed all 3 of those folders.

I reinstalled OO.o from Synaptic, and voila! 

My machine is happy, and so am I!

Thanks to all who helped.  I very much appreciate this community.

---

### Post by n0deal on 2007-07-26
> **kuja said:**
> Try running "sudo apt-get install --reinstall sun-java5-jre". Afterwards, run "sudo update-alternatives --config  java"


Thanks for the pointer, a couple of my java apps just stopped working mysteriously.  I assume it was an update I installed.  Anyhow, after installing the sun java package as you described and making sure the system was using it (it wasn't) the java apps started working again.

Cheers!

---

