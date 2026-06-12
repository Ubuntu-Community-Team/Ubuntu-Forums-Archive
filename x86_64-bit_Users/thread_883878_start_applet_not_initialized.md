---
title: "start: applet not initialized"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-08-08
When I go to a website that requires Java I get the message, "start: applet not initialized."  I can get [Java testers]("http://www.java.com/en/download/help/testvm.xml?ff3") to [work fine]("http://www.javatester.org/version.html").  But any [other page]("http://screener.finance.yahoo.com/fscr/us/launch.html") that requires Java gives me the error.  I have OpenJDK installed with the icedtea-gcjwebplugin.

I've found lots of info about users having the same problem in 32-bit.  Their solution is to switch to Sun Java.  Unfortunately, that's not an option for 64-bit.  Does anybody have insight into why this error occurs?

---

### Post by Thelasko on 2008-08-11
bump

---

### Post by philinux on 2008-08-11
[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

Does this site work. It does for me but your link gives same error for me. :confused:

---

### Post by philinux on 2008-08-11
This is what safe mode spits out. I'm using openjdk too. 
[edit]I got it to run after by switching to this plugin java-gcj-compat-plugin, but the applet crashes.


```
firefox -safe-mode
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_Initialize
GCJ PLUGIN: thread 0x622930: plugin_test_appletviewer
GCJ PLUGIN: thread 0x622930: plugin_test_appletviewer return
GCJ PLUGIN: thread 0x622930: NP_Initialize: using /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/../../bin/pluginappletviewer
GCJ PLUGIN: thread 0x622930: NP_Initialize return
GCJ PLUGIN: thread 0x622930: GCJ_New
GCJ PLUGIN: thread 0x622930: plugin_data_new
GCJ PLUGIN: thread 0x622930: plugin_data_new return
GCJ PLUGIN: thread 0x622930: plugin_get_documentbase
GCJ PLUGIN: thread 0x622930: plugin_get_documentbase return
GCJ PLUGIN: thread 0x622930: GCJ_New: creating input fifo: /home/philcb/.gcjwebplugin/gcj-instance-6717-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622930: GCJ_New: created input fifo: /home/philcb/.gcjwebplugin/gcj-instance-6717-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622930: GCJ_New: creating output fifo: /home/philcb/.gcjwebplugin/gcj-instance-6717-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622930: GCJ_New: created output fifo: /home/philcb/.gcjwebplugin/gcj-instance-6717-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622930: plugin_start_appletviewer
GCJ PLUGIN: thread 0x622930: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x622930: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x622930: plugin_create_applet_tag
GCJ PLUGIN: thread 0x622930: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-6717-0
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://screener.finance.yahoo.com/fscr/us/launch.html <EMBED CODE="com.yahoo.finance.screener.ScreenerApplet.class" ARCHIVE="FreeScreener_x.jar" HEIGHT="30" WIDTH="210" CODE="com.yahoo.finance.screener.ScreenerApplet.class" CODEBASE="/fscr" ARCHIVE="FreeScreener_x.jar" ><PARAM NAME="java_codebase" VALUE="/fscr"><PARAM NAME="name" VALUE="fscr"><PARAM NAME="NAME" VALUE="fscr"><PARAM NAME="type" VALUE="application/x-java-applet;version=1.4"><PARAM NAME="scriptable" VALUE="false"><PARAM NAME="QUERYURL" VALUE=""><PARAM NAME="screenerserver" VALUE="reports.finance.yahoo.com"></EMBED>
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: GCJ_New return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: GCJ_GetValue
GCJ PLUGIN: thread 0x622930: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x622930: GCJ_GetValue return
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-6717-0
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 39846822 width 210 height 30
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow return
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-6717-0
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 210
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-6717-0
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 30
GCJ PLUGIN: thread 0x622930: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622930: GCJ_SetWindow return
  PIPE: appletviewer wrote: running
  PIPE: appletviewer read: instance-6717-0
  PIPE: appletviewer read: tag http://screener.finance.yahoo.com/fscr/us/launch.html <EMBED CODE="com.yahoo.finance.screener.ScreenerApplet.class" ARCHIVE="FreeScreener_x.jar" HEIGHT="30" WIDTH="210" CODE="com.yahoo.finance.screener.ScreenerApplet.class" CODEBASE="/fscr" ARCHIVE="FreeScreener_x.jar" ><PARAM NAME="java_codebase" VALUE="/fscr"><PARAM NAME="name" VALUE="fscr"><PARAM NAME="NAME" VALUE="fscr"><PARAM NAME="type" VALUE="application/x-java-applet;version=1.4"><PARAM NAME="scriptable" VALUE="false"><PARAM NAME="QUERYURL" VALUE=""><PARAM NAME="screenerserver" VALUE="reports.finance.yahoo.com"></EMBED>
  PIPE: appletviewer read: instance-6717-0
  PIPE: appletviewer read: handle 39846822 width 210 height 30
Warning: <param name=... value=...> tag requires name attribute.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-6717-0
  PIPE: appletviewer read: width 210
  PIPE: appletviewer read: instance-6717-0
  PIPE: appletviewer read: height 30
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status Applet loaded.
  PIPE: plugin read: status Applet loaded.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet loaded.
**[COLOR="black"][COLOR="Red"]Couldn't load windowns look and feel javax.swing.UnsupportedLookAndFeelException: [The Microsoft Windows Look and Feel - com.sun.java.swing.plaf.windows.WindowsLookAndFeel] not supported on this platform[/COLOR][/COLOR]**
1 6 0
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status exception: java.security.AccessControlException: access denied (java.net.SocketPermission reports.finance.yahoo.com:80 connect,resolve).
  PIPE: plugin read: status exception: java.security.AccessControlException: access denied (java.net.SocketPermission reports.finance.yahoo.com:80 connect,resolve).
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status exception: java.security.AccessControlException: access denied (java.net.SocketPermission reports.finance.yahoo.com:80 connect,resolve).
java.security.AccessControlException: access denied (java.net.SocketPermission reports.finance.yahoo.com:80 connect,resolve)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:342)
	at java.security.AccessController.checkPermission(AccessController.java:553)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:549)
	at java.lang.SecurityManager.checkConnect(SecurityManager.java:1051)
	at sun.net.www.http.HttpClient.openServer(HttpClient.java:528)
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:240)
	at sun.net.www.http.HttpClient.New(HttpClient.java:321)
	at sun.net.www.http.HttpClient.New(HttpClient.java:338)
	at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:806)
	at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:747)
	at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:672)
	at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:997)
	at com.yahoo.finance.screener.ReadUrlData.getContent(ReadUrlData.java:36)
	at com.yahoo.finance.screener.ReadUrlData.getStringData(ReadUrlData.java:25)
	at com.yahoo.finance.screener.ScreenerClient.create(ScreenerClient.java:59)
	at com.yahoo.finance.screener.ScreenerLaunchable.launch(ScreenerLaunchable.java:110)
	at com.yahoo.finance.screener.ScreenerApplet.startApplication(ScreenerApplet.java:60)
	at com.yahoo.finance.screener.ScreenerApplet.init(ScreenerApplet.java:42)
	at sun.applet.AppletPanel.run(AppletPanel.java:436)
	at java.lang.Thread.run(Thread.java:636)
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback: setting status Start: applet not initialized.
  PIPE: plugin read: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622930: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Start: applet not initialized.
```

---

### Post by cariboo on 2008-08-11
I'm just using the standard java and plugins for Intrepid alha 3 and the yahoo site works the way it should here. I'm running 64bit by the way.

I did find something strange the other day though. I have a webcam with a builtin web server, it uses a java applet to view the output of the camera it works the way it should on all the computers running a linux variant, but I have to install an activex applet in windows to get it to work, it just work work in java.

Jim

---

### Post by Thelasko on 2008-08-12
philinux:  Sorry, I didn't get a chance to look at that page last night.  I've tried some [gcj plugins]("http://ubuntuforums.org/showthread.php?t=880764") in the past and none of them worked.  I'm not sure if I've tried the one you posted though.

cariboo907:  How did you do this?  Did you add the Interpid repositories? or did you just install the package?  What packages (specifically) did you install?

---

### Post by Thelasko on 2008-08-12
Philinux:  With that plugin you suggested, it loads the plugin and crashes, just like you said.  Here's the output when I launch Firefox from terminal:
```
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_Initialize
GCJ PLUGIN: thread 0x622930: NP_Initialize: using /usr/bin/gappletviewer-4.2.
GCJ PLUGIN: thread 0x622930: NP_Initialize return
GCJ PLUGIN: thread 0x622930: GCJ_New
GCJ PLUGIN: thread 0x622930: plugin_data_new
GCJ PLUGIN: thread 0x622930: plugin_data_new return
GCJ PLUGIN: thread 0x622930: plugin_get_documentbase
GCJ PLUGIN: thread 0x622930: plugin_get_documentbase return
../../../../../../src/libjava/classpath/native/plugin/gcjwebplugin.cc:978: thread 0x622930: Error: Failed to read line from whitelist file.
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: GCJ_GetValue
GCJ PLUGIN: thread 0x622930: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x622930: GCJ_GetValue return

(firefox:10036): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(firefox:10036): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed

(firefox:10036): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(firefox:10036): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' failed
Segmentation fault

```

---

### Post by Thelasko on 2008-08-12
That think broadband link works fine with OpenJDK.

---

### Post by philinux on 2008-08-18
icedtea-gcjwebplugin 

Install this it works. Uninstall any other java plugin.

It's version 1.0

---

### Post by pbhj on 2008-08-20
> **Thelasko said:**
> cariboo907:  How did you do this?  Did you add the Interpid repositories? or did you just install the package?  What packages (specifically) did you install?

Me too, where-what-how?

---

