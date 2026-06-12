---
title: "Is a bookmarkable PDF reader available?"
date: 2007-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by BobHur on 2007-11-30
I like Evince, but when I leave it and return I restart from page one. I'm fairly certain I was using a viewer in the 32bit version that returned you to your last spot when you reopened the file, but I can't remember what it was. Is there a PDF viewer with bookmarks (auto or manual) for 64bit?

---

### Post by Cappy on 2007-11-30
kpdf does this
```
sudo apt-get install kpdf
```

---

### Post by saru411 on 2007-11-30
envince loads from where i left off on my .pdfs. im unsure of why it doesnt do that for you

---

### Post by mutz on 2008-04-24
Hmm, Cappy, I don't think Kchmviewer reads pdf...or is there something I missed on their website?
> Kchmviewer does this

Anyone else...? Is there anything that supports multiple bookmarks?

---

### Post by Cappy on 2008-04-24
> **mutz said:**
> Hmm, Cappy, I don't think Kchmviewer reads pdf...or is there something I missed on their website?


Anyone else...? Is there anything that supports multiple bookmarks?

My mistake. kpdf is what you are looking for.
```
sudo apt-get install kpdf
```

Also, the "official" adobe reader version supports multiple bookmarks (it's 32-bit though and I remember it was a pain to install, there are some tutorials on installing it).

---

