---
title: "Java+Firefox2+Edgy+amd64 = crash"
date: 2006-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2006-11-30
Every time I go to this site Firefox crashes:
[http://www.hopeaz.com/Chat2.htm](http://www.hopeaz.com/Chat2.htm)

Nothing I've tried has helped (easyUbuntu, Downloading from Java and following their instructions).

Can anyone have it not crash (and see a logon applet) and give me help?

Thanks! ](*,) 

Here is my setup:
$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

$ firefox -version
Mozilla Firefox 2.0, Copyright (c) 1998 - 2006 mozilla.org

$ uname -a
Linux office 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

---

### Post by drphilngood on 2006-11-30
I´m not sure if this is what you´re looking for but [NoScript]("https://addons.mozilla.org/firefox/722/") blocks java, flash and even other plugins.  So, you can access the site while using this and not crash.

If that doesn´t suit your needs, you can use [Opera]("http://www.opera.com/pressreleases/en/2006/07/06/02/").  I have the page loaded in [Opera]("http://www.opera.com/pressreleases/en/2006/07/06/02/") and can see the user login applet right now.

---

### Post by fabertawe on 2006-12-01
I can load that page and see the logon applet using Swiftfox (32bit Firefox 2) and Sun's 32bit Java browser plugin. I believe you can use Automatix if you don't want to install them manually.

Paul

---

### Post by non-free on 2006-12-01
> **fabertawe said:**
> I can load that page and see the logon applet using Swiftfox (32bit Firefox 2) and Sun's 32bit Java browser plugin. I believe you can use Automatix if you don't want to install them manually.

Paul


Don't use the non free Swiftfox that takes away freedom to redistribute that Firefox gives you. The [less than one second speed difference]("http://www.apcstart.com/node/3097") isn't worth it.

---

### Post by fabertawe on 2006-12-01
> **non-free said:**
> Don't use the non free Swiftfox that takes away freedom to redistribute that Firefox gives you. The [less than one second speed difference]("http://www.apcstart.com/node/3097") isn't worth it.

This is the umpteenth time I've seen you say this. I think we all know how you feel now so there's no need to repeat yourself again.

Paul

---

### Post by non-free on 2006-12-01
> **fabertawe said:**
> This is the umpteenth time I've seen you say this. I think we all know how you feel now so there's no need to repeat yourself again.

Paul

There are no rules saying you cant voice your opinions on multiple threads.

---

### Post by linuxted on 2006-12-01
> **fabertawe said:**
> This is the umpteenth time I've seen you say this. I think we all know how you feel now so there's no need to repeat yourself again.

Paul

Paul,
     THANK YOU!!!!   This is the ONLY thing that has worked for two revisions of Ubuntu for me!  Swiftfox it is unless someone fixes Firefox/Java on that site (which I've reported to bugzilla many months ago).

linuxted
:D

---

### Post by radiobuzzer on 2006-12-02
Yes, but if not Swiftfox, what can I do??? I need a fast solution that I can browse pages, with Flash and Java. I spent one or two hrs trying to figure out a solution for FIrefox, but nothing. Please, when you are saying NO to something, propose some alternative.

---

### Post by fabertawe on 2006-12-03
For those who do not wish to use Swiftfox, check out the sticky "How to get specific programs to run under Dapper Drake 64-bit edition" for the link for Kilz's 32bit Firefox HowTo.

Paul

---

