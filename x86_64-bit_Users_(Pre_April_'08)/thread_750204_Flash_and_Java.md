---
title: "Flash and Java"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by JemW on 2008-04-09
I do hope someone can help me here, as elsewhere I've had no response elsewhere. I am new to Linux, although not to Windows, and running the current Ubuntu release for AMD64 / ALL updates as prompted.

I have a clean Ubuntu build and I'm using Firefox. First page I go to is bbc.co.uk which wants me to install Flash. I say Yes to the Adobe 'non-free' installation and it proceeds to apparently successful completion. Restart FF and...I get the same prompt to install Flash. Basically it doesn't work.

Java - I dare not even go there. Reason for the rebuild is I screwed my Ubuntu installation yesterday by downloading things I shouldn't have done (Java Related). I simply want to use Java in Firefox, that's all, noting else I do with Java. Just web applets as required.

Really hoping someone can hold my hand through this. It should be simple but isn't...

Thanks (I hope)

---

### Post by sio2 on 2008-04-09
Try and use the add/remove and type java - set the window to allow all applications. Then tick the java programs that pops up. That way you get a secure install of java that works in ubuntu.

If it is not enough eksplenation then wrigth again!

---

### Post by Belak on 2008-04-09
Or, you can open up synaptic (System->Administration->Synaptic Package Manager) and search for
ubuntu-restricted-extras

I'd also reccomend the medibuntu repositories with the non-free codecs

Restricted Formats (Because of Copywrite)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Flash:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
Java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

And here's the page on medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by JemW on 2008-04-09
> **Belak said:**
> Or, you can open up synaptic (System->Administration->Synaptic Package Manager) and search for
ubuntu-restricted-extras

I'd also reccomend the medibuntu repositories with the non-free codecs

Restricted Formats (Because of Copywrite)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Flash:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
Java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

And here's the page on medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thank you. I didn't realise that Adobe Flash is not supposed to work in a 64 bit build. That would explain a lot. I've removed the Adobe plug-in I previously installed, using the Package Manager, and I've now installed Gnash which is supposed to work apparently, according to the author of the Flash page you pointed me at. It sort of works on most Flash enabled pages, but some still complain.

I'll have a go at Java later, but I may to go back to running the 32 bit FF version on here to enable me to use the plug-ins correctly.

Any more thoughts on this gratefully received. Thanks.

EDIT: In fact, I just read the Java link as well, and it seems there is NO Java plug-in for FF 64 bit, so I have to go back to 32bit FF. Now I know...

---

### Post by Kilz on 2008-04-10
> **Belak said:**
> Or, you can open up synaptic (System->Administration->Synaptic Package Manager) and search for
ubuntu-restricted-extras

[B]Flash:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
Java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)[/B]


Those pages need to be updated by someone who runs 64bit.

---

### Post by Half-Left on 2008-04-10
If you want to watch bbc videos then just install totem-xine and remove totem-gstreamer, select Windows media player format on their popup and you can watch them.

---

### Post by jelly111 on 2008-04-10
I am running 64 bit ubuntu and I can see have no problems seeing flash sites and java

---

### Post by JemW on 2008-04-10
> **jelly111 said:**
> I am running 64 bit ubuntu and I can see have no problems seeing flash sites and java

So how did you achieve that? You must be running a 32 bit browser. If not, how did you configure it?

---

### Post by Half-Left on 2008-04-10
Have you not seen the sticky thread about it and how to do it? [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by JemW on 2008-04-10
> **Half-Left said:**
> Have you not seen the sticky thread about it and how to do it? [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I hadn't seen that one, no. So,what about Java? That thread is about Flash...

---

### Post by Half-Left on 2008-04-10
Read more of that thread, there is a Java part. Unless they do pure 64bit support your going to have to use work arounds but blame proprietary software for that since Ubuntu can't fix it or support it unless it's more open.

---

### Post by JemW on 2008-04-10
> **Half-Left said:**
> Read more of that thread, there is a Java part. Unless they do pure 64bit support your going to have to use work arounds but blame proprietary software for that since Ubuntu can't fix it or support it unless it's more open.

1) It quite clearly says the wrapper won't work with Java.

2) No-one has told me, in a forum answer, or in a sticky, how to get Java applets working in Ubuntu 64 bit. I don't care who's to blame. Fact seems to be, you can't do it, I want Java in my browser, so it has to be Ubuntu 32 bit. If someone tells me how, clearly, anywhere, I'll gladly try it, but no-one has.

---

### Post by Kilz on 2008-04-10
> **JemW said:**
> 1) It quite clearly says the wrapper won't work with Java.

2) No-one has told me, in a forum answer, or in a sticky, how to get Java applets working in Ubuntu 64 bit. I don't care who's to blame. Fact seems to be, you can't do it, I want Java in my browser, so it has to be Ubuntu 32 bit. If someone tells me how, clearly, anywhere, I'll gladly try it, but no-one has.

```
sudo apt-get install icedtea-java7-plugin
```

---

### Post by JemW on 2008-04-10
> **Kilz said:**
> ```
sudo apt-get install icedtea-java7-plugin
```

And that will work? If it does you're a star and you can safely ignore my other slightly stroppy reply to you ;) BTW, to find out, I'm going to have to rebuild!!! It better be worth it.

---

### Post by JemW on 2008-04-10
> **JemW said:**
> And that will work? If it does you're a star and you can safely ignore my other slightly stroppy reply to you ;) BTW, to find out, I'm going to have to rebuild!!! It better be worth it. 

Is that not the same as choosing the option when prompted in Firefox? When I first tried that in 64 bit it did not work. Is there anything different about this command line that you've posted?

---

### Post by Kilz on 2008-04-10
> **JemW said:**
> Is that not the same as choosing the option when prompted in Firefox? When I first tried that in 64 bit it did not work. Is there anything different about this command line that you've posted?

Its not the same, try it and see. Also , I recommend reading the stickies. You will have less problems if you read the stickies. They are full of good information. New users have a lot to learn, imho one of the most important things is that the documentation is incredible.

---

### Post by JemW on 2008-04-10
> **Kilz said:**
> Its not the same, try it and see. Also , I recommend reading the stickies. You will have less problems if you read the stickies. They are full of good information. New users have a lot to learn, imho one of the most important things is that the documentation is incredible.

Followed your instructions and the installation appeared to complete in the terminal window (back to the prompt). Nothing doing - it does not work in Firefox. No Java site I tried would use applets. Mapping sites reverted to static maps, Java tests failed.

---

### Post by Kilz on 2008-04-10
> **JemW said:**
> Followed your instructions and the installation appeared to complete in the terminal window (back to the prompt). Nothing doing - it does not work in Firefox. No Java site I tried would use applets. Mapping sites reverted to static maps, Java tests failed.

Open a terminal and Please give me the results of 
```
ls -al /usr/lib/mozilla/plugins
```
and 
```
ls -al /usr/lib/firefox/plugins

```

---

### Post by JemW on 2008-04-11
> **Kilz said:**
> Open a terminal and Please give me the results of 
```
ls -al /usr/lib/mozilla/plugins
```

total 8
drwxr-xr-x 2 root root 4096 2008-04-11 01:05 .
drwxr-xr-x 3 root root 4096 2007-10-16 00:27 ..
lrwxrwxrwx 1 root root   39 2008-04-11 01:05 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   36 2008-04-11 00:43 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2008-04-11 00:43 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2008-04-11 00:43 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2008-04-11 00:43 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2008-04-11 00:43 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2008-04-11 00:43 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2008-04-11 00:43 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2008-04-11 00:43 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
 

```
ls -al /usr/lib/firefox/plugins

```

total 20
drwxr-xr-x 2 root root  4096 2008-04-11 01:05 .
drwxr-xr-x 5 root root  4096 2007-10-16 00:32 ..
lrwxrwxrwx 1 root root    39 2008-04-11 01:05 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root    36 2008-04-11 00:43 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2008-04-11 00:43 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2008-04-11 00:43 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2008-04-11 00:43 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2008-04-11 00:43 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2008-04-11 00:43 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-04-11 00:43 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2008-04-11 00:43 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2007-10-08 16:34 libunixprintplugin.so

EDIT: In the meantime I ran the Flash install script and it worked perfectly. So thanks for that, just hope we can sort out the Java issue (whatever it is). Incidentally, this is a clean 7.10 install with NO updates installed. If that possible makes  a difference tell me and I'll allow them to download.

---

### Post by Kilz on 2008-04-11
Ok it looks like you have java plugin symlinks

Please givs me the results of 
```
which java
```

In the browser, click Help, then About Firefox. Near the bottom of the little window that opens is a string that starts with Mozilla/5.0. Please copy and paste it in a reply.

next, please give the results of 
```
uname -a

```

Lastly, open the browser, type in ```
about:plugins
``` in the address bar and hit enter. Do you see a java section? If please give the filename information.

---

### Post by JemW on 2008-04-11
> **Kilz said:**
> Ok it looks like you have java plugin symlinks

Please givs me the results of 
```
which java
```

**/usr/bin/java**

In the browser, click Help, then About Firefox. Near the bottom of the little window that opens is a string that starts with Mozilla/5.0. Please copy and paste it in a reply.

next, please give the results of 
```
uname -a

```

**Linux jem-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux**

Lastly, open the browser, type in ```
about:plugins
``` in the address bar and hit enter. Do you see a java section? If please give the filename information.[/QUOTE]

[B]GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes[/B]

---

### Post by utUtu on 2008-04-11
> **JemW said:**
> Followed your instructions and the installation appeared to complete in the terminal window (back to the prompt). Nothing doing - it does not work in Firefox. No Java site I tried would use applets. Mapping sites reverted to static maps, Java tests failed.

Just curious ,which mapping sites uses java?  I'd like to check it out myself.

---

### Post by JemW on 2008-04-11
> **utUtu said:**
> Just curious ,which mapping sites uses java?  I'd like to check it out myself.

For example: [http://www.uk.map24.com/](http://www.uk.map24.com/)

This is what happens if Java isn't working...

---

### Post by utUtu on 2008-04-11
> **JemW said:**
> For example: [http://www.uk.map24.com/](http://www.uk.map24.com/)

This is what happens if Java isn't working...

Are you ok now that you have icedtea java plugin?  I have icedtea, and your site is working for me.  I have hardy and FF3b5 though.

---

### Post by JemW on 2008-04-11
> **utUtu said:**
> Are you ok now that you have icedtea java plugin?  I have icedtea, and your site is working for me.  I have hardy and FF3b5 though.

No, that's the point. It doesn't work with the Iced Tea Plug-in - hopefully Kilz is looking at this for me after my last report to him.

I have Ubuntu 7.10 and FF 2.0.0.13. I have no intention of running Beta anything unless I absolutely have to. I'll wait on Kilz...

---

### Post by Half-Left on 2008-04-11
Both flash and java icedtea plugin work great in Hardy 64bit beta, it's just like using the 32bit version now how they've done it. Having the flash plugin install the extra lib32's is not idea but I guess it's better than before.

---

### Post by Kilz on 2008-04-11
> **JemW said:**
> No, that's the point. It doesn't work with the Iced Tea Plug-in - hopefully Kilz is looking at this for me after my last report to him.

I have Ubuntu 7.10 and FF 2.0.0.13. I have no intention of running Beta anything unless I absolutely have to. I'll wait on Kilz...

Ok, obviously you need a Sun java plugin. Icedtea is installed, but isnt perfect, its open source java and some selective sites dont work. But there is no 64bit sun java plugin. [The alternative is running a 32bit browser]("http://ubuntuforums.org/showthread.php?t=202537") on your 64bit install, that way you can use a sun java plugin.

---

### Post by utUtu on 2008-04-11
> **JemW said:**
> No, that's the point. It doesn't work with the Iced Tea Plug-in - hopefully Kilz is looking at this for me after my last report to him.

I have Ubuntu 7.10 and FF 2.0.0.13. I have no intention of running Beta anything unless I absolutely have to. I'll wait on Kilz...

Looks like you 'absolutely' have to now.  :)

Anyway, I fired up my gutsy and installed icedtea-java7-plugin and everything is working for me in FF2.0.0.13

```
Unpacking icedtea-java7-plugin (from .../icedtea-java7-plugin_7~b21-1.4+20071007-0ubuntu6_amd64.deb) ...
Setting up java-common (0.26ubuntu1) ...

Setting up libxp6 (1:1.0.0.xsf1-1build1) ...

Setting up lesstif2 (1:0.95.0-2.1) ...

Setting up icedtea-java7-jre (7~b21-1.4+20071007-0ubuntu6) ...
Setting up icedtea-java7-plugin (7~b21-1.4+20071007-0ubuntu6) ...

Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
root@k64g01:~# uname -a
Linux k64g01 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
root@k64g01:~#      
```

---

### Post by JemW on 2008-04-11
> **utUtu said:**
> Looks like you 'absolutely' have to now.  :)

Anyway, I fired up my gutsy and installed icedtea-java7-plugin and everything is working for me in FF2.0.0.13

```
Unpacking icedtea-java7-plugin (from .../icedtea-java7-plugin_7~b21-1.4+20071007-0ubuntu6_amd64.deb) ...
Setting up java-common (0.26ubuntu1) ...

Setting up libxp6 (1:1.0.0.xsf1-1build1) ...

Setting up lesstif2 (1:0.95.0-2.1) ...

Setting up icedtea-java7-jre (7~b21-1.4+20071007-0ubuntu6) ...
Setting up icedtea-java7-plugin (7~b21-1.4+20071007-0ubuntu6) ...

Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
root@k64g01:~# uname -a
Linux k64g01 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
root@k64g01:~#      
```

Map24 works? - Make sure you're choosing the Interactive Map!

---

### Post by JemW on 2008-04-11
> **Kilz said:**
> Ok, obviously you need a Sun java plugin. Icedtea is installed, but isnt perfect, its open source java and some selective sites dont work. But there is no 64bit sun java plugin. [The alternative is running a 32bit browser]("http://ubuntuforums.org/showthread.php?t=202537") on your 64bit install, that way you can use a sun java plugin.

Now that I've downloaded the updates, including Firefox, what's the correct command line to *remove* the Iced Tea plugin and then re-install it to see if anything works better.

---

### Post by JemW on 2008-04-11
> **Half-Left said:**
> Both flash and java icedtea plugin work great in Hardy 64bit beta, it's just like using the 32bit version now how they've done it. Having the flash plugin install the extra lib32's is not idea but I guess it's better than before.

Can you confirm on the 'map24' site that interactive mapping using Java applets is working in Hardy. Also any other Java applet sites where you can be sure Iced Tea is functioning.

Thanks

---

### Post by JemW on 2008-04-11
> **utUtu said:**
> Are you ok now that you have icedtea java plugin?  I have icedtea, and your site is working for me.  I have hardy and FF3b5 though.

When you say map24 is working - are you sure you have interactive mapping using the Java applet? Let me know....

---

### Post by Half-Left on 2008-04-11
> **JemW said:**
> Can you confirm on the 'map24' site that interactive mapping using Java applets is working in Hardy. Also any other Java applet sites where you can be sure Iced Tea is functioning.

Thanks


Yep, working fine with the map and java.

[[IMG]http://img177.imageshack.us/img177/7738/screenshot1ta6.th.png[/IMG]](http://img177.imageshack.us/my.php?image=screenshot1ta6.png)

---

### Post by JemW on 2008-04-11
> **Half-Left said:**
> Yep, working fine with the map and java.

[[IMG]http://img177.imageshack.us/img177/7738/screenshot1ta6.th.png[/IMG]](http://img177.imageshack.us/my.php?image=screenshot1ta6.png)

OK, downloading Hardy. I have Gutsy using my whole disk atm. How do I install Hardy preserving the current set-up? Start up from the CD and re-partition?

---

### Post by Half-Left on 2008-04-11
Not sure about updating from cd but when the final version of Hardy comes out, a messing in your gusty install will let you upgrade via the update manager.

I'd recommend do a fresh Hardy 64bit install to avoid issues

---

### Post by JemW on 2008-04-11
> **Half-Left said:**
> Not sure about updating from cd but when the final version of Hardy comes out, a messing in your gusty install will let you upgrade via the update manager.

I'd recommend do a fresh Hardy 64bit install to avoid issues
Running Hardy here now...

Before I screw up, do you recommend I install Iced Tea when prompted on the Test Java page or follow the Terminal install procedure as suggested by Kilz?

---

### Post by Half-Left on 2008-04-11
It's upto you, all I can say is what I did, I went into synaptic package manager and installed it through there then just refreshed the java page and the plugin worked.

---

### Post by JemW on 2008-04-12
> **Half-Left said:**
> It's upto you, all I can say is what I did, I went into synaptic package manager and installed it through there then just refreshed the java page and the plugin worked.

OK, I have Java running on the test page. Sorry to doubt you but I don't see that Map24 can be running with an Interactive map for you. This site seems to insist on JRE and gives me the same request to install Java even in Hardy. Can you check again and make sure you aren't looking at the static map? If you click on interactive map at the top it will think about it for a while and then fail with the warning.

---

### Post by Half-Left on 2008-04-12
> **JemW said:**
> OK, I have Java running on the test page. Sorry to doubt you but I don't see that Map24 can be running with an Interactive map for you. This site seems to insist on JRE and gives me the same request to install Java even in Hardy. Can you check again and make sure you aren't looking at the static map? If you click on interactive map at the top it will think about it for a while and then fail with the warning.

Here's a screenshot of it working with my city.

[[IMG]http://img175.imageshack.us/img175/2176/screenshothj4.th.png[/IMG]](http://img175.imageshack.us/my.php?image=screenshothj4.png) :)

---

### Post by JemW on 2008-04-12
> **Half-Left said:**
> Here's a screenshot of it working with my city.

[[IMG]http://img175.imageshack.us/img175/2176/screenshothj4.th.png[/IMG]](http://img175.imageshack.us/my.php?image=screenshothj4.png) :)

That looks like the static map to me.

---

### Post by Half-Left on 2008-04-12
I can move about by holding the right mouse button down and zoom in a out. Some java applets dont see you have the right version but will function regardless. I suspect it's because of Icetea and not the latest Sun Java plugin which it prefers or recommends.

---

### Post by JemW on 2008-04-12
> **Kilz said:**
> Ok, obviously you need a Sun java plugin. Icedtea is installed, but isnt perfect, its open source java and some selective sites dont work. But there is no 64bit sun java plugin. [The alternative is running a 32bit browser]("http://ubuntuforums.org/showthread.php?t=202537") on your 64bit install, that way you can use a sun java plugin.

Forget my last post - it worked. I made a stupid mistake!

---

