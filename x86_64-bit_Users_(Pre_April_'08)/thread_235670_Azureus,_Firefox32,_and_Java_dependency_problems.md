---
title: "Azureus, Firefox32, and Java dependency problems"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwshook on 2006-08-13
I previously had Azureus working on my 64-bit install but now it's broken. I think java is the root of the problem. It broke after I ran the Firefox32 installation script from [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=202537").

When I run azureus from the terminal, I get these errors. 

> 
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libswt-pi-gtk-3139.so: /usr/lib/jni/libswt-pi-gtk-3139.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1586)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1511)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)



I tried using synaptic to reinstall libswt3.1-gtk-java, and libswt3.1-gtk-jni, and Azureus. Doing this did nothing to help Azureus, but now Firefox32 crashes everytime I right-click on a toolbar, or try to use the search engine box. (regular Firefox works fine)

Any suggestions for straightening this out? My goals, from best case to scenario to worst case:

[LIST=1]
[*]Firefox and Azureus work in perfect harmony with Flash, Java plugins working as well
[*]Azureus works, and Firefox works with Flash, but no Java plugin
[*]Firefox works with Flash, and I have to use bittornado instead of Azureus
[*]I'm stuck where I am, using Firefox64, no Flash, and bittornado
[/LIST]

---

### Post by Kilz on 2006-08-13
> **mwshook said:**
> I previously had Azureus working on my 64-bit install but now it's broken. I think java is the root of the problem. It broke after I ran the Firefox32 installation script from [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=202537").

When I run azureus from the terminal, I get these errors. 



I tried using synaptic to reinstall libswt3.1-gtk-java, and libswt3.1-gtk-jni, and Azureus. Doing this did nothing to help Azureus, but now Firefox32 crashes everytime I right-click on a toolbar, or try to use the search engine box. (regular Firefox works fine)

Any suggestions for straightening this out? My goals, from best case to scenario to worst case:

[LIST=1]
[*]Firefox and Azureus work in perfect harmony with Flash, Java plugins working as well
[*]Azureus works, and Firefox works with Flash, but no Java plugin
[*]Firefox works with Flash, and I have to use bittornado instead of Azureus
[*]I'm stuck where I am, using Firefox64, no Flash, and bittornado
[/LIST]

The script uses .deb files and installs blackdown java, the version is 1.4 I think. You may need to latest java to run Azureus. It requires the latest of everything and loads of resources.
My advice to you is to uninstall the firefox32 package in synaptic. Then follow the manual howto, dont use a script. This will alow you to install what you want like flash. The java install by the howto will work to because it isnt a package but a manual install.
If you cant get that to working then the next best case would be run the firefox script and use the light weight bittornado.

---

### Post by mwshook on 2006-08-13
Do you think I need to uninstall and re-install any java packages?

> **Kilz said:**
> The script uses .deb files and installs blackdown java, the version is 1.4 I think. You may need to latest java to run Azureus. It requires the latest of everything and loads of resources.
My advice to you is to uninstall the firefox32 package in synaptic. Then follow the manual howto, dont use a script. This will alow you to install what you want like flash. The java install by the howto will work to because it isnt a package but a manual install.
If you cant get that to working then the next best case would be run the firefox script and use the light weight bittornado.

---

### Post by Kilz on 2006-08-13
> **mwshook said:**
> Do you think I need to uninstall and re-install any java packages?

Im not sure what Azureus requires. But to remove all the applications Firefox32-flash-java-mplayer script installs this should do.

```
sudo apt-get remove mplayer firefox32 flashplugin-nonfree j2re1.4 mozilla-mplayer mplayer32
```

To make sure

```
sudo rm -rfd /usr/local/firefox32
sudo rm -f /usr/local/bin/firefox32
```
Should get rid of anything left. You should then be able to follow the manual script and install firefox32 without effecting anything else thats installed because the system really shouldnt know its there to use when you just copy it in.

---

### Post by mwshook on 2006-08-13
Thanks for the holep

Well, I still don't have everything figured out, but I've made some progress.

I was barking up the wrong tree with when I assumed java was causing my Firefox headaches. 

We were both posting to [this thread]("http://www.ubuntuforums.org/showthread.php?t=229010") about graphic errors in firefox32. I could only reproduce that error with certain themes.

Well, it now appears that some themes make firefox32 look fine, but make it unstable. I switched back to the Human theme, and everything works fine with firefox32.

On the other hand, Azureus is still broken. I'm still pretty sure that it was the java install from your script that broke it, but I'm at a loss on how to fix it. I uninstalled the pkgs you suggested, I uninstalled Azureus, uninstalled it's dependencies, and reinstalled Azureus. No change.

But I did find KTorrent, and this seems to be comparable (but not as slick). I guess all just use that instead. 

I'm not sure who to report this theme bug to. Is it a firefox bug, or an ubuntu bug? 

But thanks again!

---

### Post by Kilz on 2006-08-13
> **mwshook said:**
> Thanks for the holep

Well, I still don't have everything figured out, but I've made some progress.

I was barking up the wrong tree with when I assumed java was causing my Firefox headaches. 

We were both posting to [this thread]("http://www.ubuntuforums.org/showthread.php?t=229010") about graphic errors in firefox32. I could only reproduce that error with certain themes.

Well, it now appears that some themes make firefox32 look fine, but make it unstable. I switched back to the Human theme, and everything works fine with firefox32.

On the other hand, Azureus is still broken. I'm still pretty sure that it was the java install from your script that broke it, but I'm at a loss on how to fix it. I uninstalled the pkgs you suggested, I uninstalled Azureus, uninstalled it's dependencies, and reinstalled Azureus. No change.

But I did find KTorrent, and this seems to be comparable (but not as slick). I guess all just use that instead. 

I'm not sure who to report this theme bug to. Is it a firefox bug, or an ubuntu bug? 

But thanks again!

If you removed and reinstalled Azureus and its dependancies Im not sure how what the script installs could break it. Unless you reinstall the script afterwards. What are Azureus's dependancies?

---

### Post by Ribs on 2006-08-14
Azureus does work with blackdown java 1.4. It's working just fine here. I suggest you re-install Azureus.

Did you install the AMD64 version of Azureus orginially? Are you using 32-bit java now? You might need to change to the 32-bit version of Azureus

---

### Post by mwshook on 2006-08-16
I installed Azureus using the "Add/Remove" program, so I assume it's the 64 bit version. Reinstalling does nothing.

Oh, and its dependencies are 
libbcprov-java (>=1.32)
libgnucrypto-java
libcommons-cli-java
liblog4j1.2-java
libseda-java
libswt3.1-gtk-java
libgtk-java
java-gcj-compat|java2-runtime

I've tried re-installing all those, with no results.

> **Ribs said:**
> Azureus does work with blackdown java 1.4. It's working just fine here. I suggest you re-install Azureus.

Did you install the AMD64 version of Azureus orginially? Are you using 32-bit java now? You might need to change to the 32-bit version of Azureus

---

### Post by mwshook on 2006-08-16
I found [this post]("http://www.ubuntuforums.org/showthread.php?t=232023&highlight=azureus+dependencies") from last week, that fixed my problem.

The update-alternatives command gave me a choice of gij-wrapper, java-1.5.0-sun, or j2se/1.4/bin/java.

Choosing 1.5.0-sun made azureus work again. I still think that this occured because of the firefox32 script, maybe changing the default version of java. But at least we know how to fix it.

Thanks for all your help.

---

### Post by sno on 2006-08-17
Maybe a silly question, but can sombody explain me why mozilla is installed whit the Azureus packed. 
I already have firefox installed ,and removing mozilla breaks azureus. 
So how do i get azureus only om my system whitout additional irrelevant software :confused:

---

