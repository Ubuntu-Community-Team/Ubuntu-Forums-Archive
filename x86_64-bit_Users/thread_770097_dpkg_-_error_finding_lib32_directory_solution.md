---
title: "dpkg - error finding lib32 directory solution"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by Antarctica on 2008-04-27
**The suggestion in this post has been removed: it was a workaround that may lead to system instability, and is not a supported method of fixing the problem in question -- The staff**

Hey I've been running the Ubuntu Hardy beta and finally did a fresh install of the official release.  I encountered an error trying to use nvidia-glx in the Hardware Drivers manager.  I just want to let people, especially beginners to Ubuntu and Linux,know that if you get the following or similar error in Ubuntu Hardy 64-bit:

```

dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx

```

then open a terminal and type

<snip>

This will create a link named "lib32" to "lib" in the /usr folder.  This solution will suffice until any bugs or quirks are removed.  I hope this helps!

---

### Post by zedix9 on 2008-05-25
Thank you very much for this solution - so far so good! :)

---

### Post by Sir_Jordan on 2008-05-25
Thanks a lot... After 3 hours of searching... One of many topic I found is working!!! :D:D

---

### Post by Kilz on 2008-05-26
This instruction can fubar some applications. /usr/lib in a 64bit system contains your 64bit libraries. /usr/lib32 contains your 32bit libraries. By symlinking them you stand a good chance of having a messed up install when a 32bit application looks for a 32bit library. It will only find incompatible 64bit libraries. This should mess up Flash/nspluginwrapper.

---

### Post by Yellow Pasque on 2008-05-26
Instead of linking the entire directory, just symlink the file:
```
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib/libGL.so.1
```

If you've already created the directory link, I would suggest using the GUI to delete it so you don't accidentally delete your entire /usr/lib folder:
```
gksudo nautilus
```

---

### Post by chrisccoulson on 2008-05-26
The symlinking idea is definately very bad (as Kilz has already pointed out). Just wanted to make that clear to anyone who comes across this thread, so they don't completely bork their system.

In addition to what Kilz has already pointed out - If you symlink /usr/lib32 to /usr/lib, and then come to install an application that writes 32-bit libraries in to /usr/lib32, they could overwrite the 64-bit equivalents that might be in /usr/lib - leading to serious breakage

Very bad idea.

Antarctica: you should modify your post to make this point clear, and be more careful with what you post

---

### Post by Yellow Pasque on 2008-05-26
> Antarctica: you should modify your post to make this point clear, and be more careful with what you post

I have reported the OP to the Ubuntu forum staff. Antarctica, I realize you were trying to help, but please be more careful before creating solution threads. Thanks.

---

