---
title: "Java plugin for Firefox Hardy 64"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by stchman on 2008-05-08
Is there a way to get this to work?  I tried the GCJ thing and it did not work very well.

I have been reading that if you install the 32 version of Firefox and 32 version of the Java plugin that works but that negates the advantage of 64 bit.

Thanks.

---

### Post by Kilz on 2008-05-08
Not necessarily, it would be running one application in 32bit mode. One of the advantages of running the 64bit version is to run 32bit and 64bit code, that cant be done on the i386 version.
Also firefox isnt a huge number crunching application, and its 32bit code compiled to run on the 64bit version. Its not code designed to take advantage of a 64bit processor. 
So the benefits of using the plugin you want may outweigh the very slight if any performance gain you would get.

---

### Post by stchman on 2008-05-08
> **Kilz said:**
> Not necessarily, it would be running one application in 32bit mode. One of the advantages of running the 64bit version is to run 32bit and 64bit code, that cant be done on the i386 version.
Also firefox isnt a huge number crunching application, and its 32bit code compiled to run on the 64bit version. Its not code designed to take advantage of a 64bit processor. 
So the benefits of using the plugin you want may outweigh the very slight if any performance gain you would get.

After installing Hardy 64 on my Athlon 64 the SUN Java plugin is the only thing that does not work.  Flash works very well.

I wonder what is keeping SUN from making a Java 6 64 bit plugin.  It is probably as simple as recompiling the source code with a 64 bit compiler.

I have 2 64 bit PCs so I can experiment with 64 bit Ubuntu.  I am still running 32 bit Hardy on my Quad core.

---

### Post by Yellow Pasque on 2008-05-08
Try OpenJDK. Read the sticky in this subforum: [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by old_geekster on 2008-05-08
> **stchman said:**
> Is there a way to get this to work?  I tried the GCJ thing and it did not work very well.

I have been reading that if you install the 32 version of Firefox and 32 version of the Java plugin that works but that negates the advantage of 64 bit.

Thanks.

You can use the 32-bit java with 64-bit FF3b5 and it will work great.  Here is what I did to make it work:

sudo update-alternatives --config java

Here is the results:

gene@Linuxbox-Ubuntu:~$ sudo update-alternatives --config java
[sudo] password for gene: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/ia32-java-6-sun/jre/bin/java' to provide 'java'.

As you can see, I chose option "2" which is 32-bit java.

---

### Post by jamesstansell on 2008-05-08
> **stchman said:**
> Is there a way to get this to work?  I tried the GCJ thing and it did not work very well.


Are you talking about the icedtea-gcjwebplugin package that depends on openjdk-6-jre package?  If so I'd be interested to know what didn't work for you.

---

### Post by jamesstansell on 2008-05-08
> **old_geekster said:**
> You can use the 32-bit java with 64-bit FF3b5 and it will work great.  Here is what I did to make it work:

...
Using '/usr/lib/jvm/ia32-java-6-sun/jre/bin/java' to provide 'java'.

As you can see, I chose option "2" which is 32-bit java.

Interesting - I hadn't ever heard that you could do that.

It sounds a little like this post, but I was assuming that the beta of Java 6 Update 10 was required for what he talked about.

  [http://forums.java.net/jive/message.jspa?messageID=272485#272485](http://forums.java.net/jive/message.jspa?messageID=272485#272485)

---

### Post by Kilz on 2008-05-08
> **old_geekster said:**
> You can use the 32-bit java with 64-bit FF3b5 and it will work great.  Here is what I did to make it work:

sudo update-alternatives --config java

Here is the results:

gene@Linuxbox-Ubuntu:~$ sudo update-alternatives --config java
[sudo] password for gene: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/ia32-java-6-sun/jre/bin/java' to provide 'java'.

As you can see, I chose option "2" which is 32-bit java.

I see what option you chose, but are you 100% sure that it is the 32bit sun java plugin being used? From what has been tried before it is a well known fact that a 64bit browser can not use a 32bit plugin.

---

### Post by nightfrost on 2008-05-09
> **Kilz said:**
> I see what option you chose, but are you 100% sure that it is the 32bit sun java plugin being used? From what has been tried before it is a well known fact that a 64bit browser can not use a 32bit plugin.

Indeed, I would be very interested if this truly is the fact. I have had _no_ luck getting java working in hardy 64-bit, either with this method (that I had already tried), or with icedtea, or even with firefox32. For some reason firefox keeps telling me that "additional plugins are needed"...

Java is the only reason I moved back to 32-bit.

---

### Post by old_geekster on 2008-05-09
> **jamesstansell said:**
> Interesting - I hadn't ever heard that you could do that.

It sounds a little like this post, but I was assuming that the beta of Java 6 Update 10 was required for what he talked about.

  [http://forums.java.net/jive/message.jspa?messageID=272485#272485](http://forums.java.net/jive/message.jspa?messageID=272485#272485)

I use "Frostwire".  This is the only way that I could get it to run.  It works perfectly.:)

---

### Post by Kilz on 2008-05-09
> **old_geekster said:**
> I use "Frostwire".  This is the only way that I could get it to run.  It works perfectly.:)

Yes, but frostwire is a stand alone application that is 32bit. The 32bit java does not have a java plugin for your 64bit browser. If you type ```
about:plugins
``` into the address bar of firefox and hit enter what java is listed in the java section? What location does it give?

---

### Post by VHans on 2008-05-15
Is there a way to use a Java plugin with Swiftweasel under 64bit Hardy?
I have following jvm's installed under /usr/lib64/jvm:
- java-1.5.0-gcj-4.2-1.5.0.0
- java-6-openjdk
- java-6-sun
- java-6-sun-1.6.0.06
- java-7-icedtea
- java-gcj

None of them seems to have a plugin.
I do have a plugin under /usr/local/j2re1.4.2/plugin/amd64/mozilla which is used by Swiftweasel but it crashes too often to be useful.

Hans

---

### Post by Kilz on 2008-05-15
> **VHans said:**
> Is there a way to use a Java plugin with Swiftweasel under 64bit Hardy?
I have following jvm's installed under /usr/lib64/jvm:
- java-1.5.0-gcj-4.2-1.5.0.0
- java-6-openjdk
- java-6-sun
- java-6-sun-1.6.0.06
- java-7-icedtea
- java-gcj

None of them seems to have a plugin.
I do have a plugin under /usr/local/j2re1.4.2/plugin/amd64/mozilla which is used by Swiftweasel but it crashes too often to be useful.

Hans

Find out what java plugin icedtea/gcj is using. Its probably in /usr/lib/firefox-addons/plugins, and copy it to /usr/lib/mozilla/plugins and remove the one for j2re1.4.2

---

### Post by darco on 2008-05-15
> **Temüjin said:**
> Try OpenJDK. Read the sticky in this subforum: [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

that worked for me!...
thxs
darco

---

### Post by VHans on 2008-05-16
> **Kilz said:**
> Find out what java plugin icedtea/gcj is using. Its probably in /usr/lib/firefox-addons/plugins, and copy it to /usr/lib/mozilla/plugins and remove the one for j2re1.4.2

In /usr/lib/firefox-addons/plugins I only see a flashplayer plugin (npwrapper.libflashplayer.so). It links to /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so.
Nothing for java.

Hans

---

### Post by old_geekster on 2008-05-16
> **Kilz said:**
> Yes, but frostwire is a stand alone application that is 32bit. The 32bit java does not have a java plugin for your 64bit browser. If you type ```
about:plugins
``` into the address bar of firefox and hit enter what java is listed in the java section? What location does it give?

Kilz, sorry that I didn't answer sooner, but I am on the road in Texas.  I ran the the command suggested and it shows that I am using 32-bit java.  I can't add a the output because I am using XP on the motel's computer.

---

### Post by Kilz on 2008-05-16
> **old_geekster said:**
> Kilz, sorry that I didn't answer sooner, but I am on the road in Texas.  I ran the the command suggested and it shows that I am using 32-bit java.  I can't add a the output because I am using XP on the motel's computer.

Then you have a miracle, because I tried the instructions and cant duplicate your results. You have some how done what is impossible. 32bit plugins do not and can not be interfaced by a 64bit browser to my knowledge. Either you are somehow misinterpreting the java plugin, or the browser you are running as being the wrong bit.

---

### Post by daniel.harvey on 2008-06-04
Hi,

Here is a reliable (has been for me anyway) formula which runs Java plugins in a 32-bit browser.

[LIST=1]
[*] Install package ia32-sun-java6-bin
[*] Install 32bit Swiftweasel ([http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/))
[*] Link in the Java6 plugin into Swiftweasel
```

cd /usr/local/swiftweasel32/plugins
ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```
[/LIST]

PS Swiftweasel has an APT repository

```
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) hardy multiverse
```

---

### Post by gmayer on 2008-09-24
Thanks Daniel, your solution works great and is simple enough. Much better than the gcjwebplugin based on openjdk that 64bit hardy ships with... at last I can upload photos on facebook again ;-)

---

