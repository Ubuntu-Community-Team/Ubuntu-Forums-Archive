---
title: "Steam store not working in WINE"
date: 2008-05-02
forum: Wine
---

### Post by slavik on 2008-05-02
Whenever I try to go to the store or view update news I get a message saying "storefront.steampowered.com cannot be found. Please check the name and try again."

Has anyone run into this issue?

---

### Post by sleon on 2008-05-05
From [this thread]("http://ubuntuforums.org/showthread.php?t=767044"):

```

sudo apt-get install lib32nss-mdns
```

After restarting Steam, that fixed the error on my system.

---

### Post by slavik on 2008-05-12
found the same solution on launchpad. thank you for your reply.

---

