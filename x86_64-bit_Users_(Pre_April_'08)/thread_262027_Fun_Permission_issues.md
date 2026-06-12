---
title: "Fun Permission issues"
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2006-09-21
I'm not sure what has been doing it lately, but this time I at least figured out what it was I suppose ... When I lost my sound, and I couldn't log into X any longer, I was at a loss for words, at least until now. Something changed the permission for /tmp to root:root 754. Changing it to root:users 774 fixed my issues, but I hope I don't have to do this often... Any idea what's up with it? It only started happening recently... perhaps it was an Xorg or Linux-image up date....

---

