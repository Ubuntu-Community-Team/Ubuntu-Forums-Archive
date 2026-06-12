---
title: "Error: Allowcating Virtual Memory, and why?"
date: 2008-11-07
forum: Wine
---

### Post by westomopresto on 2008-11-07
HERE IS THE ORGINAL POST: [http://ubuntuforums.org/showthread.php?t=948170]("http://ubuntuforums.org/showthread.php?t=948170")
```
Error: Allowcating Virtual Memory
```
[SIZE="5"][COLOR="Sienna"]**_Question_**[/COLOR][/SIZE]

I get that error with wine after running this game called **Blockland.**
It happens every once and a while, and i already posted a topic on this. 
but im asking again, please give me some ideas on why its giving me this error
```
Error: Allowcating Virtual Memory
```
the actuall game runs fine. its only giving me this error after a couple of hours .
(i run a dedicated server with this.)

[SIZE="5"][COLOR="sienna"]**_More Info_**[/COLOR][/SIZE]

*I use WINE completely though.. that makes sense.*
What i mean by *That* is that the game is completely ran through wine. 
its not a linux game or anything
so please post, see if you can help :D
all help is great! throw some ideas at me.
thanks -Westomopresto :confused:

**EDIT:**
> **YokoZar said:**
> Is that an error in the console, or a message the application itself is throwing (like in a message box)?

Its a message box
but it comes up in a WINE error window, not a ubuntu window.

_**ScreenShots**_
If i can get it on a screen shot
( if i can catch it again, i will upload a screen shot to clear some things up )

---

### Post by westomopresto on 2008-11-07
Bump

---

### Post by asdfoo on 2008-11-07
> **westomopresto said:**
> Bump

fyi, your post was really confusing to read with all the edits and we prefer to say Wine rather than WINE

as someone who has never used this program before, what is the simplest way for me to reproduce the problem?

---

### Post by westomopresto on 2008-11-07
> **asdfoo said:**
> fyi, your post was really confusing to read with all the edits and we prefer to say _Wine rather than WINE_

as someone who has never used this program before, what is the simplest way for me to reproduce the problem?
here is how i get the problem.
install blockland
[www.blockland.us](www.blockland.us)
v10 is the latest
then once installed. make a short cut on the desktop
(there should be one there)
on the short cut, right clikc, go to properties or what have you
and at this to the target line
-dedicated -map bedroom
it should look something like this
```
C:\Blockland\Blockland.exe -dedicated -map bedroom
```
then click on the short cut, this will start a server.
im not sure if the problem will occur with you, considering you don't own blockland, it might not let you host.
although. the problem does occur with me, when no one is on my server.
so i guess its worth a try

---

### Post by asdfoo on 2008-11-07
> **westomopresto said:**
> here is how i get the problem.
install blockland
[www.blockland.us](www.blockland.us)
v10 is the latest
then once installed. make a short cut on the desktop
(there should be one there)
on the short cut, right clikc, go to properties or what have you
and at this to the target line
-dedicated -map bedroom
it should look something like this
```
C:\Blockland\Blockland.exe -dedicated -map bedroom
```
then click on the short cut, this will start a server.
im not sure if the problem will occur with you, considering you don't own blockland, it might not let you host.
although. the problem does occur with me, when no one is on my server.
so i guess its worth a try

> 
**********************************************************
*                                                        *
*  Authentication Key required for hosting internet game *
*    Input key by via setKey("XXXXX-XXXX-XXXX-XXXX");    *
*                    (Dont screw up)                     *
*                                                        *
**********************************************************


Hmm... seems I need to be registered.

---

### Post by westomopresto on 2008-11-07
> **asdfoo said:**
> Hmm... seems I need to be registered.

Hm, well try hosting a LAN game, you dont need registration for that.
it should give you a error message
Hopefully.. this.
> error: allowcating virtual memory
thanks for you help though.

---

### Post by westomopresto on 2008-11-07
BUMP for the love of god.
:D

---

### Post by asdfoo on 2008-11-08
> **westomopresto said:**
> BUMP for the love of god.
:D


There's no point bumping this.  I don't mind trying to help, but please have some patience.

Both Lan and Internet are not selectable in the demo.  I've started a new game and I'll let it run for awhile.

---

### Post by asdfoo on 2008-11-08
> **asdfoo said:**
> There's no point bumping this.  I don't mind trying to help, but please have some patience.

Both Lan and Internet are not selectable in the demo.  I've started a new game and I'll let it run for awhile.

Memory usage remained consistent at 319MB resident for 45 minutes.

---

### Post by westomopresto on 2008-11-09
> **asdfoo said:**
> Memory usage remained consistent at 319MB resident for 45 minutes.
ok, well that doesn't help.
45 minutes, is not long enough
and in some cases the server crashes with in 5 min
sorry if i sound rough/harsh. im just irritated at this crashing! 
i need some more responses!
any comment filled with a idea can help!
thanks
-westomopresto

---

### Post by westomopresto on 2008-11-09
ok ok. i have something
ive been seaching all day and night now..
and i came up witht this
aparently i need more virtual memory.
thats it?

---

### Post by asdfoo on 2008-11-09
> **westomopresto said:**
> ok ok. i have something
ive been seaching all day and night now..
and i came up witht this
aparently i need more virtual memory.
thats it?

if there's an underlying problem the solution isn't to add more memory, it's to find out where the leak is occuring, why it is occuring by comparing it to the windows behaviour and then writing a fix.

if 45 minutes in the demo not long enough, how long is long enough?

---

### Post by westomopresto on 2008-11-10
> **asdfoo said:**
> if there's an underlying problem the solution isn't to add more memory, it's to find out where the leak is _occuring_, why it is _occuring_ by comparing it to the windows _behaviour_ and then writing a fix.

if 45 minutes in the demo not long enough, how long is long enough?
Misspelled words in above post
-behavior
-occurring
:D lol sry

well i don't think that 45 min will test this accurately.
we need a ubuntu/wine developer to come in here!

EDIT: and on second thought. the demo isn't a very good recreation of what i was doing.
i was hosting a server.
its a little different.
thanks for trying though :P

---

### Post by westomopresto on 2008-11-13
ok, i really need some help on this thing. its pissing me off!
i even tried crossover games... make the bad memory's go away! 
:-({|=

---

### Post by YokoZar on 2008-11-13
I don't know, really.  If it only happens in Wine (and not Windows) then it's probably a Wine bug somewhere, though if it's a memory leak it might be hard to pin down exactly.

Also it's mildly amusing that the error message misspells "allocate" ;)

---

### Post by westomopresto on 2008-12-05
> **YokoZar said:**
> I don't know, really.  If it only happens in Wine (and not Windows) then it's probably a Wine bug somewhere, though if it's a memory leak it might be hard to pin down exactly.

Also it's mildly amusing that the error message misspells "allocate" ;)
Its also mildly amusing that i even asked my question here.
This forums is no help.

---

