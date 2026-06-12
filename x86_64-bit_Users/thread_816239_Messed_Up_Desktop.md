---
title: "Messed Up Desktop"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-06-02
Hey - when i log into Ubuntu all i'm getting is the wallpaper, a few icons on the desktop but nothing more. No taskbar, no AWN, no nothing. i can right click on the desktop but that's about it.

Alf + F2 doesn't open anything, so i can't get to a terminal. 
I can't get to Firefox or flock because my dock doesn't load.
I have no menu's to navigate.

What's caused this? and how do i correct it? it's rendered Ubuntu unusable atm.. and i was slowly getting everything up and running as well! >_<

---

### Post by Sef on 2008-06-02
Was this situation upon install or did you do something that affected the desktop?

If it is the former, then check your disk to make sure it is good.  At boot/install, go down to "Check Disk for Errors".

If it is the latter, what happened to create that situation?

---

### Post by Kevbert on 2008-06-02
If you want to get into terminal just hit Ctrl-Alt-F1 when you get to the login screen.  You'll get a text prompt for username and password, enter these and you're there.

---

### Post by joey-elijah on 2008-06-02
> Re: Messed Up Desktop
Was this situation upon install or did you do something that affected the desktop?

If it is the former, then check your disk to make sure it is good. At boot/install, go down to "Check Disk for Errors".

If it is the latter, what happened to create that situation? 

It was certainly the latter, as i'd had a "normal" desktop. I think what may have caused it [not sure] i "added" Avant-Window Navigator to start up... Curiously there was a notification bubble in "air" to the very left of the non-taskbar, which means it's there.. but hidden? moved?

Also, i've been trying to get emerald to start up upon login with having to use the terminal, could this have caused it?

And tbh i don't know what i'd do in terminal if i could get it up

'sudo make desktop_right' maybe? lol

---

### Post by dbenc on 2008-06-02
i have this same problem, it started last night after i had an application crash ... could you post the contents of the .xsession-errors file in your home directory? maybe we have something in common .. 

cat .xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/bigdinux:/tmp/.ICE-unix/7662
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
seahorse nautilus module initialized
Initializing nautilus-share extension
gpilotd-Message: gnome-pilot 2.0.15 starting...
gpilotd-Message: compiled for pilot-link version 0.12.3
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] 
ERROR: trackerd already running on your session dbus - exiting...
<?xml version="1.0" encoding="UTF-8" ?><scanner></scanner>

(gpilotd:7773): libgpilotdcm-WARNING **: Number of devices is configured to 0

(gpilotd:7773): libgpilotdcm-WARNING **: No accessible devices available

(gpilotd:7773): libgpilotdcm-WARNING **: Number of PDAs is configured to 0
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 0
<?xml version="1.0" encoding="UTF-8" ?><scanner></scanner>
17
evolution-alarm-notify-Message: Setting timeout for 44043 1212469200 1212425157
evolution-alarm-notify-Message:  Tue Jun  3 00:00:00 2008

evolution-alarm-notify-Message:  Mon Jun  2 11:45:57 2008


(evolution-alarm-notify:7810): libecal-WARNING **: e-cal.c:318: Unexpected response
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8e0870 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8e0870 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8e0720 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8e0720 ): KAccel object already contains an action name "play_pause"
Debug: Done reading conf from /etc/beagle/config-files/BeagleSearch.xml
Got accel 65481, 0, 0
Got keycode 96
Got modmask 0
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1600003 (Evince Doc)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
transkode: starting workers
transkode: worker 11505728 running
transkode: starting workers
transkode: worker 11275632 running
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8daf90 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8daf90 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
transkode: starting workers
transkode: worker 11648944 running

** (nautilus:7761): WARNING **: Unable to add monitor: Not supported
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000060 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin Scheduler
Initialising plugin NetworkHealth
Initialising plugin TorrentPeers
Initialising plugin TorrentCreator
Initialising plugin Search
Initialising plugin NetworkGraph
Initialising plugin TorrentFiles
Initialising plugin SpeedLimiter
Initialising plugin WebUi
Initialising plugin EventLogging
Initialising plugin WebSeed
Initialising plugin BlocklistImport
Initialising plugin DesiredRatio
Initialising plugin FlexRSS
Initialising plugin TorrentNotification
Initialising plugin MoveTorrent
Applying preferences
Starting DHT...
Showing window
Found NetworkGraph plugin...
Found TorrentPeers plugin...
Found MoveTorrent plugin...
Found SpeedLimiter plugin...
Found TorrentFiles plugin...
Found NetworkHealth plugin...
Found TorrentCreator plugin...
Unloading TorrentCreator plugin...
save uploaded memory
Pickling state...
Stopping DHT...
Saving fastresume data...
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastrestranskode: stopping workers
transkode: waiting workers to end
transkode: stopping workers
transkode: waiting workers to end
transkode: stopping workers
transkode: waiting workers to end
transkode: worker 11648944 finished
transkode: workers finished
transkode: worker 11505728 finished
transkode: workers finished
transkode: worker 11275632 finished
transkode: workers finished
ume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
no old fastresume to delete
Quitting the core...
core: removing torrents...
core: removing settings...
core: shutting down session...
core shut down.
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x13b specified for 0x4400db1 (Error - Am).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x13b specified for 0x2200db1 (Error - Am).
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x13b specified for 0x2800db1 (Error - Am).
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
STARTUP
QImage::smoothScale: Image is a null image
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
amarok: ERROR: : couldn't create slave : Cannot talk to klauncher
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
  PID TTY          TIME CMD
 7734 ?        00:00:00 pulseaudio
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

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:8076): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
```

---

### Post by joey-elijah on 2008-06-02
Where abouts do i find that? in my "home" folder i don't have any xsession-errors named document/file... 

it's really annoying me now. If it wasn't for having an icon to launch firefox with i wouldn't even be able to get online.

Does no one know a way to solve this?

---

### Post by joey-elijah on 2008-06-02
Okay - i have my panels back.... for now.

Hit ctrl+alt+f2 and type ```
sudo dpkg-reconfigure gnome-panel
```

mine said that gnome-panel was either broken or not installed so i typed 

```
sudo apt-get install gnome-panel
```

hit ctrl+alt+f7 and logged out, logged in and was greeted with some error messages - seemingly over my weather applet.

i hit ```
sudo apt-get update 
``` and ```
sudo apt-get install
```
which installed lots of things...

---

### Post by Kevbert on 2008-06-03
> **joey-elijah said:**
> Where abouts do i find that? in my "home" folder i don't have any xsession-errors named document/file... 


Anything that starts with a '.' is a hidden file or directory.  You can see these in Nautilus file manager by either using Ctrl-H or by going to the View menu and ticking hidden files.  To turn off just hit Ctrl-H again.

---

### Post by joey-elijah on 2008-06-04
i have the panels back after doing what i posted previously.

However, emerald still doesn't start up at login - i have to enable ti via terminal, and yes it is enabled in compiz via usr/bin/emerald

---

