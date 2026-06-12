---
title: "Wine Menu in Applications Gone!"
date: 2008-05-29
forum: Wine
---

### Post by noahTHEpurdy on 2008-05-29
Hi! I accidentally deleted the Wine menu in the applications menu, and I'd like to get it back! I tried using Synaptics to completely remove Wine and tried reinstalling it, to no avail. Any ideas!?

---

### Post by AliTabuger7 on 2008-05-29
I believe wine-doors ([http://www.wine-doors.org/](http://www.wine-doors.org/)) does this. (install)

You might also want to try winecfg (command)

---

### Post by noahTHEpurdy on 2008-05-29
Wine-Doors is very handy, however it doesn't add the menu back to the applications menu. 

There's no options in the winecfg that handle re-adding that menu.

---

### Post by noahTHEpurdy on 2008-05-29
I figured it out!

> **mc4man said:**
> i don't know about kde (using gnome) but in gnome when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
```
<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>
```

remove the <Deleted/>
maybe kde does the same thing

---

### Post by AliTabuger7 on 2008-05-29
How exactly did you delete it?
I'm just asking because you might be able to get it back by undoing the action somehow.

alacarte?

Are you using the official ubuntu wine or are you using the repository from wine's website?

---

### Post by bmwman on 2008-05-30
> **noahTHEpurdy said:**
> I figured it out!

Great!!!

That fixed my problem too.
Thanks.

---

### Post by noahTHEpurdy on 2008-05-30
> **AliTabuger7 said:**
> How exactly did you delete it?
I'm just asking because you might be able to get it back by undoing the action somehow.

alacarte?

Are you using the official ubuntu wine or are you using the repository from wine's website?

To be honest, I don't quite remember, however I've got it fixed, so all is good!

---

