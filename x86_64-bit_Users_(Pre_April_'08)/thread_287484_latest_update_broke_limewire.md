---
title: "latest update broke limewire"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2006-10-28
Last night Limewire was working fine. This morning I installed the latest update, lib-something (not sure, don't know how to check) and now limewire is not loading properly.

The loading screen comes up and it gets to the message 'loading core components' then my computer freezes - music keeps playing and I can use the mouse, but nothing else works. I ran it from terminal and no error messages appeared, it just stopped loading when it froze.

I tried uninstalling and reinstalling. I'm on AMD64 running limewire in a 32-bit chroot.

Can anyone help please?

Thanks

---

### Post by FluffyElmo on 2006-10-29
I've had a similar lock-up, just not with Limewire. Have you tried running Limewire with a 64bit JVM? No reason why it shouldn't work I run Eclipse and Azureus that way.

---

### Post by ryan76 on 2006-10-30
Well I installed limewire with --force-architecture and it needed Java. So I installed j2re1.4 from the repositories and I'm still getting the OOPS error:

```
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

??

---

### Post by FluffyElmo on 2006-10-30
Sorry for the delay, I wanted to download it and make sure it worked. I got it working using the Sun AMD64 JVM. It think it is possible to install it via Synaptic but I download it so the instructions here reflect that.

**To install Java...**

Download the *Linux x64 Platform - J2SE(TM) Runtime Environment 5.0 Update 9* JVM from [http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp"), select  "*Linux x64 self-extracting file (use 32-bit version for applet and Java Web Start support))*".

Go to where you downloaded it in a terminal and type:
```

chmod 777 jre-1_5_0_09-linux-amd64.bin
./jre-1_5_0_09-linux-amd64.bin
```
Follow the prompts and it should install the JVM in your home directory. 


**To Install Limewire...**

Launch a terminal window and type the following:
```

wget http://www.limewire.com/LimeWireSoftOther
unzip LimeWireOther.zip
cd LimeWire
/home/username/jre1.5.0_09/bin/java -jar LimeWire.jar

```

This downloads LimeWire for "Other" platforms, basically pure Java. Unzips it and then runs it using the JVM you installed. If you already had a suitable JVM then *java -jar LimeWire.jar* would suffice.

---

### Post by slacker9876 on 2006-10-31
I don't mean to be a buzzkill here but y'all know limewire was identified as spyware used in a national identity theft ring in the US ... right?

---

### Post by FluffyElmo on 2006-11-01
I think it's been adware/spyware free for a while now. There used to be a "Clean LimeWire" project but it stopped when the original went adware free. You can also download the source and run that. 

I'm mostly an Apollon guy myself, but since I know Java I figured I could help out:)

---

### Post by ryan76 on 2006-11-02
Awesomeness, thank you. It works now, and probably a bunch of future stuff too!

Could I be cheeky and ask how to make a menu item to run it? I put that long command into the Command field but it doesn't work, running in terminal or not.

---

