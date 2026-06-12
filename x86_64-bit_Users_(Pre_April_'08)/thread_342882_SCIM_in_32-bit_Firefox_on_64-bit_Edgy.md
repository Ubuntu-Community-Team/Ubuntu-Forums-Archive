---
title: "SCIM in 32-bit Firefox on 64-bit Edgy"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by fancyydk on 2007-01-20
Hello

I use both 64-bit Firefox and 32-bit Firefox with various plug-ins enabled thanks to Kilz. I am glad using these two versions on my system except that SCIM does not work when I have 32-bit Firefox window up. It works in 64-bit Firefox. I go to both Korean websites and English websites extensively, so I need Korean, but whenever I want to type Korean, I have to close all 32-bit Firefox windows and open new 64-bit Firefox window. But then I don't have flash anymore. Is there a way to enable SCIM in 32-bit Firefox just like 64-bit Firefox? Thank you for your help.

---

### Post by Kilz on 2007-01-21
> **fancyydk said:**
> Hello

I use both 64-bit Firefox and 32-bit Firefox with various plug-ins enabled thanks to Kilz. I am glad using these two versions on my system except that SCIM does not work when I have 32-bit Firefox window up. It works in 64-bit Firefox. I go to both Korean websites and English websites extensively, so I need Korean, but whenever I want to type Korean, I have to close all 32-bit Firefox windows and open new 64-bit Firefox window. But then I don't have flash anymore. Is there a way to enable SCIM in 32-bit Firefox just like 64-bit Firefox? Thank you for your help.

On the howto, down near the bottom is a section called "Common Problems". In it is a link to a post on how to install other languages.

---

### Post by Leira on 2007-07-14
i solved the problem in 32bt opera by "ln -s /usr/lib/locale /usr/lib32/locale". it seems it's the problem of lacking locales in /usr/lib32. i hope it can help u.

this solution really worked in xorg, but when i switched to the xserver-xgl session,scim could not work in 32bit opera anymoew.

---

