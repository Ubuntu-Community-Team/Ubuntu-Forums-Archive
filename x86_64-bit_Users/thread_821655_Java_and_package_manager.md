---
title: "Java and package manager"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by krash182 on 2008-06-07
I try to run package manager and I ger an error screen telling me I need to run dpkg --configure -a.  When I do I get this
weez@weez-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

When I link to the Sun page there is no file " jdk-6-doc.zip jdk-6-doc-ja.zip" and I cant seem to get the other installations to install on my system.  I need to use package manager to get my JAVA updated but my Java wont let me open Package Manager.  I feel like i'm in a catch 22 situation.  HELP

---

### Post by digerati on 2008-06-07
I had the first message when I tried to install sun-java6.  When trying to install it whenever the screen popped up asking me to accept the license agreement it would hang.  I ended up killing the synaptic which left my packages in a broken state.

I ran sudo dpkg --configure -a
then  sudo apt-get install -f
then installed sun-java6-bin
sudo apt-get install sun-java6-jdk

This will install the jre, docs, demo, etc.
ubuntu-laptop:/sudo apt-cache search sun-java6
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files

---

### Post by krash182 on 2008-06-07
no go  Java killing me at every step


weez@weez-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
weez@weez-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
weez@weez-desktop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

---

### Post by krash182 on 2008-06-07
its working again now.  I can unistall Java 6 and return to the native application,  thanks for your help.

---

### Post by rstritmatter on 2008-06-07
I ran sudo dpkg --configure -a
then sudo apt-get install -f
then installed sun-java6-bin
sudo apt-get install sun-java6-jdk

Thanks for the clear instructions, but this did not work for me. 

on the install sun - java6 bin command I got this:
[[IMG]http://www.imagebay.us/images/cl72h509w0x8i3wdoz0o_thumb.png[/IMG]](http://www.imagebay.us/viewer.php?file=cl72h509w0x8i3wdoz0o.png)

[Attached as screenshot $1 since I'm not sure that link is working.]

At which I had no real choice other than to shut the terminal.


I also go this error message:

[IMG]http:// [[IMG]http://www.imagebay.us/images/sk0ttyj41apph4zn1j1y_thumb.png[/IMG]](http://www.imagebay.us/viewer.php?file=sk0ttyj41apph4zn1j1y.png)[/IMG]

[Attached as screenshot #2].



Further assistance would be greatly appreciated.  There seem to be many many people getting caught in a catch-22 bug trying to install java6.

Thanks for your help!

---

### Post by rstritmatter on 2008-06-08
Can anyone help with this?  If I've not been specific enough, or need to provide further detail, please let me know. I'm just trying to learn and do not have a background in linux or use of the Terminal. Your help will be much appreciated. 

Thanks!

---

### Post by Kilz on 2008-06-08
> **rstritmatter said:**
> Can anyone help with this?  If I've not been specific enough, or need to provide further detail, please let me know. I'm just trying to learn and do not have a background in linux or use of the Terminal. Your help will be much appreciated. 

Thanks!
The screenshots show a eula that you have to agree to, use the arrow keys to highlight the ok after reading it and hit enter. The other is a warning saying you have the terminal open trying to install something and another application that installs open at the same time. In linux you can only have one thing installing at one time , it locks everything else out.  Here are some links that may be useful, [look here for information]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic") on how to install any application. [The wiki can also be helpful.]("https://help.ubuntu.com/community/")(you might want to bookmark it) for such topics as [how to use the terminal]("https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal"). All in all there is a wealth of information online, google and wiki's are your friend. :D

---

### Post by rstritmatter on 2008-06-08
Thank you, Kilz. For some reason I was having trouble negotiating that user agreement, but I went back at it and everything seems to have installed properly.  Also I took your advice to bookmark the instructions on Terminal Use.  

Keep up the great work helping us newbies out!

Cheers.

RS

---

### Post by iambodin on 2009-01-07
> **rstritmatter said:**
> I ran sudo dpkg --configure -a
then sudo apt-get install -f
then installed sun-java6-bin
sudo apt-get install sun-java6-jdk

Thanks for the clear instructions, but this did not work for me. 

on the install sun - java6 bin command I got this:
[[IMG]http://www.imagebay.us/images/cl72h509w0x8i3wdoz0o_thumb.png[/IMG]](http://www.imagebay.us/viewer.php?file=cl72h509w0x8i3wdoz0o.png)

[Attached as screenshot $1 since I'm not sure that link is working.]

At which I had no real choice other than to shut the terminal.


I also go this error message:

[IMG]http:// [[IMG]http://www.imagebay.us/images/sk0ttyj41apph4zn1j1y_thumb.png[/IMG]](http://www.imagebay.us/viewer.php?file=sk0ttyj41apph4zn1j1y.png)[/IMG]

[Attached as screenshot #2].



Further assistance would be greatly appreciated.  There seem to be many many people getting caught in a catch-22 bug trying to install java6.

Thanks for your help!

First you have to kill process of synaptic manager (Use Administration > System monitor or Reboot)

then

remove the cracked package by

sudo apt-get remove sun-java6-jdk

or

sudo apt-get remove sun-java6-doc (My cracked one is sun-java6-doc)

then continue...

sudo dpkg --configure -a
then sudo apt-get install -f
then installed sun-java6-bin
sudo apt-get install sun-java6-jdk


It works for me. try it !! :)

---

### Post by Ellaine on 2009-01-07
I installed this sun java in 8.04 64bit and works great in Firefox & Opera 64bit versions.
jre-1_5_0_17-linux-amd64.bin
Download to desktop>open terminal>cd Desktop. Then type chmod a+x jre-1_5_0_17-linux-amd64.bin
Then run sudo ./jre-1_5_0_17-linux-amd64.bin

I never could get the apt-get install sun-java6-jdk to install.

---

### Post by jespdj on 2009-01-07
Note that you are replying to a post that's more than half a year old, the original poster is most likely not still waiting for an answer.

---

