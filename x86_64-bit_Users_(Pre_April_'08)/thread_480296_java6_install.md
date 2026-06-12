---
title: "java6 install?"
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-06-21
can someone please point me to a how to to install java6 (or 5) on 64bit feisty 7.04?

---

### Post by Kilz on 2007-06-21
> **kzm. said:**
> can someone please point me to a how to to install java6 (or 5) on 64bit feisty 7.04?

At present there are no howto's for installing a java plugin safely into the 64bit browser. The only one available is the java-gcj-compat-plugin plugin, it is a HUGE security risk! 
Per the Ubuntu [Java]("https://help.ubuntu.com/community/Java") page

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that** the plugin currently runs [COLOR="Red"]with no security[/COLOR] manager**. This means that applets you load can do anything a java application that you download and run can do. Be **very** careful which applets you run.

If there is an applet that will install a rootkit, it will let it. If there is a applet that will reformat your drive, it will let it.

You may need to install the 32bit Firefox if you need java.

---

### Post by kzm. on 2007-06-21
hm.. i understand. 
on my ubuntu 32bit install i was developing little programs in java5. i would like to do this again on my 64bit install but i am still confused about the 32-64bit transition..  can you tell me some more about this, if you you know, and also how to install java5, as ubuntu installs 1.4.

---

### Post by kuja on 2007-06-21
sudo apt-get install sun-java6-jre

(or 5, just change the 6 with a 5 if you want five instead, and if you're planning to do some development, use jdk instead of jre)

For the 32-bit version (if you need it, and the browser plugin (which will only work in 32-bit browsers)) then install ia32-sun-java6-bin

---

### Post by Kilz on 2007-06-21
> **kzm. said:**
> hm.. i understand. 
on my ubuntu 32bit install i was developing little programs in java5. i would like to do this again on my 64bit install but i am still confused about the 32-64bit transition..  can you tell me some more about this, if you you know, and also how to install java5, as ubuntu installs 1.4.

The [java5]("http://packages.ubuntu.com/feisty/devel/sun-java5-jdk") and [java6]("http://packages.ubuntu.com/feisty/devel/sun-java6-jdk") jdk are in the repos.  Im sorry I cant give you much more than that, I have never done java development.

---

### Post by incubus on 2007-06-22
For development you actually want the JDK counterpart, right?

```

$ sudo apt-get install sun-java6-jdk

```

It works pretty well.  I tested it with eclipse* and everything works flawlessly, although I'm not a Java or eclipse fan myself.

You may need to run:
```

$ sudo update-alternatives --config java
$ sudo update-alternatives --config javac

```

Make sure everything is working with:
```

$ java -version
$ javac -version

```

And as somebody pointed out above, this won't give you the browser plugin.  But you can safely install both 64 bit and 32 bit java environments.  Just follow Kilz instructions.

incubus

(*) In the case of eclipse, I usually download the latest version directly from their website, instead of using the one in the repositories.  Not very elegant, I know, but in my experience I had less trouble this way.

---

### Post by Unterseeboot_234 on 2007-06-22
The issues I've had with java pertain to paths and I say this from use of NetBeans, a java IDE. Within NetBeans the IDE keeps the "long" version of the path to your JRE and your JDK. If you are having problems doing ```
javac 
```or ```
java
``` from a terminal prompt, try:

```
javac /home/userName/jdk1.6.0_u/mySpiffyJavaProgram.java
```

That is, you javac in the terminal, drag the java file into the terminal window to let Ubuntu copy the long path name to your project. That will put some sanity into your java efforts and then you can look around the HowTos, pick your poison and try to fix this path issue. I've seen discussions on the Forums giving advice that points to the wrong java folder. Then, you have the plug-in problem with your browser. You need the plug-in to have java WebStart. There are no clear answers from the Forums on that one. Personally, I use the Automatix2 Swiftfox. There are a lot of negatives using the Swiftfox browser, starting with the author no longer supports Swiftfox. But, it works. It installs with a click of a button. It installs everything you will need.

It is my hope and prayer that Ubuntu can accomplish a kinder and gentler java install in the near future. Sun java is now OpenSource. Sun sent an open invitation to Linus Torvalds to perhaps collaborate his thoughts about an OS that compliments java.

---

