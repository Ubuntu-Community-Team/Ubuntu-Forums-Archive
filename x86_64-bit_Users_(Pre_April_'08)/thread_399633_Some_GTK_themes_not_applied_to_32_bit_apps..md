---
title: "Some GTK themes not applied to 32 bit apps."
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-04-02
Does anyone know why some GTK themes will apply universally and others won't apply to 32 bit applications?  For example, I have been using a modified Clearlooks theme that I got from gnome-look.  This theme is a blue-ified variation and it applies nicely to every application I use.  Recently, however, I downloaded a new theme from gnome-look called "Glossy P".  When I applied this theme it took effect for many applications, but Swiftfox and Vmware (two notable 32 bit apps running on my system) looked like an ancient Windows 95 application as they did not assume the new theme.  When I switched back to the modified Clearlooks theme all is well again.  Is there an extra step I should take to get all themes to apply universally across my desktop?  Thanks.

---

### Post by Biker on 2007-04-03
[http://ubuntuforums.org/showthread.php?t=307194&highlight=gnome+theme+chroot](http://ubuntuforums.org/showthread.php?t=307194&highlight=gnome+theme+chroot)

---

### Post by cmost on 2007-04-03
Color me dumb, but I don't think I am running a chroot environment.  I used Automatix to install Swiftfox 32 bit and I installed VMware Workstation the usual way.  I didn't do anything special to get it all to work.

---

### Post by Keyper7 on 2007-10-10
Ressurecting this thread since I ran into the same problem:
I have an amd64 Feisty and the (unfortunately 32-bit only) Acrobat Reader looks damn fugly in it,
depending on the theme.

---

### Post by Kilz on 2007-10-10
The reason is you probably dont have the 32bit theme engine installed that that theme uses. If you know which one it uses you can download a 32bit deb for it and copy the files in place.

---

