---
title: "[SOLVED] icedtea webplugin and swiftweasel"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by Nepherte on 2008-06-03
I use Swiftweasel as my main browser. Since there is no java web plugin for 64 bit from sun, I installed openjdk6 and the icedtea gcj webplugin. This works perfect under Firefox 3 RC1, but I can't seem to make it work for Swiftweasel. I tried to create some symlinks in /usr/lib/firefox-addons/plugins, /usr/lib/firefox/plugins, /usr/lib/mozilla/plugins but neither of them seem to work though it still works on Firefox 3 RC1. Can anyone shed some light on this to make it work?

---

### Post by Kilz on 2008-06-03
> **Nepherte said:**
> I use Swiftweasel as my main browser. Since there is no java web plugin for 64 bit from sun, I installed openjdk6 and the icedtea gcj webplugin. This works perfect under Firefox 3 RC1, but I can't seem to make it work for Swiftweasel. I tried to create some symlinks in /usr/lib/firefox-addons/plugins, /usr/lib/firefox/plugins, /usr/lib/mozilla/plugins but neither of them seem to work though it still works on Firefox 3 RC1. Can anyone shed some light on this to make it work?

What is the exact version of Swiftweasel that you installed? You can get this information by the package name and version of what is installed in synaptic.

---

### Post by Nepherte on 2008-06-03
I use Swiftweasel 3.0 RC1

---

### Post by Kilz on 2008-06-03
> **Nepherte said:**
> I use Swiftweasel 3.0 RC1

What steps have you taken to make sure the plugins are in the correct plugin folder?

---

### Post by Nepherte on 2008-06-04
Well basically I installed openjdk along with the iced tea web plugin through apt-get. That made it simply work in Firefox, not for Swiftweasel. From what I understood, Swiftweasel sees what plugins there are in /usr/lib/mozilla/plugins but there was not iced tea plugin. So I made a symbolic link in /usr/lib/mozilla/plugins too /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so hoping that would fix it for Swiftweasel,but it doesn't. So I guess it's not the right folder but I wouldn't know what folder else. I'm not sure what Firefox uses either.

---

### Post by Kilz on 2008-06-04
> **Nepherte said:**
> Well basically I installed openjdk along with the iced tea web plugin through apt-get. That made it simply work in Firefox, not for Swiftweasel. From what I understood, Swiftweasel sees what plugins there are in /usr/lib/mozilla/plugins but there was not iced tea plugin. So I made a symbolic link in /usr/lib/mozilla/plugins too /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so hoping that would fix it for Swiftweasel,but it doesn't. So I guess it's not the right folder but I wouldn't know what folder else. I'm not sure what Firefox uses either.

You can also try putting a symlink in /usr/local/swiftweasel-trunk/plugins

---

### Post by Nepherte on 2008-06-04
That doesn't help either.

---

### Post by Kilz on 2008-06-04
> **Nepherte said:**
> That doesn't help either.

Click Help, then about Swiftweasel. A little window will open. Near the bottom of it will be a string starting with Mozilla/5.0. Copy the string to a post here. Next, type ```
about:plugins
``` in the address bar, do you see any java sections at all?

---

### Post by Nepherte on 2008-06-04
[quote=Kilz]Click Help, then about Swiftweasel. A little window will open. Near the bottom of it will be a string starting with Mozilla/5.0[/quote]
Mozilla/5.0 (X11; U; Linux x86_64; nl-NL; rv:1.9) Gecko/2008051813 Firefox/3.0

No trace of java plugins in about:plugins.

---

### Post by TrashmanL on 2008-06-04
same stuff going on here, only I'm using swiftfox instead of swiftweasel. (same thing, different logos, right?) One thing, I don't have a /usr/local/swiftfox-trunk or /usr/local/swiftweasel-trunk directory.

I've done various installations, including trying the 32 bit versions of the Sun Java plugin. I get no java in about:plugins with the 64 bit versions.

For the 32 bit version, I get a gigantic table. 

Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes

but when I try to go to a Java test page (Sun or otherwise) I get a blank box with a Red X in the corner. Java console reports: 

load: class JavaVersionDisplayApplet.class not found.
java.lang.ClassNotFoundException: JavaVersionDisplayApplet.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:194)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:640)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)
java.lang.InterruptedException
	at java.lang.Object.wait(Native Method)
	at java.lang.Thread.join(Thread.java:1143)
	at java.lang.Thread.join(Thread.java:1196)
	at sun.applet.AppletPanel.run(AppletPanel.java:404)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by Kilz on 2008-06-04
> **Nepherte said:**
> Mozilla/5.0 (X11; U; Linux x86_64; nl-NL; rv:1.9) Gecko/2008051813 Firefox/3.0

No trace of java plugins in about:plugins.

What does ```
ls -al /usr/local/swiftweasel-trunk/plugins
``` and ```
ls -al /usr/lib/mozilla/plugins
``` return

---

### Post by Kilz on 2008-06-04
> **TrashmanL said:**
> same stuff going on here, only I'm using swiftfox instead of swiftweasel. (same thing, different logos, right?) One thing, I don't have a /usr/local/swiftfox-trunk or /usr/local/swiftweasel-trunk directory.

I've done various installations, including trying the 32 bit versions of the Sun Java plugin. I get no java in about:plugins with the 64 bit versions.



Your problem is different. You might want to make a different post to keep things strait.

---

### Post by TrashmanL on 2008-06-04
already have, thanks. Haven't got anywhere on the other thread, found this similar one and was hoping someone here might have some different insights.

---

### Post by Nepherte on 2008-06-05
ls -al /usr/local/swiftweasel-trunk/plugins gives me:
```
drwxr-xr-x  2 root root 4096 2008-06-03 20:28 .
drwxr-xr-x 15 root root 4096 2008-06-03 20:28 ..
lrwxrwxrwx  1 root root   57 2008-06-03 20:28 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```
But this is the directory and symbolic I created earlier. The directory and symbolic link weren't there at first. From what I understand Swiftweasel uses the plugins map from /usr/lib/mozilla/plugins.

ls -al /usr/lib/mozilla/plugins gives me:
```
drwxr-xr-x 2 root root   4096 2008-06-04 18:38 .
drwxr-xr-x 4 root root   4096 2008-05-29 16:02 ..
lrwxrwxrwx 1 root root     37 2008-05-29 01:40 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     27 2008-06-02 00:49 libflashsupport.so -> /usr/lib/libflashsupport.so
-rw-r--r-- 1 root root 290880 2008-05-13 12:31 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1067 2008-05-13 12:31 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 12:31 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1067 2008-05-13 12:31 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 12:31 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1067 2008-05-13 12:31 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 290872 2008-05-13 12:31 mplayerplug-in.so
-rw-r--r-- 1 root root 290880 2008-05-13 12:31 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1067 2008-05-13 12:31 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1067 2008-05-13 12:31 mplayerplug-in.xpt
lrwxrwxrwx 1 root root     26 2008-05-29 20:57 nppdf.so -> /var/lib/acroread/nppdf.so
```

I found out that Firefox gets his icedtea gcj webplugin from /etc/alternatives/. Looking in that directory I find the following entry:
```
xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```

---

### Post by Kilz on 2008-06-05
> **Nepherte said:**
> ls -al /usr/local/swiftweasel-trunk/plugins gives me:
```
drwxr-xr-x  2 root root 4096 2008-06-03 20:28 .
drwxr-xr-x 15 root root 4096 2008-06-03 20:28 ..
lrwxrwxrwx  1 root root   57 2008-06-03 20:28 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```
But this is the directory and symbolic I created earlier. The directory and symbolic link weren't there at first. From what I understand Swiftweasel uses the plugins map from /usr/lib/mozilla/plugins.

ls -al /usr/lib/mozilla/plugins gives me:


Try making a symlink in /usr/lib/mozilla/plugins

---

### Post by Nepherte on 2008-06-05
Didn't work. I guess I should just use Firefox when i need the java plugin

---

### Post by Kilz on 2008-06-05
> **Nepherte said:**
> Didn't work. I guess I should just use Firefox when i need the java plugin

I dont know why yours is not working. We have checked the most common problems. All I had to do was enter in the command
```

sudo ln -s /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so /usr/lib/mozilla/plugins

``` and it worked for me. See screenshot. You are sure that you do not see this section in ```
about:plugins
``` ?

---

### Post by Nepherte on 2008-06-05
Nope I don't see a gcjwebplugin or java entry in about:plugins. Is there a way I could see some debug information on this. In the terminal perhaps?

P.S you are showing a vlc plugin, not java :p

---

### Post by Kilz on 2008-06-05
> **Nepherte said:**
> Nope I don't see a gcjwebplugin or java entry in about:plugins. Is there a way I could see some debug information on this. In the terminal perhaps?

P.S you are showing a vlc plugin, not java :p

Yes, sorry, here is one with the java plugin. I'm not sure how you would see if a plugin is seen or not. But since other plugins in the folder are seen and the java one isnt, I dont think its an issue with swiftweasel.

---

### Post by Nepherte on 2008-06-05
I was able to uncover a little more of the problem. I tryed to create a new profile using the -profilemanager option in the terminal. Creating the profile itself was no problem, but it gave me also the following terminal output:
```
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library /usr/lib/libflashsupport.so [/usr/lib/libflashsupport.so: wrong ELF-class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [libxul.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library /usr/lib/libflashsupport.so [/usr/lib/libflashsupport.so: wrong ELF-klasse: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [libxul.so: can't open shared object: File or directory doesn't exist]
```

Note that both the files libflashsupport.so and gcjwebplugin.so do exist in the given directories. I've checked it myself. So I assume the problem is libXt.so and libXext.so

---

### Post by Kilz on 2008-06-05
> **Nepherte said:**
> I was able to uncover a little more of the problem. I tryed to create a new profile using the -profilemanager option in the terminal. Creating the profile itself was no problem, but it gave me also the following terminal output:
```
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library /usr/lib/libflashsupport.so [/usr/lib/libflashsupport.so: wrong ELF-class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [libxul.so: can't open shared object: File or directory doesn't exist]
LoadPlugin: failed to initialize shared library /usr/lib/libflashsupport.so [/usr/lib/libflashsupport.so: wrong ELF-klasse: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [libxul.so: can't open shared object: File or directory doesn't exist]
```

Note that both the files libflashsupport.so and gcjwebplugin.so do exist in the given directories. I've checked it myself. So I assume the problem is libXt.so and libXext.so

The error for flash is telling you its 32bit, we know this already. With the java problem its likely its libxul.so causing the problem. Because it says this
**libxul.so:** can't open shared object: File or directory doesn't exist
[Install this package to see.]("http://packages.ubuntu.com/hardy/libxul-dev")

---

### Post by PatheticMoFo on 2008-06-05
The following worked for me, but I don't know how things would be different in a 64-bit system.

First I ran
```
locate libxul.so
```
and got some results. I noticed that the file found in /usr/lib was called libxul.so.0d

So I quit swiftweasel, symlinked the file like this
```
sudo ln -s /usr/lib/libxul.so.0d /usr/lib/libxul.so 
```

When I started it again (in the terminal, to make sure nothing went wrong), it all worked just fine.

Hope that helps.

---

### Post by Nepherte on 2008-06-06
Thanks everyone for helping me out with this! PatheticMoFo's suggestion worked.

---

### Post by Yellow Pasque on 2008-07-26
I ran into this error again, but the directories are a bit different if you only have the new version of xulrunner (1.9.0.1). The symlink that comes with Swiftweasel 3.0.x points to /usr/lib/libxul.so.0d when it should point to /usr/lib/xulrunner-1.9.0.1/libxul.so

I searched for xul on the Swiftweasel forum, and found nothing, so I bit the bullet and reported it.

```
cd /usr/local/swiftweasel3/
rm libxul.so 
ln -s /usr/lib/xulrunner-1.9.0.1/libxul.so  libxul.so
```

---

### Post by davegp on 2009-02-12
Thanks for this solution.
I wasn't getting anywhere until I tried this symlink to libxul.so (1.9.0.6 on my machine).

---

