---
title: "[SOLVED] Running Wine with Trickle"
date: 2008-06-19
forum: Wine
---

### Post by Plasma_NZ on 2008-06-19
Ok, im using trickle to try and prevent a wine application from chewing all my upload...

i use the follow - and it doesnt seem to work..

trickle -u 20 wine-app

yet it still goes far above what i set it at... any ideas.?

---

### Post by cogadh on 2008-06-19
This is a blind guess here, but Trickle is probably trying to limit the Wine application (wineserver) and not the application that you are running through Wine, which is actually a separate process from the wineserver. I don't know anything about Trickle, but is it possible that you could run it separate from the Wine command? That way you could apply to the actual executable, instead of to the wineserver.

---

### Post by YokoZar on 2008-06-19
Maybe you could try making a small script that launches the wine application.

Eg script foo has:
wine bar.exe

Then you run trickle foo

---

### Post by Plasma_NZ on 2008-06-24
none of the above worked...

Solved by setting up another box with windows... WIne just doesnt cut the cake...

---

### Post by Freaky#Funga on 2008-08-14
I don't think this thread should be marked as solved, until it really solves a problem. I wanted to use trickle with wine and there is no advance in this thread for me. :(

---

