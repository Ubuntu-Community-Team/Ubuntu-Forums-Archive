---
title: "Java: is it there or not?"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by thaumielx72 on 2008-12-01
This has me thouroughly confused.  I have tried installing Java from Synaptic several times (and removed it several times). I have tried using get-apt from terminal and have downloaded it from sun directly.  It ran correctly all the way to the word done a couple times.  All I get in the terminal is this:

thaumiel@thaumiel-desktop:/usr/java$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
thaumiel@thaumiel-desktop:/usr/java$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * cacao
 * openjdk-6-jre-headless
 * jamvm
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


Any help would be appreciated.  Thanks in advance.
:confused:

---

### Post by wfp on 2008-12-02
Theres a good sticky on the front page that explains it. Open add/remove program. Make sure you have all available applications ticked. Do a search for icedtea> Now you should see icedtea java plugin, and right under that openJDK java runtime> down load and install those 2 and you should be ok.

---

### Post by jespdj on 2008-12-02
Try this command to see what Java packages you have installed:
```
dpkg -l | grep java
```
This will ofcourse only show what you installed with the Ubuntu package management programs, it won't show manually installed Java.

---

### Post by thaumielx72 on 2008-12-02
> **wfp said:**
> Theres a good sticky on the front page that explains it. Open add/remove program. Make sure you have all available applications ticked. Do a search for icedtea> Now you should see icedtea java plugin, and right under that openJDK java runtime> down load and install those 2 and you should be ok.

Thanks for responding.

I went right to that sticky as soon as I had Ubuntu loaded.  I got this extra machine with the sole intention of running one scientific application on it, pretty much 24/7.  It's written in Java and specifically says it will need Sun's java 6.  I have read in other forums that other Java's are not fully compatible and I will need one area of Java (I can't remember the name) that is only found in Sun's Java 6.  I believe it's the routine that writes to the screen (in some fancy way, I guess).

The problem is I have loaded it successfully already.  I simply cannot access it. The Add/Remove applet with Show Installed applications only shows me Sun Java 6 runtime already installed.  (which the update alternatives shown above clearly states.)  I'm sure the other Java's available are fine efforts in their own right but I do not understand how a program can be both installed and unavailable.

And I do not consider myself a newbie ;) - my first taste of desktop computers was the original IBM PC in 1983.  But, clearly, I have a lot to learn about either Java or Ubuntu.  :p

---

### Post by thaumielx72 on 2008-12-02
> **jespdj said:**
> Try this command to see what Java packages you have installed:
```
dpkg -l | grep java
```
This will ofcourse only show what you installed with the Ubuntu package management programs, it won't show manually installed Java.

You Bet.


thaumiel@thaumiel-desktop:~$ dpkg -l | grep java
ii  java-common                               0.30ubuntu3                           Base of all Java packages
ii  sun-java6-bin                             6-10-0ubuntu2                         Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                             6-10-0ubuntu2                         Sun Java(TM) Runtime Environment (JRE) 6 (ar
thaumiel@thaumiel-desktop:~$ java
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * cacao
 * openjdk-6-jre-headless
 * jamvm
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
thaumiel@thaumiel-desktop:~$ 


Gee - Java cannot be found.  It just told me it could (I think)   :lolflag:

---

### Post by stchman on 2008-12-02
> **thaumielx72 said:**
> This has me thouroughly confused.  I have tried installing Java from Synaptic several times (and removed it several times). I have tried using get-apt from terminal and have downloaded it from sun directly.  It ran correctly all the way to the word done a couple times.  All I get in the terminal is this:

thaumiel@thaumiel-desktop:/usr/java$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
thaumiel@thaumiel-desktop:/usr/java$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * cacao
 * openjdk-6-jre-headless
 * jamvm
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


Any help would be appreciated.  Thanks in advance.
:confused:

First make sure you have all the repositories enabled.

For 64 bit stuff the Sun Java works except for the plugin.  I use Icedtea over Sun Java.

For Hardy:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

I believe that for Intrepid they dropped Icedtea except for the browser plugin.

For Intrepid use the following:
```

sudo apt-get -y install icedtea6-plugin openjdk-6-jdk

```

This will get Java and the browser plugin working on 64 bit.

---

### Post by Beernut on 2008-12-02
> **stchman said:**
> 
For 64 bit stuff the Sun Java works except for the plugin.  I use Icedtea over Sun Java.

For Hardy:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

This will get Java and the browser plugin working on 64 bit.

I would like to get the plugin to work should Sun Java be removed first or can it coexist?

---

### Post by thaumielx72 on 2008-12-02
Appreciate all the help, guys.

While surfing with various search parameters I stumbled across this excellent little web page - *[here.]("http://www.ubuntugeek.com/tomcat-6-installation-on-ubuntu-feisty.html")*

I highly recommend it to anyone in similar situations.  Namely, need to use the .bin downloaded from Sun and make 64 bit Java (with no need for browser plug-in) the default.

It is running right now (all praise to the Ubuntu gods!) but I do have one more small question.

The Java app stubbornly refuses to load a simple .ini file which adds a user defined integrator (routine) to the application.  No big deal, but a search led me to something in the repositories called libini4j-java (0.2.6-0ubuntu3) which is described:

The ini4j is a simple Java API for handling configuration
files in Windows .ini format. Additionally, the library
includes Java Preferences API implementation based
on the .ini file.

Should I load this lib?  And if I do is there anyway to tell where it will be found?

I only ask because I had to create my own Java directory and link to it as explained on the website above.

---

### Post by thaumielx72 on 2008-12-02
> **Beernut said:**
> I would like to get the plugin to work should Sun Java be removed first or can it coexist?

Beernut,

I found another very good bit of advice on *[this link.]("http://ubuntuforums.org/archive/index.php/t-276061.html")*

Scroll down to **Ben Sprinkle's** second post.  (The one where he say's "Tis what I did.")

That quickly cleans out the default Java if you do not need it any more.  However, remember I am not using the browser plug-in - I only need to run a 64 bit stand alone Java app.

Someone else probably has a better answer.

Good Luck.

---

### Post by stchman on 2008-12-03
> **Beernut said:**
> I would like to get the plugin to work should Sun Java be removed first or can it coexist?

The SUN Java browser plugin is not available for 64 bit unless you do some tweaking.

---

