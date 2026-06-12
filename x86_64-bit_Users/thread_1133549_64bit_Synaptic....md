---
title: "64bit Synaptic..."
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by twooften on 2009-04-23
So my system became a cinder block about 2 weeks ago. Figured I would do some upgrading.
Thought, lets try out 64bit Ubuntu, now that I have a processor that supports it.
All installed nicely. 
Gigabyte EP43-UD3L, Core 2 Duo 2.8, 4G SLI DC DDR2, GeForce 9600 GSO.
So I am going through installing things that I use often, but I am getting lots of errors from synaptic.
"Unable to reload this" "cant find that" 
My question is. Does synaptic know to show me only 64bit versions?

---

### Post by bford16 on 2009-04-23
Synaptic will show you any package that is available from the Repositories listed in /etc/apt/sources.list.  There may be some 32-bit packages, but most of the available packages will be 64-bit.

Which packages are "missing?"

---

### Post by twooften on 2009-04-23
Well I didn't notice any problems until I went looking for acetoneISO2.
But, I really dont care about the problem, I am sure I will work it out.
I am more interested in how the whole 64bit universe works.
As a teen working in a local computer shop in the late 90s, 64bit was kind of a holy grail to me.
Now I have it in my hands, and not looking so good.
LOTS of crashes with firefox. Sad, but expected, lots of others having the same complaints.
Wine wont install from there, but I haven't tried downloading this or acetone from the site directly, so I am not out of options yet.
Other errors here and there, but nothing paralyzing.
So I am kinda on the fence about 64bit right now.

Any tips/tricks to filter out specific architecture when searching through synaptic?

---

### Post by Knad on 2009-04-23
As far as I know it automatically sorts itself out. I have been using 64bit on my desktop for a couple of years with no real problems, firefox just worked out of the box. Do you get any errors with the crashes?

---

### Post by Thelasko on 2009-04-23
Synaptic sorts everything out for you.  What version of Ubuntu are you using?

---

### Post by Slim Odds on 2009-04-23
First, 64 bit works great. If firefox is crashing, it's something about your configuration. I know some people have problems, but many more don't.

You Synaptic problem might just be that the repository servers are **extremely busy** when a new release comes out (like today).

---

### Post by twooften on 2009-04-25
Things are running better actually.
I am trying to get vuze running right now, I had to install java.

```
sudo apt-get install openjdk-6-jre
```

got the job done I think...
But now when I run 

```

albert@TheDoc:~/vuze$ ./vuze
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
find: `/home/albert/.azureus/plugins': No such file or directory
Browser check failed with: [COLOR="Red"]Cannot load 64-bit SWT libraries on 32-bit JVM[/COLOR]
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner for GRE
	Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-addons for GRE
	Can not use GRE from /usr/lib/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/mozilla for GRE
	Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-3.0.9 for GRE
	Can not use GRE from /usr/lib/firefox-3.0.9 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-1.9.0.9 for GRE
	Can not use GRE from /usr/lib/xulrunner-1.9.0.9 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
	Can not use GRE from /usr/lib/firefox because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-addons for GRE
	Can not use GRE from /usr/lib/xulrunner-addons because it's missing components/libwidget_gtk2.so.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuzehas better luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/albert/apps/vuze" -Dazureus.install.path="/home/albert/apps/vuze" -Dazureus.script="./vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/albert/apps/vuze/Azureus2.jar ; file:/home/albert/apps/vuze/swt.jar ; file:/home/albert/apps/vuze/
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
DEBUG::Sat Apr 25 01:18:00 EDT 2009::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::69:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (i386).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::110,Main::<init>::84,Main::main::217,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,MainExecutor$1::run::37,Thread::run::636
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:92)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:69)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:217)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
albert@TheDoc:~/vuze$ 

```

So from what I gather, I installed 32bit ver of java...
correct?

---

### Post by Thelasko on 2009-04-27
Try installing
```
sudo apt-get install sun-java6-plugin
```
and see what that does.

Did you install Vuze from the repositories?

---

