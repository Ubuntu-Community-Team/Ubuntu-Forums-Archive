---
title: "Trouble with Browse C:/ Drive"
date: 2008-07-27
forum: Wine
---

### Post by kittiphanh on 2008-07-27
When I try to launch the C drive under applications in the Wine folder it would give me a "Failed to open URL '~/.wine/drive_c' error. I am running xubuntu hardy. Is it failing to recognize because I am using Xubuntu?

---

### Post by scragar on 2008-07-27
I do belive thunar (the xubuntu file manger) doesn't recognise ~ in it's open commands, try right clicking the menu, choosing edit and opening properties for that launcher, change the command to:
```
thunar $HOME/.wine/drive_c
```

---

### Post by kittiphanh on 2008-07-27
I have Compiz as my window manager and I guess I cannot right click to edit the destination. Is there like a type of file I can go to and edit it that way?

---

### Post by scragar on 2008-07-27
the config file can be found at:
~/.config/xfce4/desktop/menu.xml
where ~ repesents your home directory, or you can try to run the menu editor directly:
```
xfce4-menueditor
```

---

### Post by kittiphanh on 2008-07-27
It doesn't mention anything about wine or anything in the middle of the separators like games, accessories, graphics, and the such. In my applications it would list all of them with Wine at the bottom just before the last separator.


```
<xfdesktop-menu>
&#8722;
<menu name="Settings" icon="gnome-settings">
<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
</menu>
<separator/>
<include type="system" style="simple" unique="true" legacy="true"/>
<separator/>
<app name="Help" cmd="xfbrowser4 /usr/share/xubuntu-docs/about/xubuntu-index.html" icon="gnome-help"/>
<app name="About Xfce" cmd="xfce4-about" icon="info"/>
<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>
```

---

