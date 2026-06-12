---
title: "Gnome-Do crashing when run"
date: 2009-06-28
forum: x86 64-bit Users
---

### Post by daygan on 2009-06-28
Last night I installed a number of new applications, and then uninstalled some of those in addition to other applications... sometime in the middle of all this Gnome-Do suddenly stopped working for me and I'm not sure why.

I am using Ubuntu 8.10 64-bit, and my Gnome-Do was 0.8.1. Specifically what was(and is) happening was that Gnome-Do just crashes as soon as I try to start it up. I have it set to the Docky format, and my windows will adjust to allow for it to fit on the bottom of the screen, the icon will appear in the system tray for a moment, and then it will just disappear.

I ran "gnome-do --debug" and this is what came out(sorry for the length):

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:18276): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Stacktrace:

  at (wrapper managed-to-native) Gdk.CairoHelper.gdk_cairo_set_source_pixbuf (intptr,intptr,double,double) <0x0006d>
  at (wrapper managed-to-native) Gdk.CairoHelper.gdk_cairo_set_source_pixbuf (intptr,intptr,double,double) <0xffffffff>
  at Gdk.CairoHelper.SetSourcePixbuf (Cairo.Context,Gdk.Pixbuf,double,double) <0x00083>
  at Docky.Interface.ClockDockItem.RenderFileOntoContext (Cairo.Context,string,int) <0x0005f>
  at Docky.Interface.ClockDockItem.MakeIconSurface (Cairo.Surface,int) <0x00143>
  at Docky.Interface.AbstractDockItem.GetIconSurface (Cairo.Surface,int,int&) <0x00115>
  at Docky.Interface.DockArea.DrawIcon (Cairo.Context,int,bool) <0x00ed3>
  at Docky.Interface.DockArea.DrawIcons (Cairo.Context,Gdk.Rectangle) <0x012ef>
  at Docky.Interface.DockArea.DrawDock (Cairo.Context) <0x007c7>
  at Docky.Interface.DockArea.OnExposeEvent (Gdk.EventExpose) <0x00393>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x0007a>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x0004d>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000b>
  at Do.Do.Main (string[]) <0x002d7>
  at (wrapper runtime-invoke) Do.Do.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x429e65]
	mono [0x44ba8d]
	/lib/libpthread.so.0 [0x7f445d5340f0]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_cairo_set_source_pixbuf+0x100) [0x7f445b9bd400]
	[0x40694cfd]

Debug info from gdb:

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f445e215720 (LWP 18276)]
[New Thread 0x416a4950 (LWP 18286)]
[New Thread 0x4055e950 (LWP 18284)]
[New Thread 0x4033d950 (LWP 18278)]
[New Thread 0x41ff1950 (LWP 18277)]
0x00007f445d532f4b in read () from /lib/libpthread.so.0
  5 Thread 0x41ff1950 (LWP 18277)  0x00007f445d533851 in nanosleep ()
   from /lib/libpthread.so.0
  4 Thread 0x4033d950 (LWP 18278)  0x00007f445d5302d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  3 Thread 0x4055e950 (LWP 18284)  0x00007f445d006d4b in read ()
   from /lib/libc.so.6
  2 Thread 0x416a4950 (LWP 18286)  0x00007f445d533851 in nanosleep ()
   from /lib/libpthread.so.0
  1 Thread 0x7f445e215720 (LWP 18276)  0x00007f445d532f4b in read ()
   from /lib/libpthread.so.0

Thread 5 (Thread 0x41ff1950 (LWP 18277)):
#0  0x00007f445d533851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005108f2 in ?? ()
#2  0x00007f445d52c3ea in start_thread () from /lib/libpthread.so.0
#3  0x00007f445d014cbd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x4033d950 (LWP 18278)):
#0  0x00007f445d5302d9 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x0000000000505bb5 in ?? ()
#2  0x000000000050832f in ?? ()
#3  0x00000000004fcf1d in ?? ()
#4  0x00000000004bd303 in ?? ()
#5  0x00000000004b9f53 in ?? ()
#6  0x000000000050952b in ?? ()
#7  0x000000000052a382 in ?? ()
#8  0x00007f445d52c3ea in start_thread () from /lib/libpthread.so.0
#9  0x00007f445d014cbd in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x4055e950 (LWP 18284)):
#0  0x00007f445d006d4b in read () from /lib/libc.so.6
#1  0x000000004103d30a in ?? ()
#2  0x0000000002584f40 in ?? ()
#3  0x0000000000080000 in ?? ()
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x416a4950 (LWP 18286)):
#0  0x00007f445d533851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005089ab in ?? ()
#2  0x00000000004b957e in ?? ()
#3  0x0000000040cb30b8 in ?? ()
#4  0x00000000033df5c0 in ?? ()
#5  0x00000000033df5c0 in ?? ()
#6  0x00007f445764c620 in ?? ()
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f445e215720 (LWP 18276)):
#0  0x00007f445d532f4b in read () from /lib/libpthread.so.0
#1  0x0000000000429f6c in ?? ()
#2  0x000000000044ba8d in ?? ()
#3  <signal handler called>
#4  IA__gdk_cairo_set_source_pixbuf (cr=0x3686000, 
    pixbuf=<value optimized out>, pixbuf_x=0, pixbuf_y=0)
    at /build/buildd/gtk+2.0-2.14.4/gdk/gdkcairo.c:210
#5  0x0000000040694cfd in ?? ()
#6  0x00007fff662341c0 in ?? ()
#7  0x0000000003686000 in ?? ()
#8  0x0000000003576270 in ?? ()
#9  0x0000000000000001 in ?? ()
#10 0x0000000003686000 in ?? ()
#11 0x0000000000000000 in ?? ()
#0  0x00007f445d532f4b in read () from /lib/libpthread.so.0

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

So, can anyone help me out with this? It was working before, but now it's not, so I guess I need to figure out what I did to my system that caused this to happen. another interesting fact is that Gnome-Do 0.8.0 works fine, but there are too many bugs in that release for it to be acceptable to me...

---

### Post by daygan on 2009-06-29
This is the latest output from gnome-do --debug:

Assembly not found: evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df
WARNING: [Do.Evolution,1.2] Could not load some add-in assemblies: The classes in the module cannot be loaded.
[Debug 03:02:49.719] [SystemService] Using org.freedesktop.PowerManager for battery information
[Info  03:02:49.731] [Services] Successfully located service of type ILogService.
[Info  03:02:49.731] [Services] Successfully located service of type IPreferencesService.
[Info  03:02:49.736] [Services] Successfully located service of type ISecurePreferencesService.
[Info  03:02:49.746] [Services] Successfully located service of type INotificationsService.
[Debug 03:02:49.755] [InterfaceManager] "Classic" interface was loaded
[Info  03:02:49.759] [Services] Successfully located service of type ILogService.
[Debug 03:02:49.759] [InterfaceManager] "Docky" interface was loaded
[Debug 03:02:49.760] [InterfaceManager] "Nouveau" interface was loaded
[Debug 03:02:49.762] [InterfaceManager] "Glass" interface was loaded
[Debug 03:02:49.763] [InterfaceManager] "Mini" interface was loaded
[Debug 03:02:49.768] [PluginManager] Loaded "ApplicationItemSource" from plugin.
[Debug 03:02:49.769] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Info  03:02:49.774] [Services] Successfully located service of type AbstractApplicationService.
[Debug 03:02:49.778] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 03:02:49.778] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Debug 03:02:49.780] [PluginManager] Loaded "EmailAction" from plugin.
[Debug 03:02:49.781] [PluginManager] Loaded "OpenAction" from plugin.
[Debug 03:02:49.787] [PluginManager] Loaded "OpenUrlAction" from plugin.
[Debug 03:02:49.788] [PluginManager] Loaded "OpenWithAction" from plugin.
[Debug 03:02:49.788] [PluginManager] Loaded "RevealAction" from plugin.
[Debug 03:02:49.788] [PluginManager] Loaded "RunAction" from plugin.
[Debug 03:02:49.789] [PluginManager] Loaded "CopyToClipboardAction" from plugin.
[Info  03:02:49.792] [Services] Successfully located service of type AbstractSystemService.
[Debug 03:02:49.794] [SystemService] No other application instance detected. Continue startup.
[Info  03:02:49.807] [Services] Successfully located service of type IPreferencesService.
[Info  03:02:49.807] [Services] Successfully located service of type ISecurePreferencesService.
[Debug 03:02:49.848] [Controller] Setting theme Docky
[Info  03:02:49.910] [Services] Successfully located service of type PathsService.

(Do:25822): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Info  03:02:50.106] [Services] Successfully located service of type ICoreService.
[Info  03:02:50.113] [Services] Successfully located service of type INetworkService.
[Info  03:02:50.324] [UniverseManager] Reloading universe...
[Debug 03:02:50.325] [UniverseManager] Reloading actions...
[Debug 03:02:50.334] [UniverseManager] Reloading item source "Applications"...
[Debug 03:02:50.855] [UniverseManager] Reloading item source "GNOME Special Locations"...
[Debug 03:02:50.877] [UniverseManager] Reloading item source "Internal GNOME Do Items"...
[Debug 03:02:50.879] [UniverseManager] Reloading item source "GNOME Do Item Sources"...
[Info  03:02:50.884] [UniverseManager] Universe contains 232 items.
[Info  03:02:51.991] [Services] Successfully located service of type IUniverseFactoryService.
[Error 03:02:52.074] [ItemsService] Could not add custom item with id: /usr/bin/alacarte-made.desktop, File already exists
[Debug 03:02:53.315] [RelevanceProvider] Successfully loaded learned usage data.

(Do:25822): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:25822): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:25822): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:25822): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(Do:25822): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Stacktrace:

  at (wrapper managed-to-native) Gdk.CairoHelper.gdk_cairo_set_source_pixbuf (intptr,intptr,double,double) <0x0006d>
  at (wrapper managed-to-native) Gdk.CairoHelper.gdk_cairo_set_source_pixbuf (intptr,intptr,double,double) <0xffffffff>
  at Gdk.CairoHelper.SetSourcePixbuf (Cairo.Context,Gdk.Pixbuf,double,double) <0x00083>
  at Docky.Interface.ClockDockItem.RenderFileOntoContext (Cairo.Context,string,int) <0x0005f>
  at Docky.Interface.ClockDockItem.MakeIconSurface (Cairo.Surface,int) <0x00147>
  at Docky.Interface.AbstractDockItem.GetIconSurface (Cairo.Surface,int,int&) <0x00115>
  at Docky.Interface.DockArea.DrawIcon (Cairo.Context,int,bool) <0x00ed3>
  at Docky.Interface.DockArea.DrawIcons (Cairo.Context,Gdk.Rectangle) <0x012ef>
  at Docky.Interface.DockArea.DrawDock (Cairo.Context) <0x007cf>
  at Docky.Interface.DockArea.OnExposeEvent (Gdk.EventExpose) <0x0039b>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x0007a>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x0004d>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000b>
  at Do.Do.Main (string[]) <0x002d7>
  at (wrapper runtime-invoke) Do.Do.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x429e65]
	mono [0x44ba8d]
	/lib/libpthread.so.0 [0x7f76abcfe0f0]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_cairo_set_source_pixbuf+0x100) [0x7f76aa191400]
	[0x4073badd]

Debug info from gdb:

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f76ac9de720 (LWP 25822)]
[New Thread 0x404e3950 (LWP 25832)]
[New Thread 0x40735950 (LWP 25830)]
[New Thread 0x40e06950 (LWP 25824)]
[New Thread 0x40144950 (LWP 25823)]
0x00007f76abcfcf4b in read () from /lib/libpthread.so.0
  5 Thread 0x40144950 (LWP 25823)  0x00007f76abcfd851 in nanosleep () from /lib/libpthread.so.0
  4 Thread 0x40e06950 (LWP 25824)  0x00007f76abcfa2d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  3 Thread 0x40735950 (LWP 25830)  0x00007f76ab7d0d4b in read () from /lib/libc.so.6
  2 Thread 0x404e3950 (LWP 25832)  0x00007f76abcfd851 in nanosleep () from /lib/libpthread.so.0
  1 Thread 0x7f76ac9de720 (LWP 25822)  0x00007f76abcfcf4b in read () from /lib/libpthread.so.0

Thread 5 (Thread 0x40144950 (LWP 25823)):
#0  0x00007f76abcfd851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005108f2 in ?? ()
#2  0x00007f76abcf63ea in start_thread () from /lib/libpthread.so.0
#3  0x00007f76ab7decbd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x40e06950 (LWP 25824)):
#0  0x00007f76abcfa2d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x0000000000505bb5 in ?? ()
#2  0x000000000050832f in ?? ()
#3  0x00000000004fcf1d in ?? ()
#4  0x00000000004bd303 in ?? ()
#5  0x00000000004b9f53 in ?? ()
#6  0x000000000050952b in ?? ()
#7  0x000000000052a382 in ?? ()
#8  0x00007f76abcf63ea in start_thread () from /lib/libpthread.so.0
#9  0x00007f76ab7decbd in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x40735950 (LWP 25830)):
#0  0x00007f76ab7d0d4b in read () from /lib/libc.so.6
#1  0x000000004088e40a in ?? ()
#2  0x00000000018841a0 in ?? ()
#3  0x0000000000080000 in ?? ()
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x404e3950 (LWP 25832)):
#0  0x00007f76abcfd851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005089ab in ?? ()
#2  0x00000000004b957e in ?? ()
#3  0x0000000041f478a8 in ?? ()
#4  0x0000000001f7f510 in ?? ()
#5  0x0000000001f7f510 in ?? ()
#6  0x00007f769a77e3a0 in ?? ()
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f76ac9de720 (LWP 25822)):
#0  0x00007f76abcfcf4b in read () from /lib/libpthread.so.0
#1  0x0000000000429f6c in ?? ()
#2  0x000000000044ba8d in ?? ()
#3  <signal handler called>
#4  IA__gdk_cairo_set_source_pixbuf (cr=0x2134590, pixbuf=<value optimized out>, pixbuf_x=0, pixbuf_y=0) at /build/buildd/gtk+2.0-2.14.4/gdk/gdkcairo.c:210
#5  0x000000004073badd in ?? ()
#6  0x00007fffb49fe940 in ?? ()
#7  0x0000000000000000 in ?? ()
#0  0x00007f76abcfcf4b in read () from /lib/libpthread.so.0

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


So, any solutions out there? or should I be posting this question in a different forum?

---

### Post by daygan on 2009-06-29
Well, never mind - I fixed it myself. After uninstalling gnome-do via package manager, I then deleted all remaining gnome-do folders and files in my file system, restarted, and then after that I was able to install successfully via the 0.8.1 deb file. So now things are fine.

---

