---
title: "install molden and tinker"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by Kevin1234567 on 2008-10-29
Hi I am a total noob in linux. I need to install molden / gmolden and tinker!
I couldn't find it in the synaptec peketmanager so i went to the molden website: [http://www.cmbi.ru.nl/molden/molden.html](http://www.cmbi.ru.nl/molden/molden.html) 
They have a .tar.gz archive file I extrakted it but I didnt know what to do with the makefile I deleted all the # from the utrix flags
and tried the make and the make gmolden command.
but both times the terminal gave me this:
fort   -c -o atomdens.o atomdens.f
make: fort: Kommando nicht gefunden
make: *** [atomdens.o] Fehler 127

then I tried the executable file for linux(molden4.6.linux and gmolden4.6.linux) I made them executable but nothing happend when I doubleclicked them.

I am using a laptop with a core2duo if it helps solve the problem

thx 4 help

---

### Post by mali2297 on 2008-10-29
Revert to the original makefile, I don't think you need to change it.

Instead, install the package **g77** (and build-essential) from the repositories. Then try *make* again.

EDIT:
You're using 64-bit ubuntu? Then you might need to uncomment the line
```

#LIBS =  -L/usr/X11R6/lib64 -lX11 -lm

```
in the makefile (row 61).

---

### Post by Kevin1234567 on 2008-10-29
well it did more when I had the g77 but it stoped with:
it made like a million errors the last ones:
xwin.c:38673: Fehler: »SIG_IGN« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c: In Funktion »dos2u«:
xwin.c:38704: Fehler: »FILE« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38704: Fehler: »in« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38704: Fehler: »out« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38707: Fehler: expected specifier-qualifier-list before »time_t«
xwin.c:38709: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcpy«
xwin.c:38710: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcat«
xwin.c:38713: Fehler: expected expression before »)« token
xwin.c:38715: Fehler: expected expression before »)« token
xwin.c:38720: Fehler: »EOF« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38731: Fehler: »struct utimbuf« hat kein Element namens »actime«
xwin.c:38731: Fehler: falsche Benutzung des undefinierten Typs »struct stat«
xwin.c:38732: Fehler: »struct utimbuf« hat kein Element namens »modtime«
xwin.c:38732: Fehler: falsche Benutzung des undefinierten Typs »struct stat«
xwin.c:38743: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »fprintf«
xwin.c:38743: Fehler: »stderr« nicht deklariert (erste Benutzung in dieser Funktion)
make: *** [xwin.o] Fehler 1

---

### Post by mali2297 on 2008-10-29
> **Kevin1234567 said:**
> well it did more when I had the g77 but it stoped with:
it made like a million errors the last ones:
xwin.c:38673: Fehler: »SIG_IGN« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c: In Funktion »dos2u«:
xwin.c:38704: Fehler: »FILE« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38704: Fehler: »in« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38704: Fehler: »out« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38707: Fehler: expected specifier-qualifier-list before »time_t«
xwin.c:38709: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcpy«
xwin.c:38710: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »strcat«
xwin.c:38713: Fehler: expected expression before »)« token
xwin.c:38715: Fehler: expected expression before »)« token
xwin.c:38720: Fehler: »EOF« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:38731: Fehler: »struct utimbuf« hat kein Element namens »actime«
xwin.c:38731: Fehler: falsche Benutzung des undefinierten Typs »struct stat«
xwin.c:38732: Fehler: »struct utimbuf« hat kein Element namens »modtime«
xwin.c:38732: Fehler: falsche Benutzung des undefinierten Typs »struct stat«
xwin.c:38743: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »fprintf«
xwin.c:38743: Fehler: »stderr« nicht deklariert (erste Benutzung in dieser Funktion)
make: *** [xwin.o] Fehler 1

The first error message is usually the most informative, can you find it?

Have you installed build-essential and uncommented the line that I suggested?

---

### Post by Kevin1234567 on 2008-10-29
I unkommentet the line.
There are so many errors that the console won't show all the first the console shows when building gmolden are:
ser Funktion)
[I]xwin.c:35518: Fehler: »GL_AMBIENT_AND_DIFFUSE« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35518: Fehler: »AxesCol« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35518: Fehler: indizierter Wert ist weder ein Feld noch ein Zeiger
xwin.c: In Funktion »ogbegg_«:
xwin.c:35540: Fehler: »display« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35540: Fehler: »win« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35540: Fehler: »cx« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35552: Fehler: »theSurf« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35562: Fehler: »GL_COMPILE« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:35565: Fehler: »GL_FRONT_AND_BACK« nicht deklariert (erste Benutzung in dieser)
xwin.c:35565: Fehler: »GL_DIFFUSE« nicht deklariert (erste Benutzung in dieser Funktion)[/I]
and for the thing with only make:
[I]
xwin.c:31749: Fehler: »struct <anonymous>« hat kein Element namens »str«
xwin.c:31751: Fehler: »struct <anonymous>« hat kein Element namens »str«
xwin.c:31766: Fehler: »struct <anonymous>« hat kein Element namens »dflt«
xwin.c:31767: Fehler: »struct <anonymous>« hat kein Element namens »str«
xwin.c:31769: Fehler: »struct <anonymous>« hat kein Element namens »active«
xwin.c: In Funktion »RedrawMAP«:
xwin.c:31778: Fehler: »MAPwin« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c:31778: Fehler: »None« nicht deklariert (erste Benutzung in dieser Funktion)
xwin.c: In Funktion »ButtonsMAP«:
xwin.c:31801: Fehler: »struct <anonymous>« hat kein Element namens »str«
xwin.c:31801: Fehler: »struct <anonym[/I]

---

### Post by mali2297 on 2008-10-29
Install the packages **xorg-dev** and **libglu1-mesa-dev**.

---

### Post by Kevin1234567 on 2008-10-31
Thanks a lot that was it :) :guitar: . now I got problems installing tinker but I opened a new thread

---

