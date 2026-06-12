---
title: "what open file playing in flash"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by raven on 2008-04-04
I have an issue of finding which file is playing in flash
example: you go to youtube (as an example), and you select a movie
it usually download the movie on your harddrive in tmp or your cache so you can replay it faster,

How can I know which file is being used/playing by flash
I want to use a command line utility to tell me which file is being used
I tried lsof on npviewer and firefox
tried ls -l /proc/PID#/fd of npviewer and firefox could not find the file name,

I disconnect form internet and I can still play the file in flash, so I know it is somewhere on my hard drive or memory, but how can I find which one and where ?

thanks in advance

Gutsy AMD64

---

### Post by jpkotta on 2008-04-05
I'm using Opera, FWIW.  I did exactly what you did and found a file in /tmp is growing as the flash video is buffering.  In my case it is /tmp/FlashU2y3al, which is almost certainly a randomly generated name, as there are a ton of them in my /tmp.

---

### Post by jpkotta on 2008-04-05
I forgot to mention, I can play the files in /tmp with mplayer.

---

### Post by raven on 2008-04-13
thanks for the reply
I understand what you are saying and I agree, 
but let me explain

I went to a site (I forgot which one, when I remember I will mention it)
and it uses a flash player for the Vclips, I can see the download progress bar as in youtube, it finishes, I can play the file and watch the Vclip, but there is nothing in tmp and there is nothing in FF cache...
I thought it is a stream...but if I disconnect from my internet
I still can play this Vclip, so I know it is somewhere on my hard drive

that is why my question is how to find out what file is playing in flash...

---

