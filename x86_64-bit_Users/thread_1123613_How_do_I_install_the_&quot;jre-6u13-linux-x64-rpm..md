---
title: "How do I install the &quot;jre-6u13-linux-x64-rpm.bin&quot; download?"
date: 2009-04-12
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2009-04-12
I just want the *most recent* 64-bit Java Runtime Environment with the 64-bit browser plug-in working correctly. 

_I would greatly appreciate a simple and short step by step guide, NO LINKS and NO google searches, please._

I've been searching a lot, but all the partial and outdated info is giving me a headache!

How do I install the downloaded "jre-6u13-linux-x64-rpm.bin"?

I got it from this website:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u13-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u13-oth-JPR@CDS-CDS_Developer)

By the way, I'm running Ubuntu 9.04 64-bit beta.

---

### Post by James_Lochhead on 2009-04-12
[My guide.]("http://ubuntuforums.org/showthread.php?t=1113039")

---

### Post by cariboo on 2009-04-12
I see you are running Jaunty, so everything you need is in the repostories. I would suggest you install the ubuntu-restricted-extras meta package. It installs Flash, Java and most codecs needed to play most audio/video media. You will have to install the 64-bit plugin seperately, it is called sun-java6-plugin. You can use Add/Remove Programs or Syanptic Package Manager to install both packages.

Jim

---

### Post by Linux user 66 on 2009-04-12
> **James_Lochhead said:**
> [My guide.]("http://ubuntuforums.org/showthread.php?t=1113039")

Thanks for the excellent guide! However, I followed the instructions, but the 64-bit browser plug-in still doesn't work. Maybe the JRE doesn't either, I'm not sure. I would also prefer to only use the JRE package instead of the JDK, which quite naturally is far bigger and contains elements I'll never use.

> **cariboo907 said:**
> I see you are running Jaunty, so everything you need is in the repostories. I would suggest you install the ubuntu-restricted-extras meta package. It installs Flash, Java and most codecs needed to play most audio/video media. You will have to install the 64-bit plugin seperately, it is called sun-java6-plugin. You can use Add/Remove Programs or Syanptic Package Manager to install both packages.

Jim

I considered that. However, how do I know that the JRE included in the restricted-extras package is the most recent one?

@ Both

Thanks a lot for your replies! =)

---

### Post by Linux user 66 on 2009-04-12
Got it working now, but thanks anyway. =)

Edit: I used and adapted some of the instructions from this thread:

[http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)

---

### Post by central101 on 2009-04-23
Hello, I need some help with this plugin aswell. I am trying to upload files to a website and to use their uploader you need this plugin. Now, It works fine on my windows machine but I need it to work on my Linux machine.

I am actually using Centos not Utuntu but I decided to post here because this thread is very recent.

What I am trying to do is upload videos on eatlime via a remote desktop. I have installed the proper Java plugin (JRE-6u13 plugin) on my linux machine that is required but it still does not work. Nothing pops ups or changes on the upload page. Ive e-mailed eatlime three times but they havent answered me.

Hopefully someone here can help me out.. I really need to get this working. 

Thanks and have a great day :)

---

### Post by TimothyLuke on 2009-04-23
To install Java 1.6.0_U13 64bit and the 64bit plugin,

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

While the fonts package should be optional it all "Just Worked" out of the box for me.

---

