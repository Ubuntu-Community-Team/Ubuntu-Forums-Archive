---
title: "java 1.4 on amd64?"
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jcapote on 2006-07-19
Is this even possible?

I tried installing j2sdk-1_4_2_12-linux-i586.bin from sun's site, using fakeroot and make-jpkg, but I get the following error:

```
Creating temporary directory: /tmp/make-jpkg.XXXXW6Ss8R
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```

It could be because its an i586 package, but I can't find an amd64 version of the 1.4 sdk on thier site. I'm sure someone else with amd64 has needed j2sdk 1.4 aswell and can shed some light on the subject...........please? ](*,)

---

### Post by jcapote on 2006-07-19
Also, I could care less about plugins and firefox support. This is for a headless server that needs to run tomcat

---

### Post by andybhoy.1984 on 2006-07-19
I followed this tutorial:
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

Although that might not be what you are looking for.  Shows you how to install Flash, Java, Real Player into Firefox...

---

### Post by andybhoy.1984 on 2006-07-19
Sorry, just read your reply, probably not helpful at all, LOL!

---

### Post by svaucher on 2006-07-19
I've installed IBM's JVM on an AMD64 bit processor. It works like a charm.

[http://www-128.ibm.com/developerworks/java/jdk/](http://www-128.ibm.com/developerworks/java/jdk/)

---

### Post by svaucher on 2006-07-19
You do not **need** to use the debian packaging system. 

At home, I got Sun's jdk up and running on my AMD32 bit using the packaging system. At work, I just dumped it in my account on NFS.

---

### Post by Kilz on 2006-07-19
> **andybhoy.1984 said:**
> I followed this tutorial:
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

Although that might not be what you are looking for.  Shows you how to install Flash, Java, Real Player into Firefox...

The howto installs the java j2re1.4 as well as the plugin. There are also automated setup scripts on the page.

---

### Post by jcapote on 2006-07-19
> **Kilz said:**
> The howto installs the java j2re1.4 as well as the plugin. There are also automated setup scripts on the page.

I tried installing the .bin (from the guide above) it and look what happens:

```
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
0
0
Extracting...
./j2sdk-1_4_2_12-linux-i586.bin: line 399: ./install.sfx.17241: No such file or directory
Done.

```

---

### Post by Kilz on 2006-07-19
> **jcapote said:**
> I tried installing the .bin (from the guide above) it and look what happens:

```
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
0
0
Extracting...
./j2sdk-1_4_2_12-linux-i586.bin: line 399: ./install.sfx.17241: No such file or directory
Done.

```

That is strange, I have tested the link and file and they unpack fine on my desktop. But there is another way. The install scripts I made use the files already in the repositories. Try this.
```
sudo apt-get install j2sdk1.4
```

---

