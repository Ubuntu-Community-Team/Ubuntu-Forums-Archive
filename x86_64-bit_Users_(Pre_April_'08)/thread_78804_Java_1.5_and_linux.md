---
title: "Java 1.5 and linux"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by TuckWat on 2005-10-18
Sorry if this is common knowledge, I'm new to linux - after trying for multiple hours to get java 1.5 to work on Ubuntu I found a thread saying that you can't instlal 1.5 on linux yet.  

If this is true, any idea when a powerpc 1.5 will be released?  Thanks a lot

---

### Post by JELaVallee on 2005-10-19
[QUOTE=TuckWat]Sorry if this is common knowledge, I'm new to linux - after trying for multiple hours to get java 1.5 to work on Ubuntu I found a thread saying that you can't instlal 1.5 on linux yet.  

If this is true, any idea when a powerpc 1.5 will be released?  Thanks a lot[/QUOTE]

Not sure w/r/t the PPC implementation of java 1.5...  I'm using a 686 Hoary installation.  BUT, I was able to get the full Sun JDK 1.5_04 installation added to my system fairly effortlessly using the command:

> **$ sudo apt-get install sun-j2sdk1.5** 

With the backports, universe, and multiverse repositories setup in my /etc/apt/sources.list

Been able to run Eclipse and build JBoss-based web apps against that install ever since, so it's definitely functional.

But like I said, not PPC.  Last I read (~2005/9/15) there's no official PPC 1.5 port from Apple, IBM, Motorola or Blackdown.  IBM's rumored to have such in the works for RPM-based systems (RedHat, SLES/SuSE) but I'm not positive on the progress or expected delivery of such.

Good luck!  If I can find any additional info, I'll post it here for you.

Cheers,
Etienne

---

### Post by paddyg on 2005-10-19
That's right.

Java works fine in Linux. I'm using JDK 1.5_05 with both Hoary and Breezy (as I did with Fedora).

If apt-get doesn't work, try doing it "manually" as root (download, unpack, and make symlinks)

---

### Post by anders_gud on 2005-10-19
TuckWat
I run IBM java SDK 1.5-beta on a Breezy tibook.
Try this wiki:
[https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)
link to IBM java downloads
[https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)

---

### Post by tiagobt on 2005-10-19
[QUOTE=anders_gud]TuckWat
I run IBM java SDK 1.5-beta on a Breezy tibook.
Try this wiki:
[https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)
link to IBM java downloads
[https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)[/QUOTE]
I followed all the steps, but couldn't get it working. I am running Kubuntu 5.10 Breezy Badger in a Mac Mini. I downloaded the package ibm-java2-sdk-50-linux-ppc.tgz from IBM's website and the package java-package_0.26_all.deb from Ubuntu Breezy Multiverse repository (I had to disable this repository in my sources.list because I kept getting an error message). I had to fix some dependencies in order to install java-package properly, but I guess it worked all right. The problem is that, when I type the command "make-jpkg ibm-java2-sdk-50-linux-ppc.tgz", I get the following message:

```
Creating temporary directory: /tmp/make-jpkg.XXXXoGnpde
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```

And no *.deb package is created.

What did I miss?

---

### Post by gpogo on 2005-10-20
You did not follow the steps.  download the .rpm and use fakeroot alien xxx.rpm(i think that is the command.) anyways it is on that wiki page

though I have recently had an issue with my java

$ /opt/ibm/java2-ppc-50/bin/java
Error loading: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by brsma on 2005-10-20
You might also want to see [http://www.debian.org/doc/manuals/debian-java-faq/ch11.html]("http://www.debian.org/doc/manuals/debian-java-faq/ch11.html") for instructions concerning installing non-free java packages. I succesfully followed those when recently setting up the latest sdk 1.4.* package from IBM (converted from .rpm).

---

### Post by felix_stegerman on 2005-10-21
Hi,

When I needed Java 1.5 on my Mac Mini (which runs Debian),
I downloaded the IBM beta and modified the java-package config.
to support it. Then I could use java-package to build a .deb.

NOTE: this config is based on Debian's java-package v0.26.

I've attached _flx.tar.bz2 which contains the _flx directory.
You could go to /usr/share/java-package/, copy _flx there
and do:
 # mv ibm-j2re.sh ibm-j2re.sh.orig
 # mv ibm-j2sdk.sh ibm-j2sdk.sh.orig
 # ln -s _flx/ibm-j2re.sh
 # ln -s _flx/ibm-j2re1.5
 # ln -s _flx/ibm-j2sdk.sh
 # ln -s _flx/ibm-j2sdk1.5
to "update" the configuration.

Now you can use:
 # fakeroot make-jpkg ibm-java2-jre-50-linux-ppc.tgz
 # fakeroot make-jpkg ibm-java2-sdk-50-linux-ppc.tgz
to build .debs


Felix

P.S.
 I do use Ubuntu on my Laptop ( which is currently broken :( )
 and on my mom's PC ;-)

---

### Post by tiagobt on 2005-10-21
gpogo,

I did follow the instructions. The problem is that they told me to download the TGZ file instead of the RPM file. I downloaded the RPM, converted it with alien, and installed it with dpkg successfully. However, when I tested it using the command "appletviewer", I got a message saying that the command was not found, what makes me think it didn't work. Thanks for the help though.

felix_stegerman,

I did everything you told me to except the command "fakeroot make-jpkg ibm-java2-jre-50-linux-ppc.tgz" since I don't have this package yet. Do I need it? The instructions at Ubuntu Wiki dont't mention this file. Anyway, I skipped to the next step: "fakeroot make-jpkg ibm-java2-sdk-50-linux-ppc.tgz". The message I got was the following:

```
Creating temporary directory: /tmp/make-jpkg.XXXXgMqXZ5
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh/usr/bin/make-jpkg: line 204: /usr/share/java-package/ibm-j2re.sh: File or folder not found

Aborted ( ibm-j2re.sh).

Removing temporary directory: done
```

Is there a way of fixing it?

Thanks again

---

### Post by tiagobt on 2005-10-21
Never mind, it worked! I was just unpacking the file in the wrong place... Thanks a lot! I got TicTacToe applet working fine.

I'm now trying to make the applet viewer work as a plugin in Konqueror/Firefox. In Konqueror, I entered "appletviewer" as the command for Java (Konqueror Configuration). When I load a webpage with a Java applet, it seems that it's going to work, but it keeps showing that "loading" message. Could it be a permission problem? Also, is there a way to do something similar in Firefox?

---

### Post by Riverside on 2005-10-22
[QUOTE=tiagobt]Also, is there a way to do something similar in Firefox?[/QUOTE]Prompted by this thread, I have just installed Java 1.5 on my Breezy machine.

I did it the manual way, first downloading jre-1_5_0_02-linux-i586.bin from [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) and then following the instructions at:

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

I found these easy to follow, both the "To install the Linux (self-extracting) file" section and the subsequent "Enable and Configure | Mozilla 1.4 and later" sections.  The result was a working Java installation and Firefox 1.0.7 plugin first time.

What you need to do to enable the plugin in Firefox is to create a symbolic link to the relevant Java component file in your Firefox plugins directory.  On my system the command to do this was:

anthony@trafford:/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/java/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

This may vary on your system depending on where your Java installation resides, and whether or not your Firefox installation is Ubuntu standard, or otherwise.  You'll also need to first close, and then re-open, Firefox once done in order to use it.

---

### Post by tiagobt on 2005-10-22
Riverside,

Are you sure that the regular Java works on a PowerPC platform? I thought it was only good fot x86 platforms.

---

### Post by strongmantim on 2005-10-25
[QUOTE=Riverside]Prompted by this thread, I have just installed Java 1.5 on my Breezy machine.

...

What you need to do to enable the plugin in Firefox is to create a symbolic link to the relevant Java component file in your Firefox plugins directory.  On my system the command to do this was:

anthony@trafford:/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/java/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
[/QUOTE]

PERFECT PERFECT PERFECT! Just what I needed. There's always something great to find in the ubuntuforums. :D

---

### Post by pvz on 2005-10-26
Thanks Felix, that finally did it :-)

I even have a java plugin in Mozilla-firefox working now.

about: plugins says
IBM Java(TM) Plug-in: J2RE 1.5.0 IBM build jclxp32dev-20050915
File name: libjavaplugin_oji.so
Java(TM) Plug-in 1.5.0

and I can succesfully run the java tester at
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Yes folks, we have a working java plugin for mozilla-based browsers for the PPC-platform, finally.

---

### Post by tiagobt on 2005-10-26
For some reason Felix's tutorial now works for me in Firefox! :p
Riverside's tutorial did not work though. I guess it only works on i586 processors.
The only thing missing is Java support for Konqueror. Did anyone get it working? What is the executable Java path?

---

### Post by felix_stegerman on 2005-10-28
Hi,

Glad to be of help.

IIRC (I use GNOME, not KDE), you should tell konqueror to use /usr/bin/java as java executable.

Whenever I use the IBM Java 1.5 beta firefox plugin (w/ Debian that is),
and then close firefox, the java executable uses 100% CPU and I have to kill it.

Has anybody else experienced this?


Felix

---

### Post by Janfi on 2005-10-28
Hi guys,

I would like to thanks Felix for his help in installing and have a functionnal IBM Java 1.5 virtual machine.
GCJ is the best choice, because it's free and I prefer free software, but needs some time to become a full replacement product. Some apps don't work with it.

So thank you again Felix.

---

### Post by felix_stegerman on 2005-10-28
[QUOTE=Janfi]GCJ is the best choice, because it's free and I prefer free software, but needs some time to become a full replacement product. Some apps don't work with it.[/QUOTE]

I agree. I have to use Java for my "Object Orientation" class at University,
and initially I hoped to use free software Java implementations like jikes,
sablevm, jamvm, gcj and gij, but they're just not usable enough for GUIs.
And I like the improvements (e.g. generics) made in Java 1.5.


Felix

---

### Post by tiagobt on 2005-10-28
[QUOTE=felix_stegerman]Hi,

Glad to be of help.

IIRC (I use GNOME, not KDE), you should tell konqueror to use /usr/bin/java as java executable.

Whenever I use the IBM Java 1.5 beta firefox plugin (w/ Debian that is),
and then close firefox, the java executable uses 100% CPU and I have to kill it.

Has anybody else experienced this?


Felix[/QUOTE]
When I try to open Java applets in Konqueror (using /usr/bin/java as the executable), the only thing I get is the message "Loading Applet". Did anyone get it working?

The Firefox plugin works just fine. No problem with CPU usage. I am using Kubuntu 5.10 in a Mac Mini.

---

### Post by felix_stegerman on 2005-10-28
[QUOTE=tiagobt]When I try to open Java applets in Konqueror (using /usr/bin/java as the executable), the only thing I get is the message "Loading Applet". Did anyone get it working?

The Firefox plugin works just fine. No problem with CPU usage. I am using Kubuntu 5.10 in a Mac Mini.[/QUOTE]

I just installed konqueror. I went to "Settings" -> "Java & Javascript" ->
"Path to Java executable ..." and entered /usr/bin/java.
Then I went to [http://stegerman.free.fr/po/java/MM.htm](http://stegerman.free.fr/po/java/MM.htm)
(my Java mastermind applet) and it just worked.

Of course, I'm using Debian unstable (on a Mac Mini).
But at least it's possible to use the IBM Java 1.5 beta w/ konqueror.


Felix

---

### Post by pvz on 2005-10-29
[QUOTE=felix_stegerman]Hi,

Whenever I use the IBM Java 1.5 beta firefox plugin (w/ Debian that is),
and then close firefox, the java executable uses 100% CPU and I have to kill it.

Has anybody else experienced this?


Felix[/QUOTE]

Yes, same here on my iBook running kubuntu.
Also, when I try to do my online banking that needs java, it still won't work unfortunately.
 
It is beta software, so let's hope IBM comes with another version soon.

---

### Post by robotgeek on 2005-11-16
Hi, 

Thanks for the instructions to enable the Java plugin for Firefox (on PPC). Relevant information has been added to the wiki page at [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)

Thanks,
Venkat Raghavan

---

### Post by peter_m on 2005-11-24
[QUOTE=gpogo]You did not follow the steps.  download the .rpm and use fakeroot alien xxx.rpm(i think that is the command.) anyways it is on that wiki page[/QUOTE]

The Wiki page clearly says to use TGZ. Should the WiKi be updated?
[https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29)

Also, if I only need to use the JRE, what should I do differently then in the WiKi?

---

### Post by robotgeek on 2005-11-24
[QUOTE=peter_m]The Wiki page clearly says to use TGZ. Should the WiKi be updated?
[https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29)
[/QUOTE]
That's for version 1.5. Version 1.4 uses binaries

---

### Post by Brian McConnell on 2005-11-26
not sure if this will help anyone, but all I did in order to install JRE 1.5 on my G5 was to simply download it and replace the relevant info from the ubuntuguide. ([http://userlinux.net/pub/stuff/ubuntu/](http://userlinux.net/pub/stuff/ubuntu/)   <-- it's the old hoary guide, but works in this case.)

Here's an updated one for easy cut and paste:

Go to: [https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)
Go to the "IBM SDK for 32-bit iSeries/pSeries"
Download ibm-java2-jre-50-linux-ppc.tgz . Registration Required.

Open up a terminal.

```
tar zxvf ibm-java2-jre-50-linux-ppc.tgz
sudo mkdir /usr/java
sudo mv ibm-java2-ppc-50/ /usr/java/
sudo chown -R root:root /usr/java/ibm-java2-ppc-50/
sudo ln -fs /usr/java/ibm-java2-ppc-50/jre/bin/java /usr/bin/java
sudo ln -fs /usr/java/ibm-java2-ppc-50/jre/bin/javaw /usr/bin/javaw
java -version
```

---

### Post by robotgeek on 2005-11-26
If you have followed the wiki guide ( [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC) ) , and have received the following error while installing java 1.5

> 
JVM not found: libjvm.so  - libjvm.so


All you need to do is to add the complete path to java. 
> 
echo "alias java='/opt/ibm-java2-ppc-50/bin/java'" >> ~/.bashrc


That should solve the problem. The wiki article has also been updated, and any feedback is welcome.

---

### Post by Entity on 2005-11-26
Was someone able to make the GCJ web browser plug-in (gcjwebplugin) work in firefox or any other browser?

---

### Post by robotgeek on 2005-11-27
[QUOTE=Entity]Was someone able to make the GCJ web browser plug-in (gcjwebplugin) work in firefox or any other browser?[/QUOTE]

If you follow the directions on the wiki, [http://wiki.ubuntu.com/JavaPPC](http://wiki.ubuntu.com/JavaPPC) , and the instructions for 1.5, it should work.

---

### Post by Entity on 2005-11-27
[QUOTE=robotgeek]If you follow the directions on the wiki, [http://wiki.ubuntu.com/JavaPPC](http://wiki.ubuntu.com/JavaPPC) , and the instructions for 1.5, it should work.[/QUOTE]
Well, it keeps crashing on me... but anyway since it's a beta version I guess it's simply a question of time ;)

Thanks

---

### Post by tenev on 2006-01-02
[QUOTE=Brian McConnell]not sure if this will help anyone, but all I did in order to install JRE 1.5 on my G5 was to simply download it and replace the relevant info from the ubuntuguide. ([http://userlinux.net/pub/stuff/ubuntu/](http://userlinux.net/pub/stuff/ubuntu/)   <-- it's the old hoary guide, but works in this case.)

Here's an updated one for easy cut and paste:

Go to: [https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)
Go to the "IBM SDK for 32-bit iSeries/pSeries"
Download ibm-java2-jre-50-linux-ppc.tgz . Registration Required.

Open up a terminal.

```
tar zxvf ibm-java2-jre-50-linux-ppc.tgz
sudo mkdir /usr/java
sudo mv ibm-java2-ppc-50/ /usr/java/
sudo chown -R root:root /usr/java/ibm-java2-ppc-50/
sudo ln -fs /usr/java/ibm-java2-ppc-50/jre/bin/java /usr/bin/java
sudo ln -fs /usr/java/ibm-java2-ppc-50/jre/bin/javaw /usr/bin/javaw
java -version
```[/QUOTE]

thanks. with those simple steps i managed to install java 1.5 on my pismo (ubuntu 5.04). however, my firefox is failing to load the plugin even after i applied the instructions given in:
[https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29)

Please help me out. I cannot get on the internet without authenticating via firefox first, and that requires the plugin.

---

### Post by robotgeek on 2006-01-03
[QUOTE=tenev]thanks. with those simple steps i managed to install java 1.5 on my pismo (ubuntu 5.04). however, my firefox is failing to load the plugin even after i applied the instructions given in:
[https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29](https://wiki.ubuntu.com/JavaPPC?highlight=%28javappc%29)

Please help me out. I cannot get on the internet without authenticating via firefox first, and that requires the plugin.[/QUOTE]

Hmm, the firefox plugin is very beta, i would guess. You might want to use Konqueror for the java part. :(

---

### Post by tenev on 2006-01-03
[QUOTE=robotgeek]Hmm, the firefox plugin is very beta, i would guess. You might want to use Konqueror for the java part. :([/QUOTE]

Thanks. where do I download konqueror? I tried [http://www.kde.org](http://www.kde.org) but can't seem to find a package for PPC. (it would have to work in ubuntu)... i am a complete newbie so i'd appreciate some help. thanks in advance.

---

### Post by akiro.yamamoto on 2006-01-03
Use synaptic if you want to get Konqueror..
However if you are using GNOME... it will be quite a download, due to the additional packages.

---

### Post by tenev on 2006-01-09
[QUOTE=akiro.yamamoto]Use synaptic if you want to get Konqueror..
However if you are using GNOME... it will be quite a download, due to the additional packages.[/QUOTE]

where do I get synaptic? Does it fit into one CD? The thing is that I cannot get on the internet with the powerbook so I would have to download it to a windows machine first... yes, i am using gnome.

thanks.
tenev

---

### Post by naturalhl2 on 2006-01-09
sudo apt-get install sun-j2sdk1.5 when I put that into my terminal it asks for my password inwhich I cant type??

---

### Post by neels on 2006-01-11
To install the plugin in firefox, try this one: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

### Post by mr.lamp on 2006-01-25
JAVA install just does not work for me.

i followed [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC) but the command "java" is just not available

```
java
bash: java: command not found

```

but "javac" is available although i do not know what this could be.

```
javac
JVM not found: libjvm.so  - libjvm.so

```

so i tried what the wiki recommends for this error:
```
echo 'PATH=/opt/ibm-java2-ppc-50/bin/:"${PATH}"' >> ~/.bash_profile

```

but this does not help it  :confused:

---

### Post by robotgeek on 2006-01-25
PLF has the software package for IBM Java. You can either add those repositories, and install java from there. (the package name is ibmj2re1.5, i think) 

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf) 

Or you can download EasyBreezy from [http://easybreezy.robotgeek.org](http://easybreezy.robotgeek.org), and it will install it for you.

---

