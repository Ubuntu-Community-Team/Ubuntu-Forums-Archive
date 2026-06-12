---
title: "how to create .tar.gz files"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-09-30
this is a uber newbie question, i've never had the need to create a .tar.gz/bz2 file, and now that i do... im stuck. I try tar -cg to create a .tar.gz file, but my terminal turns into a bunch of characters and just hangs, if anyway could give me a hand I'd be very grateful.

---

### Post by tagra123 on 2006-09-30
Here's a link that may help.

[http://www.cs.duke.edu/~ola/courses/programming/tar.html](http://www.cs.duke.edu/~ola/courses/programming/tar.html)

You can also make archives from nautilus (file manager) by right-clicking a file or files and selecting archive.

---

### Post by xstaticxgpx on 2006-09-30
I did those commands shown on the website, but for some reason it keeps giving me this 

> tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.


---

### Post by andiii on 2006-09-30
man tar

exaples on page 1

---

### Post by andiii on 2006-09-30
mkdir test
touch test/testfile
tar cvf test.tar test/

---

### Post by tagra123 on 2006-09-30
> **xstaticxgpx said:**
> I did those commands shown on the website, but for some reason it keeps giving me this

Maybe you are trying to save the to a directory you dont have permissions to write to?

tar -rvpzfh TARGETPATH SOURCEPATHANDFILE


This will backup the contents of /etc/apt

tar -rvpzfh  /home/someuser/aptbackup.tgz /etc/apt/

and you can alway add sudo to get access to all read and write permissions

sudo tar -rvpzfh  /home/someuser/aptbackup.tgz /etc/apt/

---

### Post by xstaticxgpx on 2006-09-30
idk, i just ended up right clicking > archive... ill mess around with the command-line version later tonight

---

### Post by andiii on 2006-10-01
You definitively should. The tar commands first confused me, but when you are familiar with the most common 4 or 5 options for tar it's very effective and ten times faster than using a gui.

---

### Post by xstaticxgpx on 2006-10-01
I think i figured it out, i used man tar and tried the examples... thanks guys

---

