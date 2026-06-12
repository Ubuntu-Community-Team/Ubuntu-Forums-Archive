---
title: "Does icedtea-java7-plugin work for *anyone* in Firefox 2?"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by Zorael on 2008-06-27
The symlinks point to the right direction, it shows up in about:plugins, but it doesn't work. Do note: **Firefox _2_**. It *does* work in Firefox 3, but then flash doesn't, so I'm hesistant to migrate. The lesser of two evils and all that.
```
$ ls /usr/lib/mozilla/plugins/*java* -l
lrwxrwxrwx 1 root root 45 2008-06-27 19:25 /usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so

$ ls /etc/alternatives/xulrunner-1.9-javaplugin.so -l
lrwxrwxrwx 1 root root 57 2008-06-27 21:49 /etc/alternatives/xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

$ ls /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so -l
-rw-r--r-- 1 root root 28088 2008-06-05 20:31 /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```
about:plugins says:
```
**[SIZE="3"]GCJ Web Browser Plugin (using IcedTea) 1.0[/SIZE]**

[indent]File name: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
The GCJ Web Browser Plugin (using IcedTea) executes Java applets.[/indent]
```

Opening [http://javatester.org/version.html](http://javatester.org/version.html), the browser doesn't draw the applet, and the following is output to the terminal.
```
$ firefox-2 http://javatester.org/version.html
GCJ PLUGIN: thread 0x619ab0: NP_Initialize
gcjwebplugin.cc:1450: thread 0x619ab0: Error: Invalid browser function table.
GCJ PLUGIN: thread 0x619ab0: NP_Shutdown
GCJ PLUGIN: thread 0x619ab0: NP_Shutdown return
GCJ PLUGIN: thread 0x619ab0: NP_Initialize
gcjwebplugin.cc:1450: thread 0x619ab0: Error: Invalid browser function table.
```

I don't see what I could've done wrong. Is the Firefox 2 support broken globally, or just for me?

---

### Post by jamesstansell on 2008-06-27
I'm not sure I've heard of that error before.  Just to verify, though, is it the icedtea-gcjwebplugin package that you have?

Does [http://gemal.dk/browserspy/java.html](http://gemal.dk/browserspy/java.html) work any better for you?

---

### Post by Zorael on 2008-06-27
```
$ apt-cache depends icedtea-java7-plugin
icedtea-java7-plugin
  Depends: icedtea-gcjwebplugin
```
```
$ apt-cache policy icedtea-java7-plugin icedtea-gcjwebplugin
icedtea-java7-plugin:
  Installed: 7~b24-1.6-0ubuntu7
  Candidate: 7~b24-1.6-0ubuntu7
  Version table:
 *** 7~b24-1.6-0ubuntu7 0
        500 http://se.archive.ubuntu.com hardy-proposed/universe Packages
        100 /var/lib/dpkg/status
     7~b24-1.6-0ubuntu5 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
icedtea-gcjwebplugin:
  Installed: 1.0-0ubuntu7
  Candidate: 1.0-0ubuntu7
  Version table:
 *** 1.0-0ubuntu7 0
        500 http://se.archive.ubuntu.com hardy-proposed/universe Packages
        100 /var/lib/dpkg/status
     1.0-0ubuntu5 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
```
That other test page says that it's supported **but not enabled**. It also spouts the expected terminal error message.
```
GCJ PLUGIN: thread 0x13be820: NP_Initialize
gcjwebplugin.cc:1450: thread 0x13be820: Error: Invalid browser function table.
```

edit: In my quick defense, I'm very, very certain it's enabled. I renamed the .mozilla settings folder to be sure to revert to defaults.

---

### Post by jamesstansell on 2008-06-27
Your plugin symbolic link appears to be the the openjdk-6 plugin, but the plugin package you actually have installed is the icedtea-java7 (and calling java 7 alpha right now might be generous.)

I would recommend that you give the icedtea-gcjwebplugin package a try.  (Make sure that the icedtea-java7-plugin package is not installed anymore.)

---

### Post by Zorael on 2008-06-27
```
zorael@sunspire:/usr/lib/jvm$ sudo aptitude purge icedtea-java7-plugin icedtea-gcjwebplugin
*<truncated removal>*

zorael@sunspire:/usr/lib/jvm$ find | grep plugin
./java-6-openjdk/jre/bin/pluginappletviewer
./java-6-openjdk/bin/pluginappletviewer

zorael@sunspire:/usr/lib/jvm$ sudo aptitude install **icedtea-gcjwebplugin**
*<truncated installation>*

zorael@sunspire:/usr/lib/jvm$ find | grep plugin
**./java-6-openjdk/jre/lib/amd64/gcjwebplugin.so**
./java-6-openjdk/jre/bin/pluginappletviewer
./java-6-openjdk/bin/pluginappletviewer
```
It seems to me that I am using the icedtea-gcjwebplugin library?

---

### Post by jamesstansell on 2008-06-27
> **Zorael said:**
> 
It seems to me that I am using the icedtea-gcjwebplugin library?

Yes, you are right.  I didn't read your apt-get policy output correctly.

Now that I'm looking again it appears that you have two plugin packages installed.  I started to have you remove the icedtea-java7-plugin package but I can't think that firefox should being seeing more than one java plugin.  When you do about:plugins do you only see the openjdk version?

---

### Post by stchman on 2008-06-28
I have 3 different machines running Hardy 64 bit and Icedtea and Flash 9 using Firefox 3.  Here is what I do:

Java:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

For Flash 9:
```
sudo apt-get -y install flashplugin-nonfree
```

---

### Post by Zorael on 2008-06-28
> **jamesstansell said:**
> Yes, you are right.  I didn't read your apt-get policy output correctly.

Now that I'm looking again it appears that you have two plugin packages installed.  I started to have you remove the icedtea-java7-plugin package but I can't think that firefox should being seeing more than one java plugin.  When you do about:plugins do you only see the openjdk version?
Where do you see this?

I've gone over every plugin directory and made sure that any symlinks rhyming with java link toward /etc/alternatives/xulrunner-1.9-javaplugin.so, which I use update-alternatives to manipulate. For that matter, no other *javaplugin.so alternatives seem to have other available plugins to point toward.
```
zorael@sunspire:/etc/alternatives$ for X in `ls -w1 *javaplugin.so`; do sudo update-alternatives --config $X; done

There is only 1 program which provides firefox-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides iceape-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides iceweasel-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides midbrowser-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides mozilla-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides xulrunner-1.9-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure.

There is only 1 program which provides xulrunner-javaplugin.so
(/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so). Nothing to configure
```

> **stchman said:**
> I have 3 different machines running Hardy 64 bit and Icedtea and Flash 9 using Firefox 3.
Key word: Firefox **_[COLOR="Red"]3[/COLOR]_**.

---

### Post by Zorael on 2008-06-28
Forgot some stuff.

> **jamesstansell said:**
> When you do about:plugins do you only see the openjdk version?
No, and my plugins directories (all relevant ones; mozilla, xulrunner*, firefox) don't contain any other java symlinks.

> **stchman said:**
> I have 3 different machines running Hardy 64 bit and Icedtea and Flash 9 using Firefox 3.
I can get Flash 9 installed but it crashes nspluginwrapper on every other flash page. Did a solution for this emerge?

---

### Post by philinux on 2008-06-28
I'm using GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so

With Flash 10 beta
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 b218

Working fine. Occasional npbinviewer crash but it does not crash FF.

---

### Post by Zorael on 2008-06-28
> **philinux said:**
> I'm using GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so

With Flash 10 beta
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 b218

Working fine. Occasional npbinviewer crash but it does not crash FF.
Is this in Firefox 2 or 3?

---

### Post by philinux on 2008-06-28
Soz eyes must be going, FF3

---

### Post by stchman on 2008-06-29
Why would you want FF2 when FF3 is far superior?  Just my thoughts.

---

### Post by Zorael on 2008-06-29
Flash crashing npviewer springs to mind.

---

### Post by Sebastral on 2008-07-20
Nope, and I'm using swiftweasel 2.0.0.15. Oh well, I had to make the switch to 3 sooner or later..

---

