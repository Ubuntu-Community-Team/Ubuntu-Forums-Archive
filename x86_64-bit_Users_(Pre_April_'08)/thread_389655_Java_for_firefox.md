---
title: "Java for firefox"
date: 2007-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by blockdude14 on 2007-03-21
I can't get Java to work on my Firefox browser. I have an AMD 64 Processor and using  Ubuntu 64bit. :confused:

---

### Post by chrism66 on 2007-03-21
I believe Java does not work with the 64 bit version of firefox. You can follow Kilz's [howto]("http://www.ubuntuforums.org/showthread.php?p=1174435") to get it working with the 32bit firefox.

---

### Post by John Jason Jordan on 2007-03-21
> **chrism66 said:**
> I believe Java does not work with the 64 bit version of firefox. You can follow Kilz's [howto]("http://www.ubuntuforums.org/showthread.php?p=1174435") to get it working with the 32bit firefox.
Kilz' howto for 32-bit Firefox is a good solution for some people. But it is not true that you cannot use Java with 64-bit Firefox. I've had it working for a very long time -- so long that I'm not sure how I installed it. Might be mozplugger, can't remember.

---

### Post by saneone on 2007-03-21
I think there is an alternative for Sun Java... What u need is IBM Blackdown Java... It works with 64bit Mozilla...

---

### Post by Kilz on 2007-03-21
> **saneone said:**
> I think there is an alternative for Sun Java... What u need is IBM Blackdown Java... It works with 64bit Mozilla...

The 64bit blackdown java plugin is known to crash 64bit Firefox 2.0 on Ubuntu. I couldnt even open a page with an applet on it when I tried, the browser would immediately crash.

---

### Post by saneone on 2007-03-21
> **Kilz said:**
> The 64bit blackdown java plugin is known to crash 64bit Firefox 2.0 on Ubuntu. I couldnt even open a page with an applet on it when I tried, the browser would immediately crash.

strange... i've been using blackdown for a very short time and i'm pretty sure i was able to use chat, which needed JavaPlugin...

---

### Post by John Jason Jordan on 2007-03-21
> **saneone said:**
> strange... i've been using blackdown for a very short time and i'm pretty sure i was able to use chat, which needed JavaPlugin...
Kilz is sort of right. That is, I remember occasionally crashing 64-bit Firefox 1.5 back last summer when clicking on a link that required Java. But that was uncommon, and I haven't had any problem at all for a long time. Except I should add that I remember another thread where someone posted a Russian site guaranteed to crash Firefox with Blackdown. Sure enough, it crashed my current Firefox 2.0 on Edgy with whatever the latest Blackdown is. So whatever was causing the crashes is not completely fixed with Blackdown. Nevertheless, it works 99.99% and that is good enough for me. But it depends on your individual needs. If you go to sites that require Java a lot and you need 100% reliability, then 32-bit Firefox with Kilz' how-to may make more sense for you.

---

### Post by Lonthong on 2007-03-22
> **John Jason Jordan said:**
> Kilz is sort of right. That is, I remember occasionally crashing 64-bit Firefox 1.5 back last summer when clicking on a link that required Java. But that was uncommon, and I haven't had any problem at all for a long time. Except I should add that I remember another thread where someone posted a Russian site guaranteed to crash Firefox with Blackdown. Sure enough, it crashed my current Firefox 2.0 on Edgy with whatever the latest Blackdown is. So whatever was causing the crashes is not completely fixed with Blackdown. Nevertheless, it works 99.99% and that is good enough for me. But it depends on your individual needs. If you go to sites that require Java a lot and you need 100% reliability, then 32-bit Firefox with Kilz' how-to may make more sense for you.

Would you mind to share the trick to get black down java work??
As for me, it crashes FF on any Java sites

---

### Post by John Jason Jordan on 2007-03-22
> **Lonthong said:**
> Would you mind to share the trick to get black down java work??
I really don't know which of the following made it work. But here is a list of stuff to check:

First, I did about:plugins and it said (among a long list of other things) that I had:

Java(TM) Plug-in Blackdown-1.4.2-02
    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

Then I opened Synaptic and did a search on "java." That revealed a long list of things that are installed. I don't know what half of them do, but here is the list (I left out anything clearly relating to Sun Java 1.5, which I also have installed):

j2re1.4
java-common
java-gcj-compat
libgcj7-0
libgcj7-jar
libgcj7-common
libgtksourceview-common
libhsqldb-java
libhsqldb-java-gcj
libjaxp1.2-java
libjaxp1.2-java-gcj
libjxline-java
libkjsembed1
libservlet2.3-java
libservlet2.3-java-gcj
libxalan2-java
libxalan2-java-gcj
libxerces2-java
libxerces2-java-gcj
libxt-java
libxt-java-gcj

Plus, of course, I have installed:

mozplugger

And my Firefox is 2.0.0.2 on Edgy, completely up to date. I hope that helps. If it doesn't I'm out of ideas.

---

### Post by rajeev1204 on 2007-03-22
whatabout sun java from repos?

That is 64 bit right? 

Even though whenever i installed it was broken soon.

Synaptic listed it as broken .

oops sorry i think that does not have a firefox plugin . 

sorry

---

### Post by Kilz on 2007-03-22
> **rajeev1204 said:**
> whatabout sun java from repos?

That is 64 bit right? 

Even though whenever i installed it was broken soon.

Synaptic listed it as broken .

oops sorry i think that does not have a firefox plugin . 

sorry

Exactly, it doesnt have a plugin.

---

### Post by chrisinator_Shuttle_XPC on 2007-03-23
Somehow I got it too, I think its blackdown java webstart, and ia32 sun java which works great

O yeah get ia32-libs first tho and maybe libc6-dev-i386

---

### Post by prince_niceguy on 2007-03-24
can some body confirm this. I am using feisty. I added the jre from the repository for firefox and volla... it is working... i can see the applets which i have never seen earlier... i encountered a crash but that happens on windows too some time...

can some one confirm if the jre plugin in the repository working for 64bit on their machine. seems it is working on mine...

---

### Post by slingre87 on 2007-03-24
I am so lost right now...Can someonw please tell me how to find out if I have 32 or 64 bit firefox, and how to see if my amd presario is 32 or 64 bit as well....I feel dumb about now. And everyone keeps saying something about enabling repositories. Where do I find more info on all this stuff?

---

### Post by Kilz on 2007-03-24
> **slingre87 said:**
> I am so lost right now...Can someonw please tell me how to find out if I have 32 or 64 bit firefox, and how to see if my amd presario is 32 or 64 bit as well....I feel dumb about now. And everyone keeps saying something about enabling repositories. Where do I find more info on all this stuff?

The firefox part is easy, Click help then About Mozilla Firefox. Near the bottom it will say this if its 32bit, the bold part is whats important.

Mozilla/5.0 (X11; U; **Linux i686**; en-US; rv:1.8.1) Gecko/20061010 Firefox/2.0

Enabling repositories is also easy,[ take a look here. ]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

To find out what your hardware is may be a little harder, I suggest going to the manufacturers website with the computers make, model, and serial number. You should get detailed info there.

---

### Post by slingre87 on 2007-03-24
Ok, thanx. So if i686 is 32bit, then what's 64?

---

### Post by Kilz on 2007-03-24
> **slingre87 said:**
> Ok, thanx. So if i686 is 32bit, then what's 64?

Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.8.0.10) Gecko/20070302 Ubuntu/dapper-security Firefox/1.5.0.10

but thats only the firefox version.

---

### Post by pinguin on 2007-03-25
To enable java with firefox 64 bit try:
java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1
they are in official repository and you can install by synaptic

---

### Post by Kilz on 2007-03-25
> **pinguin said:**
> To enable java with firefox 64 bit try:
java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1
they are in official repository and you can install by synaptic

java-gcj-compat-plugin and gcjwebplugin-4.1 are not avilable for Dapper.

---

### Post by Lonthong on 2007-03-28
> **pinguin said:**
> To enable java with firefox 64 bit try:
java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1
they are in official repository and you can install by synaptic

Thanks for the tips but it seemed something is still missing.

I just installed them & visited wildsnake website ( I had to reboot though, otherwise game loading did not progress). Java applet now seems to load just fine but however, I cannot play the game (pinball). The keyboard did not respond. Moreover there is no sound.

But still, I have made a progress with yr tips. Prior to this moving my mouse onto java applet would surely crash firefox.

---

### Post by sancho1980 on 2007-04-23
hi
same problem here
im running firefox on 64 bits feisty fawn and have blackdown installed
i also created the symbolic link to get java running:

```
sancho@Kiste:~/.mozilla/plugins$ ls -l libjavaplugin_oji.so 
lrwxrwxrwx 1 sancho sancho 63 2007-04-23 21:06 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so
```

but it still crashes when i open some sites
has anyone found a solution?
cheers,

martin

---

### Post by r_rehashed on 2007-05-04
the gcjwebplugin-4.1 will only allow Java 5 or earlier applets to run; ie Java 6 applets can not be run. But, that's ok as most applets are Java 5 applets.

However i feel gcj's plugin isn't as good as Sun's.

---

### Post by angryfirelord on 2007-07-22
Hopefully when the GPL'd 1.7 comes out, someone can look at the source code and make a plugin.

---

### Post by willyram on 2007-08-22
I don't know if this helps, as I am more of an end-user here, but I found that IBM has a Java 5 machine for AMD64. 

You will have to register to be able to download, which would require you to fill in a profile. 

It's up to you to try it, I will do as soon as I get back home. Will post results if you want. 

The "portal" for the download of Java 5 is here: 

[http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

I think this is Java 5 while Sun has a Java 6... I don't know the differences, does anybody has any insight if this is really a significant issue?

Best regards, Willie.

---

### Post by Kilz on 2007-08-22
> **willyram said:**
> I don't know if this helps, as I am more of an end-user here, but I found that IBM has a Java 5 machine for AMD64. 

You will have to register to be able to download, which would require you to fill in a profile. 

It's up to you to try it, I will do as soon as I get back home. Will post results if you want. 

The "portal" for the download of Java 5 is here: 

[http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

I think this is Java 5 while Sun has a Java 6... I don't know the differences, does anybody has any insight if this is really a significant issue?

Best regards, Willie.

Does the package have a plugin? You can get a 64bit package from Sun for java 5 or 6 , but it doesnt have a plugin.

---

