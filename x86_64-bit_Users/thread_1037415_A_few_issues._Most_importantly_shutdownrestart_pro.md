---
title: "A few issues. Most importantly: shutdown/restart problem"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by Teacher Lion on 2009-01-11
Dear all,

I am new to both this forum and to Linux itself - Hello, my name is Adam! I have just installed a 64 bit version of Ubuntu on my laptop and I am very pleased with it. There are, however, a few things that are preventing me from "making the jump" to getting rid of my Windows installation and plodding along happily with my new setup. If these issues are resolved then I shall uninstall Windows and the Linux Crusade will have claimed another convert.

1)

First and foremost, whenever I shutdown or restart Ubuntu the (un)loading screen shows up, promptly shows itself "unloading", and then stops. Once the loading bar is drained it then freezes (Ctrl+Alt+Del doesn't work either) and I have to switch off my laptop manually. Those of you who might fancy a go at tackling this problem will need the laptop details:

ASUS - A8Dseries - Turion TL60 with nVIDIA GeForce 8400M G - (M/B Version:A8DC)

Do please let me know if any other info is required. It really is bitterly annoying. It's a very good laptop and it runs so quietly that I can't tell if the harddisk is still running when everything freezes. I don't want to damage anything, so I try not to dabble with Linux too much. Sad, really.

2)

Onto the next problem, I'm a guitarist and I use an M-AUDIO FASTTRACK USB to record myself playing and to listen to how brilliant I am. As with the previous issue, I have tried to resolve this myself but I have found out that - as yet - nothing has been released to make the FASTTRACK Linux-friendly. The articles I have read are getting a bit old now and I am not sure where I should go for the latest info on driver developments. Where do all the Linux musicians go?

3)

Lastly, I am a teacher and I have to admit that I find MS Office 2003 more teacher-friendly than OpenOffice. There are certain word tools such as wordart that I make frequent use of. Are there any OpenOffice alternatives or programs I can use to supplement missing tools from OpenOffice? I am fully aware that a lot of this comes down to getting accustomed to the new environment - I'm doing my best!

 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Big thanks in advance for your efforts.

Kind regards,

Lion

---

### Post by Teacher Lion on 2009-01-12
Dear All,

Many apologies for having copied and pasted a previous message into a different category. The original is miscategorised and now the one that's in the right place has been locked! I appear to be making a bit of a mess. I won't do it again. Promise.

I have a shutdown problem that refuses to go away and subsequently I can't use Linux.

The original post is here: 
[http://ubuntuforums.org/showthread.php?t=1037415](http://ubuntuforums.org/showthread.php?t=1037415) 

Please don't lock me! I'm just an innocent man doing everything he can to get his damned infernal computer to work properly!

Kind regards,

Lion

---

### Post by TCSnyder on 2009-01-12
Sorry the link to the previous post did not work for me but have you tried
```
sudo shutdown -h now
```

---

### Post by TCSnyder on 2009-01-12
[http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown")
this link might work, but read through all the posts before attempting, i think a guy messed it up

---

### Post by Teacher Lion on 2009-01-12
Thank you for the info. I'll give it a try during my lunch break.

Fingers crossed...

---

### Post by Teacher Lion on 2009-01-14
It worked! Thanks again, TCSnyder. What a superb human being you are.

Now... how do I get into the shutdown menu script and make sure that 'shutdown -h now' is the standard operation for the shutdown button? Or will I need to invoke root privileges whenever I switch off my computer?!

I'd also like to thank the kind man that rearranged my posts. Again, sorry about that. Lesson learned.

I think I'll try not switching over to Windows today.

Kind regards,

Lion

---

### Post by TCSnyder on 2009-01-14
that's what these forums are for.

---

