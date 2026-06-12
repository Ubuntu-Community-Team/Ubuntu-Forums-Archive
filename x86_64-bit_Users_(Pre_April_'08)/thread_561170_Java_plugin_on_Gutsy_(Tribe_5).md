---
title: "Java plugin on Gutsy (Tribe 5)"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Emblem Parade on 2007-09-27
Hooray! I got it to work! The Blackdown plugin package seems broken, but is easily fixed with a symbolic link. Here's the whole recipe:

```

sudo aptitude install j2re1.4-mozilla-plugin
ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so

```

To test it quickly, try [this game]("http://java.com/en/games/mobile/simon.jsp")

See [here]("http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown") for more information.

Hopefully the package will just work for Gutsy's final release. Flash was installed automatically with the excellent new plugin download system.

---

### Post by Kilz on 2007-09-27
> **Emblem Parade said:**
> Hooray! I got it to work! The Blackdown plugin package seems broken, but is easily fixed with a symbolic link. Here's the whole recipe:

```

sudo aptitude install j2re1.4-mozilla-plugin
ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so

```

To test it quickly, try [this game]("http://java.com/en/games/mobile/simon.jsp")

See [here]("http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown") for more information.

Hopefully the package will just work for Gutsy's final release. Flash was installed automatically with the excellent new plugin download system.

Sounds cool. There was a bug in that plugin before, maybe they fixed it. Can you get this page to load?
[http://www.crystalsquid.com/games/cg/cg_play.php](http://www.crystalsquid.com/games/cg/cg_play.php)

---

### Post by HilliBilly on 2007-09-28
doesn't work for me. :confused:

$ **ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so**
ln: creating symbolic link `/home/xyz/.mozilla/plugins/libjavaplugin_oji.so' to `/usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so': No such file or directory

$ **ls -ltr /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so **
-rw-r--r-- 1 root root 245848 2005-08-24 18:28 /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

:~/.mozilla$ **ls -a**
.  ..  firefox

---

### Post by aJayRoo on 2007-09-28
> **HilliBilly said:**
> doesn't work for me. :confused:

$ **ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so**
ln: creating symbolic link `/home/xyz/.mozilla/plugins/libjavaplugin_oji.so' to `/usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so': No such file or directory

$ **ls -ltr /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so **
-rw-r--r-- 1 root root 245848 2005-08-24 18:28 /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

:~/.mozilla$ **ls -a**
.  ..  firefox

Try this:
```
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```

I tried some pages with java apps and can confirm they are working using this method however the link 
Kilz posted would not load. At this time I'm actually using the 64-bit tribe 5 Live CD to test this so I hadn't expected the results to be too great anyway!

---

### Post by PurposeOfReason on 2007-09-28
I just installed it with 7.04 and it worked fine.

---

### Post by HilliBilly on 2007-09-29
did the symbolic link with

sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

result was a little bizzare. followed Emblem Parade's game link, what crashed mozilla. reopened mozilla, but it crashed again. 

then (just for fun), went on 
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
couldn't see the jumping duke, just a cross in the upper left corner. went back to this game link and suddenly ... was able to play this game! next step was to try to load Kilz's page, which at first freezes mozilla for about 10 seconds and lets it crash afterwards.

uninstalled everything :(

--------------
for the records: i installed j2re1.4-mozilla-plugin (1:ubuntu6, Java plugin for firefox), j2re1.4 (1.4.2.02-1, Blackdown Java 2 RE, Standard Edition) and java-common (0.26ubuntu1) via synaptic on Gutsy (2.6.22-10-generic)

---

### Post by aJayRoo on 2007-09-29
Yeah I take back what I said before, it must have been a fluke because firefox crashes after a few seconds of displaying a java app now!

---

### Post by mwacky on 2007-10-06
I've tried the suggestions above, with no luck.  would like/need to get the Java Plugin going.  I'm running Gusty Beta.  Any help is appreciated.

---

### Post by Kilz on 2007-10-07
> **mwacky said:**
> I've tried the suggestions above, with no luck.  would like/need to get the Java Plugin going.  I'm running Gusty Beta.  Any help is appreciated.


[64bit java install script, also installs Swiftweasel ]("http://tghc.org/forum/viewtopic.php?id=4&p=1")- Swiftweasel is the only browser that doesnt crash, since its a build of firefox that shouldn't be an issue for most people. Its not perfect, there are still some odd sites that crash because the plugin is old.


[32bit java, and browser]("http://ubuntuforums.org/showthread.php?t=202537") - This will install working 32bit versions for your 64bit setup. Very stable and all sites will show. But the browser may not look as pretty as the 64bit one on Kubuntu and some themes. You may also have problems using the print function to print out pages.

---

### Post by rfurman24 on 2007-10-08
Sorry to impose but is there a fix for the print concern. If not I am going back to 32bit.

---

### Post by Kilz on 2007-10-08
> **rfurman24 said:**
> Sorry to impose but is there a fix for the print concern. If not I am going back to 32bit.

Yes, print to a file, then open the file and print it out. This should not be that big of an issue as printing out java applets isnt a common task. Use the 64bit browser for everything but the few sites that use java. If not, feel free to use a operating system that cuts your performance.

---

### Post by rfurman24 on 2007-10-09
My browser would not let me print anything nor would it show any pop up windows such as downloads. I do feel free to use 32bit(operating system that cuts your performance). Flash was very buggy in the 64bit firefox and the 32bit browser was very buggy. I personally do not like having things that do not work and I play a lot of java and flash games with my daughter. I know none of the 64bit issue are the fault of ubuntu or any linux. I can not understand why 64bit as been around for at least 3 years and java and flash still have no plugins. I also feel that the 64bit advantage over 32bit is negligible but agree any performance increase is worth it if things work correctly. I will jump at a 64bit install as soon as java and flash get there act together. Still your script worked great. I am just not willing to have a gimped os.

---

### Post by Kilz on 2007-10-09
> **rfurman24 said:**
> My browser would not let me print anything nor would it show any pop up windows such as downloads. I do feel free to use 32bit(operating system that cuts your performance). Flash was very buggy in the 64bit firefox and the 32bit browser was very buggy. I personally do not like having things that do not work and I play a lot of java and flash games with my daughter. I know none of the 64bit issue are the fault of ubuntu or any linux. **I can not understand why 64bit as been around for at least 3 years and java and flash still have no plugins.** I also feel that the 64bit advantage over 32bit is negligible but agree any performance increase is worth it if things work correctly. I will jump at a 64bit install as soon as java and flash get there act together. Still your script worked great. I am just not willing to have a gimped os.

The reason is because some people would rather take the easy path, have been lied to, or frightened into running 32bit. Some lack the intelligence to get things running correctly. So the population isnt that large yet. The people making the plugins know this so put it on the back burner. So every time you see someone say "Im going back to 32 bit" understand that it is **their **fault that 64bit isnt worked on as much.

---

### Post by kwaanens on 2007-10-15
On Gutsy beta I tried 
gcjwebplugin
and the mobile phone game stuff works. The other page listed in the first couple of posts killed Firefox.

---

### Post by Kilz on 2007-10-15
> **kwaanens said:**
> On Gutsy beta I tried 
gcjwebplugin
and the mobile phone game stuff works. The other page listed in the first couple of posts killed Firefox.

The problem is that gcj runs without a security manager. Someone could write a java applet that could format your hard drive, install a rootkit, or some other evil thing. Place it on a page called "best game in the world", and it would happen.

---

### Post by kwaanens on 2007-10-15
> **Kilz said:**
> The problem is that gcj runs without a security manager. Someone could write a java applet that could format your hard drive, install a rootkit, or some other evil thing. Place it on a page called "best game in the world", and it would happen.

Wow! Thanks for the headsup!

---

