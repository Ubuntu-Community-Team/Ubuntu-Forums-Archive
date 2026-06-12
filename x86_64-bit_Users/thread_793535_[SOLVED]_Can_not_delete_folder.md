---
title: "[SOLVED] Can not delete folder"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-13
I copied one folder from CD to desktop and now that folder is locked, I can not delete it :(

I tried to cnahge permissions for folder but failed , can you help me ?

---

### Post by Victormd on 2008-05-13
> **DachaArh said:**
> I copied one folder from CD to desktop and now that folder is locked, I can not delete it :(

I tried to cnahge permissions for folder but failed , can you help me ?

Open the terminal and type:
```
cd ~/Desktop
sudo rm -r FOLDERNAME
```
Replace FOLDERNAME with the name of the folder you want to delete.

[COLOR="Red"]**[SIZE="3"]NOTE: BE VERY CAREFULL WHEN USING THE SUDO RM -R COMMAND. IF YOU FAIL TO PUT THE "FOLDERNAME", THE COMMAND WILL WIPE YOUR HD[/SIZE]**[/COLOR]

---

### Post by Bubba64 on 2008-05-13
You can also try to highlight the folder then hold down shift then hit delete.

---

### Post by ironwolfe on 2008-05-13
even easier and something you will use in the future.

```
gksudo nautilus
```

this brings up the graphical display of folders but as the super user so you don't have to worry about permissions.  This is VERY powerful so be careful.

goo' luck

---

### Post by DachaArh on 2008-05-14
> **Victormd said:**
> Open the terminal and type:
```
cd ~/Desktop
sudo rm -r FOLDERNAME
```
Replace FOLDERNAME with the name of the folder you want to delete.

[COLOR="Red"]**[SIZE="3"]NOTE: BE VERY CAREFULL WHEN USING THE SUDO RM -R COMMAND. IF YOU FAIL TO PUT THE "FOLDERNAME", THE COMMAND WILL WIPE YOUR HD[/SIZE]**[/COLOR]


thanks did it .

And thank you all for helping

---

### Post by scouser73 on 2008-08-27
Thanks Victormd, this worked perfectly.

---

### Post by elmoosecapitan on 2008-08-27
I you run into this problem and decide not to use the terminal, for some unknown reason, open the folder or file in Konqueror and you will eventually be prompted for your root password when deleting a protected file. I am sure it is needless to reiterate the DANGER of only typing ```
sudo rm -f
```

---

