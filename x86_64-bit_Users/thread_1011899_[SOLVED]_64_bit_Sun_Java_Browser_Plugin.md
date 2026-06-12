---
title: "[SOLVED] 64 bit Sun Java Browser Plugin"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by wd5gnr on 2008-12-15
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

Early access... anyone try it? I guess I'm going to try it now.


Wow! Took me a bit to figure out. To install I did:
cd /opt
sudo sh ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

So you wind up with /opt/jre1.6.0_12

cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so 
(restart firefox)

[http://www.thinkfree.com](http://www.thinkfree.com) works! Finally!

---

### Post by Kilz on 2008-12-15
Cool , one more piece of the puzzle is in place. But it will take forever to kill the FUD.

---

### Post by Arup on 2008-12-15
Would it be possible to install this in the standard jvm folder instead of the /opt and set it as default Java for all apps including OO and Opera. This way I can remove the other Java in the system including Sun's old 1.6.10 and Open JDK.

---

### Post by wd5gnr on 2008-12-15
I'm sure it is, but I didn't want to upset the packaging since this is a pre release. But in fact, if you explore /etc/alternatives (and man update-alternatives) you should be able to put it where you like and get the system to use it as the default Java.

But having it in /opt means I'll remember to get rid of it once it becomes official.

---

### Post by Arup on 2008-12-15
Many thanks, will give it a spin, Iced Tea would have to be removed I guess, in fact Iced Tea works fine in FF but for Opera, even the Sun Java 1.6.10 though recognized doesn't work on Java sites.

---

### Post by swatsbiz on 2008-12-15
> **wd5gnr said:**
> 

[http://www.thinkfree.com](http://www.thinkfree.com) works! Finally!

It seems to be working for me without your solution ... have you enabled the medibuntu repositories etc?

---

### Post by wd5gnr on 2008-12-15
The only way I've had it work before is to use 32-bit Firefox/Java. With IcedTea (only solution on 64 bit before now) the ThinkFree site would detect you weren't using Sun Java and refuse to load. Although I haven't tried it lately -- maybe they fixed their checking. 

Anyway, the Sun Java is working fine so that's a good thing.

---

### Post by vrangforestillinger on 2008-12-15
Finally! My internetbank didnt want to play with me when it discovered I did not use the holy "Sun Java(TM) 1.5.0 or later".

Works well in firefox. But sadly does not play nice with Opera 9.62 x64 (if it works, its incredibly slow). Hm. Having problems with flash also there.

---

### Post by Arup on 2008-12-15
I have Sun Java 1.6.10 installed from the medibuntu repos and the thinkfree site worked fine with no issues on my Opera 9.62. As a matter of fact, I am yet to come across a Java site not working with Opera, as for Flash, it works really good via the Flash 10x64 plugin which I installed in /usr/lib/mozilla/plugins folder and Opera picked that up right away. You have to make sure there is no remnants of old x32 Flash lying around and nsplugin should be totally out of your system.

---

### Post by Sef on 2008-12-15
Thanks for the link about the 64-bit plug in.  I have added it to the [64-bit Java sticky]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by jespdj on 2008-12-16
Great! So finally we're getting 64-bit Flash and a 64-bit Java plugin - so in a few months time, there's *really* not a single reason anymore to not run 64-bit Ubuntu.

But I have to agree with Kilz unfortunately:
> But it will take forever to kill the FUD.

---

### Post by Tares on 2008-12-16
Works great ;-) along with flash :D

---

### Post by eyelessfade on 2008-12-16
Now we only miss support for wma9 but I rarely bump into those so ^^


Hope we get flash and java into backport soon :)

---

### Post by Thelasko on 2008-12-16
> **eyelessfade said:**
> Hope we get flash and java into backport soon :)

Agreed, especially for those of us sticking with Hardy for a while.

---

### Post by wd5gnr on 2008-12-16
> **eyelessfade said:**
> Now we only miss support for wma9 but I rarely bump into those so ^^


I have a series of videos that use some Windows-only encoding that has no 64 bit codecs for it (yes, even in mediabuntu). However, Crossover office (got it when they were giving it away) will run Windows Media Player (kind of, stick with the corporate skin) and the videos play fine using that. Haven't tried it with off the shelf wine. Wine will now handle Endicia Internet postage which was the only other reason I ever booted up Windows under Virtual Box (which is the other way to handle that problem).

---

### Post by CarlosinFL on 2008-12-16
So is this fully functional now as a plugin for Firefox?

I found the link here:

[http://developers.slashdot.org/article.pl?sid=08/12/16/0037200](http://developers.slashdot.org/article.pl?sid=08/12/16/0037200)

I really want to run 64 bit however I can't interface with my Symantec Netbackup GUI or Cisco ASDM Firefall module.

Anyone have any words of advice or should I still wait?

---

### Post by sirwhiteout on 2008-12-16
> **wd5gnr said:**
> 
cd /opt
sudo sh ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

So you wind up with /opt/jre1.6.0_12

cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so 
(restart firefox)


That didn't work for me. When i go to about:plugins on Firefox there is no mention of libnpjp2.so.

Is there anything else I should do?

---

### Post by wd5gnr on 2008-12-16
> **sirwhiteout said:**
> That didn't work for me. When i go to about:plugins on Firefox there is no mention of libnpjp2.so.

Is there anything else I should do?

That should do it unless your firefox is configured not to use that plug in directory. Are you running 64-bit firefox? If you were running 32 bit (as many have done) that could be your problem also. What plugins do you see?

---

### Post by zika on 2008-12-16
does IcedTea have to be removed (uninstalled) in order to use this Java plugin in Firefox? if so, is apt-get unistall icedtea6-plugin enough?

**update**:no, id doesn't have to be removed. I've just disabled it and this 64-bit Java works. the question remains:what to do with icedtea?

**comment1**: I have to admit that I do not see noticable difference betwee Epiphany built in Java and this 64-bit plugin. it seems that Epiphany scores 1 again. will see.
**comment2**: The moment IcedTea6-plugin was completely removed things are totally different. Java is working better than in Windows and its fast like a bullet. this is the thing that might get me back to Firefox from Epiphany ...
**comment3**: it got me to make Firefox browser of choice again because Sage is now giving great plot3d since Java is working properly for the first time. Great! Thanks wd5gnr!

---

### Post by sirwhiteout on 2008-12-16
> **wd5gnr said:**
> That should do it unless your firefox is configured not to use that plug in directory. Are you running 64-bit firefox? If you were running 32 bit (as many have done) that could be your problem also. What plugins do you see?

How do I see the plugins directory Firefox is using?

I'm running 64-bit Firefox.

Plugins I can see :

- Shockwave Flash
- Default plugin
- Demo Print plugin for unix/linux

and the Totem plugins
- iTunes application detector
- Totem web browser plugin
- Helix DNA plugin
- VLC multimedia plugin
- Windows media player plugin
- DivX web player
- QuickTime plugin

---

### Post by gusfm on 2008-12-16
Worked great! Thanks!!!

---

### Post by marcw on 2008-12-16
Not quite...

I got all of my applet sites to work except one - my Juniper SSL VPN.  It starts to work...  It looks like it's going to work...  But then, no applet.  Rats.  So close.  Oh well, back to my 32bit Swiftweasel for VPN stuff.

---

### Post by 73ckn797 on 2008-12-16
> **Kilz said:**
> Cool , one more piece of the puzzle is in place. But it will take forever to kill the FUD.

Help me out here. What does FUD mean? NEVERMIND, I think I know what it means after reading in another thread. The context makes it clear. Something like "f'n useless discussion". Kind of like FUBAR!

Java has been the main reason I do not use the 64 bit Ubuntu. If it really does work like you say, then I will begin loading the 64 Ubuntu and give it a whirl.

edit: Java would not work to do photo uploads via Aurigma Photo Uploader on several sites I use for my work.

---

### Post by tomdkat on 2008-12-16
> **73ckn797 said:**
> Help me out here. What does FUD mean? NEVERMIND, I think I know what it means after reading in another thread. The context makes it clear. Something like "f'n useless discussion". Kind of like FUBAR!
In this context, [FUD](http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt) means "**F**ear, **U**ncertainty, and **D**oubt".

Peace...

---

### Post by Thelasko on 2008-12-16
> **sirwhiteout said:**
> That didn't work for me. When i go to about:plugins on Firefox there is no mention of libnpjp2.so.

Is there anything else I should do?

Same thing here, I followed the instructions line by line.

When I use sudo update-alternatives --config java I get this message:
```
sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.

```
Am I supposed to install Java from the repositories too?

---

### Post by Thelasko on 2008-12-16
I fixed it!

I copied the link to my ~/.mozilla/plugins folder and changed the permissions on the link so they are my own.

Java from the repositories does not need to be installed.

---

### Post by jespdj on 2008-12-17
> **sirwhiteout said:**
> How do I see the plugins directory Firefox is using?

Type **about:plugins** in the address bar of Firefox.

---

### Post by zika on 2008-12-17
now, that I have installed 64-bit Java plugin and that it works great, and that I have uninstalled IcedTea plugin, do I have to do anything more to, sort of, introduce remaining Java componets to each other, like ```
sudo update-alternatives --config java
``` and which from: ```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+      1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java


``` should I choose?

versions are as follows:

```
**1**    /usr/lib/jvm/java-6-openjdk/jre/bin/java
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
**2**    /usr/lib/jvm/java-6-cacao/jre/bin/java
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu5) Runtime Environment (build 1.6.0_0-b12)
CACAO (build 0.99.3+hg, compiled mode)
**3**    /usr/lib/jvm/java-6-sun/jre/bin/java
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)
```should I choose **1** and uninstall the other 2 (above) or leave them ...?

I get:```
link currently points to /usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-cacao/jre/bin/java - priority 1059
 slave java.1.gz: /usr/lib/jvm/java-6-cacao/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.

```are these priority's reliable?

---

### Post by wd5gnr on 2008-12-17
Another set of install instructions here: [http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)

As for setting up your other Java... You can use the early release as your "system" Java, but I did not do that. All Debian releases including Ubuntu use the "alternatives" system to link things like /usr/bin/java to "the right place". So if you look up update-alternatives you can find a lot of info about how that works if you are interested.

---

### Post by kjb34 on 2008-12-17
I can't get the Java to work right.
This is what I get in terminal.
-family-computer:/opt$ cd /opt
-family-computer:/opt$ sudo sh ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sh: Can't open /home/kevin/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
-family-computer:/opt$ 

I downloaded the bin file to my desktop bit I can't seem to get it working right. Can anybody help me?

---

### Post by zika on 2008-12-17
try with this:
```
cd /opt
sudo sh ~/Desktop/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```

---

### Post by kjb34 on 2008-12-17
Thank you. that worked.

---

### Post by 73ckn797 on 2008-12-19
> **tomdkat said:**
> In this context, [FUD]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt") means "**F**ear, **U**ncertainty, and **D**oubt".

Peace...

Thanks for the clarification......):P

---

### Post by 73ckn797 on 2008-12-20
Java loaded just fine and the main obstacle to my using Ubuntu 64 bit has now been remedied.

Thank you...........:D

---

### Post by bobpaul on 2008-12-25
> **wd5gnr said:**
> [http://www.thinkfree.com](http://www.thinkfree.com) works! Finally!

As does the logmein.com client. I can finally get rid of that 32bit firefox once and for all.

---

### Post by keptang on 2008-12-25
Fantastic! Thanks a lot wd5gnr!! :)

---

### Post by dBuster on 2008-12-26
Okay, I have tried to get this installed even with removing the icedtea and to no avail.

I typed everything in verbatim with the changes since it is now a 22 dec version and a b03 instead of b02

I now have NO java...  

what else am I missing????

---

### Post by wd5gnr on 2008-12-26
> **dBuster said:**
> Okay, I have tried to get this installed even with removing the icedtea and to no avail.


What does about: plugins (no space in there... $**$ smileys) say in Firefox? There are several places you can put plugin links -- where did you put yours? I've found the .mozilla/plugins sometimes works and sometimes doesn't -- not sure why. But try every directory that you think might get scanned -- especially if you can find a plugin Firefox IS finding -- then put the link in the same place.

---

### Post by dBuster on 2008-12-26
This is what I have in my about:plugins...

libnpjp2.so

    File name: libnpjp2.so

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
application/x-java-applet;jpi-version=1.6.0_12 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_12 	Java 		Yes

---

### Post by wd5gnr on 2008-12-26
Well it looks like it is there! What makes you say Java isn't working? What happens if you go to a site that uses Java?

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

or

[http://www.javatester.org/version.html](http://www.javatester.org/version.html)

Is it possible you have adblock or something stopping Java? Or in Edit | Preferences | Content is "Enable Java" clicked? Did it work with IcedTea?

---

### Post by dBuster on 2008-12-26
Worked with icedtea, well for the most part it worked some pages were picky, but it worked at least...

When I try those pages it hangs firefox and I need to force quit. 

Something is hanging up but I do not know what.  When I go to a page like pogo.com to play games it tells me that I do not have java installed...

When I try and get a version in terminal screen I get the following:

david@david-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

When I have installed the b12 I thought...

*********************
I reinstalled iced tea as well as the repository java 6.0 and now I get no hangs in firefox and the results of the java tester are as follows:  Java Version: 1.6.0_0 From Sun Microsystems Inc.

Would like to get up to the latest version though since I am having issues getting pogo.com to work properly...

---

### Post by dBuster on 2008-12-27
Okay I found this posting and gave it a shot.  It said it installed properly and the files are there...  So I ran the tests still telling me I am running java 1.6.0_0..

Removed icedtea and now I am getting java 1.5.0_0

a step backwards...

Update:

I had removed the icedtea first and then gcjplugin and that causes the hangs.  When I install just the icedtea back in it hangs, when I add the gcjplugin it works but gives me the 1.6.0_0.....

hmmmm

---

### Post by zika on 2008-12-27
> **dBuster said:**
> Okay I found this posting and gave it a shot.  It said it installed properly and the files are there...  So I ran the tests still telling me I am running java 1.6.0_0..

Removed icedtea and now I am getting java 1.5.0_0

a step backwards...

Update:

I had removed the icedtea first and then gcjplugin and that causes the hangs.  When I install just the icedtea back in it hangs, when I add the gcjplugin it works but gives me the 1.6.0_0.....

hmmmm


give us the output of the following:```
sudo update-alternatives --config java
sudo update-alternatives --dispay java
sudo update-alternatives --list java
```on the first You can only type enter as answer to the question in order not to change anything. (see my earlier post).

maybe my 2 cents could make a difference... ;) it seems to me that only something is not linked well, or not in the right place. I've seen situations were Firefox or other browsers are simply configured so that plugins are expected on unusuall places. for example take a look at post #26 in this thread.

P.S. did You read [http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)
that is how I did my install. linking is essential.

---

### Post by zika on 2008-12-27
try:[http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin)
to get latest version: 24-Dec-2008 ... ;)

You can rerun the script we used for previous without changes (exept for the name of the file) since it does the ovewrite, after asking You ...

---

### Post by dBuster on 2008-12-27
> **zika said:**
> give us the output of the following:```
sudo update-alternatives --config java
sudo update-alternatives --dispay java
sudo update-alternatives --list java
```on the first You can only type enter as answer to the question in order not to change anything. (see my earlier post).

P.S. did You read [http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)
that is how I did my install. linking is essential.

Here is what was asked for.  And yes I did read that other post and followed those instructions as well but the same result.  I have a post there hunting for assistance...

************  Results
david@david-laptop:~$ sudo update-alternatives --config java
[sudo] password for david: 

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/gij-4.2

Press enter to keep the default[*], or type selection number: 

david@david-laptop:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/bin/gij-4.2 - priority 42
 slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.

david@david-laptop:~$ sudo update-alternatives --list java
/usr/lib/jvm/java-6-sun/jre/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/bin/gij-4.2
david@david-laptop:~$

---

### Post by zika on 2008-12-28
it all looks OK.

the only thing that makes me wonder is:

```

3    /usr/bin/gij-4.2
/usr/bin/gij-4.2 - priority 42
slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz

```make ```
 sudo update-alternatives --auto java 
```did You try step 3) in post #1 in [http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658) ?

> 
Create a symbolic link to Firefox plugin directory:

```

mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```

---

### Post by dBuster on 2008-12-28
make
Code:

 sudo update-alternatives --auto java

When I try that and then go back and do a java check to the web I now get just the gray boxes and not even java 1.6.0_0

Here is my output of those three checks again...

david@david-laptop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/gij-4.2

Press enter to keep the default[*], or type selection number: 

david@david-laptop:~$ sudo update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/bin/gij-4.2 - priority 42
 slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.

david@david-laptop:~$ sudo update-alternatives --list java
/usr/lib/jvm/java-6-sun/jre/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/bin/gij-4.2
david@david-laptop:~$ 

Now should I try to remove the icedtea?  Or the GCJ plugin?  If so what is the apt-get syntax to use....  Want to do it from the command line as I seemed to have better luck getting the flash alpha to work that way...

And yes I did do the step #3.

---

### Post by wd5gnr on 2008-12-28
As far as I know -- and I may be wrong -- Firefox does not use the Debian alternative system -- it purely uses the Java plugin which needs to be "in the right place" and that place seems to vary for reasons I don't quite understand (I know where mine looks for them).

Now it could be that the plugin has to find things -- do you have a CLASSPATH set on your system (set | grep CLASSPATH)? 

I'm not 100% sure how the plugin finds the correct JRE to use. But since firefox did "see" the plugin that's the only other thing I can think of.

---

### Post by zika on 2008-12-28
just to ask: did You enable Java in Firefox? Edit->Preferences->Content->{Enable Java Script with all sub options in Advanced, Enable Java}. sorry if I asked obvious.
wd5gnr is very much right in saying that Firefox do not use Debian alternative system ... but they must be set right in order that plugin could use them ... from what package does     /usr/bin/gij-4.2 come from ...?

---

### Post by wd5gnr on 2008-12-28
Just out of curiosity... have you tried any of the following:

1) Create a new firefox profile temporarily. Does Java work there?

2) Save your profile and reinstall firefox. How about now?

3) Create a new user login. Try running firefox and testing Java.

Seems like these might point to something peculiar to your setup that is giving a problem. If none of them work you can restore your profile and we can be pretty sure it is something in the system files and not in the per user or the firefox user configuration.

Just a thought.

---

### Post by jamesstansell on 2008-12-28
> **wd5gnr said:**
> As far as I know -- and I may be wrong -- Firefox does not use the Debian alternative system -- it purely uses the Java plugin which needs to be "in the right place" and that place seems to vary for reasons I don't quite understand (I know where mine looks for them).

Now it could be that the plugin has to find things -- do you have a CLASSPATH set on your system (set | grep CLASSPATH)? 

I'm not 100% sure how the plugin finds the correct JRE to use. But since firefox did "see" the plugin that's the only other thing I can think of.

When you installed a packaged java plugin, it puts symbolic links in the mozilla and xulrunner directories which point to the /etc/alternative link which in turn point to the lib*.so file.

The reason for the symbolic link to the lib*.so file is so that it can find its own location and thus be able to start the proper JRE for the plugin that is being used.

So for beta software like this, using a JRE and plugin that haven't been packaged yet. the main part of the exercise is to put in the missing symbolic link.

Since dBuster has done that I'm at a loss at to what the problem on his system could be.  It would be helpful if someone could replicate the problem on another system.

---

### Post by junnuh on 2008-12-28
Hi!

I have also installed 64bit Sun Java and it works great or almost,
only website where it don't work is runescape.

When I click "play" the game is loading properly but when I should have the log in-page and the log in window there, its covered with white. Only the advert in the middle top of the window can be seen! And I get this error report ( here is only the start of it):

> An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f4dc6a6c2a2, pid=9053, tid=1110059344
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.2-b01 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5802a2]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.

So I am still keeping also the 32-bit browser to be able to play runescape, it seems to be the only reason if someone can't help me with this problem. 

But in Firefox 64-bit I will use 64bit Java and Flash! Thats great!:P

Oh yes, I am using 64bit Intrepid! Works fine!:lolflag:

Thanks for everyone who are brave enough to use 64bit! And for good advices!

with light junnuh

edit! I also sent a crash report to Sun Java!!

---

### Post by dBuster on 2008-12-30
Since it seems that the java is progreesing anyone have a clue as to how far away a true 64bit release may be?  Not a build like this but one that will install?

I plan on removing all java and trying it again.  As far as creating a new profile...  Would that require a new login in order to have firefox create the new profile?

Just an fyi, my wife uses windblows and the latest ff 3.0.5 has an issue with loading one of the games pages she visits with java and it completely shuts down ff when she tries to navigate to it.  Possible FF issue?  I am not sure...

---

### Post by wd5gnr on 2008-12-30
> **dBuster said:**
>   As far as creating a new profile...  Would that require a new login in order to have firefox create the new profile?


Nope: [http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by bobpaul on 2008-12-30
> **dBuster said:**
> Since it seems that the java is progreesing anyone have a clue as to how far away a true 64bit release may be?  Not a build like this but one that will install?

I would be surprised if there wasn't a *.deb built and in the repositories in time for Jaunty, even if it's still just a beta plugin from Sun. Actually, I'm rather surprised nobody has already built an unofficial *.deb and posted it to a website somewhere. Oh well.

---

### Post by dBuster on 2008-12-30
Well I have completely removed anything in the synaptic package manager relating to icedtea and the gcj java including the webplugin that was when left in returning java 1.0.5.0 in the test pages.

This is what I have now...

david@david-laptop:~$ sudo update-alternatives --list java
/usr/lib/jvm/java-6-sun/jre/bin/java

david@david-laptop:~$ sudo update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/jvm/java-6-sun/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-sun/jre/bin/java.
david@david-laptop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
david@david-laptop:~$ 

So now when I go to the Java tester web page I get no display of java version and when I try the sun website I lock up tight.  I have gone back through and did the install all over again to make sure something I may have missed but it apparently is not working...  The libnpjp2.so -- File name: libnpjp2.so is the only plugin firefox is seeing at the moment related to java.

---

### Post by jamesstansell on 2008-12-31
> **dBuster said:**
> Since it seems that the java is progreesing anyone have a clue as to how far away a true 64bit release may be?  Not a build like this but one that will install?

I plan on removing all java and trying it again.  As far as creating a new profile...  Would that require a new login in order to have firefox create the new profile?

Just an fyi, my wife uses windblows and the latest ff 3.0.5 has an issue with loading one of the games pages she visits with java and it completely shuts down ff when she tries to navigate to it.  Possible FF issue?  I am not sure...

Sun has made noises about releasing 6u12 in February so, assuming that happens, I would highly expect a deb package in March if not sooner.  Obviously I can't predict how well it will work. :)

Since it sounds like a java game page, there's a chance that it's a problem with the java plugin.  Assuming that she's on 32-bit, using the latest release, 6u11, there are two plugins available.  The "classic" oji plugin and the new default npjp2 plugin.  In the control panel you can switch back to oji to see if the game runs better.  Which game is it?

---

### Post by dBuster on 2008-12-31
> **jamesstansell said:**
> Since it sounds like a java game page, there's a chance that it's a problem with the java plugin.  Assuming that she's on 32-bit, using the latest release, 6u11, there are two plugins available.  The "classic" oji plugin and the new default npjp2 plugin.  In the control panel you can switch back to oji to see if the game runs better.  Which game is it?

Actually when I go through the steps and remove the icedtea and openjava and then remove the one gcjplugin and then have only the new 64bit plugin present I can't even get the java test pages to load.  Nothing related to any games.  When I install back in just the icedtea in the synaptic package manager, which I believe installs openjdk as well, everything works again.  I get the test pages to tell me I am running java 1.6.0_0 but not the _12 that I had installed.

Now the interesting thing, I opened up some work in openoffice and for giggles I checked to see what version of java it was using and it is using 1.6.0_7 but it also lists 1.6.0_12-ea...

---

### Post by bobpaul on 2008-12-31
> **dBuster said:**
> Actually when I go through the steps and remove the icedtea and openjava and then remove the one gcjplugin and then have only the new 64bit plugin present I can't even get the java test pages to load.  Nothing related to any games.

He was talking about your wife's Windows machine there, not your trouble with 64bit Java on Ubuntu.

---

### Post by dBuster on 2009-01-03
Okay after all my troubles it looks like I have the latest version installed however I still get a report that I am running 1.6.0_0 and not the latest number...  

however when I run :

```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```

I get the following results:
```
david@david-laptop:~/Desktop$ ls -al /usr/lib/mozilla/plugins/
total 10812
drwxr-xr-x 2 root  root     4096 2009-01-03 06:24 .
drwxr-xr-x 4 root  root     4096 2008-04-22 13:11 ..
-rwxr-xr-x 1 david david 9526312 2008-12-10 11:13 libflashplayer.so
lrwxrwxrwx 1 root  root       46 2009-01-03 06:24 libnpjp2.so -> /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so
-rw-r--r-- 1 root  root   290880 2008-07-25 05:42 mplayerplug-in-dvx.so
-rw-r--r-- 1 root  root     1067 2008-07-25 05:42 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root  root   290880 2008-07-25 05:42 mplayerplug-in-qt.so
-rw-r--r-- 1 root  root     1067 2008-07-25 05:42 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root  root   290880 2008-07-25 05:42 mplayerplug-in-rm.so
-rw-r--r-- 1 root  root     1067 2008-07-25 05:42 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root  root   291320 2008-07-25 05:42 mplayerplug-in.so
-rw-r--r-- 1 root  root   290880 2008-07-25 05:42 mplayerplug-in-wmp.so
-rw-r--r-- 1 root  root     1067 2008-07-25 05:42 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root  root     1067 2008-07-25 05:42 mplayerplug-in.xpt
lrwxrwxrwx 1 root  root       60 2008-11-25 05:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

david@david-laptop:~/Desktop$ ls -al /usr/lib/firefox-addons/plugins
total 9816
drwxr-xr-x 2 root  root      4096 2009-01-03 06:24 .
drwxr-xr-x 5 root  root      4096 2008-04-22 13:09 ..
-rwxr-xr-x 1 david david 10022452 2008-11-18 17:53 libflashplayer.so
lrwxrwxrwx 1 root  root        46 2009-01-03 06:24 libnpjp2.so -> /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so
lrwxrwxrwx 1 root  root        60 2008-11-25 05:31 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Which is telling me that I am using the correct plugin and no others...  Am I correct in saying that?  

Also from further research pogo will not work with the 64 bit version for now.  Maybe with the final release of the plugin it might work.  Anyone know of any good java game websites?  So I can test...  I loaded runescape successfully is that a good test?

---

### Post by bobpaul on 2009-01-04
> **dBuster said:**
> Okay after all my troubles it looks like I have the latest version installed however I still get a report that I am running 1.6.0_0 and not the latest number...  

What's 'java -version' show?

> **dBuster said:**
> Which is telling me that I am using the correct plugin and no others...  Am I correct in saying that?  

Yes, it appears that way. Long shot, but maybe get rid of the flash stuff for now, just to see if nspluginwrapper is causing problems. I don't expect it to help, but it sounds like you've tried everything else. I'm running 64bit java and 64bit flash and the java with no nspluginwrapper stuff.

---

### Post by Kilz on 2009-01-04
> **bobpaul said:**
> What's 'java -version' show?



Yes, it appears that way. Long shot, but maybe get rid of the flash stuff for now, just to see if nspluginwrapper is causing problems. I don't expect it to help, but it sounds like you've tried everything else. I'm running 64bit java and 64bit flash and the java with no nspluginwrapper stuff.

Nspluginwrapper does not work with Java, at least to my knowledge. So wont make any difference. If the person having the issues cant get it to run, they should fill out a bug report with Sun.

---

### Post by dBuster on 2009-01-04
> **bobpaul said:**
> What's 'java -version' show?



Yes, it appears that way. Long shot, but maybe get rid of the flash stuff for now, just to see if nspluginwrapper is causing problems. I don't expect it to help, but it sounds like you've tried everything else. I'm running 64bit java and 64bit flash and the java with no nspluginwrapper stuff.

Alrighty...  here is the results of the java -version..

```
david@david-laptop:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b23, mixed mode)
```

Kilz, you think I should submit a bug report with Sun?

---

### Post by Kilz on 2009-01-04
> **dBuster said:**
> 

Kilz, you think I should submit a bug report with Sun?

IMHO when a good member of the open source community (that includes people who just use open source software) has a bug they report it. 

But since you are having problems with [other 64bit plugins]("http://ubuntuforums.org/showpost.php?p=6493681&postcount=568") not working correctly there may be other problems. My advice is to focus on one problem and you might get them both.

---

### Post by jamesstansell on 2009-01-04
> **dBuster said:**
> Okay after all my troubles it looks like I have the latest version installed however I still get a report that I am running 1.6.0_0 and not the latest number...  



That sounds like the icedtea6-plugin rather than one of Sun's plugins.

Do you have the java console enabled, and does it ever display?  You should be able to enable it with the jcontrol program in the 6u12 jre directory, assuming that this 64bit build is like the 32bit ones (I haven't installed 64-bit ubuntu yet; hopefully soon.  But I am fairly familiar with the available java plugins in 32-bit mode.)

What if you close firefox and run this from a terminal?

```
$ firefox http://browserspy.dk/java.php
```

Does the java console open, and if so what does it display?  If not, what is the output in the terminal?

---

### Post by jamesstansell on 2009-01-04
> **Kilz said:**
> IMHO when a good member of the open source community (that includes people who just use open source software) has a bug they report it. 


Even though Sun's java plugin isn't open source I still agree with Kilz that you should file a report.  After all, that's one of the main reasons that Sun made these pre-release versions available.

From the [https://jdk6.dev.java.net/](https://jdk6.dev.java.net/) page:

> Feedback

Please use the [Project Feedback]("https://jdk6.dev.java.net/6uNea.html#Feedback") forum if you have suggestions for or encounter issues with using the JDK 6 snapshots.

If you find bugs in a snapshot release, please submit them using the usual [J2SE bug reporting channels]("http://bugs.sun.com/services/bugreport/index.jsp"), not with the Issue tracker accompanying this project. Be sure to include complete version information from the output of the java -version command.

In this case you're not exactly sure there is a bug.  I would suggest posting to the [Java plugin feedback forum]("http://forums.java.net/jive/forum.jspa?forumID=77") to begin with.

---

### Post by jamesstansell on 2009-01-04
> **dBuster said:**
> Alrighty...  here is the results of the java -version..


The output is interesting, and would be useful for a number of other issues, but not for troubleshooting issues with the java plugin.

The java command in a user's PATH and the JRE used by the java plugin have almost nothing to do with each other.  In some (admittedly rare and weird) situations you could not have a java command in the PATH but still have a perfectly working java plugin in firefox.

How about the output of <path-to-java6u12>/bin/java -version?  That's a more useful indication that the JRE of interest is working properly.

---

### Post by Duranxl on 2009-01-05
> "You are using a newer version of JRE than the current version on Java.com" 

lol!

Anyway, the test page on java.com first crashed firefox just after installed the 64bit version 12..but now it magically works:confused:

Also, live timing on formula1.com freezes firefox...

---

### Post by campbuds on 2009-01-10
when I try to run the install as on the first page I get this...

sh: Can't open /home/jeremiah/Desktop/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

what am I doing wrong? the file is on my desktop.

---

### Post by Duranxl on 2009-01-10
> **campbuds said:**
> when I try to run the install as on the first page I get this...

sh: Can't open /home/jeremiah/Desktop/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

what am I doing wrong? the file is on my desktop.

did you chmod +x it?

---

### Post by campbuds on 2009-01-10
I do not know what that is? Sorry, most code is still greek to me. (I don't know any greek)

---

### Post by campbuds on 2009-01-10
I really could use a hand with this

---

### Post by campbuds on 2009-01-10
figured it out, it is just that the file name changed... DUH!

---

### Post by campbuds on 2009-01-10
I used to install Atunes using the multi platform installer download. Then I could just right click the file and install with Java. Java is not on that menu. How would I install atunes?

(i know my options, i just happen to like atunes)

---

### Post by jamesstansell on 2009-01-10
> **campbuds said:**
> I used to install Atunes using the multi platform installer download. Then I could just right click the file and install with Java. Java is not on that menu. How would I install atunes?

(i know my options, i just happen to like atunes)

The effect of the right-click should be to run a command like java -jar <filename>.  So if the installed is called /home/campbuds/Desktop/atunes.jar you might try this

```
java -jar /home/campbuds/Desktop/atunes.jar
```

---

### Post by swordfishRU on 2009-01-26
YAP!

It's WORK!

Thank you very much!

---

### Post by Osamabingandhi on 2009-02-07
When i type "java -version" I only get the message that java exists in other packages. Also when i type "sudo update-alternatives --config java" i don't have any alternatives. 

When i goto the page([http://www.javatester.org/version.html](http://www.javatester.org/version.html)) to see if i got it installed alright everything is fine. Java 1.6.0_12

(i'm trying to get softsqueeze to work)

I got java -version right....i didn't think you had to download it to that /opt/ folder and intall it from there.....

---

### Post by Shtirlits on 2009-02-09
After removing Iced Tea, the plugin is working for me.

---

### Post by pjaikins on 2009-02-21
Hi,
  I tried running this bin and get the following:

peter@chiba:~$ sudo sh ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sh: Can't open /home/peter/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
peter@chiba:~$ 

Any ideas?

---

### Post by zika on 2009-02-22
```
sudo chmod +x ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```

---

