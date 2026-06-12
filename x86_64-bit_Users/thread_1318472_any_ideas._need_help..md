---
title: "any ideas. need help."
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by alotofloudcheese on 2009-11-07
I have jaunty 9.04 64 bit and my wireless quit working after I was trying to fix some issues I had with virtualbox. While trying to fix it I tried installing the old version over the top of the updated version of virtualbox and of course this did not work got a partial load with errors, dumb I know. 

  Any ways my wireless does not work on my laptop now. It sees the device has wireless networks heading under connections, but does not see known wireless or unknown wireless connections. Also when ubuntu shuts down it does not get through the whole status bar at shut down, but it still shuts down. 

  So I went through my sys log after looking for ways to figure this out from other threads, and this is what I found in syslog. Any help, point me in the right direction, would be appreciated. I need my wireless.

```
 NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 

console-kit-daemon[3046]: WARNING: Couldn't read /proc/3045/environ: Failed to open file '/proc/3045/environ': No such file or directory 

 console-kit-daemon[2836]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 

 console-kit-daemon[2836]: WARNING: Unable to activate console: No such device or address 

console-kit-daemon[2836]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>' 

console-kit-daemon[2836]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

console-kit-daemon[2836]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```

---

### Post by HappyFeet on 2009-11-08
I would uninstall vbox (completely remove) then check in synaptic for broken packages, then do
```
Sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall you wireless drivers.

---

