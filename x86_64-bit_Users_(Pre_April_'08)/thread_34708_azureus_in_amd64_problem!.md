---
title: "azureus in amd64 problem!"
date: 2005-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by drews_blunted on 2005-05-16
I went ahead and installed Azureus 2.2 for AMD64 gtk.
For some reason when I try tunning it I get this error:

Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_03]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/drew/Programs/azureus/Azureus2.jar:/home/drew/Programs/azureus/swt.jar:/home/drew/Programs/azureus/swt-mozilla.jar:/home/drew/Programs/azureus/swt-pi.jar" -Djava.library.path="/home/drew/Programs/azureus" -Dazureus.install.path="/home/drew/Programs/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/drew/Programs/azureus/libswt-pi-gtk-3106.so: /home/drew/Programs/azureus/libswt-pi-gtk-3106.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:100)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:118)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:45)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:181)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:71)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:115)
Azureus TERMINATED.

Im not sure if this is an azureus, java or amd64 problem?
Has anyone else had this sort of problem on ubuntu?
If so how can I get my Azureus running! :grin:

---

### Post by FluffyElmo on 2005-05-16
I can't try it until I get home, but I did have Azureus running in the past using the IBM amd64 JDK. There was a bug with the Sun amd64 1.5 JVM and Eclipse, but Eclipse worked with the IBM JVM so I used it for Azureus as well.

May be worth a try, good luck!

---

### Post by drews_blunted on 2005-05-16
Hey, where can i get this version of jde? Im running hoary 5.10 amd64 
I followed the tutorial on ubuntuguide.org to install java.

---

### Post by FluffyElmo on 2005-05-16
You can get it here after completing registration. I installed it to a seperate directory from my Sun JDK and hard-coded Azureus to point to it. I just added the path to */home/username/azureus/azureus.sh*. 

[https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?source=lxdk](https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?source=lxdk)

---

### Post by FluffyElmo on 2005-05-16
May not be necessary though, I just tried Azureus with the Sun JDK and it's running fine. I'll download the latest version to see if I can recreate your problem...

Azureus: 2.2.0.3_B59
Sun JDK: Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)

---

### Post by drews_blunted on 2005-05-17
jre-1_5_0_03-linux-amd64.bin

Azureus_2.3.0.0_linux.AMD64.tar.bz2

Thats what i have installed right now and it is not working.
If seen similar posts about this on other forums, but no answers! 
Anyone know whats needed to get this to work? Do i need to link the librarys or something like that? Also i have tested java and its working and will even run limewire!

---

### Post by FluffyElmo on 2005-05-17
I didn't get a chance last night but I'll try the 2.3.x azureus tonight to see if it works. In my case I edited */home/username/azureus/azureus* to point directly to the jdk...you may want to try it if you have more than one installed.

---

### Post by FluffyElmo on 2005-05-17
Are you still having problems? I've just tried the most recent Azureus build and it still works. A few thoughts...

Does the file it is looking for exist? */home/drew/Programs/azureus/libswt-pi-gtk-3106.so*

Try changing the permissions on the file if it is there?

Are you using Kubuntu? If so you may have to install GTK?

---

### Post by drews_blunted on 2005-05-18
Yes, that file exist, i went ahead and edited the azureus.sh and changed it to say this!
Still it will not work!

path to java bin dir, ex. "/usr/java/jre1.5.0_03/bin/"
#PROGRAM_DIR="/home/drew/Programs/azureus"	# use full

---

### Post by tlepes on 2005-05-22
Drews, what about the error message from your output?
[QUOTE=drews_blunted]
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/drew/Programs/azureus/libswt-pi-gtk-3106.so: /home/drew/Programs/azureus/libswt-pi-gtk-3106.so: cannot open shared object file: No such file or directory[/QUOTE]

Does the file **/home/drew/Programs/azureus/libswt-pi-gtk-3106.so** actually exist?  If so, what are the permissions and such?  I am not running 64bit myself (though considering it).  But just thought I'd ask if you checked into the obvious.  I am running Azureus 2.3.0.0 on JRE 1.5.02 with Ubuntu 5.10 (32-bit) on AMD64 at the moment.

Peace & good luck to ya..
Tim

---

### Post by jarchack on 2005-05-23
[QUOTE=][/QUOTE]
 My azureus works with the Blackdown java:

[http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html](http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html)

but not the jre-1_5_0_03-linux-amd64.bin. I haven't been able to get the 64 bit to run much of anything.

---

### Post by drews_blunted on 2005-05-23
[QUOTE=tlepes]Drews, what about the error message from your output?


Does the file **/home/drew/Programs/azureus/libswt-pi-gtk-3106.so** actually exist?  If so, what are the permissions and such?  I am not running 64bit myself (though considering it).  But just thought I'd ask if you checked into the obvious.  I am running Azureus 2.3.0.0 on JRE 1.5.02 with Ubuntu 5.10 (32-bit) on AMD64 at the moment.

Peace & good luck to ya..
Tim[/QUOTE]
 yes, my problem i am sure is specific to amd64 running in 64 bit ubuntu/linux.  and yes that file does exist and its  chmod 777

---

### Post by FluffyElmo on 2005-05-24
First are you absolutely sure that you have the right version for your OS? When I try to run the AMD64 version on my 32bit Ubuntu box at work I get the *exact same error* you get. When I run the regular GTK version it works. My home 64bit box runs the AMD64 version. So I'm guessing you have the wrong version for your OS. 

Download the *Linux AMD64* build if you're running Ubuntu AMD64, and the *Linux GTK* build if you're running 32bit Ubuntu. Note that you can run *either* Ubuntu 32bit or Ubuntu 64bit on an AMD64 processor, so make sure the Azureus version corresponds to the version of Ubuntu you actually installed, not just the processor you have.

That said, the basic steps I used to download and install it on my home box are:

Download the AMD64 build from *[http://azureus.sourceforge.net](http://azureus.sourceforge.net)*
From a terminal session: ```

*bzip2 -d Azureus_2.3.0.0_linux.AMD64.tar.bz2*
*tar -xvf Azureus_2.3.0.0_linux.AMD64.tar*
*cd ./azureus*
*./azureus*
```

...and it runs without trouble. I also edited the ./azureus shell file to point directly to my JVM but that's only because I have more than one installed.

---

### Post by KRavEN on 2005-05-25
[QUOTE=drews_blunted]yes, my problem i am sure is specific to amd64 running in 64 bit ubuntu/linux.  and yes that file does exist and its  chmod 777[/QUOTE]
 I installed the sun java 1.5 version for all java programs abd the blackdown version just for the firefox plugin in accordance to the ubuntu wiki.  I then installed azureus by downloading the amd64 version from azureus website and installing it in accorance with the ubuntu newbie website instructions.  Everything works perfectly.

---

### Post by rsw on 2005-06-13
I had this same problem w/ ubuntu hoary amd64 + azureus.

What I did to fix it:

0. First, remove any other jre's you have installed previously. Lots of howtos tell you to install them to /usr/java so that's a good place to look when removing em. Note, the '#' preceeding a command means do it as root (su - ) or with sudo. '$' means just do it as a normal user.

1. find this exact file: jre-1_5_0_03-linux-amd64.bin   
  ... I found it at: [http://public.planetmirror.com/pub/java-sun/J2SE/5.0_03/amd64/](http://public.planetmirror.com/pub/java-sun/J2SE/5.0_03/amd64/)  
[COLOR=DarkOrange]*** This first step is critical! I had problems with every other version & package of jre1.5.0.03, this one works ***[/COLOR]

2. `cd' into whatever directory you downloaded it to, and then do as root (or sudo): 
 # [COLOR=Red]sh jre-1_5_0_03-linux-amd64.bin[/COLOR]

3. The installer script thing should put it in /usr/java. Verify that it is there: ls /usr/java   ... if it shows a jre1.5blahblah there, then you're ok. **If not**, it probably put it in the same directory that you downloaded it to. In that case, move it: 
 # [COLOR=Red]mkdir /usr/java[/COLOR]
 # [COLOR=Red]mv jre1.5.0_03 /usr/java[/COLOR]

4. Now we're going to make some symlinks so that any user can just type 'java' from any location and it will find our new jre install.
 # [COLOR=Red]cd /usr/java[/COLOR]
 # [COLOR=Red]ln -s jre1.5.0_03 jre[/COLOR]
 # [COLOR=Red]ln -s jre/bin/java /usr/bin/java[/COLOR]
 
5. Make sure everything is ok so far by testing (the classic test :) ...
 $ [COLOR=Red]java -version[/COLOR]
 
  This should return something like:
[COLOR=YellowGreen]java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_03-b07, mixed mode)[/COLOR]

3. Next, download the "Linux amd64" version of azureus from their site: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) ...at the time of writing, it is 2.3.0.2 (resulting filename should be something very similar to "Azureus_2.3.0.2_linux.AMD64.tar.bz2"). You should download this to some temp directory, home dir or somewhere meaningful to you (mainly so you can find it ;)).

4. Again, make sure you're in the directory you downloaded the .tar.bz2 to, and do:
  $ [COLOR=Red]bzip2 -cd Azureus_2.3.0.2_linux.AMD64.tar.bz2 |  tar x[/COLOR]

5. Next, cd into the resulting directory (simply called 'azureus') and then try running the program as a normal user:
  $ [COLOR=Red]cd azureus[/COLOR]
  $[COLOR=Red] ./azureus[/COLOR]

If all is well, good things will happen (GUI will come up, config questions will be asked, etc).

---

### Post by w0arz on 2005-07-13
**ln -s /usr/java/jre/bin/java /usr/bin/java**

and no 

ln -s /jre/bin/java /usr/bin/java

---

### Post by jon_gunnar on 2005-07-14
[QUOTE=drews_blunted]I went ahead and installed Azureus 2.2 for AMD64 gtk.
For some reason when I try tunning it I get this error:

Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_03]
Configuring environment...
Loading Azureus:
[/QUOTE]

I did this the easy way and compiled the jdk-1_5_0_04-linux-amd64.bin package from sun. Used apt-get: 
apt-get install fakeroot java-package java-common

Then:
fakeroot make-jpkg --full-name "<Your name>" --email "<Your email>" jdk-1_5_0_04-linux-amd64.bin

Answer some questions. After a little work you got the deb package to install
sudo dpkg -i sun-j2sdk1.5_1.5.0+update04_amd64.deb

It probably is easier ways to do it. But this were pretty straightforward to do, and it gave me a working, nice java for azureus.

---

### Post by nomad311 on 2005-07-27
aihgt i dunno y the hell i cant java to work ...i tried following the unofficial guides way of doin it ...sun-j2re1.5 aint in the repositor i guess ...and yes i added them ...in fact i copied there example file and replaced mine then checked EVERYTHING.

next i tried the ubuntu wiki guide ...i got an error i posted here:
[http://ubuntuforums.org/showthread.php?p=273627#post273627](http://ubuntuforums.org/showthread.php?p=273627#post273627)

next i came here and followed rsw's directions but when i try to run the java command its not registered ....i get
```
java: command not found
``` 

...even b4 i came here i went n got ibm's java sdk and followed their instructions to install but cam to a dead end cause they only have rpm or a gzip and they dont tell you what to do next!!!!

this sux ...its been months where the hell is the .deb for this 

-nomad311

---

### Post by DancingSun on 2005-07-27
Try Tamir's repository in the amd64 packages thread.
I installed the Sun Java 1.5 that Tamir packaged and it works like a charm :D

---

