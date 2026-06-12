---
title: "xsession-errors"
date: 2009-07-15
forum: x86 64-bit Users
---

### Post by tondofear on 2009-07-15
I'm a newbie in linux word, can someone tell what are this errors i have in my system and how can i fix this:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_PH.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-ZYdGDR/socket
SSH_AUTH_SOCK=/tmp/keyring-ZYdGDR/socket.ssh

(gnome-settings-daemon:14681): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:14681): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(at-spi-registryd-wrapper:14671): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(at-spi-registryd-wrapper:14671): atk-bridge-WARNING **: IOR not set.

(at-spi-registryd-wrapper:14671): atk-bridge-WARNING **: Could not locate registry
x-session-manager[14583]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup.
x-session-manager[14583]: atk-bridge-WARNING: IOR not set.
x-session-manager[14583]: atk-bridge-WARNING: Could not locate registry
** (gnome-panel:14693): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:14693): DEBUG: Adding applet 0.
Conky: desktop window (13c) is root window
Conky: window type - normal
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer
x-session-manager[14583]: WARNING: Could not launch application '10f35706dbeec31faf124765316172829300000134670021.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
** (gnome-panel:14693): DEBUG: Adding applet 1.
** (gnome-panel:14693): DEBUG: Adding applet 2.
** (gnome-panel:14693): DEBUG: Adding applet 3.
** (gnome-panel:14693): DEBUG: Adding applet 4.
** (nm-applet:14711): DEBUG: applet_common_device_state_changed
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

** (update-notifier:14722): WARNING **: already running?

[1;38mwarning : [0m [0;37m(cairo-dock-modules.c:cairo_dock_preload_module_from_directory:327) [0m 
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
evolution-alarm-notify-Message: Setting timeout for 48461 1247702400 1247653939
evolution-alarm-notify-Message:  Thu Jul 16 08:00:00 2009

evolution-alarm-notify-Message:  Wed Jul 15 18:32:19 2009

gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 3.0.0 NVIDIA 180.44
OpenGL vendor: NVIDIA Corporation
OpenGL renderer: GeForce 8500 GT/PCI/SSE2

** (nautilus:14694): WARNING **: Unable to add monitor: Not supported
[DEBUG]: NoteManager created with note path "/home/tondofear/.tomboy".
[INFO]: Initializing Mono.Addins
g_strsplit: assertion `string != NULL' failed
if your drivers are crappy, we'll know it immediately ...** (gnome-panel:14693): DEBUG: Adding applet 5.
 ok, they seem fine enough.
[1;38mwarning : [0m [0;37m(cairo-dock-config.c:cairo_dock_get_double_key_value:172) [0m 
  Key file does not have key 'scroll speed'
[1;38mwarning : [0m [0;37m(cairo-dock-config.c:cairo_dock_get_double_key_value:172) [0m 
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
cairo_dock_replace_key_values (0)
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/dialog-rendering/dialog-rendering.conf)
cairo_dock_replace_key_values (0)
g_key_file_has_key: assertion `key_file != NULL' failed
[1;38mwarning : [0m [0;37m(cairo-dock-keyfile-utilities.c:cairo_dock_flush_conf_file_full:72) [0m 
  Couldn't find any installed conf file
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/drop_indicator/drop_indicator.conf)
cairo_dock_replace_key_values (0)
[DEBUG]:            Name: Tomboy.Tomboy,0.10
[DEBUG]:     Description: 
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/Tomboy.exe
** (gnome-panel:14693): DEBUG: Adding applet 6.
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/Cairo-Penguin/Cairo-Penguin.conf)
cairo_dock_replace_key_values (0)
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/quick-browser/quick-browser.conf)
cairo_dock_replace_key_values (0)
** (gnome-panel:14693): DEBUG: Adding applet 7.
** (gnome-panel:14693): DEBUG: Adding applet 8.
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/quick-browser/quick-browser.conf)
cairo_dock_replace_key_values (0)

(gnome-panel:14693): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/illusion/illusion.conf)
cairo_dock_replace_key_values (0)
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/show_mouse/show_mouse.conf)
cairo_dock_replace_key_values (0)
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/Animated-icons/Animated-icons.conf)
cairo_dock_replace_key_values (0)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/motion_blur/motion_blur.conf)
cairo_dock_replace_key_values (0)
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/Dbus/Dbus.conf)
cairo_dock_replace_key_values (0)
cairo_dock_replace_values_in_conf_file (/home/tondofear/.config/cairo-dock/current_theme/plug-ins/icon-effect/icon-effect.conf)
cairo_dock_replace_key_values (0)
** (gnome-panel:14693): DEBUG: Adding applet 9.
n'est pas un directory, menu_path : /
inotify_add_watch: No such file or directory
n'est pas un directory, menu_path : /
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]:            Name: Evolution Mail Integration
[DEBUG]:     Description: Allows you to drag an email from Evolution into a tomboy note.  The message subject is added as a link in the note.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]:            Name: Printing Support
[DEBUG]:     Description: Allows you to print a note.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]:            Name: Backlinks
[DEBUG]:     Description: See which notes link to the one you're currently viewing.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]:            Name: Fixed Width
[DEBUG]:     Description: Adds fixed-width font style.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]:            Name: Export to HTML
[DEBUG]:     Description: Exports individual notes to HTML.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]:            Name: Sticky Notes Importer
[DEBUG]:     Description: Import your notes from the Sticky Notes applet.
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]:            Name: WebDav Sync Service Add-in
[DEBUG]:     Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]:            Name: Local Directory Sync Service Add-in
[DEBUG]:     Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]:       Namespace: Tomboy
[DEBUG]:         Enabled: True
[DEBUG]:            File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
evolution-alarm-notify-Message: Setting timeout for 48433 1247702400 1247653967
evolution-alarm-notify-Message:  Thu Jul 16 08:00:00 2009

evolution-alarm-notify-Message:  Wed Jul 15 18:32:47 2009


(evolution-alarm-notify:14700): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
cairo_dock_duplicate_surface (96.00x96.00 -> 96.00x96.00)
on positionne la miniature de Firefox 
on met a jour de force
** (update-notifier:14713): DEBUG: /usr/lib/update-notifier/apt-check returned 12 (security: 4)
** (update-notifier:14713): DEBUG: crashreport_check

on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
on met a jour de force
cairo_dock_duplicate_surface (96.00x96.00 -> 96.00x96.00)

--- Hash table keys for warning below:
--> file:///home/tondofear/.fonts

(nautilus:14694): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:14694): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
+ cairo_dock_on_button_press (4/1)
+ cairo_dock_on_button_press (7/1)
+ cairo_dock_notification_click_icon (tondofear)
no action here

** (nautilus:15788): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

on met a jour de force
on met a jour de force

---

### Post by Yellow Pasque on 2009-07-15
Are you experiencing issues because of these errors/warnings? If not, I would not recommend making changes.

You could add your user to the pulse-rt group (System -> Administration -> Users and Groups)

> (gnome-settings-daemon:14681): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
(gnome-settings-daemon:14681): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
I have the same errors on my jaunty and karmic installs.

---

