---
title: "HOWTO: x64 Eclipse + PHPEclipse"
date: 2007-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by andymagic1 on 2007-02-19
Hi,

Just thought I would share this since it took me a while to figure out.

The add/remove programs in ubuntu installs 32bit Eclipse and 64bit java. This will mean Eclipse will not work.
In order to get Eclipse and PHPEclipse working I did the following:

1) Install Java Runtime. Application > Add/Remove > Sun Java 5.0 runtime
2) Download Eclipse manually from [http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/)
3) Install.
tar -zxvf eclipse-SDK-3.2.2-linux-gtk-x86_64.tar.gz -C /opt/
4) Run application as root.
gksudo /opt/eclipse/eclipse
5) Installed PHPEclipse

See: [http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse](http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse)

   1.  Click on Help->Software Updates->Find/Install from file menu in Eclipse.
   2. Select the radio button labeled, "search for new features to install".
   3. Click on the "New Remote Site" button.
   4. Enter a name, and the URL: [http://phpeclipse.sourceforge.net/update/cvs](http://phpeclipse.sourceforge.net/update/cvs) (unstable) or [http://phpeclipse.sourceforge.net/update/releases](http://phpeclipse.sourceforge.net/update/releases) (stable)
   5. Click on "Finish".
   6. A list of features will be presented, open the list and check the one labeled "phpeclipse".
   7. Click on "Next"
   8. Follow the onscreen instructions to finish the automatic install. 

6) Close eclipse. Application should now run okay. Alt F2 (Run application) > /opt/eclipse/eclipse
7) Optional: Add shortcut to applications menu. System > Pref > Menu layout etc.....

---

### Post by golfing22 on 2007-04-05
Thanks a ton for the guide.  I just spent the last few hours trying to install Eclipse with PHP and this once I found this guide it only took 5 minutes.

Works great.

---

### Post by mario.kostelac on 2007-05-22
I tried this and then I got an error:
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/opt/eclipse/jre/bin/java
'java' in your current PATH

Please answer...
Thanx...

---

### Post by andymagic1 on 2007-05-22
BlizZ, are you using 7.04? I originally wrote this for 6.10. Perhaps things have changed.

Well it sounds like Java isn't installed properly. Did Java install properly for you? Do you see a Java icon in your menu?

---

### Post by mario.kostelac on 2007-05-22
Yes, I use Feisty, x64... And problem is that java is installed correctly...
Add/Remove and checked java 5.0 runtime

---

### Post by andymagic1 on 2007-05-22
I'm afraid I don't have Feisty x64 installed, so I can't help you any further.

Perhaps I'll give it another try soon. I gave up on 6.10 64bit since had too many issues.

---

### Post by mario.kostelac on 2007-05-22
ohhhh....
Sadly is that worked...
But I don't know why don't now...
:(:( I need eclipse... And.. do you know some cool PHP editor?

---

### Post by andymagic1 on 2007-05-22
Oh, so it was working before you upgraded to Feisty?

I had some issues with Eclipse after upgrading to 32bit Feisty. I think I just uninstalled and then installed eclipse again and it worked fine. Although I don't think my problem was related to Java.

Zend Studio is supposed to be a very good PHP IDE, but I don't think its free.

---

### Post by mario.kostelac on 2007-05-22
I installed a fresh Feisty... and now the problem is solved...
for other feisty x64 users with same issue...
so... I had deleted all java packages... and then, from Add/Remove I installed Sun Java 6 Web start (I don't know that's necessary or not, but I installed this also), Sun Java 6 Web start (32 bit) and Sun Java 6 Console...
And then just follow the rules above... but don't start with gksudo /opt/eclipse/eclipse... start with java -jar *path to eclipse*/startup.jar...
And then everthing will be OK...
Enjoy, I hope that will help...

---

### Post by puttagun on 2007-09-03
Hello,

Though this thread is a bit dated, I thought I'd post my experience, since I had similar issues and finally got it working.

After several trial and errors, here's what finally worked for me:

1. Installed Java 6 (from Add/Remove Programs) - there's a Java 6 Webstart.
(I didnt install any console programs etc.). This should be the Java 6 for x86_64 platform.

2. Installed the Europa (v 3.3) of Eclipse from the Eclipse download site. Be sure to pick the  x86_64 bit version for Linux. You can find it by clicking on the latest version link at: 
[http://download.eclipse.org/eclipse/downloads/](http://download.eclipse.org/eclipse/downloads/)
Currently, the latest version link is pointing to;
[http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php)
You may want to get the full SDK of the platform (including JDT, PDT etc.) since JDT is anyway required.

3. By default, the JVM picked up by Eclipse would be the JVM prior to your Java 6 installation, so if that is not x86_64, then you are likely to run into any number of problems including Eclipse hanging on you etc.  I had previously installed swiftweasel (32-bit) and the flash and Java 32-bit, so I didnt want to mess up that setup by changing the default links for JVM. So, to *change* the JVM used by Eclipse, you can either use the -vm command line argument (dont know the exact syntax) or simply put a symlink in the eclipse installed directory for the x86_64 JRE. e.g., on my system, here's what I did:

/opt/eclipse $. ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre jre

4. You can now install the PDT runtime (add the Europa PDT site in the Update manager and let the update manager do it for you).

Eclipse is running fine and all the modules are also ok.

Hope this helps,

Naveen.

---

### Post by adamc55 on 2007-11-02
Yes, it did -- thanks for taking the time to post it!

---

