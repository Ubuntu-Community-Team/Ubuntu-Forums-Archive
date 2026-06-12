---
title: "Java (for firefox)"
date: 2004-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by smoothrt on 2004-10-21
I have yet to find newbie-friendly instructions for allowing firefox to view java, flash, etc in firefox with ubuntu amd64.  If someone could post the recipie, or a link to them, to download, install, configure, etc. from start to finish so amd64 users can view webpages that require java that would be great.  Thank you.

---

### Post by snowx1000 on 2004-10-21
You need to get the amd64 java from [http://www.blackdown.org/](http://www.blackdown.org/)
Once you get that just follow the Installing Java for firefox thread in the howto forum section.  The only thing you need to change in the commands are the directory.  Lemme know if you need more help.

---

### Post by snowx1000 on 2004-10-21
Correction, on the ftp servers they have their own install instructions.  Do the path adding part of those.  It should allow programs such as azureus or limewire to work.

---

### Post by smoothrt on 2004-10-22
Okay, I guess I wasn't clear enough, my fault.  I am a NEWBIE.  The instructions on the blackdown site in the readme and such are not at all sufficient for someone like me.  I don't know the diference between fcs and rc1 and jre and sdk and so on.  I'm trying to read and learn on other websites out there, and I am learning more about this kind of stuff, but I'm not there yet.  Those directions do not even come close to explaining what I need to do so that I can view a website that uses java without seeing a bunch of missing plugin errors. I'm sorry for my ignorance, but I really think there should be better, more straightforward documentation on this somewhere.  I don't even see anything about installing the plugins for firefox, only mozilla.  Is it the same?

Ideally, there really should be some type of DEB package or installer for this in my opinion.  Something like this is annoying and makes me wish I had windows back (and I'm sure all Linux users feel that is a very bad thing).

---

### Post by K6-III on 2004-10-22
I, while sometimes capable and willing to follow those kind of instructions, would expect something easier and straightforward for the audience that Ubuntu is targeted at.  While I understand that it is not possible to hit all the bases at once, it would make sense to address this issue.

---

### Post by wvengen on 2004-10-26
The best way I have found is using java-package (in multiverse). It doesn't support amd64 yet (last time I checked). If you really want to plug-and-play, I'd go for an i386 install of Ubuntu.

[list]
[*][http://www.martinfowler.com/bliki/DebianJava.html](http://www.martinfowler.com/bliki/DebianJava.html)
[*][http://serios.net/content/debian/java.php](http://serios.net/content/debian/java.php)
[/list]

---

### Post by Pluk on 2004-10-26
check this thread:
[Java for firefox](http://http://www.ubuntuforums.org/showthread.php?t=198&highlight=java)

Get the 64bits java version from [www.blackdown.org](www.blackdown.org)
[Here is a belgium mirror](ftp://ftp.easynet.be/blackdown/JDK-1.4.2/amd64/rc1/j2re-1.4.2-rc1-linux-amd64.bin) 

And use these commands [HTML]sudo chmod a+x j2re-1.4.2-rc1-linux-amd64.bin
./j2re-1.4.2-rc1-linux-amd64.bin
sudo mv j2re-1_4_2 /usr/local/
cd /home/username/.mozilla/plugins
ln -s /usr/local/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so libjavaplugin_oji.so[/HTML]

Sure it isnt really straightforward but even if ubuntu you eventually will need some non-gui configuring :)

---

### Post by smoothrt on 2004-10-27
After trying the codes listed, I ran into multiple problems and firefox freezes now whenever I try and open a webpage with java.  Here's what happened.

First of all, I didn't know where to download the file, so I just put it into /home/ross

sudo mv j2re-1_4_2 /usr/local/ gave me an error message saying no such file or directory existed.  I changed it to j2re1.4.2 but don't know if that was right.  Could go back to the problem of not knowing where to install the file in the first place.

cd /home/username/.mozilla/plugins
I don't have any mozilla or mozilla plugins folder in my /home/ross directory.  I changed this to the mozilla-firefox plugins folder I found in /usr/lib64 but again, didn't know what to do.

As you can see, I'm still new and don't know how what to do when straightforward directions go bad.  Any help or advice on fixing all of this to get java working would be more than appreciated.

---

