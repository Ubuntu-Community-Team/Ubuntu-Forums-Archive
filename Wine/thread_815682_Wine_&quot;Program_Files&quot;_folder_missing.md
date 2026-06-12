---
title: "Wine &quot;Program Files&quot; folder missing"
date: 2008-06-01
forum: Wine
---

### Post by afkaos on 2008-06-01
Hey all.

I've recently reinstalled Wine, and the "Program Files" menu that is typically there under the Wine menu under Applications is now missing, anyone know why this might be?

Thanks.

---

### Post by jjk7288 on 2008-06-01
Try seeing if it might be hidden: System > Preferences > Main Menu in Gnome. Not sure what the KDE equivalent is.

---

### Post by afkaos on 2008-06-01
Nope, not there at all.

---

### Post by rrios on 2009-05-17
> **afkaos said:**
> Hey all.

I've recently reinstalled Wine, and the "Program Files" menu that is typically there under the Wine menu under Applications is now missing, anyone know why this might be?

Thanks.

I had the same issue and this is how I fixed it:  I copied the files from other user:

$ cd /home/MY_USER/.config
$ sudo cp /home/ANOTHER_USER/.config/*.menu

In the case you don't have another user, here is the content of each file (at least for Ubuntu 8.10):

$ cat applications.menu 
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

$ cat settings.menu 
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Desktop</Name>
	<MergeFile type="parent">/etc/xdg/menus/settings.menu</MergeFile>
</Menu>

Hope it helps...

---

