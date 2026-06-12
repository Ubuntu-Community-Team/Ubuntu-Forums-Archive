---
title: "[SOLVED] Java5 and JabRef"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by blurp on 2007-07-04
I have problems using JabRef from the archive.ubuntu.com repo.
Initially I couldn't find JabRef using apt-cache but later on after some googling, I found it in [http://archive.ubuntu.com/ubuntu/pool/multiverse/j/jabref/]("http://archive.ubuntu.com/ubuntu/pool/multiverse/j/jabref/").

So I downloaded the deb file and using dpkg -i. There is a app launcher in my gnome menu for jabref, but it does not work. The JabRef 2.2 splash screen does appear but the subsequent main window is greyed like the screenshot attached.

Has anyone else gotten JabRef to work?

My JRE is sun-java5-jdk installed through apt-get and I'm using the amd64 platform.

---

### Post by blurp on 2007-07-04
sorry, somehow i can't seem to attach a screenshot. The forum automatically logs me out whenever I do so.

I shall try to describe it. The main window appears with the window title "JabRef". But everything inside the window is grey. There's nothing that can be done after this except clicking on the "close" button in the title bar.

---

### Post by gaylapdancer on 2007-07-04
Try opening it via the terminal and post the error

---

### Post by blurp on 2007-07-04
well, typing "jabref" in terminal gives no output at all. Giving an argument like this gives
```
xxx@yyy:~$ jabref abc.bib
Opening: abc.bib
```

In both cases, the splash window showing "JabRef 2.2" appears and the grey window persists. No amount of clicking (regardless of left or right buttons) on the window does anything.

I just noticed something: if i mouseover some parts of the grey window, the mouse pointer changes to a cursor, as if there is some input box. Then when I hit the "X" button, a warning appears: "Database has changed. Do you want to save before closing?". Maybe it is some of the random keys I hit... but this means jabref is working internally but somehow the interface doesn't show up properly.

I tried the beta jabref 2.3 and I got the same grey window. But this time at least the context menu appears when I right-click on some parts of the window.

The output at the terminal for 2.3beta is
```
Opening: abc.bib
Opening: /home/xxx/abc.bib
Jul 4, 2007 6:38:15 PM net.sf.jabref.Globals logger
INFO: Could not get key binding for "Synchronize files"

```

Is there something wrong with Java or JabRef or even Compiz and nv?

---

### Post by blurp on 2007-07-04
I found the solution from [here]("http://www.pdfsam.org/bbforum/viewtopic.php?p=121&sid=81f9c4bc0def9f444d7d1f4b1eed1f5f"). The problem is due to Compiz/Beryl.

---

