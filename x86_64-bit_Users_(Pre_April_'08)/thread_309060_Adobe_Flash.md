---
title: "Adobe Flash?"
date: 2006-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sonic Reducer on 2006-11-29
i have a 64-bit XP3200+ on an Asus A8N-VM CSM motherboard, and i can't install flash. please help.

i downloaded the [Reccomended file]("http://www.macromedia.com/go/getflashplayer/") to my desktop and extracted the file, then i typed into terminal:
```
/home/ryan/Desktop/install_flash_player_7_linux/flashplayer-installer
``` and it said:
```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

```

can i fix this or am i SOL?

---

### Post by ditsch on 2006-11-29
The Adobe Flash player is 32 bit-only. You may try to run it with linux32 or you can follow this [Howto]("http://www.ubuntuforums.org/showthread.php?t=202537") to get Flash running on a 32-bit Firefox at least.

---

### Post by Magnes on 2006-11-29
You can try gnash also.

---

### Post by LaoLiulaoliu on 2006-11-29
I have the same problem.
Please help us!

---

### Post by gratefulfrog on 2006-11-29
Please look at the thread listed below. There is no other solution for flash on amd64.

[http://www.ubuntuforums.org/showthread.php?t=202537]("http://www.ubuntuforums.org/showthread.php?t=202537")

It's a struggle but may work!
Good luck!

---

### Post by ByeByeBill on 2006-11-29
I beg to differ,there is an eaisier way.Use Automatix2([www.getautomatix.com)and](www.getautomatix.com)and) install swiftfox and the multimedia codecs packages.It gives you flash and java(32 bit),and is very easy to do.

---

### Post by tall-male on 2006-11-29
The very simple way: install Firefox 32-bit from the tar file ([www.mozilla.com](www.mozilla.com)) in /opt/firefox/
Install flash (7 and 9-upgrade) in /opt/flash and create sumbolic links in ~/.mozilla/plugins:

libflashplayer.so -> /opt/flash/libflashplayer.so
flashplayer.xpt -> /opt/flash/flashplayer.xpt

Works perfectly, I have no problemen playing Flash.

I did the same for Java; installed Java 32 bit from [www.java.com](www.java.com) (using the tar file) in /opt/java32 and create a symbolic link in ~/.mozilla/plugins:

libjavaplugin_oji.so -> /opt/java32/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so

:-D

Why bother about chroot Firefox, Automatix, plugin wrappers etc. Firefox 32 bits run perfectly on my Ubuntu 64 bit. :p

---

### Post by xopher on 2006-11-29
Im using nspluginwrapper (0.9.90.4) at the moment -- works like a charm, and its easy to set up too.

Check out this thread [http://ubuntuforums.org/showthread.php?t=277077&highlight=nspluginwrapper](http://ubuntuforums.org/showthread.php?t=277077&highlight=nspluginwrapper)

The last post, at least for now, is mine - Ive uploaded the latest nspluginwrapper debs and you'll get information there.

Have fun!

---

### Post by Kilz on 2006-11-29
> **tall-male said:**
> The very simple way: install Firefox 32-bit from the tar file ([www.mozilla.com](www.mozilla.com)) in /opt/firefox/
Install flash (7 and 9-upgrade) in /opt/flash and create sumbolic links in ~/.mozilla/plugins:

libflashplayer.so -> /opt/flash/libflashplayer.so
flashplayer.xpt -> /opt/flash/flashplayer.xpt

Works perfectly, I have no problemen playing Flash.

I did the same for Java; installed Java 32 bit from [www.java.com](www.java.com) (using the tar file) in /opt/java32 and create a symbolic link in ~/.mozilla/plugins:

libjavaplugin_oji.so -> /opt/java32/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so

:-D

Why bother about chroot Firefox, Automatix, plugin wrappers etc. Firefox 32 bits run perfectly on my Ubuntu 64 bit. :p

You can do that, or you can run my install script. Nothing to install like automatix. link in my signature.

---

### Post by ByeByeBill on 2006-11-29
Jeez,you guys make things sooooo hard...Automatix2 now downloads with just one click(no more cutting and pasting)and includes much more than just java and flash(32 bit),it also has a whole slew of programs that work in 64 bit Ubuntu,because it was designed to work in Ubuntu 64!!If you havent checked it out in the last week or so,ya gotta do it.Its the best thing to happen to 64 bit Ubuntu(for now,at least!):mrgreen:

---

### Post by non-free on 2006-11-30
> **ByeByeBill said:**
> Jeez,you guys make things sooooo hard...Automatix2 now downloads with just one click(no more cutting and pasting)and includes much more than just java and flash(32 bit),it also has a whole slew of programs that work in 64 bit Ubuntu,because it was designed to work in Ubuntu 64!!If you havent checked it out in the last week or so,ya gotta do it.Its the best thing to happen to 64 bit Ubuntu(for now,at least!):mrgreen:

Yes a slew of non-free software like Swiftfox. Anyone who prefers free as in freedom software should think twice about installing automatix.

---

### Post by ByeByeBill on 2006-12-01
Jeez,you again.Will you stop trying to say everything non-free is evil?Get off this forum already.NO ONE CARES ABOUT WHAT YOU THINK.And if you respond to any of my posts,anywhere on this forum,again,Ill have you thrown off.No joke.

---

### Post by slicker on 2006-12-02
> **ByeByeBill said:**
> Jeez,you again.Will you stop trying to say everything non-free is evil?Get off this forum already.NO ONE CARES ABOUT WHAT YOU THINK.And if you respond to any of my posts,anywhere on this forum,again,Ill have you thrown off.No joke.

You cant have anyone thrown off of the forum. Only mods can do that. I think non-free is right. We shouldn't be using software that takes away our freedom.

---

### Post by matthew on 2006-12-02
I think this thread has run its course. I'm closing it now.

---

