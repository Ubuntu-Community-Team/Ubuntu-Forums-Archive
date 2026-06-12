---
title: "Firefox causes soft reboot X86_64bit"
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by schmitty2005 on 2008-07-27
Certain websites browsed with firefox (the latest version as of July 27, 2008) cause my system to reboot into the login screen.  The system is up to date.  

I could not find any information on this bug.  Can anyone help?

AMD 64 2800
VIA chipset
1 GB ram
ATI 9800 Pro
-other useless components.

Thank you.

---

### Post by nikgare on 2008-07-28
Which websites?
Does the machine reboot, or does just X restart

---

### Post by schmitty2005 on 2008-07-29
> **nikgare said:**
> Which websites?
Does the machine reboot, or does just X restart

Just X restarts.  The websites are hit and miss.  One week a certain CNN story with or without video will cause it.  The next time it happens, it crashes, so I don't remeber what website it is.  Hmmmm...  Maybe it is a website with media (sound/music/video/adverts)? That causes the crash.

---

### Post by nikgare on 2008-07-30
This could be another flash problem, in which case maybe upgrading to the latest version of the plugin  might help

---

### Post by philinux on 2008-07-30
Try firefox in safe mode first.

```
firefox -safe-mode
```

This will also report any errors in the terminal.

---

### Post by schmitty2005 on 2008-07-31
> **philinux said:**
> Try firefox in safe mode first.

```
firefox -safe-mode
```

This will also report any errors in the terminal.

brian@LinuxToilet:~$ firefox -safe
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

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:9666): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 200 error_code 182 request_code 155 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection reset by peer

[B]Notice I typed prompt>firefox safe instead of prompt>firefox safe-mode.  I dont' know if they both work for safe mode though.  

Anyways, here is the output. Thank you both for helping.

Here is the link that caused the problem.

[http://www.cnn.com/2008/WORLD/americas/07/31/canada.bus/index.html](http://www.cnn.com/2008/WORLD/americas/07/31/canada.bus/index.html)[/B]

 It caused X to restart.  I logged in, opened the terminal, and typed firefox -safe, and went back to the web-page to get the error data.

ANy suggestions?

---

