---
title: "Problems running two unity based games (slender and reciever) under playonlinux"
date: 2012-08-16
forum: Wine
---

### Post by javajames79 on 2012-08-16
I recently reinstalled ubuntu on a new drive after having problems with the old one, and i've noticed a few problems in games; specifically to do with 32 bit and 64 bit libraries. I'm running a 64 bit machine, and i'm trying to run slender and receiver through playonlinux with this [http://www.playonlinux.com/en/topic-9111.html](http://www.playonlinux.com/en/topic-9111.html) script - which worked fine on my previous install, however no matter what i do - i've tried reinstalling with no luck - i can't get the games to function. They always come up with this error:

```
[POL_Wine_SetVersionEnv] Message: Setting wine version path: 1.4-rc4-raw3, x86
[POL_Wine_SetVersionEnv] Message: "/home/james/.PlayOnLinux//wine/linux-x86/1.4-rc4-raw3" exists
[POL_Wine] Message: Running wine-1.4-rc4-raw3 Receiver.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\Receiver.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Receiver.exe" failed, status c0000135
[POL_Wine] Message: Wine return: 53
```

Has anyone had this problem before? i've checked winemenybuilder.exe exists and i have 32 bit mesa installed too. Am i missing any GL libraries? If anyone knows anything about this i'd be grateful. Thanks.

---

### Post by javajames79 on 2012-08-20
The games where not getting access to the 32 bit libraries. Solved.
 
I just:
~
```
export LD_LIBRARY_PATH=/usr/lib32
```

When launching the games now

---

### Post by Nymeria on 2012-08-25
> **javajames79 said:**
> The games where not getting access to the 32 bit libraries. Solved.
 
I just:
~
```
export LD_LIBRARY_PATH=/usr/lib32
```When launching the games now


Hi! I also experience the same error message when I try to install Slender using PlayonLinux. I'm really a noob, I'm not a programmer or whatever so I don't really understand these kinds of things. Anyway, may I ask what to you mean when you said "launching" the games? Where do you put in that code?

Sorry for the hassle. I really wanna play this game. Or at least have my sisters play it.

---

### Post by javajames79 on 2012-08-26
Ah no problem, unfortunately i tend to take the quicker more programatical approach to solving the problem - i.e. i have very few 32 bit games so i just added the line of code to script files i have for these games. In penumbras case:

Just change ```
export LD_LIBRARY_PATH=./lib
``` to ```
export LD_LIBRARY_PATH=/usr/lib32:./lib
``` in "~/PenumbraCollection/BlackPlague/blackplague" "~/PenumbraCollection/BlackPlague/requim" & "~/PenumbraCollection/Overtue/penumbra"

In PlayOnLinux you start games with: ```
/usr/share/playonlinux/playonlinux --run "[GAME]"
```

So you can simple find out the name of the game, (its the one that shows up in the playonlinuxmenu, which is case sensitive btw.)

So if for example you installed slender with the slender playonlinux script it should be called "Slender", so open terminal and copy this in:

```
export LD_LIBRARY_PATH=/usr/lib32
/usr/share/playonlinux/playonlinux --run "Slender"
```


================

For a more permanent solution you can have the "export LD_LIBRARY_PATH=/usr/lib32" run on startup. (But with penumbra it overwrites the LD_LIBRARY_PATH completely i think so you may still need to change the penumbra scripts (sorry);

I'm not entirely sure how to run it on startup other than adding it to ones bashrc file. :S


If you have any further queries/problems don't hesitate to ask :)

EDIT: Can be added to .profile i think ([https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables))

---

