---
title: "OpenJDK Discrepency"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by Sef on 2008-09-11
I found a discrepency with OpenJDK - what it is and what it is read as.

OpenJDK is [based on]("http://www.press.redhat.com/2008/06/24/openjdk-and-the-icedtea-project/") Java SE 6, and therefore should work with all sites that use Java SE 6.

However, when I went to [Java.com]("http://java.com/en/") and clicked on "Do I Have Java?", it says that my java is this:  > **JRE version(s):**
1.4.2_xx, 1.5.0, 6.0The box below says that it is the Vendor is GNUClass and the Version is Java 4.0.

I feel this is why some of us are having problems with certain websites:  they register that we are using an out-of-date version of Java that is not supported.

1) Is that paragraph correct?

2) Does anyone else's OpenJDK read the same?

3) Has anyone a fix for this? (If it is a bug.)

4) Where should this bug be reported? (If it is a bug.)

Update1:  This fixed now in Intrepid Ibex with an update from the proposed updates.  My java reads as 1.6.0_0.

Update2: The LiveConnect feature doesn't work.  As long as the applet doesn't require that feature it should work. (From post #12.)

Update3: [LiveConnect Bug Report]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/207064") (LaunchPad)

---

### Post by Joeb454 on 2008-09-11
This is what I get:

---

### Post by Sef on 2008-09-11
That is interesting joe454.  Why am I getting an older version.  hmmm....  What ubuntu are you running?

---

### Post by philinux on 2008-09-12
I'm using this - /usr/lib/jvm/java-6-openjdk/jre/bin/java
```
java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)
```And this plugin -
GCJ Web Browser Plugin (using IcedTea) 1.0
File name:  /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

I get this response from java.com.

---

### Post by jespdj on 2008-09-13
I wrote the following small test program to see what 64-bit OpenJDK and 64-bit Sun Java 6 report on my system.
[php]public class Main
{
	public static void main(String[] args) {
		System.out.println("java.version = " + System.getProperty("java.version"));
		System.out.println("java.specification.version = " + System.getProperty("java.specification.version"));
		System.out.println("java.vm.version = " + System.getProperty("java.vm.version"));
		System.out.println("java.vm.specification.version = " + System.getProperty("java.vm.specification.version"));
	}
}[/php]
Results with OpenJDK:
> java.version = 1.6.0_0
java.specification.version = 1.6
java.vm.version = 1.6.0_0-b11
java.vm.specification.version = 1.0

Results with Sun Java 6:
> java.version = 1.6.0_06
java.specification.version = 1.6
java.vm.version = 10.0-b22
java.vm.specification.version = 1.0

These both seem correct. Note that they both report "1.6" for Java specification version, which is what a program checking for what version of Java is implemented should look at.

I think it is a bug with the website that checks for your Java version rather than a bug in OpenJDK.

> **Sef said:**
> 4) Where should this bug be reported? (If it is a bug.)
You could report it in [Sun's bug database](http://bugs.sun.com/) or use the [feedback page](http://developers.sun.com/contact/feedback.jsp?&category=se) to notify them of a problem with their web page.

(By the way, why is this topic a sticky?)

---

### Post by Sef on 2008-09-13
> (By the way, why is this topic a sticky?)


It's a temporary sticky.   I was not sure if this was a problem affecting a lot of users or just a few.

---

### Post by jespdj on 2008-09-13
I just realized that this might have to do with the fact that you're running 64-bit Ubuntu.

As far as I know, there isn't a 64-bit Java browser plug-in yet. In the OpenJDK version that comes with 64-bit Ubuntu, some IcedTea / GNU stuff is used for the browser plug-in (I don't know the exact details). It's possible that this plug-in reports different version numbers.

I wonder what someone on a 32-bit system with OpenJDK will get.

---

### Post by Stunts on 2008-09-13
Here's what I got.
64bit Hardy here too.

Hope this helps improve everyone's 64bit experience.

---

### Post by Duranxl on 2008-09-13
I have 1.6.0 but still can't open some java applets.
When's the 64bit firefox plugin coming -.-?

---

### Post by philinux on 2008-09-15
> **Duranxl said:**
> I have 1.6.0 but still can't open some java applets.
When's the 64bit firefox plugin coming -.-?

[http://ubuntuforums.org/showthread.php?t=910447](http://ubuntuforums.org/showthread.php?t=910447)

---

### Post by wncben on 2008-09-17
I still don't have full java support either, it is almost enough to make me install 32 bit firefox like I did with edgy...  When I go to the java.com website, verify I have java (which says i hava an older version of java), and hit the 'more info' button I am told that my java vendor is sun microsystems, and the vendor url is [http://java.sun.com](http://java.sun.com)...  HOWEVER, I have the open jdk version installed.... hmmm.   

  I do have partial java support tho... the duke image is animated on the java.com page, the java applet clocks work, but, the yahoo chat applet in yahoo mai doesnt work, my banking website has menus that don't appear....  Basically, this has made me absosmurfly hate java with a hot and seething rage heretofor known only to flaming hornets dive bombing the genius with the can of hair spray and a bic from the smokey immolated remains of their nest...

feh.

---

### Post by Sef on 2008-09-17
>  	 		**Re: OpenJDK Discrepency**
 I still don't have full java support either, it is almost enough to make me install 32 bit firefox like I did with edgy... When I go to the java.com website, verify I have java (which says i hava an older version of java), and hit the 'more info' button I am told that my java vendor is sun microsystems, and the vendor url is [http://java.sun.com]("http://java.sun.com/")...  HOWEVER, I have the open jdk version installed.... hmmm.   

 I do have partial java support tho... the duke image is animated on the java.com page, the java applet clocks work, but, the yahoo chat applet in yahoo mai doesnt work, my banking website has menus that don't appear.... Basically, this has made me absosmurfly hate java with a hot and seething rage heretofor known only to flaming hornets dive bombing the genius with the can of hair spray and a bic from the smokey immolated remains of their nest...


It could be a problem with those sites.  I have one site that I can't get into.  It loads, but never goes beyond that.

---

### Post by Thelasko on 2008-09-18
> **wncben said:**
> I still don't have full java support either, it is almost enough to make me install 32 bit firefox like I did with edgy...  When I go to the java.com website, verify I have java (which says i hava an older version of java), and hit the 'more info' button I am told that my java vendor is sun microsystems, and the vendor url is [http://java.sun.com](http://java.sun.com)...  HOWEVER, I have the open jdk version installed.... hmmm.   

  I do have partial java support tho... the duke image is animated on the java.com page, the java applet clocks work, but, the yahoo chat applet in yahoo mai doesnt work, my banking website has menus that don't appear....  Basically, this has made me absosmurfly hate java with a hot and seething rage heretofor known only to flaming hornets dive bombing the genius with the can of hair spray and a bic from the smokey immolated remains of their nest...

feh.

The LiveConnect feature doesn't work.  As long as the applet doesn't require that feature it should work.

---

### Post by Thelasko on 2008-09-18
The output when I run the test:

> Vendor: Sun Microsystems Inc.
Version: Java 6  Update
Operating System: Linux

However, it does say I'm using an older version of JRE.  This appears to be the same as the output Philinux has.

I notice that when the applet first runs it's output changes rapidly about two times.

---

