---
title: "[SOLVED] The panel encountered a problem while loading &amp;quot;OAFIID:GNOME_GnoMenu&amp;quot;."
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by JoseReyes on 2008-11-16
How do I delete an application from the add to panel list. I added GnoMenu, but now it gives me this error when I try to add it to the panel.

The panel encountered a problem while loading "OAFIID:GNOME_GnoMenu".

and won't load. I try the delete opition but it does not delete. When I rebot it gives me the same error..

How can I remove it from the list so it won't give error?

---

### Post by laceration on 2008-11-16
system->preferences->sessions find it in the startup programs tab and uncheck.

---

### Post by JoseReyes on 2008-11-16
> **laceration said:**
> system->preferences->sessions find it in the startup programs tab and uncheck.


I have completely removed the package from the PC but still shows in the window that opens when you right click on the panel and add to panel. That window shows it there and I can't figure out how to remove it from the list of amplets. When I try to load it it give the error then ask if I want to delete it I click yes but it does not remove it.

---

### Post by laceration on 2008-11-17
So ignoring it is not enough?  I don't think anybody has every applet installed, but there are still applets in addto that are built into gnome and non-removable.  I don't know how gnoMenu got stuck there. Maybe its a 64-bit thing or just bad programming.  Maybe you could find a setting in gconf-editor or check bug reports for a solution.
OAFIID:GNOME scares me as I used to get it from glipper and eventually had a gnome meltdown.  I'll add gnoMenu, along with glipper, to my list of suspected crapware to avoid. (Klipper is great by the way even in a gnome environment)

---

### Post by JoseReyes on 2008-11-17
> **laceration said:**
> So ignoring it is not enough?  I don't think anybody has every applet installed, but there are still applets in addto that are built into gnome and non-removable.  I don't know how gnoMenu got stuck there. Maybe its a 64-bit thing or just bad programming.  Maybe you could find a setting in gconf-editor or check bug reports for a solution.
OAFIID:GNOME scares me as I used to get it from glipper and eventually had a gnome meltdown.  I'll add gnoMenu, along with glipper, to my list of suspected crapware to avoid. (Klipper is great by the way even in a gnome environment)

I was able to remove the GnoMenu amplet by doing a search then going to terminal and removing each folder/files separate... this did the work but I still can't install it again.. but I don't get the error anymore...

---

