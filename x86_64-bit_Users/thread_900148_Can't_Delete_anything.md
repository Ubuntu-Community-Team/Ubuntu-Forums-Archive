---
title: "Can't Delete anything"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by parakeets11 on 2008-08-25
I have absolutely no space left on my partion and cannot delete anything.  I do believe that this is my problem with nautilus crashing in gnome and kde not being able to start.  I had to switch my Desk environment to XFce to be  able to post this thread.  Any ideas on how to delete files and/or compress them?

---

### Post by mellowd on 2008-08-25
What exactly happens when you try and delete anything? Have you sudo'd?

---

### Post by parakeets11 on 2008-08-25
It says failed to copy "file" to "trash" and it asks to retry or skip. I say retry and it takes me back to the failed copy screen.  I dont know how exactly I managed to get to 0b of free but it happened.  I'm also quite new to linux.

---

### Post by mellowd on 2008-08-25
Have you tried deleting through the terminal? It's not mving to trash as it has no space.

To delete from the terminal type:

```
sudo rm file.to.delete
```

to delete a folder type:

```
sudo rm -r folder/
```

be VERY careful with the second, it will delete that folder and everything in it. Be sure before you type it

---

### Post by parakeets11 on 2008-08-25
Awesome thanks, I was getting scared that I had to reinstall Linux.

---

### Post by alex2035 on 2008-09-01
By the way, I have opposite problem. I do have something in the trash i cannot delete by any means, trash appears always with this folder that contains five or six files owned by root. I have tried from a root nautilus session, no way, trash for my user is invisible. From a Terminal ( user or root) it is the same. How can I see Trash from a root term so I can get rid of this? thank you for your help! And last one, is there a way to DELETE something without going through Trash, ala windows, when you press SHIFT+DELETE?

---

### Post by IntuitiveNipple on 2008-09-02
The trash directory is **/home/${USER}/.local/share/Trash/** and it contains two sub-directories, **files/** and **info/**. From a root shell terminal you should be able to see the files in all user Trash directories using:
```

sudo ls -al /home/*/.local/share/Trash/files/

```

---

### Post by Kooothor on 2008-09-02
> **parakeets11 said:**
>  I'm also quite new to linux.

This is your major problem.
Try to resolve this and the rest should run flawlessly...

---

### Post by alex2035 on 2008-09-03
> **IntuitiveNipple said:**
> The trash directory is **/home/${USER}/.local/share/Trash/** and it contains two sub-directories, **files/** and **info/**. From a root shell terminal you should be able to see the files in all user Trash directories using:
```

sudo ls -al /home/*/.local/share/Trash/files/

```

Thanx IntuitiveNipple, quite easy. One of those thing you never forget again.
regards, alex

---

### Post by computer_freak_8 on 2008-12-22
> **IntuitiveNipple said:**
> The trash directory is **/home/${USER}/.local/share/Trash/** ...

So *there* it is! I kept seeing stuff like **/home/username/.Trash**, but it didn't exist.

I'd hit the "Thank" button, but there's not one there.


Thanks!
computer_freak_8

---

