---
title: "Trouble with Counter Strike (Steam games in general)"
date: 2008-06-24
forum: Wine
---

### Post by Kidfork on 2008-06-24
Ok so here the trouble. I install Steam through PLAYONLINUX then installed Counter Strike. But when i go to start up counter-strike through steam i get this 

Engine Error

Platform Error: Module Failed to Initalize


IM using wine-0.9.59 With Ubuntu 8.04. 
2.4ghx Processer
512mb Geforce 6200 DDR2
640MB of RAM

---

### Post by Phyrax on 2008-06-25
I'm having the same problem and still looking for an answer.

Any help or information people could give would be great.

---

### Post by Sleaka J on 2008-06-25
Turn off the "Steam Community In-Game" overlay.

File -> Settings -> In-game -> Uncheck the box.

The overlay doesn't work properly in Wine. It has to be disabled.

---

### Post by Phyrax on 2008-06-25
thanks it worked!

one more thing, how can i change the text? it's a bit off and i think i read somewhere something about microsoft fonts, just wondering what to do, i can read it, but it's a bit hard.

---

### Post by Blue Thunder on 2008-06-26
Tahoma? 

Was randomly browsing around and I remembered that I just read something a few moments ago about having to install MS font 'Tahoma' to get steam to work (apparently its no longer needed though).

EDIT: here it is (see last few posts) = [http://ubuntuforums.org/showthread.php?t=839091](http://ubuntuforums.org/showthread.php?t=839091)

---

### Post by Sleaka J on 2008-06-26
> **Phyrax said:**
> thanks it worked!

one more thing, how can i change the text? it's a bit off and i think i read somewhere something about microsoft fonts, just wondering what to do, i can read it, but it's a bit hard.

I suggest you download the SteamFonts.zip file from the Steam Support Site:

[https://support.steampowered.com/kb_article.php?ref=1974-YFKL-4947](https://support.steampowered.com/kb_article.php?ref=1974-YFKL-4947)

and install them into your "./wine/drive_c/windows/fonts" directory

---

