---
title: "64 or 32 bit Java"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by willsomebody on 2007-06-20
I recently installed a new 64-bit processor, and I installed 64-bit feisty. Using this tutorial: [http://ubuntuforums.org/showthread.php?p=1174435]("http://ubuntuforums.org/showthread.php?p=1174435")
I successfully installed flash and tried to install java.  the test link on that how-to works, but neither runescape or azureus will work.  When I run azureus in a terminal it tells me this:
 
[INDENT]changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jni/libswt-pi-gtk-3236.so: /usr/lib/jni/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS64
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
[/INDENT]
Can anyone help me?

(I have an amd athlon 64 x2 3600+ 1.9 ghz brisbane core sitting on the socket am2 of a bio star motherboard with a via k8m800 chipset and 1 gig of pny ram and a 160 gig WD sata harddrive.)

feel free to request any more info

I also installed the 64 bit java from sun's website, that did not work.  I know it would be faster to use the 64-bit version, but i will take any java I can get.

---

### Post by _simon_ on 2007-06-20
Can I suggest that you try installing 64bit Java via automatix?

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29)

---

### Post by Kilz on 2007-06-20
> **_simon_ said:**
> Can I suggest that you try installing 64bit Java via automatix?

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29)

Let me suggest you NOT use Automatix to install java. The reasons?
1. Automatix gives no information as to what version of java is installed. But for AMD64 there is only 1 that works with the 64bit browser.
2. The one Java that works is the java-gcj-compat-plugin. Which if you really wanted to install is available with synaptic.
3. The java-gcj-compat-plugin plugin is a **[COLOR="Red"]HUGE[/COLOR]** security risk! 
Per the Ubuntu [Java]("https://help.ubuntu.com/community/Java") page

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that** the plugin currently runs [COLOR="Red"]with no security[/COLOR] manager**. This means that applets you load can do anything a java application that you download and run can do. Be **very** careful which applets you run.

If there is an applet that will install a rootkit, it will let it. If there is a applet that will reformat your drive, it will let it.

I forgot to add a solution.
I see you installed the 32bit version of Firefox/java/flash from my script. The reason some of the applications other than it cant use it is that the java it installs is 32bit. 
You now have a 64bit java from sun,[ you might want to take a look here]("http://ubuntuforums.org/showthread.php?t=325657&highlight=azureus"). The search feature is your friend, use it if this doesnt fix the problem, there are lots of posts on this subject.

---

### Post by willsomebody on 2007-06-20
Thanks, that really helped.  Java works fully now.

---

### Post by arnieboy on 2007-06-20
> **Kilz said:**
> 
1. Automatix gives no information as to what version of java is installed. But for AMD64 there is only 1 that works with the 64bit browser.
nonsense.

---

### Post by Kilz on 2007-06-20
> **arnieboy said:**
> nonsense.

Then prove it with a link, exactly what java is installed?

---

### Post by arnieboy on 2007-06-20
> **Kilz said:**
> Then prove it with a link, exactly what java is installed?
open automatix and look it up yourself (its there in bold).. and stop using alien in your scripts.. You will break a dozen upgrades.. Make some real nspluginwrapper debs  or wait for us to make them so that they dont hose systems.

---

### Post by Kilz on 2007-06-20
> **arnieboy said:**
> open automatix and look it up yourself (its there in bold).. and stop using alien in your scripts.. You will break a dozen upgrades.. Make some real nspluginwrapper debs  or wait for us to make them so that they dont hose systems.

Sorry, I would rather not install automatix. If using Alien is going to break automatix updates, you better fix the script. Alien is in the Ubuntu repos and I am just using whats there. As are lots of other people. I dont think I will wait, nether will I recommend using automatix. There is no hosing of systems on my end.

---

### Post by arnieboy on 2007-06-20
> **Kilz said:**
> Sorry, I would rather not install automatix. If using Alien is going to break automatix updates, you better fix the script. Alien is in the Ubuntu repos and I am just using whats there. As are lots of other people. I dont think I will wait, nether will I recommend using automatix. There is no hosing of systems on my end.
It wont break automatix updates.. it would break apt because alien has no clue about how to set dependencies and correctly debianize a package (setting paths etc) .. you are injecting these broken packages into people's computers with your scripts.. and you dont even know or want to learn why and how these breakages can happen. 
As for whether you recommend automatix or not, I don't really care.

---

### Post by Kilz on 2007-06-20
> **arnieboy said:**
> It wont break automatix updates.. it would break apt because alien has no clue about how to set dependencies and correctly debianize a package (setting paths etc) .. you are injecting these broken packages into people's computers with your scripts.. and you dont even know or want to learn why and how these breakages can happen. 
As for whether you recommend automatix or not, I don't really care.

Maybe you should convince Ubuntu not to include Alien in the repo's? After all if what you say is true. Then each time someone uses it, it breaks Ubuntu........ 
Wait a second, if that happened there would be millions of posts saying something was broken after using alien, aint happened yet. As soon as the number of posts on the forums about alien match the number of those that say automatix messed up their setup, Ill ask Ubuntu to take it out of the repos with you. 
Why not go back to your site and document what automatic installs until then?

---

### Post by willsomebody on 2007-06-20
I used kilz's script to install flash in 64-bit Ubuntu, and it worked fine.

I also used Automatix to install 64-bit java, and it worked fine.

---

### Post by Kilz on 2007-06-20
> **willsomebody said:**
> I used kilz's script to install flash in 64-bit Ubuntu, and it worked fine.

I also used Automatix to install 64-bit java, and it worked fine.

In that case (that it is installed to a 64bit browser) Im almost sure that its the java-gcj-compat-plugin that automatix installs. Per the warning from Ubuntu realize you have a HUGE security risk running on your computer. [Please see my earlier post.]("http://ubuntuforums.org/showpost.php?p=2881307&postcount=3") It isnt that it wont run, but that if someone puts something like a rootkit, or even a drive format command in a applet, your java will allow it.

---

### Post by willsomebody on 2007-06-20
It asks you whether or not you trust an applet.  All I use it for is Azureus, Sun Download Manager, and Runescape.

---

### Post by Kilz on 2007-06-20
> **willsomebody said:**
> It asks you whether or not you trust an applet.  All I use it for is Azureus, Sun Download Manager, and Runescape.

Would you please type ```
about:plugins
``` into the 64bit Firefox's address bar. An internal page will show. It will list all the installed plugins. Can you see if java is listed and what the version that is installed is? You can even copy the section and paste it here.

---

### Post by willsomebody on 2007-06-20
[http://willsomebody.googlepages.com/AboutPlug-ins.html]("http://willsomebody.googlepages.com/AboutPlug-ins.html")

---

### Post by Kilz on 2007-06-20
> **willsomebody said:**
> [http://willsomebody.googlepages.com/AboutPlug-ins.html]("http://willsomebody.googlepages.com/AboutPlug-ins.html")

It installed the java-gcj-compat-plugin.

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

Please , go to [the Java page]("https://help.ubuntu.com/community/Java") of the Ubuntu wiki and check this section out for yourself.

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that **[COLOR="Red"]the plugin currently runs with no security manager.[/COLOR]** This means that **[COLOR="Red"]applets you load can do anything a java application that you download and run can do[/COLOR]**. Be **very** careful which applets you run.

So if someone puts a nasty evil applet and names it "best game on the internet" and you load it up and it has a rootkit, you just gave your computer to a hacker. If the applet is designed to format your hard drive, say bye bye to your data.

---

### Post by _simon_ on 2007-06-21
If it's a security risk, how / where should we install java from for 64bit?

---

### Post by kzm. on 2007-06-21
can anybody please provide a link to the how-tos for flash and java on feisty 7.04 64bit.. do i still have to install firefox 32bit for flash?

---

### Post by Kilz on 2007-06-21
> **_simon_ said:**
> If it's a security risk, how / where should we install java from for 64bit?

I know of no safe java plugin for the 64bit browser. The good news is that sun has a new version under development, and a 64bit plugin is planned.

> **kzm. said:**
> can anybody please provide a link to the how-tos for flash and java on feisty 7.04 64bit.. do i still have to install firefox 32bit for flash?

You dont have to install 32bit firefox for flash. I even have a script that will install Flash to your 64bit browser. But you need to read my posts in this thread about the java plugin that runs with the 64bit browser. It is a security risk. If you need java , you may have to run a 32bit firefox if you want to remain safe.

---

### Post by kzm. on 2007-06-21
thanx for the info. i got your link:
wget [http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz](http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz)
unzip
./nspw install

---

