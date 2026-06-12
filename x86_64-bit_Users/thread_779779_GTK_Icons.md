---
title: "GTK Icons"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by peddy on 2008-05-03
Hey everyone

I am using the Nimbus theme on 64-bit Hardy. For some reason, mimetypes that I have set custom icons for (in this example .torrent files), the icons do not show correctly on my desktop. 

However, they show (correctly) in "Open" dialogs as shown in the attached image. I do not mind messing around with theme settings and whatnot, if someone could please tell me with what to do, or with what is going on it, would be appreciated. 


Cheers

Peddy

---

### Post by peddy on 2008-05-03
Its the same with Firefox downloads, the correct icon appears beside the download, and in the File Browser and my desktop, the icon is incorrect. 

Any ideas?

---

### Post by kurtpete on 2008-05-03
Assuming you're running Gnome and haven't restarted since applying this theme, you may need to kill all instances of Nautilus (or restart).  There's a good chance the icon on your desktop is a cached version.

---

### Post by peddy on 2008-05-03
thanks for the info. Yes, I have restarted numerous times and the problem persists.


edit: The Nimbus theme is based around the Tango icon theme.


happens only with the Tango theme

---

### Post by peddy on 2008-05-03
Fixed by changing /usr/share/icons/nimbus/index.theme to say inherits=glass-icons rather than inherits=Tango.

This makes the theme use the [glass-icons](http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146) icon theme for any mimetypes which nimbus-icon-theme does not specify icons for (rather than Tango). 

Its  not really a full solution, but I like the glass-icons theme anyway. 

Cheers

launchpad report [here](https://bugs.launchpad.net/tango-icon-theme/+bug/73846)

---

