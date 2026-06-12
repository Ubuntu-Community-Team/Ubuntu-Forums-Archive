---
title: "BMPX amd64"
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by xopher on 2006-07-19
Ive compiled the latest bmpx for amd64.. I got the debs here: [http://koti.mbnet.fi/xopher/Files/bmpx/](http://koti.mbnet.fi/xopher/Files/bmpx/)

Try them out if you like to, but tell me how they work.

---

### Post by dazvid on 2006-07-21
Thanks a lot for this, saves me some time :)
Works great.

---

### Post by jamesford on 2006-07-21
wont install, says dependency problem with libnotify1, which ive got installed :/

---

### Post by s_spiff on 2006-07-21
ok i'm a noob at this, can someone tell me what exactly to do in this? I added the repo add [ 
deb [http://koti.mbnet.fi/xopher/Files/bmpx-repo](http://koti.mbnet.fi/xopher/Files/bmpx-repo) ./ ] to the repo's list, but am still not able to find it gives me a error 302 not found..or something of that sort.

---

### Post by xopher on 2006-07-24
Well Im not sure about the 'repo', so you're better off just manually downloading and installing it at the moment. Havent had time to configure a decent repository yet so.

And for that libnotify1, I could probably upload it too.

Thanks for the good reply though ;)

Edit: **The libnotify-debs are now up.**

---

### Post by xopher on 2006-07-24
> **s_spiff said:**
> ok i'm a noob at this, can someone tell me what exactly to do in this? I added the repo add [ 
deb [http://koti.mbnet.fi/xopher/Files/bmpx-repo](http://koti.mbnet.fi/xopher/Files/bmpx-repo) ./ ] to the repo's list, but am still not able to find it gives me a error 302 not found..or something of that sort.

Ah, found out the problem, I had the 'repo' on my computer in a folder called bmpx-repo, so I accidentally typed that into the file, even though it should be bmpx.

Summa summarum, the correct address for the repository would be

```
deb http://koti.mbnet.fi/xopher/Files/bmpx ./
```

---

