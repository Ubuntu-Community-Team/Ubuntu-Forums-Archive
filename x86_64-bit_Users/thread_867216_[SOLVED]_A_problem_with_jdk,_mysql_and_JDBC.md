---
title: "[SOLVED] A problem with jdk, mysql and JDBC"
date: 2008-07-22
forum: x86 64-bit Users
---

### Post by porchrat on 2008-07-22
I'm running hardy 8.04.1 with sun-java6-jdk, mysql server 5.0.3 (I think...I'm not in front of the Linux machine at the moment but I will confirm this at a later stage) and the latest JDBC (5.1).

The software I'm trying to run is a set of in-house java programs that insert data into mysql databases.  I've been running it with no problems on a Gentoo system.  It was compiled under java1.4 and run under 1.6.  The mysql server was older (version 3 or so) and the JDBC was 1.3.  (again only 100% sure on the java - will check the others in the morning).

I've since moved the software to a new hardy system and have been having some trouble getting it running again.  Whenever I run it (in a nohup session) I get a lot of pagefaults (both major and minor) and I really have no idea what could be causing them. 

I've compiled the software under the above-mentioned sun javac and it seems to communicate with the mysql database fine.

Is there anything that I've missed?  Otherwise does anyone know of any conflicts between the above-mentioned software or have any ideas on what may be causing these pagefaults?

Any help would be greatly appreciated.

If you require any other information from me then please ask.

---

### Post by porchrat on 2008-07-23
checked the new machine this morning and I'm running version 5.051a-3ubuntu5.1 of mysql server.

Again I ask is there anyone out there with any ideas I'm stumped.

Some people have suggested it is a hardware problem, however everything else seems to run fine.  Compiz for example runs easily as does the actual mysql server when I use it directly.

---

### Post by porchrat on 2008-07-24
Don't worry all I solved it on my own.

Some programs were using a JDBC in a separate location so I just updated that version as well and viola.

---

### Post by porchrat on 2008-07-31
Hi all.  Have marked this thread as UNSOLVED again.

While everything is now communicating just fine and databases are being created they are nowhere near the size they were on the old system and some files seem to be missing.

I have a feeling this has to do with the pagefaults, which are still occurring.  If anyone has any suggestions please let me know as I need help.

---

