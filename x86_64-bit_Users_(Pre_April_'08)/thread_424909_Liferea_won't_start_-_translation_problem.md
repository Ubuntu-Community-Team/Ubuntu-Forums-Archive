---
title: "Liferea won't start - translation problem"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Garyu on 2007-04-27
I wanted to monitor an RSS channel, so I thought I would install Liferea. I did so using the "Add applications" thing in the menu. But when I try to start Liferea it just dies and disappears without explanation. So I tried running it from a terminal, and I got an error report about "kanallista.opml".

So it's looking for the file "kanallista.opml" which does not exist. But there does exist a "feedlist.opml". So I'm guessing they translated the name somewhere but forgot to translate somewhere else. A simple copy solved the problem, "sudo cp /usr/share/liferea/opml/feedlist.opml /usr/share/liferea/opml/kanallista.opml".

I don't know anything about bug reporting, but if someone could make a note of this and fix it, that would be grate. :)

PS. Feisty Fawn x64 is what I use...

---

