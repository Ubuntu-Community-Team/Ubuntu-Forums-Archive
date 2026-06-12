---
title: "Jockey-kde error on Broadcom STA driver"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by carra on 2008-12-29
Hi there,
I installed Kubuntu 8.04.1 on HP Tx 1250el (Tx 1000 series) and, when I try to install Broadcom STA driver as in other *buntu, I got this error: 
>   File "/usr/bin/jockey-kde", line 288, in on_handler_changed
    self.toggle_handler(item.handler)
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 487, in toggle_handler
    if not self.confirm_action(title, handler.name(), subtext, action):
  File "/usr/bin/jockey-kde", line 186, in confirm_action
    text += subtext
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 14: ordinal not in range(128) 

Any workaround to this? You know... wi-fi is a must!
Thanks in advance to anyone helping.

carra from Italy

---

### Post by carra on 2009-04-04
Bump...

---

