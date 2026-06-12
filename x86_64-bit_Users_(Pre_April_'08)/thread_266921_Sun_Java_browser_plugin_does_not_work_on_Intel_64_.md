---
title: "Sun Java browser plugin does not work on Intel 64 bit dual processor chip"
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jwbales on 2006-09-27
I installed Dapper on a Gateway GT4024 computer with an Intel 64 bit processor (Intel Pentium D 805 Dual core 64 bit processor). I installed Sun Java JRE and enabled it on Firefox--the only browser which is available for 64 bit machines. (I was surprised to learn that Opera, Mozilla and Galeon will not install on 64 bit Dapper, at least not with the Intel 64 bit processor.) The Java browser plugin doesn't work. I have /usr/lib/mozilla/plugins/libjavaplugin_oji.so as well as $HOME/.mozilla/plugins/libjavaplugin_oji.so which is a soft link to /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
 
Although the Java browser plugin does not work, *javascript* does work. But when I visit websites which *check* for the presence of javascript, they inform me that I must enable javascript and refuse to serve me the page.

Has anyone been able to get the Java browser plugin working on the Intel 64 bit processor? 

Has anyone been able to get websites to recognize that javascript is present and working?

---

### Post by kuja on 2006-09-28
That's funny, I'm looking at this post right now in Opera, on a 64-bit machine.

At any rate, I've been working on something lately to solve problems just like this. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=266290")

The solution to using java applets within your browser on a 64-bit machine, at least for the moment, is to use 32-bit java and a 32-bit browser.

---

### Post by RAOF on 2006-09-28
Sun doesn't distribute a 64bit Java web-plugin.  What you have there is a 32bit Java plugin, which won't work with the 64bit Firefox you've got.

Your options from here include: 
1) Complain to Sun and get them to release a 64bit Java plugin
2) Install blackdown-java, which is a Java 1.4 implementation which includes a 64 bit plugin
3) Try the GCJ gnu-java plugin.
4) Get a 32bit version of Firefox and use that.

---

### Post by kuja on 2006-09-28
> **kuja said:**
> That's funny, I'm looking at this post right now in Opera, on a 64-bit machine.

At any rate, I've been working on something lately to solve problems just like this. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=266290")

The solution to using java applets within your browser on a 64-bit machine, at least for the moment, is to use 32-bit java and a 32-bit browser.
I hadn't actually tested my Java fix yet, so I just now did, by looking at a java applet in Opera... worked fine, wait, tried it in Firefox32, works great.

I'll have to get the app to copy the plugin file to the firefox32 plugin folder, and have leave a message on how to get opera to recognize the plugin.... hmmmmmmmmmmm

---

