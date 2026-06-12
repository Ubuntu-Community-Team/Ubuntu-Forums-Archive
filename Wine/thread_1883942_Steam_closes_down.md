---
title: "Steam closes down"
date: 2011-11-20
forum: Wine
---

### Post by Arvidos on 2011-11-20
Hey everyone! Since a week back, I'm a happy ubuntu user.

Today I installed PlayOnLinux, installed Steam through PlayOnLinux, and tried starting it up. It starts up and logs in just fine, the interface shows up, but after a few seconds it closes down. I can start it again, same thing.

Any ideas what my problem is?

I run Ubuntu 11.10 on an Acer Aspire One 772, kind of between a netbook and a laptop. Can provide additional details.

---

### Post by Elfy on 2011-11-20
Thread moved to Wine.

---

### Post by murdockpt on 2011-11-20
bumping with same issue

installed this morning, left fro work installing tf2. came back, tf2 was installed, but now steam wont stay open and i cant find it in my programs list.

had the problem before as well with it automatically closing down, so OP, youre not the only one with the problem

---

### Post by ergo-proxy on 2011-11-20
> **Arvidos said:**
> Hey everyone! Since a week back, I'm a happy ubuntu user.

Today I installed PlayOnLinux, installed Steam through PlayOnLinux, and tried starting it up. It starts up and logs in just fine, the interface shows up, but after a few seconds it closes down. I can start it again, same thing.

Any ideas what my problem is?

I run Ubuntu 11.10 on an Acer Aspire One 772, kind of between a netbook and a laptop. Can provide additional details.

I didn't have this problem using the latest wine...

---

### Post by Firezap on 2011-11-20
What version of wine are you using? Steam works flawless for me.

---

### Post by Arvidos on 2011-11-21
This is what I've got.

---

### Post by desktorp on 2011-11-22
Launch Steam from the terminal, so you can see the errors.

---

### Post by Arvidos on 2011-11-25
> **desktorp said:**
> Launch Steam from the terminal, so you can see the errors.

I'm quickly feeling really lost, but I managed to start PlayOnLinux through the terminal, and from there start Steam. This is **is what it said:

---
arvid@arvid-AO722:~$ playonlinux
PlayOnLinux v3.8.8

/usr/share/playonlinux/lib/main: rad 248: /usr/share/playonlinux/plugins/plugins.lst: Filen eller katalogen finns inte *((File or folder missing))*

(python:20153): Gtk-WARNING **: Kan inte hitta temamotorn i "module_path": "pixmap", *((Could not find theme engine ?? in "module_path": "pixmap",))*
Running Steam
---

And that's it. If there is a way to run steam directly from the terminal, rather than PlayOnLinux, I don't know how.

---

### Post by P-I H on 2011-11-25
Try to use this command in the terminal:
env WINEPREFIX="/home/p-i/.local/share/wineprefixes/steam" wine C:\\windows\\command\\start.exe /Unix /home/p-i/.local/share/wineprefixes/steam/dosdevices/c:/users/Public/Desktop/Steam.lnk
Replace p-i with your own userid.

I got this command by right clicking the Steam launcher and then select properties.

---

### Post by Arvidos on 2011-11-25
P-I H, I tried your suggestion, but it turns out my installation path was way different.

Eventually I re-installed through winetricks, and that did the trick (ha ha)

Thanks for your help!

---

