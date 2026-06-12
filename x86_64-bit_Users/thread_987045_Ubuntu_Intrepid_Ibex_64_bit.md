---
title: "Ubuntu Intrepid Ibex 64 bit"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by mark clark on 2008-11-19
Have couple things like to ask ! I have dell 420 xps  like to know with 64 bit OS what max gigs of ram ? 8 gigs? Also like to know if anytime soon gone be fix to Java with 64 bit browser Firefox.Thanks really like 64 bit Ubuntu Intrepid Ibex

---

### Post by blakjesus on 2008-11-19
Im not sure but i think that the max RAM for 64-bit is much higher than 8GB but most laptops have a max of 8GB. And as for java? I haven't had any problems yet with that, so i dont think you have much to worry about. :)

---

### Post by Bokonon on 2008-11-19
Yup, the OS won't limit your memory.  I don't know what the addressing limit of the 64 bit OS is, but it is crazy for the current hardware and much more than 8GB.

As for Java and browsers, the IceTea plugin works fine for me and I can see Java enabled sites just fine.  (same as Hardy)

---

### Post by john_navarro on 2008-11-19
Something like 16 exabytes; 2 raised to the 64th power. Or 16 million gigabytes. ( megabytes -> gigabytes -> terrabyes -> exabytes )

---

### Post by Roberticus on 2008-11-19
64 bit limit is about 2^64 (= 1.84467441 × **10^19** bits, equivalent to approximately 17.2 billion gigabytes)
as 32 bit limit is 2^32 (= 4 294 967 296 bits)

---

### Post by Svenstaro on 2008-11-19
We have 64bit Java AND NATIVE FLASH 10 64BIT(!) since 30 hours ago so you should be fine :)
Don't worry about the memory. All your stuff should be faster, too. In 64bit, you get about 10% performance gain on average.

---

### Post by mark clark on 2008-11-19
Thanks for all the info it helped.But java still dose not work for me maybe should re-stall ?

---

### Post by jespdj on 2008-11-19
> **Roberticus said:**
> 64 bit limit is about 2^64 (= 1.84467441 × **10^19** bits, equivalent to approximately 17.2 billion gigabytes)
as 32 bit limit is 2^32 (= 4 294 967 296 bits)
No, it is not 2^64 BITS, but 2^64 BYTES.

2^64 = 18,446,744,073,709,551,616 bytes

This is only a theoretical number. In reality, current 64-bit processors can address at most 2^40 bytes (1024 gigabytes). But current motherboards place the limit even lower, most motherboards can't address more than 4, 8 or 16 GB.

The problem with Java is that there is no 64-bit browser plug-in for Sun Java (yet; Sun is working on it). However, if you use OpenJDK Java and the IcedTea plugin, many Java applets will work. Install like this:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```
Note that unfortunately not all Java applets work with this, because OpenJDK is not yet 100% compatible with Sun Java 6. Is there a specific website that uses Java that doesn't work for you?

---

### Post by mark clark on 2008-11-19
mark@mark-desktop:~$ sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  icedtea-gcjwebplugin: Depends: icedtea6-plugin but it is not going to be installed
E: Broken packages

dose not work 
:lolflag:

---

### Post by lonniehenry on 2008-11-19
mark clark:  the needed plugin is icedtea6-plugin which is an update to gcjwebplugin.  Install icedtea6-plugin, openjdk-6-jre, openjdk-6-jre-headless, and openjdk-6-jre-lib.

---

### Post by mark clark on 2008-11-19
I did update with extra packages ! still don't work at all anything use java all i want  is work around that works  for now until there 64 bit java plugin thanks

---

### Post by jespdj on 2008-11-20
So, what does "it don't work at all anything" mean? Do you get error messages? If so, then what are the error messages? It would be easier to help you solve this if you would give some more information.

Did you install the packages that lonniehenry mentioned?
```
sudo apt-get install icedtea6-plugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
```
Did that go without any errors? Did you restart Firefox after installing those packages?

Make sure that OpenJDK Java is the default Java that's in use on your system:
```
sudo update-java-alternatives -s java-6-openjdk
```
What do you get if you enter "java -version"?

---

### Post by mark clark on 2008-11-20
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)


problem I'm having is like this pogo.com is java games !Page comes up and says Java is not installed!So makes me think it not gone work until there Java 64 bit plug-in!Even went back and reinstalled  whole 64 bit make sure it was not my error !What I read allot of people have same issues really like way everything else works just that one issue with java not  working on any browsers installed :confused: .

---

### Post by jespdj on 2008-11-21
> **mark clark said:**
> java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)
This indicates that you are using **Sun** Java 6 update 10. Unfortunately, Sun Java 6 does not include a browser plugin for 64-bit systems.

You should be using **OpenJDK** Java 6, the IcedTea plugin works with OpenJDK.

Did you use the commands I posted?

---

### Post by huntzire on 2008-11-22
> **jespdj said:**
> No, it is not 2^64 BITS, but 2^64 BYTES.

2^64 = 18,446,744,073,709,551,616 bytes

This is only a theoretical number. In reality, current 64-bit processors can address at most 2^40 bytes (1024 gigabytes). But current motherboards place the limit even lower, most motherboards can't address more than 4, 8 or 16 GB.

The problem with Java is that there is no 64-bit browser plug-in for Sun Java (yet; Sun is working on it). However, if you use OpenJDK Java and the IcedTea plugin, many Java applets will work. Install like this:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```
Note that unfortunately not all Java applets work with this, because OpenJDK is not yet 100% compatible with Sun Java 6. Is there a specific website that uses Java that doesn't work for you?

Thats incorrect, currently x86-64 processors can only physically addresss 48 bits of physical memory, you can verify by cat /proc/cpuinfo | more
and see that it only uses 48 bits at the moment but can be expanded in the future when memory tech gets to that point.

---

### Post by Arup on 2008-11-22
Even with Sun Java installed, you can also have the alternate Java and Icedtea plugin installed as well, FF sees the icedtea plugin and works fine on Java sites, problem is with Opera which doesn't work on any Java sites either with Sun Java or with the other one.

---

### Post by jespdj on 2008-11-22
Ok, I didn't know that. By the way, Sun is planning to have a 64-bit Java plugin sometime in early 2009, with Java 6 update 12, so running Java in your browser on 64-bit systems is (hopefully) going to be easier in a few months.

---

### Post by smfoy on 2009-02-13
And it's still broken.  Same error.  Wife needs to play Pogo.com.  Help!

---

### Post by novafluxx on 2009-02-13
According to Dell, the XPS 420 supports a maximum of 8GB of RAM:

[http://support.dell.com/support/edocs/systems/xps420/en/OM/HTML/appendix.htm#wp1057811](http://support.dell.com/support/edocs/systems/xps420/en/OM/HTML/appendix.htm#wp1057811)

Therefor you'll need a 64bit OS to use it easily!

---

### Post by jespdj on 2009-02-13
Sun Java 6 update 12 is out with a 64-bit browser plug-in, search to forum here on howto's for installing it. (It's not in the repository for Ubuntu 8.04 and 8.10 but will be included with 9.04 in April).

---

### Post by seicean on 2009-02-13
I'm migrating from 32bit to 64bit. My laptop is quite fast, so it's not that much of a difference. There is though something weird:

nVidia GeForce 9300M GS is seen correcly now, while in 32 bit it was seen as "Genuine GeForce 9400".

in CPU monitor, both cores are listed to work at 800MHz/2GHz, and the refresh rate is pretty precise.

Wine is a little bit faster and COD 2 is fluent at 1280 res. Better than in 32bit.

---

