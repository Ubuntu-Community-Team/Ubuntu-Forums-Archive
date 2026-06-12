---
title: "Creating a new Java File"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by Sakrimo on 2008-06-21
Hey, i am a fairly new user to Ubuntu, but i have set up most of my Java environment already (OpenJDK), and it seems to be running okay!

The only problem that I have however, is that when i type:

edit examplejavafile.java

To create a new java file, i'm taken into a screen in the terminal, rather than Scite(it's the closest editor I could find for Linux to Notepad++).

I've got a feeling theres a pretty easy way to solve this, but I can't even remember how managed to set it up on Vista! anyone know this one?

---

### Post by jamesstansell on 2008-06-21
If you want the edit command to work I think you'll need to configure your MIME settings.  That's something I haven't messed with for a long time.

Can you just type scite instead of edit?

---

### Post by jpkotta on 2008-06-22
jamesstansell is right, "edit" uses MIME types to pick the editor program (I don't know how to change MIME types either).  FYI, other programs look at the EDITOR env variable.  Personally, I make an alias in my ~/.bashrc:
```

export EDITOR=xemacs
alias E=$EDITOR

```

---

### Post by Sakrimo on 2008-06-22
thanks guys for the quick replies! that works fine, also helped me to realise how fast Scite and Ubuntu are together, can't wait to push it on some big applets later on to see how it handles it, but i was somewhat very impressed by how fast scite opened up and closed down!

---

