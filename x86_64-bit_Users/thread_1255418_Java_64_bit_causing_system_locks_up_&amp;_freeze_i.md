---
title: "Java 64 bit causing system locks up &amp; freeze in Jaunty"
date: 2009-09-01
forum: x86 64-bit Users
---

### Post by bob67 on 2009-09-01
Hi all

I am experiencing intermediate hard locks in Jaunty due to what I believe is Java 64 bit.

While using a Java based application (Eclipse and Virtualbox have both caused the issue) the application will become unresponsive causing all unrelated open applications to hang. 

I am able to move the mouse and operate the Gnome menu to open applications but the applications never come up. (i.e. I open a terminal and it says starting terminal but it never pops up).

If I am lucky, I can force close the application and everything resumes as normal, i.e. the applications I asked to open finally open and all open applications unhang.

I'm not sure how to get any debugging output and thus I am turning here. Output of dmesg does not indicate any soft locks are issues.

Is anyone else experiencing these issues or have any ideas? This is making my system really unstable.

System:

Drives: EXT3

Linux 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

---

### Post by ernstp on 2009-09-03
I have a colleague with the problem also, and googling gives some results for this with exactly update-14. Have you tried a different java version? Haven't tested here yet.

---

### Post by bob67 on 2009-09-03
I noticed a bug submission that might be related as well: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/326477](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/326477)

I'm going to try a previous version of java.

---

### Post by bob67 on 2009-09-04
I've tried updating to 16 and downgrading to 13. I am still experiencing serious hard locks.

---

### Post by bob67 on 2009-09-04
I should also mention that originally I thought this was an EXT4 problem given the known issues but I reinstalled with EXT3 and I am still experiencing the frequent locks.

Applications that are running when it locks:

* VirtualBox
* Firefox
* SQL Developer
* Eclipse
* Pidgin
* Totem Movie Player (Music)

This is the usual mix, however, it has locked without many of them open. I.e. just Eclipse open.

---

### Post by bob67 on 2009-09-04
The freeze occurs at random too. It could be anywhere from several hours to 5 minutes from boot.

My music ALWAYS stops right before the freeze. No repeating music or anything, just stops.

Interestingly, I am able to navigate and use my virtual machine in virtual box even though my host is frozen.

---

### Post by bob67 on 2009-09-04
I have also run dell diagnostics which reported no problems with memory, hard drive, etc.

---

### Post by cooldude on 2009-09-05
> **bob67 said:**
> I've tried updating to 16 and downgrading to 13. I am still experiencing serious hard locks.

I think 64 bit java was implemented in java 6 update 12...

---

