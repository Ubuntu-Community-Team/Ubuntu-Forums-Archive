---
title: "Java for 64 bit?"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fixman on 2007-08-29
How do I install Java on Firefox 2 on Ubuntu Feisty on AMD64?

---

### Post by John.Michael.Kane on 2007-08-29
> **Fixman said:**
> How do I install Java on Firefox 2 on Ubuntu Feisty on AMD64?

Have a read.
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")

For any other codec's you can read this sticky
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Arcturus691 on 2007-08-31
Hello,
Looks like sun plans to release a 64bit browser plugin for java in version 7 according to this thread:
[http://ubuntuforums.org/showthread.php?t=533090]("http://ubuntuforums.org/showthread.php?t=533090")

Also you can use a 64bit browser like konqueror and link directly to java.  This is what I use when I go to java sites.   From what I understand there are some security risks linking directly to java instead of using the plugin

Hope this helps

---

### Post by merlin666 on 2007-09-05
> **Fixman said:**
> How do I install Java on Firefox 2 on Ubuntu Feisty on AMD64?

Download the amd64 bin from 

[http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg](http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg)

and then run it with sudo sh. I tried it on a few websites that I know have java and it worked fine for me. First test was the sun downloader on the site, which is a java app.

---

### Post by Kilz on 2007-09-05
> **merlin666 said:**
> Download the amd64 bin from 

[http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg](http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg)

and then run it with sudo sh. I tried it on a few websites that I know have java and it worked fine for me. First test was the sun downloader on the site, which is a java app.

All the 64bit downloads on that page have this  warning on them
```
(use 32-bit version for applet and Java Web Start support)
```
I know from experience that you cant use a 32bit plugin with the 64bit browser that is in the AMD64 version of Ubuntu. Did you by chance find a working 64bit plugin in one of the downloads? From what I understand there wont be a 64bit plugin until java 7 is released (I cant wait)

---

### Post by merlin666 on 2007-09-05
The file that I downloaded is called

jre-1_5_0_07-linux-amd64.bin

I was directed to the sun site by a site that popped up messages that my Windoze Java6 was not suitable. So I downloaded the bin along, and when I booted into feisty and installed it I found that it worked.

---

### Post by Kilz on 2007-09-05
> **merlin666 said:**
> The file that I downloaded is called

jre-1_5_0_07-linux-amd64.bin

I was directed to the sun site by a site that popped up messages that my Windoze Java6 was not suitable. So I downloaded the bin along, and when I booted into feisty and installed it I found that it worked.

But I dont think there is a browser plugin in that file, can you please tell me the name of the browser plugin you are using. type ```
about:plugins
``` in the firefox address bar and copy/paste the java section here. Or attach a screen shot of the section.

---

### Post by paradoxni on 2007-09-06
all I did to get java applets working in firefox was to run synaptic and search for libgcj7-0 and install it and its dependencies.. java now works a treat, I didnt have to do anything else.

---

### Post by Kilz on 2007-09-06
> **paradoxni said:**
> all I did to get java applets working in firefox was to run synaptic and search for libgcj7-0 and install it and its dependencies.. java now works a treat, I didnt have to do anything else.

Only one thing, gjc doesn't run with a security manager. So anything an applet can be written to do, it will. Like format your hard drive when you open a page. I like a little security.
[From the Java page in the wiki]("https://help.ubuntu.com/community/Java?highlight=%28java%29")
"Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that the plugin currently runs with no security manager. This means that applets you load can do anything a java application that you download and run can do. Be **very** careful which applets you run."

---

### Post by kuja on 2007-09-06
I win. 
 
64-bit Konqueror + 64-bit java 
```
 
  |   
  |   
  |   
  |   
 \|/ 
```

---

### Post by paradoxni on 2007-09-06
> **Kilz said:**
> Only one thing, gjc doesn't run with a security manager. So anything an applet can be written to do, it will. Like format your hard drive when you open a page. I like a little security.
[From the Java page in the wiki]("https://help.ubuntu.com/community/Java?highlight=%28java%29")
"Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that the plugin currently runs with no security manager. This means that applets you load can do anything a java application that you download and run can do. Be **very** careful which applets you run."

hmm that dont sound so good, didnt realise, so what the best alternative? (im using 64bit firefox)

---

### Post by John.Michael.Kane on 2007-09-06
> **paradoxni said:**
> hmm that dont sound so good, didnt realise, so what the best alternative? (im using 64bit firefox)

Your options for java are listed in this post. [http://ubuntuforums.org/showpost.php?p=3276818&postcount=2](http://ubuntuforums.org/showpost.php?p=3276818&postcount=2)

---

### Post by merlin666 on 2007-09-06
> **Kilz said:**
> But I dont think there is a browser plugin in that file, can you please tell me the name of the browser plugin you are using. type ```
about:plugins
``` in the firefox address bar and copy/paste the java section here. Or attach a screen shot of the section.

Theres one plugin related to Java:

Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

---

### Post by Kilz on 2007-09-07
> **merlin666 said:**
> Theres one plugin related to Java:

Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

But that is 1.4.2 Blackdown java. The page you linked to before was from Sun and had version 1.5.0. It doesnt look like you got it there.

---

### Post by Angelbeast on 2007-09-07
Okay so i'm a little confused...IS there a 64 bit java plugin available now?

---

### Post by John.Michael.Kane on 2007-09-07
> **Angelbeast said:**
> Okay so i'm a little confused...IS there a 64 bit java plugin available now?

Short answer yes there is a 64bit java plugin,However.The current 64bit  java-gcj-compat-plugin runs with no security manager.


For now users needing java are advised to use the 32 bit Firefox with Flash w/sound and Java for AMD64 guide if you need Java.

---

### Post by Kilz on 2007-09-07
Im looking into the old Blackdown 64bit plugin at the moment thanks to merlin666. When I was running Dapper that plugin crashed the browser on every applet. I am testing the plugin on Feisty and it seems to be running ok with Swiftweasel, but it still crashes Firefox. I may just script a swiftweasel and java install as it would be nice to loose the 32bit browser.

---

### Post by mojoman on 2007-09-07
> **Kilz said:**
> Im looking into the old Blackdown 64bit plugin at the moment thanks to merlin666. When I was running Dapper that plugin crashed the browser on every applet. I am testing the plugin on Feisty and it seems to be running ok with Swiftweasel, but it still crashes Firefox. I may just script a swiftweasel and java install as it would be nice to loose the 32bit browser.

Sounds good but will it run without the security manager? And speaking of security managers, what exactly are they? Here I was, thinking that all Java was a potential security risk but to tell you the truth, I haven't read up much on it and gotten used to use the ff-plugin to block it from untrusted sites. One reason is that I've just been using your scripts and they work so damn good that there hasn't really been any need to read up any further...

cheers
/mojoman

---

### Post by Kilz on 2007-09-07
> **mojoman said:**
> Sounds good but will it run without the security manager? And speaking of security managers, what exactly are they? Here I was, thinking that all Java was a potential security risk but to tell you the truth, I haven't read up much on it and gotten used to use the ff-plugin to block it from untrusted sites. One reason is that I've just been using your scripts and they work so damn good that there hasn't really been any need to read up any further...

cheers
/mojoman

I did a search on the web, here is [a good page on the security manager.]("http://java.sun.com/j2se/1.4.2/docs/api/java/lang/SecurityManager.html") I then went into the Blackdown install I am testing and found the security folder and security policy jar. So it does have a security manager.
 Just to be sure that java-gcj-compat information was still correct, I downloaded the package. It still does not have a security manager or security policy jar.

---

### Post by Fixman on 2007-09-07
fixed using 32 bit version of firefox and 32 bit version of Java 1.6

---

### Post by John.Michael.Kane on 2007-09-07
> **Fixman said:**
> fixed using 32 bit version of firefox and 32 bit version of Java 1.6

The 32bit firefox install method is the best way to go for now if one needs java. 

One thing though if you can please try to take note of any issues while veiwing flash based sites, As there has been some reports of flash acting odd.

---

### Post by zatoichiino on 2008-06-22
That's a link for a script for ubuntu 64 family. That men do a very nice job. The script is installing a firefox 32 bit and java sun 32 bit, also flash and mplayer plugin. It's easy to upgrade firefox 2.14 to firefox 3.0. Every thinks are working amazing. No more problem with incorrect pages. [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435) :)

---

