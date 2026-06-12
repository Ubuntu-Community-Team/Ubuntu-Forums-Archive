---
title: "Installing Java plugin for Firefox in 7.04"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Alnico on 2008-04-26
Hi, 

I'm having a problem with installing the Java plugin for Firefox.

These are my details:
* OS = Ubuntu 7.04 (x64)
* Browser = Firefox 2.0.0.14 (extracted at: /home/alpha/firefox )
* JRE 32-bit version from Java.com (filename: jre-6u5-linux-i586-rpm.bin)

1. After I extracted the JRE, I got two subfolders, an /etc folder and a /usr folder in my home directory.
2. I then copied the file **jexec** to **/etc/init.d** with root permissions.
3. I then copied the **/home/alpha/etc/java/jre1.6.0_05** folder to **/etc/java/jre1.6.0_05**
4. I then made a softlink for the file **libjavaplugin_oji.so** located in **/etc/java/jre1.6.0_05/plugin/i386/ns7** in the folder **/home/alpha/firefox/plugins**

Now after doing this, I still cannot view the Java applets when I verify my Java installation on java.com. What is going wrong?

Please help.

---

### Post by TenPlus1 on 2008-04-26
It may be easier to enter Synaptic, search for Java6 and select runtime and plugin for installation...  This works no problem...

---

### Post by Alnico on 2008-04-26
Tried, but that does not work anymore.

---

