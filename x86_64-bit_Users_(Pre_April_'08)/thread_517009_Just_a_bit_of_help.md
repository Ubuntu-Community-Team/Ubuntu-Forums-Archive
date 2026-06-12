---
title: "Just a bit of help"
date: 2007-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-08-03
I couldn't thing of a title for this but what I want to do it is have a file deleted when I open a program. i want to have the clientregistry.blob deleted when I open steam. For some reason I have to delete it before I can start steam.  If I can do this please help me out.

---

### Post by ashvala on 2007-08-04
Which file & which program... It depends.

---

### Post by bford16 on 2007-08-04
> **DaGGer said:**
> I couldn't thing of a title for this but what I want to do it is have a file deleted when I open a program. i want to have the clientregistry.blob deleted when I open steam. For some reason I have to delete it before I can start steam.  If I can do this please help me out.

You could always start the program with a script, by creating a file in nano, then running the file with the "sh" command.

In a Terminal, type "nano filename."

Add something like the following.

rm \path\to\file
openprogram

Save the file.

I created a plain text file with nano to open Mirage (an image viewer) in a certain directory.  When I want to run the program, I just type "sh file" in a terminal. I also created a launcher for this program with the "sh file" command.  This method should work, as long as you don't need sudo to remove the file.

---

