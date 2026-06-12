---
title: "Java for 64bit AMD"
date: 2009-06-16
forum: x86 64-bit Users
---

### Post by Nitewalker on 2009-06-16
I have just installed Ubuntu 9.04 64bit on my Acer Aspire 5100 laptop and when I try and access a webpage that is using Java Script it does not show it.  It shows where the links should be but does not place them in view to use, it just says "starting applet" and doesn't load them.  When I went to the page the 1st time it said I needed to download a application "teacup" I think which I did, but still doesn't work.  What do I need to do?  thanks:-?

---

### Post by Therion on 2009-06-16
Go to Add/Remove and search on "Ubuntu-Restricted-Extras".  

Install it.

If Add/Remove can't find it, post back.  You need to install the Medibuntu Repository.

---

### Post by Nitewalker on 2009-06-16
added the 'Ubuntu-Restricted-Extras".using the package manager, restarted computer, still links do not show, it just says "starting applet" and the box where the links should be is there but no links:confused:

---

### Post by oldos2er on 2009-06-16
I don't recall if ubuntu-restricted-extras installs sun-java6-plugin, but you could run **sudo apt-get install sun-java6-plugin** just to be sure.

---

### Post by Nitewalker on 2009-06-16
checked for java6 plugin, it says the latest version is installed

---

### Post by Yellow Pasque on 2009-06-16
Does about:plugins (enter that in the FF URL bar) show the Java plugin installed? It should be listed as libnpjp2.so
If you have multiple Java plugins installed, this command may be helpful:
```
sudo update-alternatives --config xulrunner-1.9-javaplugin.so
```

---

### Post by jespdj on 2009-06-17
> **Nitewalker said:**
> I have just installed Ubuntu 9.04 64bit on my Acer Aspire 5100 laptop and when I try and access a webpage that is using Java Script it does not show it. ...
Java**Script** is something totally different from Java. Despite the word "Java" in the name, the two are unrelated.

Support for JavaScript is built-in into every webbrowser and doesn't require Java or any other kind of plug-in to be installed.

If you're talking about Java, install Sun Java 6 like this:
```
sudo apt-get install sun-java6-plugin
```

**Note**: The package ubuntu-restricted-extras does not install Sun Java 6 on 64-bit Jaunty the last time I checked. In fact, I filed a [bug report](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/351389), the dependencies of ubuntu-restricted-extras are wrong.

---

