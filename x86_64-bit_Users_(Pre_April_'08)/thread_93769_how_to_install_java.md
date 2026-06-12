---
title: "how to install java"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by osiris999 on 2005-11-22
ive been using [www.ubuntuguide.org/](www.ubuntuguide.org/) for codes to enter in terminal but the one for java doesnt work. i went to javas site and downloaded the file now its on my desktop but i have no idea how to install it. im very new to linux and have no idea how to really install things.

---

### Post by HunterCo on 2005-11-22
[http://java.com/en/download/help/5000010500.xml]("http://java.com/en/download/help/5000010500.xml")
The link I put here is from the Sun Java website. It's generic, which will work on any Linux distribution. Since you downloaded manually, I figured I give you the manual install instructions. There are other more "Ubuntu-specific" ways to do it, but I'm running off to work and didn't have time to throw that up here... Hope what I gave you works.

Also, here's a link to getting it working with Mozilla Firefox, if you use it.
[http://java.com/en/download/help/5000011200.xml]("http://java.com/en/download/help/5000011200.xml")

---

### Post by osiris999 on 2005-11-22
when i type su in terminal it says  Authentication failure

---

### Post by RAOF on 2005-11-22
I recommend following [this guide]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+package").  It'll install Java, set it up properly the Breezy way, and allow you to remove/update it easily.

Additionally, ubuntuguide.com is somewhat out of date.  More up to date is [help.ubuntu.com]("http://http://help.ubuntu.com/starterguide/C/")

---

### Post by HunterCo on 2005-11-22
[QUOTE=RAOF]I recommend following [this guide]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+package").  It'll install Java, set it up properly the Breezy way, and allow you to remove/update it easily.[/QUOTE]
Yeah, that's the link I wanted to find for him but didn't have time to look up... I had the other one's bookmarked so it was easier. I probably should also stop checking these forums when I should be getting ready for work. ;) 

Also, to fix the authentication error, it is because there is no password currently assigned to root. If you follow RAOF's link/guide, though, you don't need to give root a password. I'd recommend the "no password" method first.

---

### Post by ubuntu27 on 2005-11-22
IF YOU ARE USING  Ubuntu Breezy Badger 5.10.  Try this:

      Make sure the multiverse repository is enabled. (See How do I add Universe and Multiverse?)
   2.

      Go to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and click on “Download JRE 5.0 Update 4”. Ensure you do not choose the link with the NetBeans bundle.
      [Note]	

      At the time of this writing J2SE is at version 5.0 Update 4. This is subject to change. If you do not see this version on Sun's website, download the newest version displayed.
   3.

      You must first accept the licence, then click on “Linux self-extracting file” (jre-1_5_0_04-linux-i586.bin). Save this file to your hard drive.
   4.

      Install the java-package package with Synaptic (See How do I use Synaptic to install packages?)

      Miscellaneous - Text Based (multiverse) > java-package

   5.

      Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

```
chmod +x jre-1_5_0_04-linux-i586.bin
```

   6.

      To install JRE, run the downloaded file. Type

```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```

   7.

```
dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb
```



Taken from the OFFICIAL Ubuntu guide: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)

---

### Post by osiris999 on 2005-11-22
ok i get this error

 osiris@ubuntu:~$ sudo apt-get install fakeroot java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

but the package is on my desktop

---

### Post by osiris999 on 2005-11-22
now this

osiris@ubuntu:~$ sudo apt-get install fakeroot java-package java-common
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
osiris@ubuntu:~$

---

### Post by osiris999 on 2005-11-22
ok i got sudo apt-get install fakeroot java-package java-common to work

but when i put in fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin it says  file "jre-1_5_0_05-linux-i586.bin" does not exist. i even tried takeing out i586 and putting amd64 in its place and i get the same error

---

### Post by HunterCo on 2005-11-22
[QUOTE=osiris999]fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin it says  file "jre-1_5_0_05-linux-i586.bin" does not exist. i even tried takeing out i586 and putting amd64 in its place and i get the same error[/QUOTE]

It is just a matter of replacing that text with the exact filename of the file you downloaded. Figure out the filename you saved from download, be sure to use the full filename, and be sure you are in the same directory you downloaded the file to when you run that command.

PS: Who knew I could get on this site from work? ;) I'll have to remember this.

---

