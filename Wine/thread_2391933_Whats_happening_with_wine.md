---
title: "Whats happening with wine?"
date: 2018-05-14
forum: Wine
---

### Post by me-mitch on 2018-05-14
I installed wine 3.0 on ubuntu 18.04 and when i log back in to ubuntu the config doesn't show up.

---

### Post by monkeybrain20122 on 2018-05-14
Because all .desktop files associated with wine are missing .[https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326](https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326)

You can start wine config by typing in the terminal.

```
winecfg
```

For right clicking to run an .exe file, you need wine.desktop for wine program loader to show up as an option in the "open with menu". wine.desktop still exists but is deliberately put in a "wrong" location, to restore it
```

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

I don't know the full story, but these changes apparently have something to do with some security considerations in Debian and trickle down to Ubuntu.

---

### Post by me-mitch on 2018-05-15
Winecfg worked but the last command didn't do anything no problem i was thinking i did something wrong i can access it from the command when i need to.

Thank you

---

### Post by mc4man on 2018-05-15
Personally i use this version of wine-stable, it includes all the expected & useful .desktop files
[https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)

(the next version of nautilus is [dropping support for .desktop and binary files altogether]("https://www.omgubuntu.co.uk/2018/05/nautilus-remove-ability-launch-binaries-apps"), nemo here..

---

### Post by mlnease on 2018-06-12
> **monkeybrain20122 said:**
> Because all .desktop files associated with wine are missing .[https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326](https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326)

You can start wine config by typing in the terminal.

```
winecfg
```

For right clicking to run an .exe file, you need wine.desktop for wine program loader to show up as an option in the "open with menu". wine.desktop still exists but is deliberately put in a "wrong" location, to restore it
```

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

I don't know the full story, but these changes apparently have something to do with some security considerations in Debian and trickle down to Ubuntu.

Fantastic MB, thanks a million.  I haven't worked it out yet but am very glad to have the problem explained.  I should've found these posts earlier I guess--thanks for your diligence, time and attention.

---

### Post by DGINSD on 2018-10-13
Do the Ubuntu devs understand that for new users they've essentially broken wine with that change, and making such a change without a non-complicated (read graphical) workaround, even if temporary, would frustrate the hell out of a new users? A good learning experience perhaps, but for someone moving from windows, being told there's easy ways to run windows programs; a big turn off. I have some experience and it was frustrating, wine is frustrating enough as is, or as was.

---

### Post by wildmanne39 on 2018-10-13
Devs almost never come to the forum, you will have to contact them through other means if you want them to answer your question.

---

### Post by nicholasarussell on 2019-02-21
I can use Wine via the Terminnal

I tried your fix and it is still not working, unsure what else to try at this point :) running latest  LTS 18.04 fully updated.

updates and upgrade and autocleanup been completed also.

If you have any other tips to get this showing would be awesome :P

---

### Post by nicholasarussell on 2019-02-21
oh could be that I am using the staging branch for Cemu

---

