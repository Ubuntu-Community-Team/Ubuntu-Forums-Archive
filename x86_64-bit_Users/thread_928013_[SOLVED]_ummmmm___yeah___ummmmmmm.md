---
title: "[SOLVED] ummmmm   yeah   ummmmmmm"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by ryry46d9 on 2008-09-23
so I have read 50% of the how-to s for this flash problem. I when to 2.0.0.16 and got a flash page to display 9.* but on "flashes" page it still wants me to down load it. the problem im having with 3.* and 2.* is I chat on a flash based server I can hear all the system room noises but I can not hear any voice from the users. running 2.* out of the shell i get 
" ALSA lib ../../../src/pcm/pcm.c:6625:(snd_pcm_slave_conf) unknown format unchanged " flooding the screen. also I have the MIC issue AKA not working 

where do i go from here ? 

I also just seen 

*** e = [Exception... "ServiceManager::GetService returned failure code:"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 294"  data: no]

---

### Post by ryry46d9 on 2008-09-23
also I built   alsa   from src  and read 60% of them how-tos

---

### Post by Sef on 2008-09-23
[LEFT]1) What version of Ubuntu are you running?

2) How did you download flash?  
[/LEFT]

---

### Post by ryry46d9 on 2008-09-23
ubuntu 8.0.4 
I grabbed the tar ball and moved the file in to the plugin DIR and sim-linked the file 

(sorry im a little brain dead right now)

---

### Post by tuxxy on 2008-09-23
OPen your browser and type

```
about:plugins
```

Check you have it installed, if its not there you could try installing flashplugin-nonfree from the repos.

```
sudo apt-get install flashplugin-nonfree
```

Also you could take a look at the package ubuntu-restricted-extras, this includes the flash plugin amongst other things.

---

### Post by Sef on 2008-09-24
> sudo apt-get install flashplugin-nonfree

It is best to update the repositories before downloading from there.

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree 
```

You can copy and paste the code instead of retyping it.

Also you will need to open Multiverse if it is not open yet.  It will tell you if you need to and how.

---

### Post by ryry46d9 on 2008-09-24
ok I did the update /install 

and in the about:plugins under flash it only shows Shockwave Flash 9.0 r124


so I did some thing wrong 

im going to retrace my steps and try again

---

### Post by Kilz on 2008-09-24
For flash that is what it should say.

---

### Post by ryry46d9 on 2008-09-24
OK hmmmm I just right clicked in the room and went to about flash  and got   You have version 9,0,124,0 installed

about:plugins  

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

so thats why i was lost 


so must be the  VIA High Definition Audio Controller :lolflag:

like I was saying I got full system sound but in the "FLASH" chat based room I go in,  I here all the room sounds but when the users talk and my mic is not working. 

I have a bluetooth adapter that also failed in the room I get it to play a audio CD but after each track it restarts the service (so that project is on hold)

I built alsa-*-1.0.17 (following the wiki), I read some where that some one degraded alsa and got thier mic working in their laptop. im going to RTFM the wiki again  im sure its a typo is one of the conf files 

thank you for the help 


I'll post back here for future people having the fame problem when I find the fix



now for AMD to open the all-in-wonder TV tuner  (2006 edition (X-1300 based) source so I can ditch media center edition (can't stand the MS-DVR files)

---

### Post by Sef on 2008-09-24
>  I'll post back here for future people having the fame problem when I find the fix

It would be best to start a new thread for them.  Otherwise they will most likely just get lost in here.

---

### Post by ryry46d9 on 2008-09-24
yeah that might be the best option  unless they where looking for flash chat audio which is still my problem

---

### Post by ryry46d9 on 2008-10-04
ok problem fixed ..... I found a old PCI sound blaster card stuck it in went to the bios and disabled the onboard and POW got to hear people talking in the FLASH BASED ROOM I go to.

so it would seam after 20 years VIA still sucks!!!!!!!!!!!!

---

