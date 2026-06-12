---
title: "Java"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sayers on 2007-07-19
Hello, I've googled around a little bit and seen a lot of alternatives on installing java. however they aren't guaranteed in my oppinion. Can anyone who has got java working explain how I should do it?

---

### Post by Kilz on 2007-07-19
> **Sayers said:**
> Hello, I've googled around a little bit and seen a lot of alternatives on installing java. however they aren't guaranteed in my oppinion. Can anyone who has got java working explain how I should do it?

The only safe version of java is from sun. But its 32bit, and needs some setup and a 32bit browser to install (link in my signature) There is a jgc-compat plugin. But it runs without a security manager, thats not a good idea imho.

---

### Post by tszanon on 2007-07-19
I use a 32bit chroot for Firefox since breezy (5.10). So, it's easy: just download the JRE from [http://java.sun.com](http://java.sun.com) (the binary version, not the rpm) and install it. If I recall correctly, you will need to create a symbolic link in the plugin folder of Firefox, but that's just as easy.

---

### Post by phidia on 2007-07-19
I got here looking for a Q&D java plugin install how-to.
I'm using gutsy, is there any difference that anyone knows about to getting the plugin to work with 64bit gutsy? Thanks!

---

### Post by Sayers on 2007-07-19
> **tszanon said:**
> I use a 32bit chroot for Firefox since breezy (5.10). So, it's easy: just download the JRE from [http://java.sun.com](http://java.sun.com) (the binary version, not the rpm) and install it. If I recall correctly, you will need to create a symbolic link in the plugin folder of Firefox, but that's just as easy.

 How do I create this symbolic link?

---

### Post by nielson on 2007-07-19
The best way I found is use Blackdown, the Java compiled by IBM. It works fine, but it still in version 1.4.2, the sufficient to java web applets.

You can download it at:
[http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html](http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html)

A more direct link:
[ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/JDK-1.4.2/amd64/03/j2re-1.4.2-03-linux-amd64.bin](ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/JDK-1.4.2/amd64/03/j2re-1.4.2-03-linux-amd64.bin)

Logged as root, copy this file to /opt directory, make it a executable ans install it:
```
# cp j2re-1.4.2-03-linux-amd64.bin /opt
# chmod +x j2re-1.4.2-03-linux-amd64.bin
# ./j2re-1.4.2-03-linux-amd64.bin
```

Now, go to /usr/lib/mozilla-firefox/plugins/ directory and make a symbolic link to the plugin:
```
# cd /usr/lib/mozilla-firefox/plugins/
ln -s /opt/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
```

That is it...

As you can have any number of Java machines in your system, you can install the Sun's official x64 JDK/JRE for other uses.

---

### Post by tszanon on 2007-07-19
> **Sayers said:**
> How do I create this symbolic link?
Just like nielson wrote above. The only difference is that I create the link under my home folder, like this:
```
cd ~/.mozilla/plugins
ln -s /opt/jre1.6.0_01/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by phidia on 2007-07-20
Nielson, Thanks for the clear guide. It works in Epiphany, but not in Firefox. Everything is installed-no errors during install symbolic links are there, but java doesn't work in firefox.

Added later:
Actually it only partially works in Epiphany it shows as installed at java check/test sites but it won't play applets.
FF doesn't show as installed.

---

### Post by windtalker on 2007-07-20
I did a little of what nielson said to do and a little of what tszanon said to do and now have jre1.6.0.0 succesfully installed into my sytem. I even have the link installed into my mozilla firefox folder :) ,,,,,,,,,,,,,,,,,,,,,,,,,,,,with a big red X next to the folder. :mad: Permission is denied on alowing me to change the permissions to allow it to run. I can't find any documentation that will tell me how to change the permission to allow it to run when I go somewhere that uses the jre.  I also tried installing Kaffe as a runtime environment through synaptic with no success at having a runtime environment.:confused:

---

### Post by tszanon on 2007-07-20
> **windtalker said:**
> I did a little of what nielson said to do and a little of what tszanon said to do and now have jre1.6.0.0 succesfully installed into my sytem. I even have the link installed into my mozilla firefox folder :) ,,,,,,,,,,,,,,,,,,,,,,,,,,,,with a big red X next to the folder. :mad: Permission is denied on alowing me to change the permissions to allow it to run. I can't find any documentation that will tell me how to change the permission to allow it to run when I go somewhere that uses the jre.  I also tried installing Kaffe as a runtime environment through synaptic with no success at having a runtime environment.:confused:
If I recall correctly, it's not necessary to change permissions...but, anyway, the syntax is:
```
sudo chmod +x <filename>
```
When I get home I'll take a look at it.

---

### Post by tszanon on 2007-07-20
Well, I don't have a solution now, only 2 questions:
1. What have you done, exactly?
2. What are the error messages?

---

