---
title: "[SOLVED] Accessing network shared folders through wine applications"
date: 2008-06-17
forum: Wine
---

### Post by Ralphie on 2008-06-17
Is this possible?
I am able to browse to the folder via ubuntu and SMB, but am not able to do so through the "open file" dialog in an application that I am running (mp3 direct cut) through wine.

Is it possible to access shared folders through wine?

How would I go about mapping that, or to what location could I browse to, to find my shares?

Thanks!

---

### Post by Ralphie on 2008-06-17
Thanks to Jordan_U in the #ubuntu IRC channel I have figured out how to browse to a network share via wine applications!

> Jordan_U: You can either mount the shares to whatever folder you want or you can check ~/.gvfs

Basically browse to the folder ~/.gvfs in the wine application and there you have it, your network shares! yay

---

