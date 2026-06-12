---
title: "problem with lotrolinux"
date: 2008-05-24
forum: Wine
---

### Post by adramalech on 2008-05-24
okay everytime i run lotrolinux it gives me this...

[html]adramalech@adramalech:~/Desktop/Turbine/The Lord of the Rings Online$ mono LotROLinux.run

(LotROLinux:6777): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(LotROLinux:6777): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
[/html]

i don't understand what to do....i have all the files extracted and in the the lord of the rings online folder...

i get this message by the launcher...

Initialising, please wait...
No language files found.

---

### Post by ajackson on 2008-05-25
> **adramalech said:**
> okay everytime i run lotrolinux it gives me this...

[html]adramalech@adramalech:~/Desktop/Turbine/The Lord of the Rings Online$ mono LotROLinux.run

(LotROLinux:6777): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(LotROLinux:6777): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
[/html]

i don't understand what to do....i have all the files extracted and in the the lord of the rings online folder...

i get this message by the launcher...

Initialising, please wait...
No language files found.
OK I have a series of questions
- Why are you running using mono LotROLinux.run?
- What version of LotROLinux have you got (if the instructions are saying run it that way)?
- Why not ask in the main LOTRO thread?

---

### Post by adramalech on 2008-05-25
well maybe i should run it in lotro thread...

but it says to use ./LotROLinux.run or mono LotROLinux.run....i was just wondering if someone is having the same issue...

---

### Post by ajackson on 2008-05-25
> **adramalech said:**
> well maybe i should run it in lotro thread...

but it says to use ./LotROLinux.run or mono LotROLinux.run....i was just wondering if someone is having the same issue...
OK I'll try one last time.

What version of LotROLinux are you using?

---

### Post by adramalech on 2008-05-25
version 0.9.1.1

---

### Post by ajackson on 2008-05-26
> **adramalech said:**
> version 0.9.1.1
Don't see where you found the instruction to run it via mono ./LotROLinux.run if you have that version.

OK delete the directory ~/.LotROLinux

compile & install LotROLinux

Run using LotROLinux and set it up

---

### Post by adramalech on 2008-05-30
i am sorry but what is the syntax for removing the directory???

2nd thing is that i don't know how to use the Mozilla launcher for it...from what i understand there is only 3 ways to launch lotro...one is to use the cli, the other is to use mono compiler and lotrolinux, and the third is using Firefox and lotrolinux...

which one should i use because i didn't like the cli launcher and i like the gui launcher but the mono compiler one doesn't seem to work...

and i learned how to install and run the lotrolinux from the readme that came with the file

---

### Post by ajackson on 2008-05-31
> **adramalech said:**
> i am sorry but what is the syntax for removing the directory???
in this case it would rm ~/.LotROLinux

> 2nd thing is that i don't know how to use the Mozilla launcher for it...from what i understand there is only 3 ways to launch lotro...one is to use the cli, the other is to use mono compiler and lotrolinux, and the third is using Firefox and lotrolinux...
I don't know anything about a Mozilla launcher so I can't help you with that one. Unless you are referring to the version of LotROLinux that uses the Gecko web browser on the left hand side.

> which one should i use because i didn't like the cli launcher and i like the gui launcher but the mono compiler one doesn't seem to work...
The GUI launcher (if you are referring to LotROLinux) is the mono compiled one, so I'm not certain what you are going on about.

Do you have a version of LotROLinux that you can run by typing LotROLinux (or selecting it in Applications -> Games)?

---

### Post by adramalech on 2008-05-31
yeah i was talking about the gecko one....

i don't understand how the package manager one works do i just install the package??? is that the one u want me to install???

EDIT: okay i got the launcher where i don't have to go through mono compiler...but still get the NO Language found error is there something wrong with the code or am i missing a file??

It seems that the language.cs file isn't being read correctly...what class would call the language.cs file inorder to get the options????

---

### Post by ajackson on 2008-06-01
> **adramalech said:**
> i don't understand how the package manager one works do i just install the package??? is that the one u want me to install???
With the ones in the package manager you can just install them without needing to do anything else to them (like compiling). If you are using a gnome based distro (ie Ubuntu) you should have a menu option in Applications -> Games. Not sure if it adds one for KDE based distros.

> EDIT: okay i got the launcher where i don't have to go through mono compiler...but still get the NO Language found error is there something wrong with the code or am i missing a file??
You need to go to Tools -> Options and set the Game Directory to the place where you installed Lord of the Rings. While in options set the patch window to simple as complex doesn't seem to work properly anymore.

---

