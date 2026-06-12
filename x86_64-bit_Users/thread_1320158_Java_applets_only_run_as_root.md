---
title: "Java applets only run as root"
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by PizzaPower on 2009-11-09
Hi, guys.

I've installed 64-bit sun-java6-* packages as expected and even applications such as eclipse work fine. The problem happens when I use firefox or chromium as a normal user. Applets simply don't work. A solid block just stands there where the applet should appear.

When I type "sudo -s" in the terminal and run firefox or chromium, applets work as expected. I've checked firefox "about: plugins" configuration and java6 is there even when I am not root.

Anyone ever seen something like this?

---

### Post by PizzaPower on 2009-11-09
OK, solved it myself. AWT_TOOLKIT was set to "MToolkit" because of some java applications that need it to work with compiz.

The problem is that that string makes the java sdk segfault with some applications, such as ControlPanel and javaws. Apparently, it segfaults the java plugin for the browser too.

Removing the environment string above solved it. ;)

---

