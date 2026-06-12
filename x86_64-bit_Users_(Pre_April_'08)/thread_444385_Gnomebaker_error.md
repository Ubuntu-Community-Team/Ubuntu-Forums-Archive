---
title: "Gnomebaker error"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2007-05-15
I just tried running gnomebaker for the first time since i installed it a while ago and i got the following error:

> 
xsx@xsx-desktop:~/Desktop$ gnomebaker

(process:4057): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.


I don't know how that will affect my burning cd's, but it would be nice if I could just fix that so I don't have to worry about it... any ideas?

---

