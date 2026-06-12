---
title: "Flash Souns like crap"
date: 2007-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-06-19
Ok well I've been looking around on how to fix my sound for flash on firefox. Now any other player for video works fine. sounds great but for some reason flash has this chatter (best I can descirbe it) when its playing. it seems to get louder as th sound gets louder but really just destroys watching videos.

---

### Post by jusmurph on 2007-06-19
How is your sound set up?

You running ALSA?

---

### Post by DaGGer on 2007-06-19
you know, I really don't have a clue. Your going to have to walk me through this. I believe that someone before showed me how to shut that off but I can' be sure.

---

### Post by capecove on 2007-06-19
> **jusmurph said:**
> How is your sound set up?

You running ALSA?

Hello! I just wanted to tell you that, even though this won't likely help, I am running Feisty and use an MX1000 mouse with no issues. :neutral: maybe you should post this and give some details on motherboard, etc.?

---

### Post by jusmurph on 2007-06-20
> **DaGGer said:**
> you know, I really don't have a clue. Your going to have to walk me through this. I believe that someone before showed me how to shut that off but I can' be sure.

Ok lets start simply.

I assume your plugging into inboard sound of the motherboard listed in your Sig?

Under Systems > Preferences > Sound
List or Screen shot what you have there.

In the top right hand corner their should be the little speaker, double click that and check for abnormalities.

Also, in between responses have a look at this guide:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Capecove, I tried that, however it dropped off ignored like every other thread i have found regarding it.

---

### Post by Cappy on 2007-06-20
Also, under the Systems > Preferences > Sound on the "Sounds" tab try unchecking "Enable software sound mixing (ESD)".

---

### Post by DaGGer on 2007-06-20
Ok well I uncheck the ESD, still doesn't fix the sound.  Here are the screen shots.

---

### Post by Cappy on 2007-06-20
Make a file in your home directory called .openalrc
and put this in it:
```

(define devices '(native))
```
Came across this fix in the game section just now.

---

### Post by DaGGer on 2007-06-20
tried adding that file and nothing happened.

---

### Post by DaGGer on 2007-06-22
bump

---

