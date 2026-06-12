---
title: "Games?"
date: 2005-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flac on 2005-07-16
I read that america's army and Enemy terretory run on ubuntu. Im not on my linux part atm so i havnt checked, wanted to ask if anyone knows if they run on 64 bit atm?

 Thanks in advance :)

---

### Post by Jet2k5 on 2005-07-16
As far as I know, yes it does work.  I'm downloading Americas Army right now so that when I get my computer I can just copy it over and be ready to play it.  AMD64's are backward compatable, which means they can executre 32-bit code.  Americas Army and Enemy Terretory don't have 64bit versions but the 32-bits will run just fine. 

Keep us posted on how it all turns out.  I'm hoping you come back with good results :) :-P

---

### Post by Tamir on 2005-07-16
do this : apt-get install linux32

- linux32 sh america's-army.run

many games are working like that.

---

### Post by Jet2k5 on 2005-07-16
[QUOTE=Tamir]do this : apt-get install linux32

- linux32 sh america's-army.run

many games are working like that.[/QUOTE]

That is going to help me a lot, thanks Tamir :)

---

### Post by Tamir on 2005-07-16
No problem  ;-)

---

### Post by Flac on 2005-07-16
Alright, following the directiosn of the wiki, i wget'ed enemy terretory. aftewards i did 

```
sudo ./et-linux-2.60.x86.run
```

to install,
> 
sudo: ./et-linux-2.60.x86.run: command not found

i then get this message, any hints on what i should do?

---

### Post by Jet2k5 on 2005-07-16
[QUOTE=Flac]Alright, following the directiosn of the wiki, i wget'ed enemy terretory. aftewards i did 

```
sudo ./et-linux-2.60.x86.run
```

to install,


i then get this message, any hints on what i should do?[/QUOTE]

First Link us to the wiki so that we can see what it's suggesting that you do.

Secondly have you tried running the game like Tamir suggested?  Running the game with the *linux32* command?  Try this,

```
sudo linux32 ./et-linux-2.60.x86.run
``` 

Don't know if that might work, but try doing it with and without the *sudo*

---

### Post by Flac on 2005-07-17
ok, finaly had time to reply, wiki 
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

THough the part i posted in code, was what it was telling me to do

 I tried the linux32 ./et-ectect. no go


when i try linux32 ./et-ectect.run, It spits at me that my permission is denied

 I tried it both with and without sudo same message either case.

---

### Post by Tamir on 2005-07-18
[QUOTE=Flac]ok, finaly had time to reply, wiki 
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

THough the part i posted in code, was what it was telling me to do

 I tried the linux32 ./et-ectect. no go


when i try linux32 ./et-ectect.run, It spits at me that my permission is denied

 I tried it both with and without sudo same message either case.[/QUOTE]
 do that with root - chmod 775 enemy_blabla.run,
and then normal user permission should be ok, or maybe you should try to run with root, or check if you have sudo at all.

---

### Post by DancingSun on 2005-07-20
I'm getting this error when executing the installer by "sudo ./et-linux-2.55.x86.run":
```
./setup.sh: line 143: 28527 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0
```
What does this mean?  My glibc-2.0 is not working?

---

### Post by Jet2k5 on 2005-07-20
[QUOTE=DancingSun]I'm getting this error when executing the installer by "sudo ./et-linux-2.55.x86.run":
```
./setup.sh: line 143: 28527 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0
```
What does this mean?  My glibc-2.0 is not working?[/QUOTE]


There seems to be someting with x86 ( which is 32-bit ) and glibc.  Try running it with the *linux32* command so that it would looks soemthing like this ...

```
linux32 ./setup.sh
``` 

Don't think that might work but it's worth the shot .

---

### Post by DancingSun on 2005-07-20
[QUOTE=Jet2k5]There seems to be someting with x86 ( which is 32-bit ) and glibc.  Try running it with the *linux32* command so that it would looks soemthing like this ...

```
linux32 ./setup.sh
``` 

Don't think that might work but it's worth the shot .[/QUOTE]

Oops, I pasted the wrong command, but yes, I tried the "linux32" in front as well...hence the output was "...have failed on x86/glibc-2.0", and not "...have failed on x86_64/glibc-2.0".

Actually, if I don't run it with "linux32" the installer will quit after extraction.

I wonder if it's because the glibc that we have is 64-bit and it's looking for the 32-bit glibc?

---

### Post by Tamir on 2005-07-20
[QUOTE=DancingSun]Oops, I pasted the wrong command, but yes, I tried the "linux32" in front as well...hence the output was "...have failed on x86/glibc-2.0", and not "...have failed on x86_64/glibc-2.0".

Actually, if I don't run it with "linux32" the installer will quit after extraction.

I wonder if it's because the glibc that we have is 64-bit and it's looking for the 32-bit glibc?[/QUOTE]
 are you sure glibc2-0 is installed ? I just know that I installed enemy terrirory on amd64 with no problem.

---

### Post by negatory on 2005-07-20
America's Army works "out of the box",I've been playing it and loving it but right now I'm waiting for the 2.4 version for linux to come outr.
ET I don't know...
Pedro Carrico

---

### Post by DancingSun on 2005-07-20
[QUOTE=Tamir]are you sure glibc2-0 is installed ? I just know that I installed enemy terrirory on amd64 with no problem.[/QUOTE]
Good point.  Well, according to Synaptic there isn't even a package called "glibc"... ](*,) 

Ok...time for America's Army....just how do I navigate that flash website without flash? ](*,)

Edit: Ok, I just typed americasarmy/downloads, good thing there urls are not oddly named...

Great, I only see Windows download...time to "yahoo"....

---

