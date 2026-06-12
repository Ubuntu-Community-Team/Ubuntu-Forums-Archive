---
title: "Java on 64 bit test"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by OldGaf on 2009-06-19
OK..... I am having trouble with some Java but not all in Fire Fox.

On my 32 bit install I am able to see the logo and water effect on this page:

[_Java water logo_]("http://www.nialm.com/index/waterlogo.htm")

On my 64 bit install I "usually" only get a grey box.

Here is the odd bit....
If I make any changes to the Java installed, the page will display fine..... but ONLY until I refresh the page or restart FF.... then it never works again.

I had this installed...

> There are 3 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-6-sun/jre/bin/java
+ 2 /usr/lib/jvm/java-6-openjdk/jre/bin/java
3 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 

and the page was only showing a grey box.

I removed all the openjdk-6-jre "stuff" and switched back to the logo tab in fire fox (which was still running) and low and behold there was the logo and water effect. Refreshed the page and there it was..... gone.

This is what I have now: 

> sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
*+ 1 /usr/lib/jvm/java-6-sun/jre/bin/java
2 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 

> java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode) 

My question is..... what the heck is going on?
Obviously it CAN be displayed......

---

### Post by Arup on 2009-06-19
Using Java 1.6.0_14 it works fine here on Opera, you will need to remove the older Java.

---

### Post by dspisak on 2009-06-19
Hello.  You can try this.  It works for me in 8.10 and 9.04, each 64-bit.

Install Java_14 64-bit
1.	Remove all existing Java installations from the system by running:
sudo apt-get remove icedtea6-plugin openjdk-6-jre.
2.	Download the Lunux x64 JRE bin from [https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html).  A dialog box will appear asking you where to save the file.
3.	Save the .bin file to your desktop and wait for the file to download completely.  Close the browser.
4.	Unpack/Extract the file by running:
sudo chmod a+x jre-6u14-linux-x64.bin (&#8220;14&#8221; may be superseded)
sudo ./jre-6u14-linux-x64.bin
sudo mv jre1.6.0_14 /usr/lib/jvm
5.	Create a symbolic link to the Firefox plugin directory: 
cd ~/.mozilla
mkdir plugins
ln -s /usr/lib/jvm/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
6.	Launch your browser.  To verify installation in Firefox enter about:plugins from the browser menu.  You should see the Java Plig-in, and the file libnpjp2.so listed.
7.	If Firefox does not recognize Java then write about:config to the address bar. Write "java" to the filter so that you can find the settings more easily.  Change the following settings:
java.default_java_location_others = /path_to_jre/jre1.6.0_14
java.java_plugin_library_name = libnpjp2

---

### Post by Arup on 2009-06-19
[https://launchpad.net/~jauntybleed/+archive/ppa](https://launchpad.net/~jauntybleed/+archive/ppa)

Add this to your repo and get latest Java the easy way.

---

### Post by OldGaf on 2009-06-20
Thanks for the input guys.... I will try to upgrade my java to 1.6.0_14 when I get off work today...

---

### Post by OldGaf on 2009-06-20
Upgraded to 14...... same thing with both FF and Opera...

---

### Post by philinux on 2009-06-20
White box every time. Freezes FF and the java process goes to 50%cpu.

libnpjp2.so

    File name: /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so

---

### Post by Arup on 2009-06-21
Can you tell me what video driver and flash you are using currently?

---

### Post by OldGaf on 2009-06-21
> **Arup said:**
> Can you tell me what video driver and flash you are using currently?


Video = nVidia 180.44


Flash should not matter as there is no prob with flash. The test logo is java only.....

---

### Post by Arup on 2009-06-21
> **OldGaf said:**
> Video = nVidia 180.44


Flash should not matter as there is no prob with flash. The test logo is java only.....

Just out of curiousity, would be be willing to upgrade the nvidia driver to the latest 185.18.14? I tried this site with older Java 13 as well as latest 14 on both FF and Opera and it works fine, I do have latest nvidia drivers.

---

### Post by istblacken on 2009-06-22
here, crashes with 1.6.0_13 and works fine with 1.6.0_14 using nvidia driver 185.18.14.

---

### Post by OldGaf on 2009-07-16
> **istblacken said:**
> here, crashes with 1.6.0_13 and works fine with 1.6.0_14 using nvidia driver 185.18.14.

Well..... I un-installed the old Java... now I only have the latest:

> java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

> sudo update-alternatives --config java
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

I did a small upgrade to my nvidia driver... 180.44 to 180.60

Still the same thing.

Not sure if I want to upgrade to 185.18.14... are there any issues with this driver? How did you install it.. I am using Kubuntu Jaunty.

This is still bugging me..... most Java is working for me.... some, like the test page only work sometimes.... very strange.

---

### Post by OldGaf on 2009-07-16
OK.... went ahead an upgraded my nVidia drivers to the latest:

> glxgears -info                                         
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/4687 the monitor refresh rate.                        
GL_RENDERER   = GeForce 9800 GT/PCI/SSE2
GL_VERSION    = 3.0.0 NVIDIA 185.18.14
GL_VENDOR     = NVIDIA Corporation
BLA BLA BLA
31703 frames in 5.0 seconds = 6337.940 FPS
35993 frames in 5.0 seconds = 7198.555 FPS
35988 frames in 5.0 seconds = 7197.560 FPS
36059 frames in 5.0 seconds = 7211.720 FPS
34458 frames in 5.0 seconds = 6890.790 FPS
35758 frames in 5.0 seconds = 7150.684 FPS


FF still displays this page correctly:
[Test Clock]("http://www.nialm.com/index/menu2/clock1.html")

But not this one "most" of the time:
[Test logo]("http://www.nialm.com/index/waterlogo.htm")

Also, if I open the logo page first and then the clock page.... the clock will not display until I close the logo page.... like the logo is "hanging" Java.

Anyone got any more ideas?

---

### Post by Arup on 2009-07-16
Both works fine here on Opera 10 or FF with nvidia GeForce 8400GS using 185.14 installed via sh. Using Java installed from repos. The Ubuntu team has updated to latest Java 1.6.0_14 thankfully.

---

### Post by darco on 2009-07-17
> **OldGaf said:**
> OK.... went ahead an upgraded my nVidia drivers to the latest:



FF still displays this page correctly:
[Test Clock]("http://www.nialm.com/index/menu2/clock1.html")

But not this one "most" of the time:
[Test logo]("http://www.nialm.com/index/waterlogo.htm")

Also, if I open the logo page first and then the clock page.... the clock will not display until I close the logo page.... like the logo is "hanging" Java.

Anyone got any more ideas?

nope.

Running Mint x64, latest java, nvidia 185.18.14....tried w/FF 3.011...logo shows black screen with grey box...Test clock is fine...

Opera 9.64 black screen on both links

Chromium 3.0 195 using black screen on both links...

darco

**edit** updated to Opera 10 beta, ENABLED java, and I see both logos.....

---

### Post by OldGaf on 2009-07-17
> **darco said:**
> 
**edit** updated to Opera 10 beta, ENABLED java, and I see both logos.....

If you move your mouse over the logo in Opera...... does it leave a water "trail" behind the mouse?

---

### Post by OldGaf on 2009-07-17
HAHAHAHAHA...................

OK..... all the Java works with Opera..... but Opera does not display Flash !!!!!


OMG....... this is too much!

---

### Post by Yellow Pasque on 2009-07-17
Something must be wrong with the page. It doesn't work for me on FF and I'm using the Java 6u14 included in Jaunty. I'm also using radeonhd (Mesa 3D) drivers.

NVM, it works in a new tab

---

### Post by OldGaf on 2009-07-17
OK..... quick search on the forum and flash is fixed...... 

WOW.... what a lucky guy I am... I finally have a browser that can do BOTH Java and Flash!

If only I knew why it does not work in FF or Epiphany....

Oh well....looks like I am an Opera man now!

---

### Post by Arup on 2009-07-17
> **OldGaf said:**
> OK..... quick search on the forum and flash is fixed...... 

WOW.... what a lucky guy I am... I finally have a browser that can do BOTH Java and Flash!

If only I knew why it does not work in FF or Epiphany....

Oh well....looks like I am an Opera man now!

Opera works fine with x64 Flash 10, make sure to put the libflashplayer.so in /usr/lib/mozila/plugins folder.

---

### Post by darco on 2009-07-18
Just installed Opera 10 beta w/QT4....100/100 Acid test results...flash/java works fine....I wish it had add ons like ad blocker...

[http://snapshot.opera.com/unix/snapshot-4453/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-4453/x86_64-linux/)

I am really starting to think firefox is losing it , especially for us x64 bit users...tracemonkey isnt an option for us and its the heart of 3.5 x32!....

Also running Chromium.....and I like it very much!



darco

---

### Post by Arup on 2009-07-18
> **darco said:**
> Just installed Opera 10 beta w/QT4....100/100 Acid test results...flash/java works fine....I wish it had add ons like ad blocker...

[http://snapshot.opera.com/unix/snapshot-4453/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-4453/x86_64-linux/)

I am really starting to think firefox is losing it , especially for us x64 bit users...tracemonkey isnt an option for us and its the heart of 3.5 x32!....

Also running Chromium.....and I like it very much!



darco


[http://www.fanboy.co.nz/adblock/](http://www.fanboy.co.nz/adblock/)

Adblocker for Opera, works quite well.

---

### Post by darco on 2009-07-18
Good to know, thanks!

darco

---

### Post by OldGaf on 2009-07-22
> **Arup said:**
> Opera works fine with x64 Flash 10, make sure to put the libflashplayer.so in /usr/lib/mozila/plugins folder.


Ya... you missunderstood my post.... I said it *does* work for me with Opera.... but thanks for the tip :)


Would still like to get it to work in FF etc.... but I am moving on to something funner!

---

### Post by grege on 2009-07-24
Difficult to answer the poll, depends on which Java and which browser.

Sun Java seems to work OK as a plugin in Firefox 3.5.

Standalone programs work fine for me with either Sun Java or OpenJDK.

IcedTea plugin does not operate for me in Firefox 3.5 - I just get a grey box.

I tried an early alpha of karmic and it was not resolved, but have not tried again for a while.

So, for the moment, Sun Java works best on my machine.

---

