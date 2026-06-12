---
title: "The Blackdown Java(TM) 2 for amd64 / plugin installation"
date: 2005-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardflip on 2005-04-23
Hope this helps someone...

Where to get this: (right click + save link as..)
[ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/01/j2re-1.4.2-01-linux-amd64.bin](ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/01/j2re-1.4.2-01-linux-amd64.bin)

What to do with it?

1. Make shell script executable,
-> chmod +x j2re-1.4.2-01-linux-amd64.bin

2. Run the script,
-> ./j2re-1.4.2-01-linux-amd64.bin
-> Answer "yes" to the question

3. When script execution has been completed, following directory should have been created:

for example i ran the script in ~/download/, and now in download is direcotory called j2re1.4.2

4. Now you can move the j2re1.4.2-directory somewhere else if you want. I moved it to the /opt/j2re1.4.2 (sudo mv j2re1.4.2 /opt).

5. Make symbolic links in firefox/mozilla-plugin directory,
-> cd /usr/local/lib/mozilla-firefox/plugins
-> sudo /opt/j2re1.4.2/plugins/amd64/libjavaplugin_oji.so libjavaplugin_oji.so

And now you have succesfully (hopefully =) installed java + java plugin for mozilla/firefox.

---

### Post by ifrflyer on 2005-04-24
Thanks for that. I also posted an article on my personal site on how to do it with both apt-get and synaptic. 

[http://nickselby.com/articles/technology/?a=1806](http://nickselby.com/articles/technology/?a=1806)

Hope these resources help!

---

### Post by ildfroe on 2005-05-02
I can't get the plugin to work.
It's installed and appears ok in firefox's about:plugins.
However when I visit a site with java (like java.com), firefox just shuts down with a segmentation error.
Anybody have any ideas to solve this?

---

### Post by Gandalf on 2005-05-02
if i were you i wouldn't do that, but i will follow [this HOWTO](http://ubuntuforums.org/showthread.php?t=23592) instead...

---

### Post by ildfroe on 2005-05-02
I've also tried that, doesn't work. All I get is the segmentation fault  :mad: 
Other ideas?

---

### Post by Gandalf on 2005-05-02
[QUOTE=ildfroe]I've also tried that, doesn't work. All I get is the segmentation fault  :mad: 
Other ideas?[/QUOTE]
 weird it worked for me, well ok
sudo apt-get install j2re1.5

---

### Post by DutchLau on 2005-05-02
@Gandalf

Okay, now the question os: Does your guide with Blackdown java work for Hoary 64? 

I get my PC tomorrow, (well the parts at least) and I wanted to know if this will work for Hoary64. It seems like your guide was made for the i386 version, but I could be misteken. 

Cheers, 

DutchLau

---

### Post by Gandalf on 2005-05-02
[QUOTE=DutchLau]@Gandalf

Okay, now the question os: Does your guide with Blackdown java work for Hoary 64? 

I get my PC tomorrow, (well the parts at least) and I wanted to know if this will work for Hoary64. It seems like your guide was made for the i386 version, but I could be misteken. 

Cheers, 

DutchLau[/QUOTE]
 well my guide work with any JAVA version, it uses the make-jpkg that is a debian package to build java deb from a java.bin so it has nothing to do with 32 or 64 just get the right java bin file (either from blackdown or sun, both works too)

---

### Post by DutchLau on 2005-05-02
@ Gandalf

Ooops. Sorry, I was thinking about flash. Now it would be nice if you could also make a Howto on getting Flash working for Hoary 64 ;-) 

DutchLau

---

### Post by Jarz Corp on 2005-05-04
Might just be me but.

I have followed "these" guides, because I wanted to test the difference before I posted.

IT seems that U end up with quite an old version of Java, can this be true.

---

### Post by ebonflame on 2005-05-05
I've tried all the suggestions here with my Hoary Kubuntu.  Each method gives me the same problem.... Firefox segfaults when a java page is accessed.  I've tried the .bin method, the converting the .bin to .deb, and the downlading the deb directly from Blackdown's ftp site and installing it.  Each one results in a Firefox that will kill itstelf when a java page is accessed.

---

### Post by ebonflame on 2005-05-05
Wondering if the segfault was firefox's fault or not, I decided to install Mozilla proper.  It too crashed with a segfault when trying to access Java content.

---

### Post by ildfroe on 2005-05-05
Same here. Epiphany crashes too but with a different message:

INTERNAL ERROR on Browser End: Exec of "java_vm" failed: 2
<
System error?:: Ingen sådan fil eller filkatalog

** (epiphany:15356): WARNING **: Serious fd usage error 16

** (epiphany:15356): WARNING **: Serious fd usage error 17

** (epiphany:15356): WARNING **: Serious fd usage error 15
INTERNAL ERROR on Browser End: Could not read ack from child process

---

### Post by etitor on 2005-06-18
Something similar worked for me! Now I run the Blackdown java plugin in Firefox on 64 bits. Havent find yet a java-enabled webpage that rejects Blackdown Java.

As to installation instructions, however, my advice is:

1. Just search the net for "j2re-1.4.2-01-linux-amd64.bin"

2. Download the package from wherever you can (ftp.tux.org is dead most of the time)

3. Follow the instructions that come with the package (read that readme!).

This is what I did and it worked (for my AMD64 K8 processor running a k8 Ubuntu kernel).

Wish you all luck.

---

