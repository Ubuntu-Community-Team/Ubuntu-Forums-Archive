---
title: "Uninstall Java"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thelasko on 2008-03-19
I have been having trouble getting Java to work on my machine as I have[ posted previously]("http://ubuntuforums.org/showthread.php?t=701004").  I installed and uninstalled various versions of Java from the repositories and none of them worked.  Now I have completely uninstalled Java from my machine using Synaptic with the exception of OpenOffice.org files and Firefox still seems to think I have Java installed.  When I go to the [javatester website]("http://www.javatester.org/version.html") it tells me I have GNU Java installed.  Why is this happening?  There doesn't even appear to be any plugins installed in Firefox but it does look like some of the Java files didn't uninstall cleanly when I look under my \etc\ folder.

---

### Post by jrib on 2008-03-19
uninstall the gcjwebplugin package.

See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for instructions on how to install Java.  Feel free to ask if you're not sure about something.

---

### Post by Thelasko on 2008-03-19
Let me get this straight.  Ubuntu comes with GCJ but I need IcedTea.  Does GCJ not play nice with IcedTea?

---

### Post by Thelasko on 2008-03-20
I uninstalled GCJ completely and installed IcedTea and the plugin from the doko repository.  Now when I go to the Java tester it says "Sun Java 1.7" however, whenever I go to another site I still get just a grey box.  For example, I tried the [Yahoo Stock Screener]("http://screener.finance.yahoo.com/fscr/us/launch.html").

---

