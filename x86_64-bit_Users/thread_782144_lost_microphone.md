---
title: "lost microphone?"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by absalom on 2008-05-04
Okay, i need to use skype... and after getting it from medibuntu.ö

Then i tested the mic in sound recorder. Oddly enough the front mic jack acted as a line-in, but in case i set it's volme to zero it worked as a mic (although imho. worse quality than i'd gotten out of the mic before.)

After a bit of fiddling around (mainly running skypes sound test) i don't get that either to work though! i can neither get any sound recorded with the darn thing, and it still acts as a line in... what should i do? can you guys give me any steps?

---

### Post by absalom on 2008-05-04
Oh never mind, apaprently all i had to do was use alsamixer through the command line interface and put on the capture from there... darned gui tools don't work...

---

### Post by neil6412 on 2008-10-11
Please can you explain exactly how to do this?  Having a bit of a problem trying to get the built-in mic on Dell 1520 to work in Skype.

Thanks,
Neil

---

### Post by bro on 2008-11-10
@neil6412 
```
~$ alsamixer
```

But how do I switch away from pulse?

---

### Post by bro on 2008-11-10
@neil6412 
```
~$ alsamixer
```

But how do I switch away from pulse?

---

### Post by rabdoel on 2009-07-10
removing pulse and installing esound
[COLOR=DarkGreen]
ps -A | grep pulse to  find the process id 
[/COLOR]then

[COLOR=DarkGreen]kill (process id of pulse)[/COLOR]

[COLOR=Black]then remove pulse

[COLOR=DarkGreen]sudo apt-get install remove pulseaudio[/COLOR]

install esound

[COLOR=DarkGreen]sudo apt-get install esound[/COLOR]

remove pulse directory 

[COLOR=DarkGreen]sudo  rm /etc/X11/Xsession/70pulseaudio[/COLOR][/COLOR]

---

### Post by Th3_uN1Qu3 on 2009-07-10
EsounD is very outdated and it is not needed - ALSA alone does good software mixing nowadays. You will only need to remove Pulse and reinstall ALSA.

```
sudo apt-get remove pulseaudio
sudo apt-get remove alsa
sudo apt-get install alsa
```

Now go into Sound Preferences and set everything to ALSA. If you need help to get the mic working just ask.

---

