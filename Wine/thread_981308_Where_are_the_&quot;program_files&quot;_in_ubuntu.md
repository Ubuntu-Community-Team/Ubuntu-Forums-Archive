---
title: "Where are the &quot;program files&quot; in ubuntu?"
date: 2008-11-13
forum: Wine
---

### Post by F4T4LFL4W on 2008-11-13
Well I installed a game but now I need to find the folder where it is installed like in windows program files but where is that in Ubuntu?

---

### Post by quimico69 on 2008-11-13
You can check under 
/usr/games 
/usr/share
/usr/local

anyway, why do you need to find the folder.  Usually all your settings and preferences should be stored in a hidden folder in your home directory.  Try

ls -al

to see all the hidden folders (the ones that start with a dot).  Maybe you will recognize the one that belongs to the game in question, because it has the same name as the game.

---

### Post by F4T4LFL4W on 2008-11-13
i need it because I am installing a trainer and to use it I need to put it in the root.

---

### Post by quimico69 on 2008-11-13
Hmmm... isn't that taken care of by the program installer?  Or are you running a windows game under wine?

A little more info would really help in diagnosing this:

what is the name of the game? 
is it a linux version or is it a windows version under wine?
how did you install the game? through synaptic? apt-get? compiled from source?

each case should be dealt with differently

---

### Post by F4T4LFL4W on 2008-11-13
there we go. I found it. it was under wine.

---

### Post by quimico69 on 2008-11-13
glad to hear that.

---

