---
title: "apt-get not makeing links to programs"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by xmagixx on 2008-10-03
Hej
well the thing is 
when i install a program with apt-get install or atitude or what ever i use
first time it makes a shortcut in the programs menu
how ever some programs needs a diffrient start parameter 
i change it and try out the program, and if i dont like it i uinstall
first i change the startmenu shortcut back to default
then i apt-get remove/purge 
the problem is when i then reinstall it
then the installer doesnt make a shortcut to programs
i have to make it my self..... a bug or a way to fix this ?

---

### Post by mindoms on 2008-10-03
thats not what you asked for, but you can try programs with different parameters using the run-dialog

alt+f2
totem --fullscreen /media/disk/Latest_Movie.divX.avi

you may use a terminal too.

instead of uninstalling/installing the application:
```

sudo dpkg-reconfigure <package-name>
# for example:
sudo dpkg-reconfigure totem

```

---

### Post by xmagixx on 2008-10-03
thanks for this info, dosent solve my issue though 
but nice to know from now on :)

---

### Post by mindoms on 2008-10-04
Im not too sure if i understand your question. but:

right click your ubuntu menu bar (top left) -> Edit Menus -> try to find the Application launcher you miss -> make sure it is checked.

To revert it to default, right click it and choose:
Revert to Original.

If you cant find your launcher here, than this might really be a bug.
You can file a bug-report on launchpad.net - Though i haven't done this so far myself

---

### Post by xmagixx on 2008-10-04
the problem is that if i in someway have alterd a launcher and change it back ofc for removeing the program. when i then reinstall the program it doesnt remake the launcher
i have to make one manuelly
first time install = it makes a shortcut(launcher
secound time install = i have to make it manuelly

---

