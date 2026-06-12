---
title: "[Waiting for Headers] problem"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Washington Irving on 2006-08-03
my apt-gets have started to spend a very long time on [Waiting for Headers] and they often freeze for a while at 99%. Anyone got any idea why? This happens in Synaptic and Automatic Updates aswell.

---

### Post by jamesford on 2006-08-03
its the same here, i think its just the servers having some problems. will probably be fine again tomorrow. its happened a few times before

---

### Post by Washington Irving on 2006-08-04
Hmmm mine seems better now but I still don't think that it's as good as before, how about your's jamesford?

---

### Post by Titus A Duxass on 2006-08-04
Same here in Germany, eventually worked.

---

### Post by darrenm on 2006-08-04
Same here in the UK, but seems better now.

---

### Post by jamesford on 2006-08-04
seems like the canonical repos are slow, the ubuntu ones are fine here

edit: i spoke too early, now its all fcked again. seems to be a bit up and down

---

### Post by Vlatko on 2006-08-04
i'm having troubles as well. extremelly slow and unresponsive. update manager won't even update. get this error:
```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu3_amd64.deb)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu3_amd64.deb)
```

---

### Post by mack609 on 2007-06-06
so all yo saying that its the servers prolem and it could br fixed in a day or two caus im having the same problem with the headers after it worked and i had a system crash so the linux os couldnt work after that. when i installed it again i couldnt get any updates again kinda weared isnt it .. i didnt have that problem .. so if any one got something just plz hlp and post it

---

### Post by minj on 2007-06-08
It is definitely NOT the servers problem. Something is wrong with apt-get. It just waits for EXACTLY 2min doing nothing before downloading everything in 5s (at least for me :) ). And this happens no matter the server. HELP?

---

