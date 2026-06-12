---
title: "WebEx on 64-bit Jaunty"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by dgoldssfo on 2009-04-27
Anyone got this working yet? When I try to bring up WebEx, the Java applet downloads, I get the Meeting in Progress screen, the progress bar goes to 100%, and then ... nothing.

I am using JDK 6 with the plug-in. Tried setting JAVA_HOME in my .profile as one of the other threads suggested but no luck.

Thanks in advance for any help with this.

---

### Post by alex.pujols on 2009-05-04
same exact issue here.... here is the dump

ap



java.lang.RuntimeException: Failed to handle message: handle 52485952 Thread[Thread-1,5,main]
    at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:440)
    at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:295)
    at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:72)
Caused by: java.lang.NullPointerException
    at net.sourceforge.jnlp.NetxPanel.isAlive(NetxPanel.java:147)
    at sun.applet.PluginAppletViewer.<init>(PluginAppletViewer.java:313)
    at sun.applet.PluginAppletViewerFactory.createAppletViewer(PluginAppletViewer.java:121)
    at sun.applet.PluginAppletViewer.parse(PluginAppletViewer.java:1604)
    at sun.applet.PluginAppletViewer$7.run(PluginAppletViewer.java:1528)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.applet.PluginAppletViewer.parse(PluginAppletViewer.java:1537)
    at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:414)
    ... 2 more
[JDownload] Java Client Service home:[https://ciscosales.webex.com/client/T26L10NSP49EP26/javaclient/webex/](https://ciscosales.webex.com/client/T26L10NSP49EP26/javaclient/webex/)
[JDownload] Production home: /home/apujols/.webex/824
[CallBackPhoneListMgr]    fileName:/home/apujols/.webex/callbacknumber.bak
[CallBackPhoneListMgr]label1:Alternate phone 1
chat component version = 2008.04.15.0051
Resource: atlchat
Resource: atlchat_en
Resource: atlchat_en_US
Exception in thread "Thread-40" java.lang.UnsatisfiedLinkError: /home/apujols/.webex/824/libatdv.so: /home/apujols/.webex/824/libatdv.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at JNRW.<init>(JNRW.java:33)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at java.lang.Class.newInstance0(Class.java:372)
    at java.lang.Class.newInstance(Class.java:325)
    at jDocView.CreateDocViewUI(jDocView.java:470)
    at jDocView.PDNewInstance(jDocView.java:3797)
    at MeetingClientFrame.<init>(MeetingClientFrame.java:271)
    at jmeetingclient.connectToMeeting(jmeetingclient.java:448)
    at jmeetingclient.init(jmeetingclient.java:398)
    at JDownload.run(JDownload.java:233)
    at java.lang.Thread.run(Thread.java:636)

---

### Post by aadam12 on 2009-05-14
Same issue. Also don't load 64-bit Java plug-in into 32-bit Firefox. It crashes Firefox.

---

### Post by pixel :-) on 2009-05-14
JDK is still incomplete

this is 32bit java

sudo apt-get install sun-java6-plugin ia32-sun-java6-bin

sudo update-alternatives --config java

and uninstall icedtea-6plugin

and restart firefox

If you whant you can also try sun-java6-bin it 64 bit java from java corp, it's buggy. You pass from one to an other with update alternatives command above.

---

### Post by herda05 on 2009-10-29
Gone through all the java's on my machine:
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java
 +        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          6    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          7    /usr/lib/j2sdk1.6-sun/bin/java
          8    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

But they all give 404 not found when I start a webex session. Anyone have a workaround for this?

---

### Post by empty_spaces on 2009-10-29
My workaround for Webex is Windows XP in Virtualbox

---

