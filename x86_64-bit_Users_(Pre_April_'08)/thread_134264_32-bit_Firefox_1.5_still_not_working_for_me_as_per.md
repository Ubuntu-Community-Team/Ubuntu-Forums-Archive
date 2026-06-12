---
title: "32-bit Firefox 1.5 still not working for me as per instructions in this forum"
date: 2006-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Daggett on 2006-02-21
If I follow the instructions in the Wiki and this forum, all I get when I start Firefox is this:

/usr/local/firefox32/run-mozilla.sh: line 166: /usr/local/firefox32/firefox-bin: cannot execute binary file

I have all the 32-bit libs installed as instructed. 

I downloaded 32-bit Firefox 1.5 and installed it in /usr/local/firefox32

Here is my shell file (as you can see I tried both the LD_PRELOAD and the PANGO_RC), no difference:

#!/bin/sh

export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
#LD_PRELOAD=/usr/lib32/libpangohack.so.0
linux32 /usr/local/firefox32/firefox $@

I'm using Kubuntu AMD64 Breezy

Help please?

---

### Post by BorgHunter on 2006-02-21
What are the permissions on that binary? Try
```
sudo chmod 777 /usr/local/firefox32/firefox-bin
```

---

### Post by Daggett on 2006-02-22
The permissions were 755, which should work.  Regardless, I changed them to 777 and got the same error message.

---

