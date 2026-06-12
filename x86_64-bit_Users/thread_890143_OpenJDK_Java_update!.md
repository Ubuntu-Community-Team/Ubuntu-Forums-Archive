---
title: "OpenJDK Java update!"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-08-14
I have the following packages installed for Java:
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin

I received an update to openjdk and Java now works much better on 64-bit.  Everything works, except the Facebook photo uploader.:( (rather anticlimactic)

But the [Yahoo! finance stocks screener works.]("http://screener.finance.yahoo.com/fscr/us/launch.html")

---

### Post by Thelasko on 2008-08-14
I am attaching the final section of the terminal output from running the Facebook photo uploader:
```
Jar string: FacebookPhotoUploader.jar
jars length: 1
initializing JNLPRuntime...
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
Exception in thread "Applet" java.lang.NoClassDefFoundError: netscape/javascript/JSObject
	at java.lang.Class.getDeclaredMethods0(Native Method)
	at java.lang.Class.privateGetDeclaredMethods(Class.java:2444)
	at java.lang.Class.getDeclaredMethod(Class.java:1952)
	at java.awt.Component.isCoalesceEventsOverriden(Component.java:5791)
	at java.awt.Component.isCoalesceEventsOverriden(Component.java:5780)
	at java.awt.Component.access$100(Component.java:167)
	at java.awt.Component$3.run(Component.java:5745)
	at java.awt.Component$3.run(Component.java:5743)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Component.checkCoalescing(Component.java:5742)
	at java.awt.Component.<init>(Component.java:5711)
	at java.awt.Container.<init>(Container.java:270)
	at java.awt.Panel.<init>(Panel.java:64)
	at java.awt.Panel.<init>(Panel.java:56)
	at java.applet.Applet.<init>(Applet.java:65)
	at javax.swing.JApplet.<init>(JApplet.java:130)
	at com.aurigma.imageuploader.ImageUploader.<init>(Unknown Source)
	at com.facebook.facebookphotouploader.FacebookPhotoUploader.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:441)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:401)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:580)
Caused by: java.lang.ClassNotFoundException: netscape.javascript.JSObject
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClassExt(JNLPClassLoader.java:700)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClass(JNLPClassLoader.java:657)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 27 more
java.lang.NullPointerException
	at net.sourceforge.jnlp.NetxPanel.runLoader(NetxPanel.java:82)
	at sun.applet.AppletPanel.run(AppletPanel.java:380)
	at java.lang.Thread.run(Thread.java:636)
  PIPE: appletviewer wrote: status exception: java.lang.NullPointerException.
java.lang.NullPointerException
	at sun.applet.AppletPanel.run(AppletPanel.java:430)
	at java.lang.Thread.run(Thread.java:636)
  PIPE: appletviewer wrote: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status exception: java.lang.NullPointerException.
  PIPE: plugin read: status exception: java.lang.NullPointerException.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status Start: applet not initialized.
  PIPE: plugin read: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return



```
I chose to only show the last section of the output for privacy purposes.  It appears to get much farther than it did before.

---

### Post by tinny on 2008-08-15
Java Applets on 64 bit Ubuntu dont work well.

The OpenJDK browser plugin works sometimes. The Sun Java browser plugin doesnt exsit for 64 bit Ubuntu. :(

If this functionality is important to you I would suggested that you install the 32 bit version of Ubuntu.

BTW: Ive heard good things about OpenJDK in Ubuntu intrepid (the next version).

---

### Post by Thelasko on 2008-08-15
> **tinny said:**
> Java Applets on 64 bit Ubuntu dont work well.

The OpenJDK browser plugin works sometimes. The Sun Java browser plugin doesnt exsit for 64 bit Ubuntu. :(

If this functionality is important to you I would suggested that you install the 32 bit version of Ubuntu.

BTW: Ive heard good things about OpenJDK in Ubuntu intrepid (the next version).

That's my point, the update I received yesterday makes Java applets work much better.  I suspect the updated OpenJDK is similar to the version in Intrepid.

---

### Post by Yellow Pasque on 2008-08-15
> If this functionality is important to you I would suggested that you install the 32 bit version of Ubuntu.

Just run a 32-bit browser. No need for an entire separate 32-bit OS.

---

### Post by tinny on 2008-08-15
> **Temüjin said:**
> Just run a 32-bit browser. No need for an entire separate 32-bit OS.

How do you do this? Link please :)

---

### Post by wd5gnr on 2008-08-15
[http://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](http://help.ubuntu.com/community/AMD64/FirefoxAndPlugins). Note you have to run either 32 bit FF or 64 bit FF at any given time. Switching requires you close all your firefox instances.

---

### Post by Thelasko on 2008-08-15
<venting>
This Java situation is really frustrating me.  **I understand that OpenJDK is not as good as Sun Java!**  But it's *really* close, and it frustrates me that nobody is willing to tinker with it to figure out what's wrong.  Maybe the people who are tinkering with it simply aren't sharing their knowledge.  Either way, it's still frustrating.

What's more frustrating is when I share the knowledge I have learned about OpenJDK, I'm told to use 32-bit.

I'm willing to go the extra mile, who's with me?
</venting>

The updated version of OpenJDK runs more things than it did before the update.  It now downloads the applet, stores it in a cache, and manages the security blacklist/whitelist. These are things it didn't do two days ago.  Perhaps someone who knows more about Java than I do can figure out why it fails on some applets and not others.  I think it has to do with the way the applet is embedded in the page.

---

### Post by tinny on 2008-08-15
> 
I think it has to do with the way the applet is embedded in the page.


Something like using <object>.... or <applet>....?

I dont think that this would make a difference. Maybe you could try it out.

---

### Post by Thelasko on 2008-08-15
I Googled the first line of the error message I received
```
java.lang.NoClassDefFoundError: netscape/javascript/JSObject
```
I discovered [this page]("http://java.sun.com/products/plugin/1.3/docs/jsobject.html").  It says:
> To compile Java code to take advantage of JSObject, you must have the package netscape.javascript in the CLASSPATH. Currently, Java Plug-in 1.3 ships netscape.javascript in a JAR file called JAWS.JAR. To compile an applet which uses JSObject, please add JAWS.JAR in the CLASSPATH before compilation.
JSObject handles Java to Java-script communication.  Which goes along with my theory about the functionality of the applet depends on how it's embedded in the page.  I assume when the article mentions "please add JAWS.JAR in the CLASSPATH before compilation" they mean compilation of the plugin.

I may need a crash course in Java.

---

### Post by tinny on 2008-08-15
> **Thelasko said:**
> I Googled the first line of the error message I received
```
java.lang.NoClassDefFoundError: netscape/javascript/JSObject
```
I discovered [this page]("http://java.sun.com/products/plugin/1.3/docs/jsobject.html").  It says:

JSObject handles Java to Java-script communication.  Which goes along with my theory about the functionality of the applet depends on how it's embedded in the page.  I assume when the article mentions "please add JAWS.JAR in the CLASSPATH before compilation" they mean compilation of the plugin.

I may need a crash course in Java.

You may be on to something. :confused:

Im pretty sure we dont need to worry about that now. Java 1.3 is really old! However the Applets in question may be really old...

---

### Post by Thelasko on 2008-08-15
I found an interesting article in Red Hat Magazine.  It says:
> We’re making good progress on gcjwebplugin’s two missing features: a LiveConnect Java/JavaScript bridge and signed applet verification. Future Fedora releases will boast increasingly better integration of these Java deployment technologies.
It appears that last night's update took care of the signed applet verification.  This explains why more applets work after the update.  The LiveConnect issue is yet to be resolved.

Interestingly, Mozilla has a note on their [development page]("http://developer.mozilla.org/en/docs/LiveConnect") that says LiveConnect is no longer needed.  I don't know what that means.

---

### Post by Thelasko on 2008-08-15
> Interestingly, Mozilla has a note on their development page that says LiveConnect is no longer needed. I don't know what that means. 
LiveConnect wouldn't be needed if Sun would finish developing [this plugin.]("https://jdk6.dev.java.net/plugin2/")

---

### Post by Thelasko on 2008-08-15
> Im pretty sure we dont need to worry about that now. Java 1.3 is really old!
From what I have gathered, Sun hasn't updated it's plugin in a long time.  If they have, they didn't bring it up to [current standards]("http://en.wikipedia.org/wiki/NPAPI").  Programs that use the current NPAPI standard, like Adobe Flash, benefit from a wonderful program called [nspluginwrapper]("http://gwenole.beauchesne.info/en/projects/nspluginwrapper") on systems with architectures other than i386.  Nspluginwrapper is what allows Flash to work with Firefox on Ubuntu 64.  If Sun Java used that standard, then in theory, nspluginwrapper would solve the Java problems too.

Sun is developing a [plugin]("https://jdk6.dev.java.net/plugin2/") that conforms to the NPAPI standard.  I think that Sun is focusing on this new plugin and therefore isn't working on a 64-bit version of the current plugin.

The current open source plugin for Firefox is based on [GCJ]("http://en.wikipedia.org/wiki/GNU_Compiler_for_Java"), since Sun didn't release the source code of their plugin.

---

### Post by wd5gnr on 2008-08-15
The one site I wish worked that doesn't is Thinkfree. Even then, I wonder if it _would_ work. It simply detects that you don't have the version of Java it expects and that's it. You have to wonder if there is a way OpenJava could "alias" itself the way some browsers look like IE?

---

### Post by Thelasko on 2008-10-29
I just received an update to icedtea-gcjwebplugin, any word on what this fixes?  It appears that LiveConnect still doesn't work.

---

### Post by Thelasko on 2008-10-29
It appears that [this bug]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/199732") was fixed by the new update.

---

### Post by 080818jk on 2008-10-30
&#65292;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#24182;&#22312;&#20844;&#21496;&#36816;&#33829;&#20013;&#20005;&#26684;&#25511;&#21046;&#25191;&#34892;&#36136;&#37327;&#20307;&#31995;&#12290;&#12288;&#12288;&#30334;&#22478;&#24681;[&#30417;&#25511;](http://www.cydjk.com/jk.htm)&#31185;&#25216;&#25104;&#31435;&#22810;&#24180;&#20197;&#26469;&#65292;[**&#30417;&#25511;&#24037;&#31243;**](http://www.cydjk.com/jkgc.htm)&#19982;&#22810;&#23478;&#31995;&#32479;&#38598;&#25104;&#21830;&#26377;&#30528;&#20146;&#23494;&#30340;&#21512;&#20316;&#20851;&#31995;&#65292;&#32463;&#36807;&#20182;&#20204;&#30340;&#22823;&#21147;&#25903;&#25345;&#21644;&#20844;&#21496;&#20869;&#37096;&#35757;&#32451;&#26377;&#32032;,&#39640;&#25216;&#26415;&#27700;&#20934;,[**&#30417;&#25511;&#22120;&#26448;**](http://www.cydjk.com/jkqc.htm)&#26377;&#24320;&#21019;&#31934;&#31070;&#30340;&#24037;&#31243;&#25216;&#26415;&#20154;&#21592;&#21450;&#20855;&#22791;[**&#21271;&#20140;&#30417;&#25511;**](http://www.cydjk.com/bjjk.htm)&#29616;&#20195;&#21270;&#20225;&#19994;&#35201;&#27714;&#30340;&#31649;&#29702;&#20154;&#21592;&#30340;&#20849;&#21516;&#21162;&#21147;&#19979;

---

### Post by Sef on 2008-10-30
>   It appears that LiveConnect still doesn't work.

A fix for Live Connect is coming.  It will take some time to get it fixed.

---

### Post by jamesstansell on 2008-11-02
> **Sef said:**
> A fix for Live Connect is coming.  It will take some time to get it fixed.

Liveconnect is supposed to be fixed in Ubuntu 8.10 (Intrepid) in the icedtea6-plugin package.

---

### Post by Modplanman on 2008-11-02
Use the Icedtea6 plugin, not gcjwebplugin.

---

### Post by jamesstansell on 2008-11-02
> **Thelasko said:**
> LiveConnect wouldn't be needed if Sun would finish developing [this plugin.]("https://jdk6.dev.java.net/plugin2/")

Sun has finished that plugin, and it makes use of liveconnect.  In fact, that page includes what seems to be the new liveconnect specification.

---

### Post by Thelasko on 2008-11-03
> **Modplanman said:**
> Use the Icedtea6 plugin, not gcjwebplugin.

I use [this one]("http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin"), which is technically both Icedtea6 and gcjwebplugin.

---

### Post by jarl on 2008-11-11
> **Thelasko said:**
> I use [this one]("http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin"), which is technically both Icedtea6 and gcjwebplugin.

:confused: How did you install that. I have problems due to [bug 292432]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/292432/") and/or [bug 284299]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/284299/").

---

### Post by Thelasko on 2008-11-11
> **jarl said:**
> :confused: How did you install that. I have problems due to [bug 292432]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/292432/") and/or [bug 284299]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/284299/").

Well, I'm still on Hardy.  From what I read in those bug reports, users on Intrepid should install the [icedtea6-plugin]("http://packages.ubuntu.com/intrepid/icedtea6-plugin") instead.  I might be wrong.

---

### Post by jarl on 2008-11-11
> **Thelasko said:**
> Well, I'm still on Hardy.  From what I read in those bug reports, users on Intrepid should install the [icedtea6-plugin]("http://packages.ubuntu.com/intrepid/icedtea6-plugin") instead.  I might be wrong.

Well I've tried that, and the online bank I use does not work with icedtea6-plugin so I would like to give icedtea-gcjwebplugin a try, but the bug blocks me.

---

### Post by Thelasko on 2008-11-11
> **jarl said:**
> Well I've tried that, and the online bank I use does not work with icedtea6-plugin so I would like to give icedtea-gcjwebplugin a try, but the bug blocks me.

Do other sites, [like this one]("http://www.java.com/en/download/installed.jsp"), work?

---

### Post by jarl on 2008-11-12
> **Thelasko said:**
> Do other sites, [like this one]("http://www.java.com/en/download/installed.jsp"), work?

In Konqueror, No!.
In firefox, yes, apart from the "More Information" button is misplaced on top of the dancing duke.

Regarding basisbank.dk. I can login to it (though a java applet), but whenever I do a transaction (paying a bill, or transfer money), the procedure requires my signature code once again in a java applet, and the applet also displays alright there, but when I hit "enter", then the banking application goes to a 404 page. The other bank I have tested (eikbank.dk) works fine.

---

### Post by Thelasko on 2008-11-12
> **jarl said:**
> In Konqueror, No!.
In firefox, yes, apart from the "More Information" button is misplaced on top of the dancing duke.

Regarding basisbank.dk. I can login to it (though a java applet), but whenever I do a transaction (paying a bill, or transfer money), the procedure requires my signature code once again in a java applet, and the applet also displays alright there, but when I hit "enter", then the banking application goes to a 404 page. The other bank I have tested (eikbank.dk) works fine.

Sounds like the LiveConnect bug.  Your best option is to install 32-bit Firefox with the 32-bit version of Java.

---

