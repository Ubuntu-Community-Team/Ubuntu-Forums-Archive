---
title: "System Shock 2 and Wine"
date: 2007-05-27
forum: Wine
---

### Post by mikeym on 2007-05-27
Hi,

This is my second attempt at getting a game to run in wine and I'm not getting very far. Although this is the furthest I've managed. Tantalisingly I can play the intro select level but no further.

I'm using the home of the underdog version and I've run the ogg setup program successfully. I've had a go at the game with 2 outcomes. The first loads the main screen and when I start a new game it gives me a blank screen. This appears before the loading screen pops up. (I've saved the output of this in Output1.txt) 

The second, I removed the cutscenes' folder and I got into the game and through the first level, but it went to a blank black screen as soon as I entered the level exit. This produced quite a lot of complaints from wine. (I've saved the output as Output2.txt)

I've read that some people have done this using Cedega but I'm not keen to start messing around with that.

Thanks,

Mikey

---

### Post by mikeym on 2007-05-28
Has anyone managed this?

---

### Post by mikeym on 2007-05-30
I guess this is a no go then? 

I've found 2 Wine pages one sais it doesn't work the other says it does. But since no-one's got it working.

---

### Post by mikeym on 2007-05-30
The cut scenes cause the program to crash on my system and I havn't been able to get them working, but I found out that it was crashing for a different reason after I'd removed the folder 'cutscenes'. 

It was because wine wasn't working with my anchient graphics card (nvidia TNT2). It was trying to change to a 16 bit graphics mode and failing. I can get it to work (kinda) by editing my /etc/X11/xorg.conf file and changing my DefaultDepth to 16.

To give:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480
"

```

Then pressing [CTRL]+[ALT]+[BCKSP] to restart X. However after all this it still runs like ****. So not worth the effort realy.

P.S. remember to PUT THE DEFAULTDEPTH BACK.

---

### Post by Gorgofdoom on 2008-01-02
hi, i am also trying to get system shock 2 working. I was able to get it to install, the codec installer crashed(which was mentioned in the wine post for ubuntu), but when i attempt to run the game my computers cpu usage spikes for about 2 seconds, and nothing happens. i ran the exe in a terminal, and it came out with this... 
'root@valdez:/home/tim# '/home/tim/.wine/drive_c/Sshock2/shock2.exe' 
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 7bc622a9 esp 7ffddbf0 stack 0x241000-0x350000


if anyone can help me i would appreciate it...

*notes
1)i am running this with an nvidia card, with nvidia drivers.
2) i am using a cracked .exe(no-cd), it was mentioned in the wine post that you need to use one.

---

### Post by Gorgofdoom on 2008-01-02
also, for the post above, i renamed the cutscenes folder, and i attempted changing the color-depth to 16-bit, but it did not help.

---

### Post by Gorgofdoom on 2008-01-02
> **mikeym said:**
> Hi,

This is my second attempt at getting a game to run in wine and I'm not getting very far. Although this is the furthest I've managed. Tantalisingly I can play the intro select level but no further.

I'm using the home of the underdog version and I've run the ogg setup program successfully. I've had a go at the game with 2 outcomes. The first loads the main screen and when I start a new game it gives me a blank screen. This appears before the loading screen pops up. (I've saved the output of this in Output1.txt) 

The second, I removed the cutscenes' folder and I got into the game and through the first level, but it went to a blank black screen as soon as I entered the level exit. This produced quite a lot of complaints from wine. (I've saved the output as Output2.txt)

I've read that some people have done this using Cedega but I'm not keen to start messing around with that.

Thanks,

Mikey
im no genius, but it looks like the first error could be fixed by changing your default color depth to 16... but you already know that? i don't know what the problem with mine is.

---

### Post by Woojoo//.deb on 2008-05-04
for ur info sirs there is a way to disable the hardware video and to set it to software which helps with the problem here

: 

you need to set at the sshock2.cfg in the game folder 

```
hardware 0
```

this sets the software video rendering
but also it set the game to windowed mode which can be solved by adding

```
full_screen 1
```

hope that helps some of you
but it didnt helped me couse my game crashed at starting the cutscene which i cant solve 

the maximum resolution that can be set at the .cfg file which doesnt crash is 800x480 

if your able to play ^^ tell me what its like

---

### Post by mikeym on 2008-05-04
Well for me it's a bit late as I've upgraded my machine. I was running a slightly older version of wine to get it to run 0.9.43 but the new version works ok. 

Also on my machine I need to run it on one core with:
[I]
taskset -c 1 [/I]

---

### Post by Woojoo//.deb on 2008-05-04
O_o i cant make it work!!

ok anyone who tells me the "secret" is out of my chain-mail for life and does not get a windows xp cd for x-mas!

deal?

---

