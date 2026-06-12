---
title: "Kino Crash"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by queenorych on 2005-10-21
I've just installed Breezy.  Kino consistantly crashes when I lock on the save toolbar or the save menu item.

I installed Hoary's kino, and that works just fine.

Any ideas?

---

### Post by SickBoy on 2005-11-20
Same problem here.

I also tried to compile kino from source and it still crashes as soon as i try to save anything.

---

### Post by queenorych on 2005-11-21
I installed the hoary version for now.  That works just fine.

---

### Post by JuanC on 2005-11-21
My Kino also crash when i try to save file.

---

### Post by SickBoy on 2005-11-26
Kino from hoary seems to work but some plugins freeze the machine.

---

### Post by queenorych on 2005-12-23
Problem is with gtk_file_chooser_dialog_new.  NULL isn't always NULL i guess.  Either recompile with gcc-3.4 or patch kino_common.cc as below.  Let me know if this works so we can try to get the kino package patched

Here's a patch:
--- kino_common.cc.org  2004-10-23 02:00:55.000000000 -0500
+++ kino_common.cc      2005-12-21 21:08:39.000000000 -0600
@@ -844,7 +844,7 @@
                                GTK_FILE_CHOOSER_ACTION_OPEN,
                                GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
                                GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT,
-                               NULL );
+                               (const gchar *) NULL );

        preview = ( GtkDrawingArea* )gtk_drawing_area_new();
        gtk_widget_set_size_request( GTK_WIDGET(preview), 160, 120 );
@@ -919,7 +919,7 @@
                                        GTK_FILE_CHOOSER_ACTION_SAVE,
                                        GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
                                        GTK_STOCK_SAVE, GTK_RESPONSE_ACCEPT,
-                                       NULL);
+                                       (const gchar *) NULL);
        gtk_window_set_modal( GTK_WINDOW( dialog ), TRUE );
        if ( last_directory == "" )
        {

---

### Post by shadowman on 2005-12-27
[QUOTE=queenorych]I installed the hoary version for now.  That works just fine.[/QUOTE]


Ok I've been using ubuntu for only a few weeks.  Since my kino is crashing how do I intall  the hoary version?  Is this something that I do through synaptic?

Thanks

---

### Post by queenorych on 2005-12-28
Here's my patched version.
[http://www.mdobbs.com/download/kino_0.75-7ubuntu2_amd64.deb](http://www.mdobbs.com/download/kino_0.75-7ubuntu2_amd64.deb)

Download and do a "sudo dpkg -i kino_0.75-7ubuntu2_amd64.deb" and viola.

Let me know if it works for you.  I just casted NULL to a (const gchar *).  Get me why you would have to do that.

To get older packages just go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .  Search for kino under the hoary and download the amd64 package.

Then do a "sudo dpkg -i kino-whatever.deb" and viola.

FYI "sudo dpkg -r kino-whatever.deb" to uninstall.  See "man dpkg" for more info.

---

### Post by olafbooij on 2006-04-30
Hi,

I also experienced the same problem when adding a sound file with the FFMPEG Dub plugin.

The following work-around works for me (I didn't feel like patching and compiling, sorry...).

Because the bug seems to be in the file-chooser, avoid using it all together. With the FFMPEG Dub plugin you can directly type in the file. So just search for a file using some other method like the gnome file browser. Find the audio file you want to use and copy paste its path and filename to the plugin-dialogue-window. Press the render-button, and everything works as expected.

I'm using Breezy Badger

Cheers,
Olaf

---

### Post by madflying on 2006-05-05
[QUOTE=queenorych]Here's my patched version.
[http://www.mdobbs.com/download/kino_0.75-7ubuntu2_amd64.deb](http://www.mdobbs.com/download/kino_0.75-7ubuntu2_amd64.deb)

Download and do a "sudo dpkg -i kino_0.75-7ubuntu2_amd64.deb" and viola.

Let me know if it works for you.  I just casted NULL to a (const gchar *).  Get me why you would have to do that.

To get older packages just go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .  Search for kino under the hoary and download the amd64 package.

Then do a "sudo dpkg -i kino-whatever.deb" and viola.

FYI "sudo dpkg -r kino-whatever.deb" to uninstall.  See "man dpkg" for more info.[/QUOTE]

can i use the same package on a no-amd64 or any other no-64bit machines?

Thanks

---

