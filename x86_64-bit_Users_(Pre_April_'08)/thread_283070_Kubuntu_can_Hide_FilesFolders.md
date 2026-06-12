---
title: "Kubuntu can Hide Files/Folders ?"
date: 2006-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by eskimokid on 2006-10-23
Can Kubuntu hide files/folders as windows do ?
Some files i need to hide for my own privacy
or can kubuntu set password on certain folders ?

---

### Post by ReaderRat on 2006-10-23
I believe that to hide files/folders you add a "." (dot) to the beginning of the filename/foldername.
Don't know for sure...

---

### Post by incubus on 2006-10-24
Yep.

"Hidden" files and directories in Unix/Linux start with a dot.  Hidden in the sense that they don't show up in a regular listing of a directory, but of course anybody who knows a little can see they are there.

This is mostly used for config files, to separate them from your regular files.

If you want to do something more fancy, such as not allow other users to read a file or access a directory you can look into modifying permissions instead.

best,
incubus

---

### Post by incubus on 2006-10-24
I think I wasn't very helpful in my last post.

Let me give an example. Suppose you have a directory "private" in your home directory and you want it to be accessed only by you. First let's create that directory.

```

$ cd
$ mkdir private
$ ls -l
drwxr-xr-x  2 user group       4096 2000-01-01 00:00 private
$
$ chmod 700 private
$ ls -l
drwx------  2 user group       4096 2000-01-01 00:00 private

```

In Kubuntu you can do the same thing in Konqueror, by right-clicking and changing the file permissions in properties.  With this, other users cannot access your directory or read its contents.

Now if you want to make it "hidden", you simply rename it to something like ".private".  Only if somebody runs

```

$ ls -a
.  ..  .private

```

...will he/she see that you have that directory. In Konqueror the person can go to View and choose to see hidden files. But he/she won't be able to access it, if you set the permissions properly.

Now with respect to encryption, I've never done that, but I'm pretty sure you can. Hopefully somebody will come up with an answer to that.

best,
incubus

---

