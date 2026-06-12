---
title: "Java and Ubuntu Hardy 64 bit"
date: 2008-06-16
forum: x86 64-bit Users
---

### Post by stchman on 2008-06-16
Hello all, I am posting this for information.

There is a lot of talk about Java and Hardy 64 bit.  The main thing centers around the SUN Java plugin for web browsers.

I run Hardy 64 on an Athlon 64 machine and this works very well for me.

I use Icedtea for my Java in 64 bit.

```
sudo apt-get install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

The most important thing is that the browser plugin WORKS for 64 bit.  I have found that nearly ALL sites that use imbedded Java applets function with the Icedtea plugin.

Now if you are a hardcore Java programmer the Icedtea version may not cut it for you.  I have personally noticed that Swing Java applications don't look the same when using the Icedtea Java as the SUN Java.  If you use AWT Java apps then Icedtea works fine.  For those times you can use SUN Java besides the plugin for you Java work.

```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre
```

Now it is reported that SUN will be releasing a 64 bit browser plugin this month or next so all will be good.

There are some that prefer a complete open source environment so they may prefer the Icedtea version.

I find that for the non Java developer the Icedtea Java.

I hope this has helped.

---

### Post by Kilz on 2008-06-16
> **stchman said:**
> 

Now it is reported that SUN will be releasing a 64 bit browser plugin this month or next so all will be good.



Do you have a link to that info?

---

### Post by Yellow Pasque on 2008-06-16
Note that 'IcedTea' is now OpenJDK. See the sticky at the top of this forum.

---

### Post by stchman on 2008-06-17
> **Kilz said:**
> Do you have a link to that info?

It is in this forum.  I realize that the forum is not gospel.

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by Kilz on 2008-06-17
> **stchman said:**
> It is in this forum.  I realize that the forum is not gospel.

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

Thanks, but I was hoping for an announcement from Sun.

---

### Post by Sef on 2008-06-17
> Thanks, but I was hoping for an announcement from Sun.

It was a Sun document that had that statement one it.  If I can find it again. I will provide a link.

---

### Post by stchman on 2008-06-17
I have been noticing that a few websites don't work with the Icedtea plugin.  I use a very few websites that need Java so it is not a huge factor for me.

I think it is strange that SUN would give us the JRE, JDK, and the binaries in 64 bit but stop when it comes to the plugin.

I wonder what Apple is doing?  OS X on Core 2 Macs are 64 bit.  I wonder what they are doing for Java applets in Safari?

---

### Post by Nepherte on 2008-06-17
They don't really follow the sun releases. That's why you can't get 1.6 for Mac OSX. Not sure, but they must change some code to make it work obviously, or they use 32bit libraries.

---

