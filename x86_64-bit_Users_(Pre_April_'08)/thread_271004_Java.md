---
title: "Java?"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-10-04
I want to install software.  I'm new so go slow.  I have DD 64bit 6.06.

I need new software but before I do it says install Java.

[http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp)

But at that link if I click on instructions it says Radhat and Suse only.  Does Ubuntu not support Java?  And whay is there a Linux64 and a Linux64 RPM?  WHat is RPM?

Thanks,
Confusimo

---

### Post by kuja on 2006-10-04
RPM is a packaging format that some Linux distributions use. Ubuntu uses a different one, Debians package format. Anyhow, the easiest way to install the java runtime environment is to install the "sun-java5-jre" package. It resides in Ubuntu's multiverse repository.

---

### Post by xstaticxgpx on 2006-10-04
Confusimo: go to system > administration > software properties. Select 6.06-LTS (_Source_) and then click add. Check all the boxes (Multiverse, Universe, etc) then click OK.

Then go to system > administration > synaptic package manager, click the refresh buttom on the left side, then search for "java" and right-click > install sun-java5-jre, etc.

Also if you want support in firefox post back and I'll explain the way i did it without scripts/blackhawk

---

### Post by confusimo on 2006-10-04
Ya, I found it in Add and Remove Programs last night thanks.

---

### Post by TooRight on 2006-10-04
I finally got it installed on my own system, and enabled, but no sites are recognizing it as being on my machine :(

Could I be sym-linking it to firefox wrong?

---

### Post by kuja on 2006-10-04
If you want to use java applets, you'll need to install the ia32-sun-java5-bin package as well, and copy the plugin file to your browser directory - granted, you can only use this 32-bit java plugin with a 32-bit browser.

---

### Post by TooRight on 2006-10-04
I'm trying to install java to know how to do it on a friend's machine... he's a pogo addict...32 bit? Umm...we're using firefox 1.5.0.7

---

### Post by kuja on 2006-10-04
64-bit firefox 1.5.0.7, or 32-bit firefox 1.5.0.7?

64-bit would be installed by default, a 32-bit browser would have to be installed manually.

If you need a 32-bit browser with the java plugin working, you could try the program that is the subject of [this thread.](http://www.ubuntuforums.org/showthread.php?t=266290) A program of my own design, written to handle such problems.

---

### Post by russianpirate on 2006-10-05
I was just wondering, why not use Blackdown Java2 1.4? It has a 64-bit mozilla plugin and it actually has better performance than Sun's crap!

Got this from the file list of Blackdown J2RE1.4:
```

...
usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so
...

```

---

### Post by JGuru on 2006-10-05
It's better to install Sun's Java JRE 1.5 .Since Sun's Java is the reference
 implementation of Java. Even if you install 64-bit Java JRE, the Java Plugin
 is 32-bit!! So it won't work!!!

---

### Post by russianpirate on 2006-10-05
actually no, blackdown's jre has 64-bit plugin

[http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html](http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html)

> 
64-bit build of Mozilla 1.0 or newer (needed only for the Java Plug-In)

read my post above as well it has a amd64 version of the plugin!

and like i said blackdown is much faster (and better supported for linux):

[http://www.ics.muni.cz/~makub/java/speed.html](http://www.ics.muni.cz/~makub/java/speed.html)

---

### Post by Jonnycat26 on 2006-10-07
> **russianpirate said:**
> actually no, 
and like i said blackdown is much faster (and better supported for linux):


Sun's java used to be (I can't say that it still is) Blackdown's java with some sanity added.

---

### Post by russianpirate on 2006-10-07
what do u mean with sanity?

---

### Post by russianpirate on 2006-10-08
anyway here's a screenshot of me (even though im using edgy) using java1.4 by blackdown on 64-bit firefox 2.0

[[IMG]http://img172.imageshack.us/img172/4743/amd64blackdownfg7.th.png[/IMG]](http://img172.imageshack.us/my.php?image=amd64blackdownfg7.png)

---

### Post by Jonnycat26 on 2006-10-08
More important...  Blackdown does not yet support Java 5 (JDK 1.5), which adds a lot of nifty stuff to the language, and is generally faster.

Until they do, you're better off using Sun Java, especially for things like Azureus.

---

### Post by russianpirate on 2006-10-08
> **Jonnycat26 said:**
> More important...  Blackdown does not yet support Java 5 (JDK 1.5), which adds a lot of nifty stuff to the language, and is generally faster.

Until they do, you're better off using Sun Java, especially for things like Azureus.

the only thing i use java for is firefox (in linux at least) and 1.5 is planned to be released shortly :D

---

### Post by Lonthong on 2007-02-04
> **russianpirate said:**
> I was just wondering, why not use Blackdown Java2 1.4? It has a 64-bit mozilla plugin and it actually has better performance than Sun's crap!

Got this from the file list of Blackdown J2RE1.4:
```

...
usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so
...

```

Hi Russianpirate, can you explain how to get Java working with 64bit firefox v2???
I just did a fresh install of Edgy. I also installed Blackdown Java with no problems. There are symlinks in my mozilla & firefox plugins directory. Also about:plugins confirmed that as well.
However, everytime i visit a site with Java applet & moving mouse onto it will just crash Firefox.
Would really appreciate for yr help......

I before ran Dapper &used Kilz howto for 32bit firefox & Java was running with no problem

---

### Post by phossal on 2007-02-04
> **Lonthong said:**
>  can you explain how to get Java working with **64bit firefox**
Is that possible?

> **Lonthong said:**
> 
I before ran Dapper &used Kilz howto for **32bit firefox & Java** was running with no problem
Exactly

---

### Post by Lonthong on 2007-02-04
> **phossal said:**
> Is that possible?

It is indeed possible.
After searching & googling ups and downs, I finally managed to get Black down Java working with Firefox 64bit.
Besides following the official guide to install:
sudo apt-get install j2re1.4 j2re1.4-mozilla-plugin
You also have to install libxp
In my case I already had libxp6 installed. Re installing solved my firefox from crashing

Just one hour ago, I followed another howto for installing flash with ndiswrapper that went with no problem.

I know have firefox 64bit with Java & flash enabled...........

---

### Post by phossal on 2007-02-04
> **Lonthong said:**
> It is indeed possible.
After searching & googling ups and downs, I finally managed to get Black down Java working with Firefox 64bit.
Besides following the official guide to install:
**sudo apt-get install j2re1.4 j2re1.4-mozilla-plugin**
You also have to install libxp
In my case I already had libxp6 installed. Re installing solved my firefox from crashing

Just one hour ago, I followed another howto for installing flash with ndiswrapper that went with no problem.

I know have firefox 64bit with Java & flash enabled...........

Why would you pull outdated packages?

---

### Post by Lonthong on 2007-02-04
> **phossal said:**
> Why would you pull outdated packages?

Those are the version available from repo.
Mind you, I am talking about blackdown Java, not Sun Java

---

### Post by Lonthong on 2007-02-05
My excitement is too soon unfortunately.
Java is still crashing Firefox even after 2nd time reinstallation of libxp6

---

### Post by phossal on 2007-02-05
I know it's not a popular stance in many places, but I believe 32bit Ubuntu is still the right choice for me and my AMD64. Problem free for *months*. I haven't shut my computer off in a *week*, and I do a bunch of software development, play chess, use applet and flash plugins. It's a *dream.* :) My wireless hardware works *very well* under 32bit, yet it isn't even an option in 64.

---

### Post by m2.g5ru6y7s on 2007-02-23
> **russianpirate said:**
> I was just wondering, why not use Blackdown Java2 1.4? It has a 64-bit mozilla plugin and it actually has better performance than Sun's crap!

Got this from the file list of Blackdown J2RE1.4:
```

...
usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so
...

```
Because this site only works with sun's JAVA:

[http://www.forexpf.ru/_quote_show_/java/](http://www.forexpf.ru/_quote_show_/java/)

---

### Post by Kilz on 2007-02-23
> **m2.g5ru6y7s said:**
> Because this site only works with sun's JAVA:

[http://www.forexpf.ru/_quote_show_/java/](http://www.forexpf.ru/_quote_show_/java/)

Ummmmmm I only have Blackdown 1.4 installed. Take a look at the screenshot.

---

### Post by m2.g5ru6y7s on 2007-02-24
> **Kilz said:**
> Ummmmmm I only have Blackdown 1.4 installed. Take a look at the screenshot.

Thank you very much. Actually I had not tried it yet:) 
It's bye bye for Sun from now on.
Great

---

