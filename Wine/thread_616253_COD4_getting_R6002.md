---
title: "COD4 getting R6002"
date: 2007-11-18
forum: Wine
---

### Post by finito on 2007-11-18
I tried looking around so far i have gotten to a splash screen saying R6002 Floating point not supported.
I am running Gutsy 7.10 64-bit

I have a AMD64 4400+ with a 7300GT. I have tried cedega as well, but I can't even get it to installl with that...

I have tried installing C++ Runtime files 64-bit to no avail.

any help appriciated.

---

### Post by subs on 2007-11-18
speaking only from c/c++ background

the app is using scanf() to read a float value from the console into an uninitialized float var a R6002 "floating-point format support not loaded" error creeps up

initialize the float var or use the var in an expression in the routine that contains the scanf() call

heres an example

> 
#include <stdio.h>

//float x ;
main()
{
      x = 100.101 ;
      scanf ("%f", &x) ;
      printf ("%f\n", x) ;
}



remove the comment on the variable initialization or add a suitable variable declaration

---

### Post by finito on 2007-11-18
COD4 as in Call of Duty 4. How do you suggest I get the source code of it...

---

### Post by Polygon on 2007-11-18
its most likely not supported in wine yet as it just came out....

---

### Post by cogadh on 2007-11-18
Current Wine AppDB rating is "garbage", meaning it doesn't work in Wine (yet):
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699)

---

### Post by finito on 2007-11-18
I found this, it clims to make it work but I'll be darned if i know what to do..
can anyone tell me how to use that patch...

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4")

---

### Post by SM0k3 on 2007-11-18
> **finito said:**
> I found this, it clims to make it work but I'll be darned if i know what to do..
can anyone tell me how to use that patch...

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4")

I was going to attempt this but I haven't been able to successfully compile the cvs always get an error.

---

### Post by subs on 2007-11-19
Its a problem with your windows emulator

i had a similar problem when i was installing bioshock on my windows box... 

i sorted it out by updating my .net framework...

what version of  wine / cedega are u using

---

### Post by finito on 2007-11-19
wine 0.9.49 and cedega 6.0.3
Cedega stops at setup installer.
I will try updating the .net framework but u want me to install directly or update a few files...

---

### Post by cogadh on 2007-11-19
> **subs said:**
> Its a problem with your windows emulator

i had a similar problem when i was installing bioshock on my windows box... 

i sorted it out by updating my .net framework...

what version of  wine / cedega are u using
***W***ine ***I***s ***N***ot an ***E***mulator. 

BioShock had that problem because it requires up to date .NET to run, CoD4 does not require .NET at all, so installing or updating .NET in Wine won't help at all.

As for that patch, it dates from July, so I think whatever it fixed is actually already included with the latest Wine, but I'm not 100% sure about it. If you want to try it, all you need to do is download the current Wine sources and the patch, "cd" to the directory they are in and run the commands as described in that how-to.

---

### Post by drarem on 2007-11-19
I would wait for the COD4 linux client release and run it in native code =)

---

### Post by finito on 2007-11-19
@ cogadh : I don't know how to do that, when i click the link that says patch i go to another web page that shows some code, what do i do after that please I need step by step guide. as I am still very new to UNIX command line..

---

### Post by hikaricore on 2007-11-19
> **drarem said:**
> I would wait for the COD4 linux client release and run it in native code =)

I really hope you're joking.

Why do all you people think that there will be a native linux client for COD4?
Did I miss the announcement that they're porting it or something??

---

### Post by jacob01 on 2007-11-19
is their going to be a linux client for cod4

if their is that would be awsome:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by finito on 2007-11-19
Well, even with all the cross-platform releases, I believe linux ports wont be released for a good while. Mac are starting to get  cross-platform releases (i.e WOW)

maybe in 5 or so years (being really optimistic) we might see cross-platform releases which include Linux...

But i guess the main problem is too many distros. 

I mean testing phase of the game is going to go through the roof if they include linux. Surely they will have to at least test all the "main" distros such as RedHat, SUSE, Mandrake, Ubuntu, etc. (There are quite a bit) So maybe Linux cross-platform releases may just have to stay a dream..

---

### Post by hikaricore on 2007-11-19
If developers would include required libraries in the game installation files aside from things specific to video drivers, I fail to see why the number of distros would have anything to do with games not being ported.
The whole distro problem is just an excuse that works because the public doesn't really understand how anything works.

---

### Post by finito on 2007-11-19
Every game has to be tested throughly on every platform it is to be released. Correct me if i am wrong but testing phase is supposed to be 40~50 % of the whole time taken to release the software.

Now lets say they don't test all the main distros but they will have to test at lest two or three types. I am not sure but I would guess that would at least add a few months to the release.

---

### Post by hikaricore on 2007-11-19
While you are close on the testing (give or take depending on the company) phase time...

A properly configured system with the proper libraries included locally in one of the game's folders would make cross-distro testing unneeded.

Me thinks you missed my point.

---

### Post by finito on 2007-11-20
> **hikaricore said:**
> A properly configured system with the proper libraries included locally in one of the game's folders would make cross-distro testing unneeded.


Golden Rule of programming the user is stupid. Although that doesn't hold true for most Linux users (I may be wrong). You can't expect any Commercial company to send out a game untested, it's their reputation at stake, even if every single Linux user made a petition that they don't mind buggy products (which I must say is better than nothing) I fully doubt they (the Commercial company) would agree. 


P.S. has any1 been able to make COD4 work yet that is what the post is about or at least was about..

---

### Post by subs on 2007-11-22
> **cogadh said:**
> ***W***ine ***I***s ***N***ot an ***E***mulator. 

BioShock had that problem because it requires up to date .NET to run, CoD4 does not require .NET at all, so installing or updating .NET in Wine won't help at all.

As for that patch, it dates from July, so I think whatever it fixed is actually already included with the latest Wine, but I'm not 100% sure about it. If you want to try it, all you need to do is download the current Wine sources and the patch, "cd" to the directory they are in and run the commands as described in that how-to.

finito is getting the error is showing that cod4 is somehow trying to use some micrsoft visual c++ code.... so i thght that there may be a problem in the software wine is using to **"**emulate**"** windoze

---

### Post by hikaricore on 2007-11-22
> **subs said:**
> finito is getting the error is showing that cod4 is somehow trying to use some micrsoft visual c++ code.... so i thght that there may be a problem in the software wine is using to **"**emulate**"** windoze

There is no "emulation" of any sort taking place.  WINE does API conversion.

---

### Post by lightrush on 2007-11-27
finitto,

It is the crack thats faulty. There is a second release by RAZOR1911 which worx. :popcorn:

---

### Post by Mr_HeNtAi on 2007-11-29
It seems the game is now rated as Silver status on the WINE site. I'll have to give it a try.

---

