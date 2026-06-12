---
title: "Java related error."
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by feight on 2005-10-18
Hello fellow ubuntu'ites, I'm having an issue with kLoOge Werks installing in Breezy, originaly there was a problem installing gcj-4.0 which was apparently related to the whole GPG key scenario and is now fine.

Now that gcj-4.0 is installed I'm having an all new problem that I never had issue with in Hoary, in fact I didn't have to do any of this with Hoary, apparently the default installed software has changed as kLoOge installed perfectly after simply installing Sun's java package.

The new error is...
```
(.:30224): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted

```

I installed everything that seemed vaguely related to gdk and pixbuf and awt that I could find that looked even remotely like it related to gdk, gtk, gcj or java.

Could someone give me a hand?

---

### Post by zekolas on 2005-10-18
Ok I have never used kLoOge Werks, but it seems to only require java Runtime Environment. Are you sure you have sun's java installed? As far as I know sun's java is not in any of the apt repositories and you have to download it yourself from sun's java site. Open up an xterm and type

```
java -version
```

to make sure you have the correct sun java installed. It should say something like java runtime environment 1.5 or something like that. You can get sun's java from 
[http://java.sun.com/](http://java.sun.com/)

there are guides on how to install it but I have never read them. What I did was download the .bin file from sun's java site and ran the file. That inflated into a JRE directory. Then I simply created a link to the "java" file in the JRE directory and placed it in the /bin directory. Make sure the link is simply named "java" and not "short cut to java" or "Link to java" or something like that.

---

### Post by feight on 2005-10-19
Yep, it was installed. I downgraded to Hoary to solve my issues for the time being so I can't check at the moment, but Java isn't installed by default and I only ever use the Sun amd64 version; in other words the very fact that I got that error means that Sun's version was installed; in fact I actually installed Breezy before the official release and had the same problem, I was hoping whatever was causing it was fixed with the official release.

Appreciate the response though, you're the first to take a crack at it. I should probably mention that until I installed gcj-4.0 (a problem that I mentioned in another thread that was fixed) I had even more extensive errors, but I remember it mentioning gcj in the errors. Although looking at Hoary gcj is not installed but both Hero Designer and kLoOge Werks are working perfectly.

---

### Post by RAOF on 2005-10-19
Actually, java **is** installed by default - openoffice uses it.  The gnu java runtime (of which gcj or whatever it is is a part) is the default runtime for Breezy, even if you install the Sun JVM.  You have to change the default VM using "sudo update-alternatives --config java", and selecting the Sun VM you installed.  This is **almost certainly** the problem you had - the gnu java runtime doesn't work correctly for some stuff (of which azureus is a notable example ;))

---

### Post by feight on 2005-10-19
You... you are my hero. 

Obligatory:"If I wasn't married..." etc, etc.

I will test this out immediately after I get home from... Windows 2003 Administration class. Don't worry, my degree requires Linux classes as well, smart move on the part of the administration.

---

### Post by feight on 2005-10-19
I do not see the sun java in the list, only...
```
  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

```

I could easily replace the current java simlink in /usr/bin but is there a way to make the system officially recognize the Sun jre in /usr/java I installed?

[COLOR="Red"]EDIT: Nevermind, I fumbled my way through it. For those that may wonder, to install the Sun JRE as an option in update-alternatives, considering that you move the finished folder jre1.5.0_05 to /usr/java...[/COLOR]
```
[color="Red"]feight@feightbox:~$ sudo update-alternatives --install /usr/bin/java java /usr/java/jre1.5.0_05/bin/java 1
[/color]
```
And then of course, as our good friend RAOF has shown us...
```
[color="Red"]feight@feightbox:~$ sudo update-alternatives --config java
  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/java/jre1.5.0_05/bin/java

Press enter to keep the default[*], or type selection number: 3
[/color]
```
```
[color="Red"]  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/java/jre1.5.0_05/bin/java

Press enter to keep the default[*], or type selection number:[/color]
```

---

### Post by RAOF on 2005-10-19
Sorry, I thought you'd built a package the Sun java installer and installed that.  To do that, you just need to follow this simple [howto]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=make+java+package").  This has the advantage that the apt is now aware of your installed Sun java (so you can easily remove it cleanly) and that everything is installed into the right place.

---

### Post by feight on 2005-10-19
Oh, wow... I guess sometimes when I'm able to stumble through something on my own I don't consider if there's a better way; sometimes it's not very easy to find something like that unless you expect to find it.

Thanks for your help again, all of you.

---

