---
title: "Gaim just doesnt work"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jvictor on 2005-10-15
Ubuntu 5.10 final AMD64
Gaim doesnt connect

this is the debug message... I dont have any proxy / firewall

Its a direct connection to the adsl router and router connects to net. Router uses NAT. 


juby@powercube:~$ gaim -d

(gaim:7977): Gdk-WARNING **: locale not supported by Xlib

(gaim:7977): Gdk-WARNING **: cannot set locale modifiers
sound: Initializing sound output drivers.
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
plugins: probing /usr/lib/gaim/autorecon.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaim-remote.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnapster.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /home/juby/.gaim/smileys
plugins: probing /home/juby/.gaim/accounts.xml
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
prefs: Reading /home/juby/.gaim/prefs.xml
prefs: Reading /etc/gaim/prefs.xml
prefs: Finished reading /etc/gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
tray icon: plugin loaded
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/notify.so
pounces: Error reading pounces: Failed to open file '/home/juby/.gaim/pounces.xml': No such file or directory
status: Error reading statuses: Failed to open file '/home/juby/.gaim/status.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 101cb30c86000112940147400000073030020
Session Management: Using gaim as command
account: Connecting to account 0x6f7720. gc = 0x710bd0
connection: Connecting. gc = 0x710bd0
connection: Requesting password
connection: Destroying connection 0x710bd0
Session Management: Received first save_yourself
Session Management: Received save_complete
tray icon: embedded
accounts: Writing accounts to disk.
account: Connecting to account 0x6f7720. gc = 0x8c95a0
connection: Connecting. gc = 0x8c95a0
connection: Calling serv_login
server: gaim 1.5.0 logging in jubygetsmail using Yahoo
dns: Created new DNS child 7978, there are now 1 children.
dns: Host 'scs.msg.yahoo.com' resolved
proxy: Connecting to scs.msg.yahoo.com:5050 with no proxy
proxy: Connect would have blocked.
accounts: Writing accounts to disk.
dns[7978]: nobody needs me... =(

---

### Post by jvictor on 2005-11-03
Seems that we need to give the IP add instead of names for the accts... then it works fine

---

### Post by estel on 2005-11-03
Works fine for me... :s

---

