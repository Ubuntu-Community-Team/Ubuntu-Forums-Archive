---
title: "Frostwire installed, but won't run."
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by trekguy on 2009-02-14
No success in the AB forum, so I'll try here. :)

I installed Frostwire, and there is an icon in Apps/Internet. When I click on it, it does nothing. When I run it in Terminal, I get the message shown below. I have the new 64 bit Java 1.6.0_12

It does find Java, but there seems to a problem accessing it when Frostwire starts to load.  :confused:

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in /usr/lib/ hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
[B]Java exec found in /usr/java/jre1.6.0_12/bin/
Suitable java version found [/usr/java/jre1.6.0_12/bin/java = 1.6.0_12][/B]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
[B]Unable to access jarfile FrostWire.jar
[/B]
/usr/java/jre1.6.0_12/bin/
************************************************** ****************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found

---

### Post by trekguy on 2009-02-17
[B]The version of Java in your PATH is:
/usr/lib/frostwire/runFrostwire.sh: line 158: java: command not found[/B]

Anyone have any ideas about how I can get Frostwire to see the path to Java 1.6, and/or find the proper command for line 158?

---

### Post by CoreyB. on 2009-02-17
Try this

[Java - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Java")

It resolved a problem I had with java.

---

### Post by Mr_bleu on 2009-02-17
I use frostwire and have to use sun's java to get it working.  Below is the command to choose your java.  I got the lines below that from another posting in the forums when I typed config java in search.

sudo update-alternatives --config java

"sun-java6-plugin, sun-java6-bin, and sun-java6-jre are the 3 required to make the plugin work. The fonts are a good add on."

---

### Post by trekguy on 2009-02-18
Hmmm, SunJava6 is 32 bit... I have the new 64 bit SunJava... 1.6_12.  It works great in everything else, it even works with Yahoo PageBuilder.

Frostwire has recognized Java in my system, and knows where it is... but there seems to be a path problem still.

---

### Post by novafluxx on 2009-02-19
How does one set thier path?  I want to download and install the new Java for 64 bit, but I only know how to symlink the plugin, not put java in the path

---

### Post by Yellow Pasque on 2009-02-19
I personally prefer gtk-gnutella as my gnutella client. You might want to give that a try (it's available from Ubuntu's standard repos). Even if you ultimately decide that you prefer frostwire, it can serve as a temporary way for you to access gnutella.

---

### Post by trekguy on 2009-02-19
> **Temüjin said:**
> I personally prefer gtk-gnutella as my gnutella client. You might want to give that a try (it's available from Ubuntu's standard repos). Even if you ultimately decide that you prefer frostwire, it can serve as a temporary way for you to access gnutella.

Installed gtk-gnutella from the repos.  I get a message stating that it is an "ancient version" (0.96.4)    Says I am TCP abd UDP firewalled.  ??  Also, I get 0/3 connections.  It doesn't seem to work.  :(

---

### Post by Yellow Pasque on 2009-02-19
I take it you're using Hardy/8.04?  

Also, are you behind a router? If so, you'll have to set up port forwarding in you router's setup.

---

### Post by trekguy on 2009-02-19
> **Temüjin said:**
> I take it you're using Hardy/8.04?  

Also, are you behind a router? If so, you'll have to set up port forwarding in you router's setup.

Yes, 8.04.  And yes on the router,as well.  Port forwarding??  Can you explain that, or point me in the right direction?

---

### Post by Yellow Pasque on 2009-02-19
Port forwarding varies by router. You can enter your router setup by pointing your browser to [http://192.168.0.1/](http://192.168.0.1/)
Here's an example [http://kbserver.netgear.com/kb_web_files/N101145.asp](http://kbserver.netgear.com/kb_web_files/N101145.asp)
A useful command to figure out what address your router has assigned to your wireless device is:
```
ifconfig -a
```

---

### Post by trekguy on 2009-02-22
gtk-gnutella won't connect...followed directions for port forwarding... didn't help.  Maybe version is too old??

Reinstalled JRE into /usr/lib/jvm as per SunJava64 thread... still no FrostWire. :(

Running frostwire in terminal results in:

(Don't understand why it can't find unpack200...  I found it in _/usr/lib/jvm/jre1.6.0_12/bin_)

sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
HOSTNAME IS dean-desktop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_12]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO:
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_12"
Java(TM) SE Runtime Environment (build 1.6.0_12-b04)
Java HotSpot(TM) 64-Bit Server VM (build 11.2-b01, mixed mode)

---

### Post by trekguy on 2009-02-22
Alright, here's the fix for running FrostWire in 64 bit Ubuntu...

I upgraded to 8.10 Intrepid... installed FrostWire... works like a charm!!!!

---

### Post by bootdoc on 2009-02-24
doesn't work on my amd64.  neither frostwire nor limewire, apollon will connect.

---

### Post by Tomfitzy on 2009-05-19
hi im new to this can someone please tell me in "engish" what i need to do to get frostwire to open this is what the terminal tells me

tom@thinkpad-r50e:~$ frostwire
HOSTNAME IS thinkpad-r50e
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
hope this is helps thanks

---

### Post by cybrsaylr on 2009-05-20
Use Nicotine-Plus instead which works just as well.
It's in, Applications>Add/Remove>put 'Nicotine-Plus' in the search bar, then install.

---

### Post by Yellow Pasque on 2009-05-20
Tomfitzy, if you installed the 32-bit/i586 .deb of Frostwire from their site, you probably need a 32-bit Java, so..
```
sudo apt-get install ia32-sun-java6-bin
```

---

