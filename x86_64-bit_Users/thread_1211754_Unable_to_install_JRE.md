---
title: "Unable to install JRE"
date: 2009-07-13
forum: x86 64-bit Users
---

### Post by ngchaudhry on 2009-07-13
Hi
I am not new to UNIX but new to Ubuntu and the packages. I have a Acer Aspire with Intel 2 Duo processor running Ubunto 9.04 Jaunty Jackalope. I am trying to install JRE but I get the following 

Unpacking...
Checksumming...
Extracting...
./install.sfx.23464: 1: ELF: not found
./install.sfx.23464: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

when I try to run  jre-6u14-linux-x64.bin 

I have searched the forum and seen some old posts ( 2008 ) where people have said that such errors have to do with ia32-libs library being not installed. I tried installing it with those suggestions but I am unable to accomplish the task. May be I missed some relevant post so any new suggestion or reference to a relevant old post will be very helpful.
Thanks
Nadeem

---

### Post by sanderj on 2009-07-13
I guess you've downloaded SUN Java? If so: don't do that. 

Best ways to install Java:

Via GUI:
Ubuntu logo -> Add/Remove -> fill out 'java'. Then select the SUN Jave Runtime Environment, and install it.

Via commandline:
sudo apt-get install sun-java6-jre


Possibly you first have to 1) enable Universe and Multiverse repositories via System -> Administration -> Software Source, and 2) enable "All Available Applications" in Add/Remove.

HTH

---

### Post by Sef on 2009-07-14
> Via GUI:
Ubuntu logo -> Add/Remove -> fill out 'java'. Then select the SUN Jave Runtime Environment, and install it.


Not quite right, it should be this:

Ubuntu logo (Applications) > Add/Remove > Show: All Available Software > Search: Sun Java 6 > tic both boxes > apply changes > apply > close

---

### Post by QIII on 2009-07-15
The Ubuntu repositories currenly (as of this post) are Update 13, whereas Sun's latest update is 14 - which is the version the OP has attempted to install.

However, it is not likely that Update 14 would be critical.

For the OP:  Please not that the .bin you are trying to install is the 64 bit version (notice the "x64"), which will not work if you are running 32 bit Jaunty.

Since it is not likely that Update 14 will be critical for you, either add from Synaptic or via the terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin
```If you want, add these two also:  

```
sun-java6-fonts sun-java6-jdk
```.

After either method of installation, make sure that Sun is preferred over OpenJDK by 

```
sudo update-java-alternatives -s java-6-sun
```

Finally, check your version

```
java -version
```

On my machine, I have the Update 14 version, but you should get something back like this:

```
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
```

---

### Post by Yellow Pasque on 2009-07-15
Jaunty repos were just updated to JRE 6u14 :popcorn:
[http://packages.ubuntu.com/jaunty-updates/sun-java6-bin](http://packages.ubuntu.com/jaunty-updates/sun-java6-bin)

---

### Post by QIII on 2009-07-15
Hadn't made it out to my mirror yet.  Interesting.

But you are right.  It is on the main server, by golly!

---

### Post by ngchaudhry on 2009-07-16
Thank you all for your replies. It took me quite a while to download all the updates because of power failures and slow internet connection. But I finally got Java up and running. Thanks again.
Nadeem

---

