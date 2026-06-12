---
title: "64 bit update problem"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by 3mb0 on 2009-03-19
Ok i was using 32-bit Ubuntu 8.10 but i fancied a change, and with it i chose 64 bit, it seemed like more of a challenge, and it's prooving to be.

(I'm using Ubuntu 8.10 Ultimate Edition KDE)

So i finish installing the majority of updates, and there are 3/4 left uninstalled, and it says i am missing a key to carry out the updates. I can't even enter synaptics while these updates are here. What do you advise I do? Uninstall all the programmes that need the updates, or find the keys (i have no idea how to make a key or find one, i would need help with this)

[http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=Error.png](http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=Error.png)

not the best picture, if you want a better one i can take another.

3mb0

---

### Post by dcstar on 2009-03-20
> **3mb0 said:**
> Ok i was using 32-bit Ubuntu 8.10 but i fancied a change, and with it i chose 64 bit, it seemed like more of a challenge, and it's prooving to be.

(I'm using Ubuntu 8.10 Ultimate Edition KDE)

So i finish installing the majority of updates, and there are 3/4 left uninstalled, and it says i am missing a key to carry out the updates. I can't even enter synaptics while these updates are here. What do you advise I do? Uninstall all the programmes that need the updates, or find the keys (i have no idea how to make a key or find one, i would need help with this)
......

ppa repositories have nothing to do with the official Ubuntu repositories, remove them from your /etc/apt/sources.list file.

This issue has little to do with 64 bit Ubuntu, it has to do with these put-together distros that "assume" that these extra repositories will always be there.

---

### Post by 3mb0 on 2009-03-20
> **dcstar said:**
> ppa repositories have nothing to do with the official Ubuntu repositories, remove them from your /etc/apt/sources.list file.

This issue has little to do with 64 bit Ubuntu, it has to do with these put-together distros that "assume" that these extra repositories will always be there.

Thank you very much, but i have only been using Ubuntu for around 2-3 months, and im realy not sure what things to get rid of in the sources.list file.

Screenshot of sources.list: [http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=Error1.png](http://s655.photobucket.com/albums/uu279/3mb0/?action=view&current=Error1.png)

Hope you can help

3mb0

---

### Post by drs305 on 2009-03-20
I don't think we can see the entire sources.list

A better way to present the information for analysis on this forum is to paste the contents within a "code" section. Hit the # symbol at the top of the post and it will enter a "code" section. Paste the contents of sources.list within the "code" entries.

To output the sources.list, type:
```

cat /etc/apt/sources.list

```

---

