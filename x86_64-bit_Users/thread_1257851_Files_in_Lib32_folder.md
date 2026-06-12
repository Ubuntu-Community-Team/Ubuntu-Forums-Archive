---
title: "Files in Lib32 folder"
date: 2009-09-04
forum: x86 64-bit Users
---

### Post by Martin Marshalek on 2009-09-04
I just started using 64bit Jaunty again and, after removing 32bit flash and installing the native 64bit, I noticed there are still files (they seem to relate to nvidia) in the lib32 folder. Why are these files there and how can I remove them? I want to have no 32bit in a 64bit install.

---

### Post by Yellow Pasque on 2009-09-04
If you installed nvidia drivers, they're going to install 32-bit libraries as well. The shared libraries are installed in case you run a 32-bit program. Other than taking up a relatively small amount of disk space, they're harmless, and they won't be used unless you run a 32-bit program. I highly suggest you don't touch them.

---

### Post by Martin Marshalek on 2009-09-06
Oh, ok that makes sense, I just wanted to make sure that I wasn't actually using any 32bit programs on my 64bit install. I'm gonna leave the files alone then.

Thanks

---

