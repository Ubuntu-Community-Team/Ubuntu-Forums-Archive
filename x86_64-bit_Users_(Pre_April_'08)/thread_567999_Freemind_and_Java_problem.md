---
title: "Freemind and Java problem"
date: 2007-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by lensteruk on 2007-10-05
I have just installed Freemind 0.8 which seems have partial functionality on my system for some reason. I have been reading around this subject and think the problem lies with my install of java.

I would be grateful for some assistance in getting this sorted as i am new to Linux and do not want to put a perfectly serviceable and very fast platform at risk thro tinkering before i am suitably educated.

my java install returns the following

mark@mark-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

The problems manifest as 

1. Unable to print (despite all other apps working fine with the printer)
2. I cannont get the preferences element from freemind toolbar to execute. 

I note that at [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu)
there is a note about freemind 0.8 not supporting Java 6 but freemind 0.9 will.

The question is will rolling back to java 5 (i am assuming that means 1.5) cause problems on my system ? If so i might wait until freemind 0.9 is on the streets.

My system is ubuntu feisty Fawn 64Bit AMD install.

grateful for any pointers before i go causing trouble from the command prompt !!:)

---

### Post by lensteruk on 2007-10-05
Not sure if this is related i now cannot get sound from embedded apps in my browser. ?? Both swiftweasel and firefox.

:confused::confused:

---

### Post by Kilz on 2007-10-05
> **lensteruk said:**
> I have just installed Freemind 0.8 which seems have partial functionality on my system for some reason. I have been reading around this subject and think the problem lies with my install of java.

I would be grateful for some assistance in getting this sorted as i am new to Linux and do not want to put a perfectly serviceable and very fast platform at risk thro tinkering before i am suitably educated.

my java install returns the following

mark@mark-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

The problems manifest as 

1. Unable to print (despite all other apps working fine with the printer)
2. I cannont get the preferences element from freemind toolbar to execute. 

I note that at [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu)
there is a note about freemind 0.8 not supporting Java 6 but freemind 0.9 will.

The question is will rolling back to java 5 (i am assuming that means 1.5) cause problems on my system ? If so i might wait until freemind 0.9 is on the streets.

My system is ubuntu feisty Fawn 64Bit AMD install.

grateful for any pointers before i go causing trouble from the command prompt !!:)

Java 1.5 is ok, it wont hurt anything if you want to go back and try it.

---

### Post by lensteruk on 2007-10-08
Java 1.5 has resolved the problem. Many thanks for the advice.

:KS

---

