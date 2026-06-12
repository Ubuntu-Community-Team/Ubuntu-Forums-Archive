---
title: "Massive lockup in Shiretoko"
date: 2009-09-27
forum: x86 64-bit Users
---

### Post by Oldhacker on 2009-09-27
Today, I clicked on a link from a Chess site which I believe used perl. A lockup to end all lockups ensued. I was unable to exit Shiretoko by any normal means. Both the original site tab and the blanked out link tab remained. Finally, I was able to shut down Ubuntu from the upper right shutdown control. Going back into Shiretoko brought back the same two locked up tabs. After exiting Ubuntu again by the same means, I rebooted and deleted Shiretoko from Synaptic Package manager. Then, I tried re-installing Shiretoko from Synaptic, and the same two locked up tabs returned!
Deleting the entire cache did not help either.

As of now, I deleted Shiretoko again from Synaptic and am back to using Firefox 3.0.14 to write this. I am COMPLETELY baffled by this. Is there any way that I can re-install Shiretoko without going back to the two blank tabs lockup condition?

---

### Post by Tanker Bob on 2009-09-27
Sounds like you have Firefox set to reopen the last session tabs when starting. Simply start Firefox 3.5 in safe mode from the terminal:

```
firefox -safe-mode
```

If Firefox doesn't start, check out [this page](http://support.mozilla.com/en-US/kb/Safe+Mode) for more on safe mode. Once you get 3.5 up and running in safe mode, go to Edit -> Preferences, Main tab, at the top change "Show my windows and tabs from last time" to something else. Then close Firefox and restart it normally.

---

### Post by Oldhacker on 2009-09-28
It was a good logical try, but it did not work. Starting Firefox 3.5 in safe mode from the terminal still brought up the two tabs that locked up Firefox. Here are the error messages that appeared on the terminal log:

brooks@brooks-desktop:~$ firefox-3.5 -safe-mode
../IcedTeaPlugin.cc:3858: Error: create process
../IcedTeaPlugin.cc:1666: Error: started appletviewer

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_write_chars: assertion `channel != NULL' failed
../IcedTeaPlugin.cc:4067: Error: Failed to write bytes to output channel

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_flush: assertion `channel != NULL' failed
../IcedTeaPlugin.cc:4081: Error: Failed to flush bytes to output channel

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_write_chars: assertion `channel != NULL' failed
../IcedTeaPlugin.cc:4067: Error: Failed to write bytes to output channel

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_flush: assertion `channel != NULL' failed
../IcedTeaPlugin.cc:4081: Error: Failed to flush bytes to output channel

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_write_chars: assertion `channel != NULL' failed
../IcedTeaPlugin.cc:4067: Error: Failed to write bytes to output channel

(firefox-3.5:11588): GLib-CRITICAL **: g_io_channel_flush: assertion `channel !=

---

### Post by Oldhacker on 2009-09-28
I am not certain what I did this time, but after a couple of reboots I attempted to launch Shiretoko (Firefox 3.5) in safe mode and got an opening screen showing "This is embarassing, but --" and three running tabs. I removed two of them and my Shiretoko is back to normal running. 

It still would be nice to know what caused this condition and what made the cure fail more than once and then work. ???

However, thanks for pointing me in the correct direction. :-)

---

### Post by Tanker Bob on 2009-09-28
Most likely a bad page that crashed a plugin, but glad it worked out for you.

---

