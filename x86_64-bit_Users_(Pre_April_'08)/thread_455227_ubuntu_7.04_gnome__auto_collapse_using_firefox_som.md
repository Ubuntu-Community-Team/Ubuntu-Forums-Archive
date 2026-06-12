---
title: "ubuntu 7.04 gnome  auto collapse using firefox sometimes"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by hairuo on 2007-05-26
$ uname -a
Linux hairuo 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux 

#######################################

my ubuntu 7.04 gnome  collapse often when  using firefox sometimes, it came back to the welcome screen, as we do ctrl+Alt+BackSpace during gnome.
anyonw can help me? thanks a lot!

######################################

my computer consist of:
AMD Athlon 64 X2 3600+
AN52
DDR2 667 1GB
Nvidia 7300GT 256M 

####################################
there are my history log below:
####################################

/var/log/$cat syslog

gdm_slave_xioerror_handler: Fatal X error - Restarting :0



##################################
/etc/log/syslog

May 19 19:56:42 hairuo gconfd (cbg-6428): Resolved address "xml:readwrite:/home/cbg/.gconf" to a writable configuration source at position 0
May 19 19:56:46 hairuo NetworkManager: <information>^IUpdating allowed wireless network lists.
May 19 19:56:47 hairuo NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
May 19 20:01:33 hairuo gconfd (cbg-6428): Received signal 15, shutting down cleanly
May 19 20:01:37 hairuo gconfd (cbg-6428): Exiting
May 19 20:01:37 hairuo gdm[6357]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May 19 20:01:47 hairuo gdm[6761]: gdm_auth_user_add: /home/cbg/.Xauthority has wrong permissions (should be 0600)
May 19 20:01:49 hairuo gconfd (cbg-6832): starting (version 2.18.0.1), pid 6832 user 'cbg'
May 19 20:01:49 hairuo gconfd (cbg-6832): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 19 20:01:49 hairuo gconfd (cbg-6832): Resolved address "xml:readwrite:/home/cbg/.gconf" to a writable configuration source at position 1
May 19 20:01:49 hairuo gconfd (cbg-6832): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 19 20:01:49 hairuo gconfd (cbg-6832): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 19 20:01:49 hairuo gconfd (cbg-6832): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 19 20:01:53 hairuo gconfd (cbg-6832): Resolved address "xml:readwrite:/home/cbg/.gconf" to a writable configuration source at position 0
May 19 20:01:55 hairuo NetworkManager: <information>^IUpdating allowed wireless network lists.
May 19 20:01:55 hairuo NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

###########################
~/.xseesion-error

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "cbg"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=zh_CN.
Start IM through /home/cbg/.xinput.d/zh_CN linked to /etc/X11/xinit/xinput.d/fcitx. 
Start FCITX error. Another XIM daemon named fcitx is running?
SESSION_MANAGER=local/hairuo:/tmp/.ICE-unix/6779
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 14285 1179590400 1179576115
evolution-alarm-notify-Message: Sun May 20 00:00:00 2007

evolution-alarm-notify-Message: Sat May 19 20:01:55 2007


(gnome-panel:6858): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New
alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Sun May 20 00:00:00 2007


20:04:56: ERROR: FIXME: tagtype = 74

20:04:58: ERROR: sprite::add_display_object(): unknown cid = 6

---

