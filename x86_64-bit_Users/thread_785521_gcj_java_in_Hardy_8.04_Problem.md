---
title: "gcj java in Hardy 8.04 Problem"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by bazcor on 2008-05-07
Hello.. I have a problem with java in hardy 8.04 64 bit. The test page at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) just shows a grey square.


Firefox 3 in about:plugins shows :-
GCJ Web Browser Plugin (using IcedTea) 1.0 followed by about 20 instances of the plugin (using icedtea) all enabled.

This is a new install of hardy, and I don't think a reinstall would acheive anything, as it never worked immediately after install(and install of GCJ icedtea).

Any suggestions or comments would be very much appreciated.

Thanks in anticipation ... Barry

---

### Post by philinux on 2008-05-07
Same here.

Messages 
Starting applet
Applet loaded.
Start: applet not initialized

I've tried all combinations of plugins etc. Other sites work though.

---

### Post by philinux on 2008-05-07
Ran firefox from the terminal. Looks like a problem from java but not the plugin. I'm no expert on this.


```
GCJ PLUGIN: thread 0x622910: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622910: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622910: NP_GetValue
GCJ PLUGIN: thread 0x622910: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622910: NP_GetValue return
GCJ PLUGIN: thread 0x622910: NP_GetValue
GCJ PLUGIN: thread 0x622910: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622910: NP_GetValue return
GCJ PLUGIN: thread 0x622910: NP_Initialize
GCJ PLUGIN: thread 0x622910: plugin_test_appletviewer
GCJ PLUGIN: thread 0x622910: plugin_test_appletviewer return
GCJ PLUGIN: thread 0x622910: NP_Initialize: using /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/../../bin/pluginappletviewer
GCJ PLUGIN: thread 0x622910: NP_Initialize return
GCJ PLUGIN: thread 0x622910: GCJ_New
GCJ PLUGIN: thread 0x622910: plugin_data_new
GCJ PLUGIN: thread 0x622910: plugin_data_new return
GCJ PLUGIN: thread 0x622910: plugin_get_documentbase
GCJ PLUGIN: thread 0x622910: plugin_get_documentbase return
GCJ PLUGIN: thread 0x622910: GCJ_New: creating input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: created input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: creating output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: created output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: plugin_start_appletviewer
GCJ PLUGIN: thread 0x622910: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x622910: plugin_create_applet_tag
GCJ PLUGIN: thread 0x622910: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-0
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaCom.class" CODEBASE="../../../applet" HEIGHT="250" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_New return
  PIPE: appletviewer wrote: running
  PIPE: appletviewer read: instance-11368-0
GCJ PLUGIN: thread 0x622910: NP_GetValue
GCJ PLUGIN: thread 0x622910: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622910: NP_GetValue return
GCJ PLUGIN: thread 0x622910: GCJ_GetValue
GCJ PLUGIN: thread 0x622910: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x622910: GCJ_GetValue return
  PIPE: appletviewer read: tag http://www.java.com/en/download/help/testvm.xml?ff3 <EMBED CODE="testvmDynamicJavaCom.class" CODEBASE="../../../applet" HEIGHT="250" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-0
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 58720981 width 390 height 250
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-0
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 390
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-0
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 250
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow return
  PIPE: appletviewer read: instance-11368-0
  PIPE: appletviewer read: handle 58720981 width 390 height 250
GCJ PLUGIN: thread 0x622910: GCJ_New
GCJ PLUGIN: thread 0x622910: plugin_data_new
GCJ PLUGIN: thread 0x622910: plugin_data_new return
GCJ PLUGIN: thread 0x622910: plugin_get_documentbase
GCJ PLUGIN: thread 0x622910: plugin_get_documentbase return
GCJ PLUGIN: thread 0x622910: GCJ_New: creating input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: created input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: creating output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: created output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: plugin_start_appletviewer
GCJ PLUGIN: thread 0x622910: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x622910: plugin_create_applet_tag
GCJ PLUGIN: thread 0x622910: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-1
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://www.java.com/en/download/help/testvm.xml <EMBED CODE="testvmDynamicJavaCom.class" CODEBASE="../../../applet" HEIGHT="250" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_New return
GCJ PLUGIN: thread 0x622910: NP_GetValue
GCJ PLUGIN: thread 0x622910: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622910: NP_GetValue return
GCJ PLUGIN: thread 0x622910: GCJ_GetValue
GCJ PLUGIN: thread 0x622910: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x622910: GCJ_GetValue return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-1
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 58720984 width 390 height 250
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-1
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 390
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-11368-1
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 250
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: GCJ_SetWindow return
  PIPE: appletviewer wrote: running
  PIPE: appletviewer read: instance-11368-1
  PIPE: appletviewer read: tag http://www.java.com/en/download/help/testvm.xml <EMBED CODE="testvmDynamicJavaCom.class" CODEBASE="../../../applet" HEIGHT="250" WIDTH="390" ><PARAM NAME="alt" VALUE="Java Runtime Environment is not working on your system"><PARAM NAME="border" VALUE="0"></EMBED>
  PIPE: appletviewer read: instance-11368-1
  PIPE: appletviewer read: handle 58720984 width 390 height 250
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-11368-0
  PIPE: appletviewer read: width 390
  PIPE: appletviewer read: instance-11368-0
  PIPE: appletviewer read: height 250
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-11368-1
  PIPE: appletviewer read: width 390
  PIPE: appletviewer read: instance-11368-1
  PIPE: appletviewer read: height 250
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status Applet loaded.
  PIPE: plugin read: status Applet loaded.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet loaded.
TestVM 4.18 sc
Copyright (c) 2008 Sun Microsystems, Inc.
All Rights Reserved.
Current JRE version set in file: 605
  PIPE: appletviewer wrote: status exception: java.lang.NumberFormatException: For input string: " ".
java.lang.NumberFormatException: For input string: " "
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
	at java.lang.Integer.parseInt(Integer.java:470)
	at java.lang.Integer.<init>(Integer.java:636)
	at testvmDynamicJavaCom.init(testvmDynamicJavaCom.java:195)
	at sun.applet.AppletPanel.run(AppletPanel.java:436)
	at java.lang.Thread.run(Thread.java:636)
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status exception: java.lang.NumberFormatException: For input string: " ".
  PIPE: plugin read: status exception: java.lang.NumberFormatException: For input string: " ".
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status Start: applet not initialized.
  PIPE: plugin read: status Start: applet not initialized.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Stop: applet not started.
  PIPE: appletviewer wrote: status Destroy: applet not stopped.
  PIPE: appletviewer wrote: status Dispose: applet not destroyed.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status Stop: applet not started.
  PIPE: plugin read: status Stop: applet not started.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status Destroy: applet not stopped.
  PIPE: plugin read: status Destroy: applet not stopped.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback: setting status Dispose: applet not destroyed.
  PIPE: plugin read: status Dispose: applet not destroyed.
GCJ PLUGIN: thread 0x622910: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x622910: GCJ_Destroy
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: appletviewer read: destroy
  PIPE: plugin wrote: destroy
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_stop_appletviewer
GCJ PLUGIN: thread 0x622910: plugin_stop_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_data_destroy
GCJ PLUGIN: thread 0x622910: GCJ_New: deleting output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: deleted output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: deleting input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: deleted input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-1-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: plugin_data_destroy return
GCJ PLUGIN: thread 0x622910: GCJ_Destroy return
GCJ PLUGIN: thread 0x622910: GCJ_Destroy
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer
  PIPE: appletviewer read: destroy
  PIPE: plugin wrote: destroy
GCJ PLUGIN: thread 0x622910: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_stop_appletviewer
GCJ PLUGIN: thread 0x622910: plugin_stop_appletviewer return
GCJ PLUGIN: thread 0x622910: plugin_data_destroy
GCJ PLUGIN: thread 0x622910: GCJ_New: deleting output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: deleted output fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x622910: GCJ_New: deleting input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: GCJ_New: deleted input fifo: /home/philcb/.gcjwebplugin/gcj-instance-11368-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x622910: plugin_data_destroy return
GCJ PLUGIN: thread 0x622910: GCJ_Destroy return
GCJ PLUGIN: thread 0x622910: NP_Shutdown
GCJ PLUGIN: thread 0x622910: NP_Shutdown return
  PIPE: appletviewer read: shutdown
APPLETVIEWER: exiting appletviewer
  PIPE: appletviewer read: shutdown
APPLETVIEWER: exiting appletviewer
```

---

### Post by tighem on 2008-05-07
Sun's test page doesn't work, but I've noticed other Java applet pages load just fine.

---

### Post by philinux on 2008-05-07
> **tighem said:**
> Sun's test page doesn't work, but I've noticed other Java applet pages load just fine.

Yes same here, interesting this, but why?

---

### Post by jazzman65 on 2008-05-07
I've had the same experience.  Sun's test page doesn't work, but others do.

---

### Post by Kilz on 2008-05-07
> **philinux said:**
> Yes same here, interesting this, but why?

Because gcj java is not Sun Java. Sun is in the business of making sure Sun Java is used. gcj java could probably care less if the java test on sun works as long as the java plugin does.

---

### Post by Naguz on 2008-05-23
> **Kilz said:**
> Because gcj java is not Sun Java. Sun is in the business of making sure Sun Java is used. gcj java could probably care less if the java test on sun works _as long as the java plugin does_.
Too bad then, that when the java test on sun doesn't work, that means the plugin doesn't either. Which you can see for yourself if you try various betting or banking sites which either use java, or has a java-based login.

The open plugin is, as of now, worth ****. Too bad that there is no real working 64 or 32 bit alternative for 64 bit. After testing out umpteen different hints and tips in these forums and other forums I guess I just have to face the fact that ubuntu 64 bit is not ready yet.

---

### Post by jespdj on 2008-05-24
> **Naguz said:**
> The open plugin is, as of now, worth ****. Too bad that there is no real working 64 or 32 bit alternative for 64 bit. After testing out umpteen different hints and tips in these forums and other forums I guess I just have to face the fact that ubuntu 64 bit is not ready yet.
The 64-bit OpenJDK plug-in (which is from Sun, and not from GNU) is not working 100% yet. As far as I know there are also some problems with Java and Compiz. Try switching off Compiz and see if you can see the GUI instead if just a gray box.

Concluding that Ubuntu isn't 64-bit ready yet just because of these minor problems goes a bit far. In my opinion, especially 64-bit Hardy works really well.

Note that if you really can't get it to work, you can install a 32-bit browser and 32-bit Java on your 64-bit system.

---

