---
title: "[SOLVED] Unable to run Java JRE on AMD64 Ubuntu 8.04"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by micile on 2008-10-10
Dears,

As I've tried to install extensions to OpenOffice, I get an error message saying JRE is not installed.

I've checked with APT and verified that all Java packages were installed, BTW I re-installed them all.

Then I browsed [www.java.com](www.java.com) and tested java installation. Results? My PC were not running any java. Anyway the java website proposed me to download and install a linux64 version of java. I did it.
The installation procedure went well and finished without errors.

But the situation has not changed: the Java website says I've no java installed, and so do Openoffice.

Ofcourse I've checked that in firefox preferences, that java is enabled.

I've googled around on forums for this problem and I've found someone having similar java behavior, all were on 64 architecture, but nobody solved it.

Any ideas from you?
Thanks a lot

Micile

---

### Post by Nepherte on 2008-10-10
The website test will only work if you have the java browser plugin, which is unfortunately not available for 64bit. There is however a openjdk alternative version with a web plugin that does work on 64bit.

To verify you have 64bit java working on your machine, you can start off with:
```
java -version
```

---

### Post by micile on 2008-10-10
Thank you Nepherte,

openjdk is already installed.

I'll post the result of "java -version" as I'll arrive home (in around 3 hrs). 

grazie

Micile

---

### Post by Thelasko on 2008-10-10
The following packages should be installed for OpenJDK to work.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin

Any other Java packages (GCJ, Sun Java, etc.) may interfere with OpenJDK.

Also, please note that OpenJDK has some bugs at the moment.  Namely, the LiveConnect feature doesn't work.  If you require perfect execution of Java Applets, please install the [32-bit version of Firefox and Java.]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz")

---

### Post by micile on 2008-10-10
that's results from java -version

~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

---

### Post by Thelasko on 2008-10-10
If you run 
```
sudo update-java-alternatives --list
```
what do you get?

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by Therion on 2008-10-10
Installing **ubuntu-restricted-extras** has always solved my Java issues.

---

### Post by WWSmith36 on 2008-10-10
I run the sun-java which is a slightly different version

```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

I installed with 

```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

It is in the multiverse repository, and is available for both amd64 and i386

Hope this helps

---

### Post by Thelasko on 2008-10-10
> **WWSmith36 said:**
> ```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

It is in the multiverse repository, and is available for both amd64 and i386

Hope this helps
Are you sure about that?  [The repository says otherwise.]("http://packages.ubuntu.com/hardy/sun-java6-plugin")

---

### Post by baizon on 2008-10-10
Hi, remove the openjdk-* pkg and install the sun-java6-* pkg.

---

### Post by Thelasko on 2008-10-10
> **baizon said:**
> Hi, remove the openjdk-* pkg and install the sun-java6-* pkg.

Do you run 64-bit?

---

### Post by baizon on 2008-10-10
> **Thelasko said:**
> Do you run 64-bit?
Ou sry, got a 32bit OS, didnt try it on 64bit.

---

### Post by Thelasko on 2008-10-10
> **baizon said:**
> Ou sry, got a 32bit OS, didnt try it on 64bit.
Sun-Java-6 doesn't have a web plugin for 64-bit.  Therefore web applets don't work with it.  Any other Java program should work fine.

---

### Post by WWSmith36 on 2008-10-10
> **Thelasko said:**
> Are you sure about that?  [The repository says otherwise.]("http://packages.ubuntu.com/hardy/sun-java6-plugin")

Thanks pointing that out the first 2 packages are available for amd64 but the sun-java6-plugin is not.

---

### Post by wetling on 2008-10-10
So...what do you do if you want to view a web page that using Java in a browser plugin?

---

### Post by Thelasko on 2008-10-13
> **wetling said:**
> So...what do you do if you want to view a web page that using Java in a browser plugin?
This
[Quote=Thelasko]The following packages should be installed for OpenJDK to work.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin

Any other Java packages (GCJ, Sun Java, etc.) may interfere with OpenJDK.

Also, please note that OpenJDK has some bugs at the moment. Namely, the LiveConnect feature doesn't work. If you require perfect execution of Java Applets, please install [the 32-bit version of Firefox and Java.]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz")[/Quote]

---

### Post by jespdj on 2008-10-14
> **micile said:**
> As I've tried to install extensions to OpenOffice, I get an error message saying JRE is not installed.
This is a [known bug in OpenOffice](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/270467) - it can't detect your JRE, even if it's installed.

---

### Post by bsilverwood on 2008-10-14
"Sun-Java-6 doesn't have a web plugin for 64-bit. Therefore web applets don't work with it. Any other Java program should work fine."

Try accessing a juniper networks web portal
Try accessing some banking sites

The non-Sun java packages will NOT work in these instances including many online java-based games.

I have been working on this for weeks and have not found a solution.

---

### Post by jmszr on 2008-10-15
Micile,
        Go to the Synaptic Package Manager,search for "openoffice.org-java-common"   and install. That should do it. Just for the open office extension portion, of course.

---

### Post by peakshysteria on 2008-10-15
For keeping up with java:

[**[COLOR="Red"]Java on 64-bit Systems[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=774956")

Browser plugin isn't available until 2009.

---

### Post by micile on 2008-10-16
thanks to all of you

So installing openoffice.org-java-common solved the problem in openoffice (even though I'm not able to run the googledoc extension, but I think this is another story)
Moreover it's right that java works fine but in the web. 
Installing firefox 32 solved that.
thanx

---

