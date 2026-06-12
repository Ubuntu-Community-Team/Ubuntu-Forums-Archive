---
title: "Java doesn't run properly on Ubuntu 64-bit."
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by looi76 on 2009-01-08
Hi, Java doesn't seem to run properly on Ubuntu. I usually play [Spades on Yahoo! Games]("http://games.yahoo.com/games/login2?page=sp&ss=1") which requires Java. Is there a solution for this problem?

Yahoo! Spades on Ubuntu:
[[IMG]http://img211.imageshack.us/img211/9198/ubuntujavaxm5.th.png[/IMG]](http://img211.imageshack.us/my.php?image=ubuntujavaxm5.png)

Yahoo! Spades on Windows XP:
[[IMG]http://img522.imageshack.us/img522/9606/windowsxpjavaug1.th.png[/IMG]](http://img522.imageshack.us/my.php?image=windowsxpjavaug1.png)

---

### Post by Sef on 2009-01-08
What version of Java did you install?

---

### Post by looi76 on 2009-01-08
Sun Java 6 Runtime, I downloaded it from [http://java.sun.com]("http://java.sun.com/").

---

### Post by Kilz on 2009-01-08
> **looi76 said:**
> Sun Java 6 Runtime, I downloaded it from [http://java.sun.com]("http://java.sun.com/").

Thats the problem, the 64bit java from sun doesnt have a plugin. You can look at the java sticky for all the links to the various working plugins. I also have a setup script in the flash sticky for the new 64bit Sun Java beta.

---

### Post by hyperdude111 on 2009-01-08
I use the ubuntu-restricted extras command and have never had any problems with any codecs. Try that?

---

### Post by jespdj on 2009-01-08
> **hyperdude111 said:**
> I use the ubuntu-restricted extras command and have never had any problems with any codecs. Try that?
That will not work.

There is currently not a 64-bit Java browser plug-in from Sun. It's coming in the next update of Sun Java 6. There's currently a prerelease version of it, which is ofcourse not yet in the Ubuntu repository. Read: [HOWTO: install 64-bit java plugin](http://ubuntuforums.org/showthread.php?t=1032338) and [[SOLVED] 64 bit Sun Java Browser Plugin](http://ubuntuforums.org/showthread.php?t=1011899) if you want to install it.

There's also the IcedTea plugin which works with OpenJDK Java.

Read: [Java on 64-bit Systems](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by ndale686738 on 2009-01-08
IcedTea works great with x64.

sudo apt-get install icedtea6-plugin
sudo update-java-alternatives -s java-6-openjdk

---

### Post by looi76 on 2009-01-11
I have tired IcedTea but I didn't work for me at all! I even tired this tutorial [http://ubuntuforums.org/showthread.php?t=1019314](http://ubuntuforums.org/showthread.php?t=1019314) and still Java works like crap!

Isn't there any solutions for using Java on Firefox in Ubuntu 64-bit?! :(

---

### Post by Kilz on 2009-01-11
> **looi76 said:**
> I have tired IcedTea but I didn't work for me at all! I even tired this tutorial [http://ubuntuforums.org/showthread.php?t=1019314](http://ubuntuforums.org/showthread.php?t=1019314) and still Java works like crap!

Isn't there any solutions for using Java on Firefox in Ubuntu 64-bit?! :(

[Here is the list of java solutions.]("http://ubuntuforums.org/showthread.php?t=774956")

---

