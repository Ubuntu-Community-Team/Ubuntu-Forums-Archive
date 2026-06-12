---
title: "Java for 64-bit"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by mardawi on 2008-04-24
Hi,

Just installed 8.04 64-bit, everything works perfect.

Before I miss things up, what is the best way to install java 6? I don't seem to be able to find it in the repos. Should I just install it from java.com?

---

### Post by ire on 2008-04-24
> **mardawi said:**
> Hi,

Just installed 8.04 64-bit, everything works perfect.

Before I miss things up, what is the best way to install java 6? I don't seem to be able to find it in the repos. Should I just install it from java.com?

There is no Sun Java plugin for 64bit just yet - you can use IcedTea - when you hit a Java enabled site, you should get prompted to install it

Works fine here for me so far.

---

### Post by FredB on 2008-04-24
Iced Tea is now known as OpenJDK.

---

### Post by Angus77 on 2008-04-24
I've got the OpenJDK plugin installed, but I still can't load the applet in [this page]("http://http://jdee.sourceforge.net/jdedoc/html/jde-ug/jde-ug.html") (the Emacs JDEE User's Guide page).

---

### Post by ire on 2008-04-24
> **Angus77 said:**
> I've got the OpenJDK plugin installed, but I still can't load the applet in [this page]("http://http://jdee.sourceforge.net/jdedoc/html/jde-ug/jde-ug.html") (the Emacs JDEE User's Guide page).

Yeah, no joy here either.

---

### Post by scientist434 on 2008-04-24
I am having the same problem. I have gotten IcedTea installed and it only works for some sites other sites I get an error message about it not being able to create a directory on my computer. Any idea how to fix this.

---

### Post by old_geekster on 2008-04-24
Use "ia32-sun-java6.bin".  It is in "Synaptic".  I couldn't get "Frostwire" to run any other way.  It is now running great.

---

### Post by ndale686738 on 2008-04-25
After weeks of strong effort I resorted to 32bit Java. Once Sun gets their act in gear for 64bit plug ins I will re-explore it. Never had any luck with Iced Tea.

---

### Post by vitalik on 2008-04-25
I just gave 64bit a try.
What about development, I need JDK for college.
Will I be able to use Netbeans?

---

### Post by ndale686738 on 2008-04-25
i have a Java development environment set up on x64 no problem. you can still run any 32 bit program on x64 until the native packages come along a little further for x64. no worries on JDK working.

---

### Post by jespdj on 2008-04-25
> **vitalik said:**
> I just gave 64bit a try.
What about development, I need JDK for college.
Will I be able to use Netbeans?
Ofcourse.

If you don't need the Java browser plug-in (to run applets), you can just install Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
NetBeans, Eclipse etc. all work perfectly with this on 64-bit Ubuntu.

---

### Post by Julius on 2008-04-25
I want to install netbeans too but I have a question. I have installed both JRE and JDK, but if I want to install a lot of packages that I'm not sure I want installed, including openjdk, which I'm not sure why is installed to since I already have sun's jdk? 

Am I better off downloading its website and installing it? I only just want Java SE support anyway

---

### Post by jespdj on 2008-04-25
The preferred way to install software on Ubuntu is by using the package management system (apt-get or synaptic). So, do not download and install Java from Sun's website and install it manually - it's not necessary and it will make it hard to uninstall and may interfere with other Java stuff on your system.

If you have both Sun Java 6 and OpenJDK installed, you can choose which one you want to use with the following command:
```
sudo update-alternatives --config java
```
By the way, NetBeans and Eclipse work fine on OpenJDK too.

---

### Post by Melk79 on 2008-04-25
I just installed the ubuntu-restriced-packages package from synaptic and it successfully installed JDK, Flash and all the other critical media packages for restricted plug-ins, etc.  No issues so far.

---

### Post by thekat on 2008-04-25
> **jespdj said:**
> 

If you have both Sun Java 6 and OpenJDK installed, you can choose which one you want to use with the following command:
```
sudo update-alternatives --config java
```


I used OpenJDK for the plugin so if I install Sun Java 6 for Frostwire
then it should not affect my browser..??

just for the record.. Kudos to the developers on this 64 bit release..

---

### Post by Angus77 on 2008-04-27
You know, what?  I think it's the page I linked to above that has a problem, and not the plugin.  I seem to be able to use a lot of pages with Java tonight, but still no luck with the JDEE site!

---

