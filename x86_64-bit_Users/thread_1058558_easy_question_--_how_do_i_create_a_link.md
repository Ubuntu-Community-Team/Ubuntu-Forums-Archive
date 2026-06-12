---
title: "easy question -- how do i create a link?"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by sovietdoughnut on 2009-02-03
I need to create a link like the one mentioned in the following post:

>  
 Re: ut2004 wont run on 7.10 amd64 ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64
Similar problem here,

I installed ut2004 fine on ubuntu 7.10 then when i tried running it i get that same error everyone stated before:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I exported LD_LIBRARY_PATH to /usr/lib32 where this file is located but i now started getting the error:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS32

Does anyone have any idea how to solve this one? I noticed some of you spoke aboutut a file '2004-bin-linux-amd64' but after checking my install dir i don't seem to find that binary there.

Any Ideas? Thanks in advance for the help

Edit:
I've managed to get this going, i installed the 3369 patch then tried running the original ut2004-bin (not the one from the patch) it complained that libSDL-1.2.so.0 was wrong ELF class: ELFCLASS64 so i simply created a local link to /usr/lib32/libSDL-1.2-so.0 and voilá it all worked perfectly.

Hope this helps others with the same problem.


Alex
Last edited by alexuntu; October 26th, 2007 at 07:10 PM.. . 

how do i create a link to /usr/lib32/libSDL...?

---

### Post by NullHead on 2009-02-03
```
ln -s /from/here /to/here
```

Do it like that.

---

### Post by cdtech on 2009-02-03
He say's he created a link to his 32 bit library file. Just go into your 64 bit library (/usr/lib64) and create a link (symbolic) to the 32 bit library file.....

---

### Post by sovietdoughnut on 2009-02-03
I'm not sure if I did it right. The game still doesn't run. Here's what I did:

sudo ln -s /usr/lib64 /usr/lib32 

if i try something like

sudo ln -s /usr/lib64 /usr/lib32/libSDL-1.2.so.0

it says "file exists"

???

and how do i remove a link? i read the man page, but i didn't see anything about removing links?? i assume i need to remove the links that i don't need.

---

### Post by cdtech on 2009-02-03
You need the file to name the link:
```
sudo ln -s /usr/lib64/**libSDL-1.2.so.0** /usr/lib32/libSDL-1.2.so.0
```
That's if the file exist within the /usr/lib32 directory.......

---

### Post by jocko on 2009-02-03
> **cdtech said:**
> He say's he created a link to his 32 bit library file. Just go into your 64 bit library (/usr/lib64) and create a link (symbolic) to the 32 bit library file.....

> **sovietdoughnut said:**
> I'm not sure if I did it right. The game still doesn't run. Here's what I did:

[COLOR=Red]sudo ln -s /usr/lib64 /usr/lib32 [/COLOR]

if i try something like

sudo ln -s /usr/lib64 /usr/lib32/libSDL-1.2.so.0

it says "file exists"

???

and how do i remove a link? i read the man page, but i didn't see anything about removing links?? i assume i need to remove the links that i don't need.

> **cdtech said:**
> You need the file to name the link:
```
sudo ln -s /usr/lib64/**libSDL-1.2.so.0** /usr/lib32/libSDL-1.2.so.0
```That's if the file exist within the /usr/lib32 directory.......

1. The quote in the first post says "created a** local **link to /usr/lib32/libSDL-1.2-so.0".
This probably means he made a link from the **game directory** to the libSDL-1.2-so.0 file.
2. Making a link in the lib64 directory to a library in the lib32 directory will most certainly completely **break every 64 bit application** that needs that library.
3. The command [COLOR=Red]sudo ln -s /usr/lib64 /usr/lib32 [COLOR=Black]will probably cause** a lot of problems**. It will overwrite the link /usr/lib64 (which should be there and point to /lib[/COLOR][/COLOR]). If /usr/lib64 starts pointing to /usr/lib32 instead of the native 64 bit libs, things are bound to break.
4. It says "file exists" because now you have the made the link /usr/lib64 to point to /usr/lib32, so every file which is under /usr/lib32 will also be found in /usr/lib64... You need to repair the original link:
```
sudo ln -s /usr/lib64 /lib
```
5. Check [this page]("http://gaming.gwos.org/doku.php/guides:64bit:ut2004"). It seems to have some fairly sane and simple instructions for how to set up UT2004 to run on 64bit Ubuntu.
From what I can see there your problem is **a)** ut2004 is 32 bit, but can be patched into 64 bit. **b)** The game directory contains (32 bit) versions of libsdl and libopenal, so you need to remove those and make links to 64 bit versions, otherwise the game will try to use the bundled 32 bit libs... But all this is deskribed in the link...

---

### Post by sovietdoughnut on 2009-02-04
I got the game working, with a much more simple solution: 

install libstdc++5 -- ubuntu 8.10 comes with libstdc++6 which ut2004 doesn't like. you can have libstdc++5/6 installed at the same time :) thanks for everyone's help though, now i at least know how to create links if i need them :)

---

