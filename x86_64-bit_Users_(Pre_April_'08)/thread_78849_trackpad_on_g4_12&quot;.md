---
title: "trackpad on g4 12&quot;"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by gumara on 2005-10-19
command #/sbin/trackpad tap 
for use trackpad on my ibook. howto run that command auto with start laptop


*i can use english language a little. sorry if word not friendly

---

### Post by spoetnik on 2005-10-19
For tap-click on the trackpad;
edit hte file /etc/pbbutons.conf
change “TPMode = notap” in
“TPMode = drag”

restart your pbbuttons (sudo /etc/init.d/pbbutons restart)

---

### Post by gumara on 2005-10-19
it work on my ibook
tankyou :o

---

