---
title: "can't get java working no matter what"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by nightfrost on 2008-05-12
I've been following all sorts of guides, followed bug reports, and read wiki pages to try and make java working in a 64-bit environment. Nothing has worked.

Firefox behaves like the plugin is not installed, although it is. Every time a site needs the plugin, I am prompted to install it, after which synaptic tells me that the icedtea plugin already is installed.

Does anybody have any idea of how I can troubleshoot this?

(I've tried both openjdk and sun-java).

---

### Post by Zorael on 2008-05-12
What is the output of the following terminal command?
```
$ ls -l /etc/alternatives/*applet*
```

---

### Post by nightfrost on 2008-05-12
> **Zorael said:**
> What is the output of the following terminal command?
```
ls -l /etc/alternatives/*applet*
```

Thanks a lot for the quick reply!

The output is:
```
lrwxrwxrwx 1 root root 54 2008-05-12 17:39 /etc/alternatives/pluginappletviewer -> /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer
```

---

### Post by Zorael on 2008-05-12
Oh, hm. What of this one?
```
$ ls -l /etc/alternatives/xulrunner-1.9-javaplugin.so
```

---

### Post by nightfrost on 2008-05-12
> **Zorael said:**
> Oh, hm. What of this one?
```
$ ls -l /etc/alternatives/xulrunner-1.9-javaplugin.so
```

Hm. I don't seem to have that file. However, ls -l /etc/alternatives/xulrunner gives

```
lrwxrwxrwx 1 root root 22 2008-05-08 16:35 /etc/alternatives/xulrunner -> /usr/bin/xulrunner-1.9

```

and dpkg -l | grep xulrunner:
```

ii  xulrunner-1.9                              1.9~b5+nobinonly-0ubuntu4~8.04.0mt1        XUL + XPCOM application runner
ii  xulrunner-1.9-gnome-support                1.9~b5+nobinonly-0ubuntu4~8.04.0mt1        Support for Gnome in xulrunner-1.9 applicati
```

---

### Post by clever on 2008-05-12
It's hard to believe, but Sun does not (yet) provide a Java plug-in for 64-bit architecture.  That means no Applets and no Web Start.

See this link [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695")

I don't know if there are other Java implementations that might work.  I ended up removing my 64-bit installation of Hardy and installed 32-bit instead.

---

### Post by Zorael on 2008-05-12
There is no official 64-bit Sun applet viewer, no. OpenJDK's seems to work for me, though.
```
(from about:plugins)

GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.
```
```
zorael@sunspire:/etc/alternatives$ ls -l xulrunner-1.9-javaplugin.so
lrwxrwxrwx 1 root root 57 2008-05-12 18:21 xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```
```
$ sudo aptitude install openjdk-6-jre
```
[http://javatester.org](http://javatester.org)


Another very possible alternative would be to install a 32-bit browser.

---

### Post by nightfrost on 2008-05-12
> **clever said:**
> It's hard to believe, but Sun does not (yet) provide a Java plug-in for 64-bit architecture.  That means no Applets and no Web Start.

See this link [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695")

I don't know if there are other Java implementations that might work.  I ended up removing my 64-bit installation of Hardy and installed 32-bit instead.

Yeah, I'm dual booting for this very reason, but I'm still trying to make the best of the 64-bit installation. The thing is, I would be happy if there was a nice firefox32 deb for the 64-bit environment along with 32-bit debs of all plugins. I would happily run that until sun gets its act together (I'm no purist), but I haven't found any such packages.

The script to be found here that installs a 32-bit firefox + plugins seems to install the a 2.x version of firefox and it's hard to go back to ff2 after using ff3 for a while. Besides, even with that script I keep having the problems I posted this thread for.

All that said, I was of the impression that the iceadtea plugin should work reasonably well. Perhaps I was wrong.

---

### Post by philinux on 2008-05-12
I'm using the openjdk version, which uses icedtea plugin. Seems to work most websites with applets except on the java.com test.

---

### Post by Zorael on 2008-05-12
> **nightfrost said:**
> All that said, I was of the impression that the iceadtea plugin should work reasonably well. Perhaps I was wrong.
Try it. :>

[quote="Wikipedia on OpenJDK"]**IcedTea**

    Main article: IcedTea

Because of the still encumbered components in the Class library, it is not yet possible to build OpenJDK only with free software components. In order to be able to do this before the whole class library is made free, and to be able to bundle OpenJDK in Fedora and other free Linux distributions, a project called IcedTea has been started by Red Hat. It is basically an OpenJDK/GNU Classpath hybrid that can be used to bootstrap OpenJDK using only Free Software.[32][33]

IcedTea is a software development and integration project launched by Red Hat in June 2007.[34] The goal is to make the OpenJDK software which Sun Microsystems released as free software in 2007 usable without requiring any other software that is not free software. For Red Hat, this would make it possible to add OpenJDK to the Fedora Linux distribution, as well as other distributions.

On November 05, 2007, Red Hat has signed both the Sun Contributor Agreement and the OpenJDK Community TCK License[35].One of the first benefits of this agreement is tighter alignment with the IcedTea project, which brings together Fedora and JBoss technologies in a Linux environment, IcedTea providing Free Software alternatives for the few remaining proprietary sections in the OpenJDK project.

As of March 2008, the Fedora 9 distribution will be released with OpenJDK 6 instead of IcedTea[14]. Some of the stated reasons for this changes are:

    * Sun has replaced most of the encumbrances for which IcedTea was providing replacements (there is still approximately 1% of encumbered code in the class library).
    * OpenJDK 6 is a stable branch, whereas OpenJDK 7 is unstable and not expected to ship a stable release until 2009.
    * Sun has licensed the OpenJDK trademark for use in Fedora.

As of April 2008, Ubuntu also focuses on their OpenJDK 6 IcedTea[16], showing less activity on their OpenJDK 7 IcedTea[36].[/quote]

---

### Post by nightfrost on 2008-05-12
Zorael: Would you mind giving me the output of dpkg -S /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so?

I just can't find that file, I've tried package after package...

---

### Post by nightfrost on 2008-05-12
> **nightfrost said:**
> Zorael: Would you mind giving me the output of dpkg -S /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so?

I just can't find that file, I've tried package after package...

Ah, found it, it was in the icedtea package, but for some reason I had to create the link in /etc/alternatives manually to have things working.

Thanks a lot for your help! It seems to work now. Weird problem though...

---

### Post by saru411 on 2008-05-12
If you want a simple work around that doesn't take any time or real headache you should use Kilz script to install 32 bit firefox with 32 bit flash,mplayer,and java. It can be found [**_[COLOR="Red"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java").
I have used this script for a very long time on multiple builds and it has worked every time. Kilz keeps his script up to date so you dont need to worry about it being old.

---

### Post by nightfrost on 2008-05-12
> **saru411 said:**
> If you want a simple work around that doesn't take any time or real headache you should use Kilz script to install 32 bit firefox with 32 bit flash,mplayer,and java. It can be found [**_[COLOR="Red"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java").
I have used this script for a very long time on multiple builds and it has worked every time. Kilz keeps his script up to date so you dont need to worry about it being old.

I'd love to use that script, but as far as I understand it only supports firefox 2.x. And as I said above, having used firefox 3, it's impossible for me to go back.

---

### Post by Zorael on 2008-05-12
> **nightfrost said:**
> I'd love to use that script, but as far as I understand it only supports firefox 2.x. And as I said above, having used firefox 3, it's impossible for me to go back.
Same thing for me; FF2 performance is simply not acceptable on my system. For the time being I'll use the buggy FF3 and pop up an Opera on the side whenever I really need to see flash content.

---

### Post by nightfrost on 2008-05-12
> **Zorael said:**
> Same thing for me; FF2 performance is simply not acceptable on my system. For the time being I'll use the buggy FF3 and pop up an Opera on the side whenever I really need to see flash content.

Flash is working fine on ff3 64-bit for me, though. That stuff was just automatic on hardy...

---

### Post by Zorael on 2008-05-12
> **nightfrost said:**
> Flash is working fine on ff3 64-bit for me, though. That stuff was just automatic on hardy...
The installation was automatic, but it won't work properly.
> Some people have reported that NSPluginwrapper crashes with the new Flash 9 Update 3 (9.0.115) plug-in. It turns out this is triggered in multithreaded context and is more visible on SMP/CMP machines.
[http://ubuntuforums.org/showthread.php?t=786392](http://ubuntuforums.org/showthread.php?t=786392)
[http://ubuntuforums.org/showthread.php?t=791127](http://ubuntuforums.org/showthread.php?t=791127)


Do you have a processor with multiple cores, or several processors?

---

### Post by nightfrost on 2008-05-12
> **Zorael said:**
> The installation was automatic, but it won't work properly.

[http://ubuntuforums.org/showthread.php?t=786392](http://ubuntuforums.org/showthread.php?t=786392)
[http://ubuntuforums.org/showthread.php?t=791127](http://ubuntuforums.org/showthread.php?t=791127)


Do you have a processor with multiple cores, or several processors?

Ah, I didn't know that. As a matter of fact, I hardly use flash so I haven't noticed any problems yet. But good to know.

I have two cores, one processor.

---

### Post by ethoxyethaan on 2008-05-12
i can confirm i had the same problem on ubuntu 7.10
maybe this tread will become helpful to me as well.

java dident worked in my browser so i installed a 32 bit firefox and installed the 32 bit java version.

---

### Post by Kilz on 2008-05-12
> **Zorael said:**
> Same thing for me; FF2 performance is simply not acceptable on my system. For the time being I'll use the buggy FF3 and pop up an Opera on the side whenever I really need to see flash content.

Please tell me exactly what "performance" you are getting from a buggy not working correctly FF3.

---

### Post by Zorael on 2008-05-13
> **Kilz said:**
> Please tell me exactly what "performance" you are getting from a buggy not working correctly FF3.
I'm not sure you understand, though I may be the one misinterpreting.

FF3 performance is agreeable. Flash with FF3 is borderline acceptable. See the links in my previous post.

FF2 performance is dismal. Example: if I open up ubuntuforums.org and middle-click five forum sections, Firefox will go unresponsive and grey out for about 30 seconds before starting to draw them. This is on a dual-core 2ghz processor.

---

### Post by Kilz on 2008-05-13
> **Zorael said:**
> I'm not sure you understand, though I may be the one misinterpreting.

FF3 performance is agreeable. Flash with FF3 is borderline acceptable. See the links in my previous post.

FF2 performance is dismal. Example: if I open up ubuntuforums.org and middle-click five forum sections, Firefox will go unresponsive and grey out for about 30 seconds before starting to draw them. This is on a dual-core 2ghz processor.

Looking at your post history I see you are having graphics driver issues, are you still experiencing them? Because that may all be tied together because of the driver.

---

### Post by Zorael on 2008-05-13
> **Kilz said:**
> Looking at your post history I see you are having graphics driver issues, are you still experiencing them? Because that may all be tied together because of the driver.
Graphics driver issues? Now I'm confused.

Feisty, Gutsy and Hardy have pretty much worked out of the box as graphics are concerned; the posts I've made on video-related threads are mostly trying to help people getting their xorg.confs worked out after upgrading. I did post in one thread regarding screen brightness, but that was out of curiosity on finding out how applications interacted with the acer apci interface to brighten/darken the screen as well as toggle wireless and bluetooth.

---

