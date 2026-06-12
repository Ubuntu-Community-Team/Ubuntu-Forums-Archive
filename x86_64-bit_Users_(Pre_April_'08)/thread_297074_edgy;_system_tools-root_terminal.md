---
title: "edgy; system tools-root terminal"
date: 2006-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by balaram on 2006-11-10
In the Dapper's Main Menu there was a System Tools-Root Terminal option. This would open the terminal as root user and prompt you for the password. I can't find it in Edgy. Unnecessary perhaps but convenient. Is it available for Edgy 64-bit?

---

### Post by kuja on 2006-11-10
Dunno. You can get the same effect like this:
1. open up a regular terminal
2. sudo su - root OR sudo -s

---

### Post by balaram on 2006-11-10
Yea i know but I'm a lazy *** and I wanted to avoid the extra step.

---

### Post by fabertawe on 2006-11-11
Make a launcher and use this for 'command'...
```
gksu /usr/bin/x-terminal-emulator
```

Paul

---

### Post by balaram on 2006-11-11
PERFECT! Thank you.

---

