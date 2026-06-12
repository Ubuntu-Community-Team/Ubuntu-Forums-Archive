---
title: "Can't Install Unreal Tournament"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by NorthBridge4839 on 2008-08-29
I've followed many tutorials on how to install it and I've downloaded the package from different sources but I always get the same error.

snowman@snowman4839:~/Desktop$ bash ut-install-436-goty.run
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 416648479 1835706998

There is ALWAYS an error in the check sums. I'm running an x86-64 AMD Opteron 1.8Ghz (obviously x64 Ubuntu). 2Gb of RAM. Nvidia 6150 Graphics.

---

### Post by Crafty Kisses on 2008-08-30
What version of UT2k4 do you have. (collectors?)

---

### Post by tjotser on 2008-08-30
The poster is trying to run Unreal Tournament 99 GOTY.

Go to the loki installers for linux games-website here
[http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51)

this installer works for me.. when i type "sudo sh <name of installer>
then exit after it is installed. Then run the game as a normal user.
Good luck ! :KS

---

### Post by ynell on 2008-08-30
the unreal tournament install discs come with linux installers

if it doesnt come up auto then just view the files on it and you'll see it.. then just double click it and it'll do its thing

---

### Post by NorthBridge4839 on 2008-08-30
Now I get the error...

snowman@snowman4839:~/Desktop$ sudo sh unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................
/home/snowman/.setup2798: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by tjotser on 2008-08-30
oops, i forgot... the installer needs these...

"sudo apt-get install libgtk1.2"

happy Unrealing !!:popcorn:
See you in STD assault

---

### Post by Butthead on 2008-08-30
Using K/Ubuntu 8.04?  Install Wine using the "System Settings - Advanced Tab (found at top of page)".  Just went through exactly the same thing myself about a month ago. :guitar:

Only thing I haven't figured out yet is how to unpack UMOD files under Wine. :confused:  Game runs like a dream under it though. :)

---

### Post by soxs on 2008-08-31
> **Butthead said:**
> Using K/Ubuntu 8.04?  Install Wine using the "System Settings - Advanced Tab (found at top of page)".  Just went through exactly the same thing myself about a month ago. :guitar:

Only thing I haven't figured out yet is how to unpack UMOD files under Wine. :confused:  Game runs like a dream under it though. :)

Why do you even consider running the game with a "wrapper system" instead of pure native linux??

---

### Post by tjotser on 2008-08-31
> **soxs said:**
> Why do you even consider running the game with a "wrapper system" instead of pure native linux??

As he said, to unpack the umodfiles.

Original poster, did you get it to work after all ?

---

### Post by Butthead on 2008-08-31
> **soxs said:**
> Why do you even consider running the game with a "wrapper system" instead of pure native linux??

Because, for some reason, UT '99 doesn't want to seem to run on an x86_64 system without jumping through a bunch of hoops first. ](*,)

I'm all for making stuff as easy as possible. :wink:

---

### Post by soxs on 2008-09-01
> **tjotser said:**
> As he said, to unpack the umodfiles.

Original poster, did you get it to work after all ?

There is a script somewhere out there (a perl one) to extract UMOD archives.

Note:
I googled a little and I came across this:
```
/path/to/ucc-bin umodunpack -x <umod_file>
```

---

### Post by Butthead on 2008-09-01
I heard that "umodpack" requires you to have a lot of Perl libraries installed first before it supposedly will work for you in Linux. :confused:

That takes it out of the "quick & easy" category right there for me. :)

Now, since Wine runs Windows programs, why not have a standalone Windows UMOD unpacker?

---

### Post by tjotser on 2008-09-03
> **Butthead said:**
> I heard that "umodpack" requires you to have a lot of Perl libraries installed first before it supposedly will work for you in Linux. :confused:

That takes it out of the "quick & easy" category right there for me. :)

Now, since Wine runs Windows programs, why not have a standalone Windows UMOD unpacker?

[http://www.acordero.org/prog_proj_UTUMODEX.html](http://www.acordero.org/prog_proj_UTUMODEX.html)
Umod Extractor, i have not tried it as i do not need any mods for my UT. If you know any cool mods and what they do, i am willing to try them..

---

### Post by Butthead on 2008-09-04
> **tjotser said:**
> [http://www.acordero.org/prog_proj_UTUMODEX.html](http://www.acordero.org/prog_proj_UTUMODEX.html)
Umod Extractor, i have not tried it as i do not need any mods for my UT. If you know any cool mods and what they do, i am willing to try them..

Thanks for the link!  Unfortunately, it doesn't tell you if you need to have certain Perl libraries installed first before it will work. :confused:

As for UMOD files, I believe the special bonus map packs but out by InfoGames for Christmas and stuff were all (packed?) as UMOD's.  That, and u4e (a cool looking modification for UT '99) all come as UMOD's. :mad:

---

