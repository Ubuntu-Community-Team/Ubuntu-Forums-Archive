---
title: "Hulu just stopped working"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-10-29
When I run firefox from the command line I get the following output.
```
(npviewer.bin:23519): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()

(npviewer.bin:23519): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
```
I have an Intel 965 on board graphics card and Flash 10 installed with Kilz's script.
Edit: All other flash works.
Edit: This is for Hardy Heron

---

### Post by Thelasko on 2008-10-29
I just restated Firefox and Xserver crashed.  WTF?  I'm going to let it run and see if things smooth out.  I think this is related to some updates I received today.

---

### Post by Thelasko on 2008-10-30
After restarting my machine I was finally able to get Hulu to work.  The player was much slower than normal.  I walked away and a few minutes later the video started playing.  Clicking on buttons seem to have a delayed reaction and full screen is less than smooth.  I was able to watch full screen before and it was very smooth.

---

### Post by Thelasko on 2008-10-30
I tried running an older version of the Intel driver and that didn't fix it.  Anybody know how to remove flash 10?  It's not in synaptic.

---

### Post by Thelasko on 2008-11-01
I found the remove script and got rid of Flash 10.  I even forced the older version of Flash 9.  It seems that Flash 9 performs better on my machine.  I can once again move my mouse without the full screen video freezing.  However, it still takes quite a while for the Flash video to load.  This is very odd.

---

