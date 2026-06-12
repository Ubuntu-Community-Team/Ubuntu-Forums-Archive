---
title: "Troubles with Java"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pay87 on 2007-06-13
I managed installing flash on my Feisty 64 using this script:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

So now i tried installing Java.
What i did:
-i installed the 32but linux package in /usr/local/java32/
-then i tried to make a symlink with this command (ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./) in following folders:
-/usr/lib/firefox/plugins
-/usr/lib/mozilla/plugins

I am not sure why there are 2 folders which seem to have firefox plugins included..
I activated Java but it is still not working and not shown in about : plugins pay, any solution for me? :(

---

### Post by Gannin on 2007-06-13
Just for the heck of it, have you tried making a symlink in your ~/.mozilla/plugins directory?

---

### Post by Kilz on 2007-06-13
> **Pay87 said:**
> I managed installing flash on my Feisty 64 using this script:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

So now i tried installing Java.
What i did:
-i installed the 32but linux package in /usr/local/java32/
-then i tried to make a symlink with this command (ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./) in following folders:
-/usr/lib/firefox/plugins
-/usr/lib/mozilla/plugins

I am not sure why there are 2 folders which seem to have firefox plugins included..
I activated Java but it is still not working and not shown in about : plugins pay, any solution for me? :(

Ok, first off what you are trying to do is install a 32bit plugin into a 64bit browser.  this will never work. the only reason you can use a 32bit flash plugin is because of nspluginwrapper. But nspluginwrapper will not work with the java plugin.
There is no safe way to run java in the 64bit browser. Someone is bound to post about java-gcj-compat-plugin. It is avilable, but You should be aware of this from the [java page]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that the **plugin currently runs with[COLOR="Red"] no [/COLOR]security manager.** This means that applets you load can do anything a java application that you download and run can do. **Be **very** careful which applets you run.**

What this is saying is that if someone makes an applet that installs a rootkit, formats your hard drive, or does some other nasty thing. The plugin will let it. I will not and will suggest you never run this plugin.
You do have tghe option of installing a safe 32bit install if you want, link in my signature.

---

### Post by Pay87 on 2007-06-13
> **Kilz said:**
> Ok, first off what you are trying to do is install a 32bit plugin into a 64bit browser.  this will never work. the only reason you can use a 32bit flash plugin is because of nspluginwrapper. But nspluginwrapper will not work with the java plugin.
There is no safe way to run java in the 64bit browser. Someone is bound to post about java-gcj-compat-plugin. It is avilable, but You should be aware of this from the [java page]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

Starting with Ubuntu 6.10 (EdgyEft), you can install the experimental java-gcj-compat-plugin from the universe archive. It is available on all architectures. Note however, that the **plugin currently runs with[COLOR="Red"] no [/COLOR]security manager.** This means that applets you load can do anything a java application that you download and run can do. **Be **very** careful which applets you run.**

What this is saying is that if someone makes an applet that installs a rootkit, formats your hard drive, or does some other nasty thing. The plugin will let it. I will not and will suggest you never run this plugin.
You do have tghe option of installing a safe 32bit install if you want, link in my signature.

OK now i used your 3in1 script and installed Swiftweasel.
I have to say this script is the best i ever used for a 64Bit system! thanks alot!! :D
One question. Does Swiftweasel update itself when there are updates available?
Is Swiftweasel 32Bit safety on a 64 Bit sytem? 

thank alot!! :p

---

### Post by Kilz on 2007-06-13
> **Pay87 said:**
> OK now i used your 3in1 script and installed Swiftweasel.
I have to say this script is the best i ever used for a 64Bit system! thanks alot!! :D
One question. Does Swiftweasel update itself when there are updates available?
Is Swiftweasel 32Bit safety on a 64 Bit sytem? 

thank alot!! :p

Yes Swiftweasel is safe to use on a 64bit system . The package that is installed is created by the developer of Swiftweasel. As of the version you installed Swiftweasel does not update itself. But reading the [Swiftweasel home page]("http://swiftweasel.sourceforge.net/"), auto update notifications were just added to the development builds just released. I expect that they will be in the next main release.

---

