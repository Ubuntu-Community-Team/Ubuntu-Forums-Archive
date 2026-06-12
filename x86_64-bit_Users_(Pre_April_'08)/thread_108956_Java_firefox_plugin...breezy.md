---
title: "Java firefox plugin...breezy"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by dasaivet on 2005-12-27
Hi there,

I just upgraded to breezy a couple of days ago..great stuff!

I have one problem...In Hoary i installed the plugins for java in firefox using the IBM Java 1.5 Jre. It wokred perfeclty.

In breezy I tried the same procedure but it doesn't seem to work...when I link the plugin into the firefox plugins directory nothing happens.

Any ideas?

Cheers

---

### Post by audax321 on 2005-12-27
A quick way to install java is to use the PLF repositories available here: [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

Then, just do: sudo apt-get install sun-j2re1.5

I didn't have to link anything and Firefox just started using it.

---

### Post by dasaivet on 2005-12-27
Thanks for that.
But I already have installed Java 1.4 from IBM which I got used to and wors fine for uni projects...so I would like to keep that.
I just want to use the plugins for firefox without changing my ibm java installation...is this possible by getting sunjre?

Cheers

---

### Post by audax321 on 2005-12-27
Not sure, but the sun jre is installed in: /usr/lib/j2re1.5-sun

I'm assuming if the paths are different it shouldn't cause a problem. But, again, not sure :)

---

### Post by sulobanks on 2005-12-27
I saw this thread and was amazed that maybe I could install sun java with apt. Alas, it appears the PLF repository is x86 only. No PPC :(  Or did I miss something on their website? Looks like I could try to build from source, but since I haven't heard from a lot of other ppc users doing that, I'll assume it's a rather painful process. I'm currently trying to figure out how to make the jre plugin from the IBM java work in Firefox.  If I succeed, I'll post what I did (even if I don't understand it). ;)

---

### Post by pvz on 2005-12-28
[QUOTE=sulobanks]I saw this thread and was amazed that maybe I could install sun java with apt. Alas, it appears the PLF repository is x86 only. No PPC :(  Or did I miss something on their website?[/QUOTE]

[http://packages.freecontrib.org/ubuntu/plf/pool/powerpc/non-free/ibm-java/](http://packages.freecontrib.org/ubuntu/plf/pool/powerpc/non-free/ibm-java/)
Get it directly from there, or with apt-get after adding the right depository to your /etc/apt/sources.list:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

---

### Post by dasaivet on 2005-12-28
Ok so I got it working now...It was a matter of installing 2 other packages. Here's a little howto to get the java plugin for firefox..if it didn't work by following [https://wiki.ubuntu.com/JavaPPC?highlight=%28ppc%29%7C%28java%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28ppc%29%7C%28java%29)

1. Go to www6.software.ibm.com/dl/lxdk/lxdk-p
2. Download ibm-java2-jre-50-linux-ppc.tgz (this is the ibm JRE)
3. Extract it anywhere you want

4. sudo apt-get install libglib1.2
    sudo apt-get install libgtk1.2

5. cd /usr/lib/mozilla-firefox/plugins
    sudo ln -s /anywhere/ibm-java2-ppc-50/jre/bin/libjavaplugin_oji.so

This way you don't need to install it from repositories and it doesn't cause problems with Java 1.4

thanks again

PS: I saw a post with people having trouble running Limewire. Just get IBM Java 1.5 SDK and run it java -jar LimeWire.jar

---

### Post by Jason-X on 2006-01-02
I'm a bit confused with this whole Java thing. The only reason I want Java is to run Limewire. Should I just install the SDK, or can I install the JRE and SDK?

---

### Post by dasaivet on 2006-01-02
For Limewire get the SDK.
To run Limewire: cd into LimeWire dir and "java -jar LimerWire.jar"

---

### Post by neels on 2006-01-11
@Jason-X: The SDK also contains the JRE. (in the jre subdirectory)
SDK = JDK = Software Development Kit = Java Development Kit
JRE = Java Runtime Environment.

Obviously, the development kit also has to contain the runtime environment. But, the runtime environment does not contain the development tools. Installing both is nonsense.
It is most confusing to newbies, but don't panic dude.....

for the firefox java plugin, try this one: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

### Post by Jason-X on 2006-01-14
Thanks guys:) 

I finally have LimeWire working on PPC.

---

### Post by will.first on 2006-02-13
I have an iBook (white clamshell 500Mhz circa 2002) with Breezy installed, no problem getting everything to work, but this firefox-java plugin thing is driving me insane...

j2sdk-ibm-ppc Java 1.5 works well on its own.  It is my default java, with links to all the programs added in /usr/bin, and paths to the ...jre/bin and ...jre/lib added.  LimeWire runs flawlessly on it (except for LimeWire's media player - no problem since I prefer gxine anyway).

The browser plugin works perfectly under Mozilla browser, but will not work under Firefox.  I tried it with the firefox 1.07 from Ubuntu and the browser just terminates if an applet loads.  I then installed firefox 1.5 (without replacing 1.07) and the firefox works perfectly, until it tries to run an applet and terminates.  I'm using libjavaplugin_oji.so in all instances, linked (not copied) from the ...jre/bin.

Anyone have this happening?  Any ideas for me to try?

---

### Post by will.first on 2006-03-19
I know this is an old thread now but I thought I should share my solution...

After switching to Mozilla every time I hit a page with java for a few weeks I realized how ridiculous it is to need two browsers.  I prefer firefox, especially for Adblock.  AHA!  ADBLOCK!  I removed Adblock Plus and the browser stopped crashing upon loading java applets.  I tried switching to Adblock (not Plus) but the crashing started again.

If anyone else has a problem with the IBM J2SE firefox plugin on Breezy PPC and Adblock is installed, remove Adblock.  Disabling it isn't enough, you have to uninstall it.

Now my quest is to find a way to get back some form of ad blocking without killing java.

---

