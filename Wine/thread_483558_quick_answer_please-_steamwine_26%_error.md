---
title: "quick answer please- steam/wine 26% error?"
date: 2007-06-24
forum: Wine
---

### Post by mark. on 2007-06-24
so i was trying to get cs 1.6 to work on linux. i installed wine correctly (i think), winecfg/ect. works,

but when i launched steam, it stopped at 26%, but whenever i checked the error it said to run this
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
but when i launch that i get 
```
mark@l--desktop:~$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found

```
yeah. also the question with that solution in this faq said the problem was to fix if "Steam crashes at 26% of the update with a "Sharing violation"", but i have this--

ERROR: unable to open steam.exe for for reading (copying)
:/ how do i fix this?

(ps: when i originally put wine steam.exe into terminal it said that steam was'nt in the system32 folder, so i just copied the steam.exe file from the program files into the system32 folder, if that is what you are supposed to do) if that is any help.


anyway, thanks in advance, i can always rely on this forum :D

---

### Post by Keisad on 2007-06-24
Uhm... I don't think that you can just copy files like that...

Did you install it through synaptic or was it self compiled?

---

### Post by mark. on 2007-06-24
yeah, i was thinking that. i installed steam, its just that when i started it up it had that error

when i installed wine i used sudo apt-get install wine and then apt-get upgrade, got the apt keys (or w/e) and the gtk libraries too.

i dont know how to get the steam.exe into the system32 folder, so i just copied it :/

---

### Post by hikaricore on 2007-06-24
You're getting that error because you're trying to run Steam.exe from a directory it does not exist in.

When WINE fails to find a file in the current directory it starts checking PATH, which under WINE is pretty much limited to ~/.wine/drive_c/windows/system32

Always run software from the directory you have it in for best results, even after install.

---

### Post by mark. on 2007-06-25
hmm, makes sense. but when i put wine Steam.exe i get this

```
mark@l--desktop:~$ wine Steam.exe
wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found
```

i installed steam using the steam installer, is there anything else i have to do to make it run?

---

### Post by Keisad on 2007-06-25
I think I see what hikaricore is saying. You need to find the place where the executable steam file actually is. And then you can run it.

---

### Post by mark. on 2007-06-25
well the steam.exe is in c:/program files/steam/steam.exe (pretty sure), but how do i run the .exe from there without terminal? because whenever i put wine Steam.exe i get that error.

---

### Post by Keisad on 2007-06-25
I believe you have to use the terminal. The thing is, every time you try to run steam you are on your desktop. You need to switch to the directory into the folder that has steam.exe in ti. Than you can run

```
wine steame.exe
```

or whatever.

And I believe that wine emulates the windows file system... It may be in a folder such as home/user/.wine/programfiles/steam or something like that.

If you can't find it at all, then run

```
locate steam
```]

And a bunch of things will pop up. It's the basic search tool of linux. In that blob of information you should see the finle your looking for, with it's path right beside it. Just use cd and copy and paste, then run the file from there.

---

### Post by mark. on 2007-06-25
OMG TY--

yeah i dont know how to change directories (linux noob) but that did the trick, thank you.

---

### Post by KushMaster on 2007-09-10
I tryed all of this and nothing worked for me :(

---

