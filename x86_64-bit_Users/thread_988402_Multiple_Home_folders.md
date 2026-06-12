---
title: "Multiple Home folders???"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by xaegis on 2008-11-20
Hello all...
I have reinstalled 8.10 and created second partition for my home folder but it seems that both home folders are still in use. How can I verify that this is or not happening?

=)

---

### Post by bodhi.zazen on 2008-11-20
echo $HOME

mount

cat /etc/fstab

---

### Post by sinanimam on 2008-11-20
When you write "mount", you will see whether your current home directory is a location mounted on the newly-created partition or not. First unmount the new folder. You will see your old home directory. If you mount another partition on that directory, only the new partition's contents will be seen there. So create a temporary directory outside your home directory and move all files from the home directory there. Don't forget the hidden files (starting with "."). Then mount it and move the files from the temporary location to the mounted home directory. Add an entry in /etc/fstab to make it mounted at startup.

---

### Post by xaegis on 2008-11-21
This was what I needed.

Thank you!

:)

---

### Post by Sukarn on 2008-11-21
I didn't know it was possible to mount a partition into a non-empty directory

---

