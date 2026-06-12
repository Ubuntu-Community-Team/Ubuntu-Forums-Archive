---
title: "What's the deal with gcjwebplugin?"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-08-05
I haven't had working Java since Feisty.  This morning I was playing around with Synaptic and noticed there is more than one gcjwebplugin.  This is what I found:

[LIST=1]
[*]IcedTea-gcjwebplugin [INDENT]Java applets say they're loaded but aren't[/INDENT]
[*]gcjwebplugin-4.2 [INDENT]Firefox crashes upon loading a Java applet[/INDENT]
[*]gcjwebplugin-4.1       [INDENT]Nothing happens, it's like it's not even there[/INDENT]
[*]gcjwebplugin           [INDENT]Nothing happens, it's like it's not even there[/INDENT]
[/LIST]

Which one am I supposed to use?  I don't care which Java I use, I just want it to work.

---

### Post by ajgreeny on 2008-08-05
I removed all the gcj stuff and installed sun-java which seems to work much better.  It is also a lot more useful with Open Office as far as I can make out.

---

### Post by Thelasko on 2008-08-05
> **ajgreeny said:**
> I removed all the gcj stuff and installed sun-java which seems to work much better.  It is also a lot more useful with Open Office as far as I can make out.
But don't you need the web plugin to make it work?  I installed Sun Java too, but when I go to a website that requires Java, I get a message that Java isn't installed.

---

### Post by ajgreeny on 2008-08-05
You need the **sun-java6-plugin** as well for firefox, though the only way I could get it to work was to remove the gcj stuff.  For some reason even ```
sudo update-alternatives --config java
```  and choosing sun java, didn't get sun-java working instead of the gcj plugin.  No idea why, as it should have done.  I have **sun-java6-plugin**, **sun-java6-bin**, **sun-java6-fonts** and **sun-java6-jre** installed and it seems to work faultlessly.

---

### Post by NilsE on 2008-08-05
**sun-java6-plugin**, **sun-java6-bin**, and **sun-java6-jre** are the 3 required to make the plugin work. The fonts are a good add on.

They key however was hit on twice in this thread.  Install these 3 and make sure all other javas are removed.

---

### Post by Thelasko on 2008-08-05
> make sure all other javas are removed.
That's the hard part.  How do I make sure all of the old java's are removed without disturbing OpenOffice?  When I was working with Gusty I installed Java 6 and then removed IcedTea.  I don't think I removed all of IcedTea since Java 6 never worked.  I could never figure out what package was left behind.

---

### Post by NilsE on 2008-08-05
> **Thelasko said:**
> That's the hard part.  How do I make sure all of the old java's are removed without disturbing OpenOffice?  When I was working with Gusty I installed Java 6 and then removed IcedTea.  I don't think I removed all of IcedTea since Java 6 never worked.  I could never figure out what package was left behind.
When I search on java in Synaptic using just the name search outside of the 3 sun-java packages all I have installed is java-common and tzdata-java

I just removed anything with icedtea or gcj in the name that were related to java

---

### Post by Thelasko on 2008-08-05
Thanks, I'll try that.

---

### Post by Thelasko on 2008-08-05
Ok, sun-java6-plugin isn't in the repositories.  I have main, universe, restricted, and multiverse enabled.

---

### Post by NilsE on 2008-08-06
> **Thelasko said:**
> Ok, sun-java6-plugin isn't in the repositories.  I have main, universe, restricted, and multiverse enabled.Go into Software Sources and turn all of the repos on and see if it shows up.  It should be there especially if all the other version 6 packages are there. Be careful if you turn on the proposed repo since that is test stuff.

---

### Post by Thelasko on 2008-08-06
The plugin isn't available for 64-bit.  I tried OpenJDK, but it doesn't work.

---

### Post by philinux on 2008-08-06
I've got these installed as well as sun-java6 but I used 

sudo update-alternatives --config java
to set the default to openjdk

openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

and
icedtea-gcjwebplugin

The reason being.
> OpenJDK Java runtime

The packages are built using the IcedTea build support and patches
from the IcedTea project.

And this combo works for me, even on the java site now.

---

### Post by stchman on 2008-08-06
> **Thelasko said:**
> I haven't had working Java since Feisty.  This morning I was playing around with Synaptic and noticed there is more than one gcjwebplugin.  This is what I found:

[LIST=1]
[*]IcedTea-gcjwebplugin [INDENT]Java applets say they're loaded but aren't[/INDENT]
[*]gcjwebplugin-4.2 [INDENT]Firefox crashes upon loading a Java applet[/INDENT]
[*]gcjwebplugin-4.1       [INDENT]Nothing happens, it's like it's not even there[/INDENT]
[*]gcjwebplugin           [INDENT]Nothing happens, it's like it's not even there[/INDENT]
[/LIST]

Which one am I supposed to use?  I don't care which Java I use, I just want it to work.

I have Java working well in 64 bit.  Install the following:

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

The browser plugin works, but not as good as the SUN one.

---

### Post by Thelasko on 2008-08-06
Sorry, neither OpenJDK or IcedTea works. It appears that IcedTea is dependent on Open JDK.

When I install the icedtea-gcjwebplugin  with open JDK it says "applet loaded" and nothing else.

When I install icedtea-java7 I get "start: applet not initialized"

---

