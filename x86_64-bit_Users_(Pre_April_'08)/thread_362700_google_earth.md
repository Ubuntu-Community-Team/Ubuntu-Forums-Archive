---
title: "google earth"
date: 2007-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by cgons on 2007-02-15
i'm having a problem installing google earth on my system. when i try to run ge the splash screen stalls with no errors...i've read several other posts but with no conclusion..i have beryl installed so i "should" have the correct driver installed but what do i know....any help would be apprieciated..thanks

dell 1501
amd64 tl-56
ati express graphics card "200M" i think

---

### Post by prince_niceguy on 2007-02-15
i used to face the same problem. start it from the a terminal and try out. it will tell you what error are coming. for doing this you will to open a terminal and go to the google earth directly . once there run using ./googleearth. post the stack trace back and people should be able to figure out.

---

### Post by cgons on 2007-02-15
i do and i get no error messages.none at all.?? i think it may be a driver issue however i'm not too knowledgable on the subject...i'm also investigating an "APIC error on CPU0: 40(40)" so maybe this has something to do with it???

---

### Post by cgons on 2007-02-16
does anyone have any ideas??? if it is a driver issue how do i go about solving it...also its 32bit i beliave i installed all the 32bit libs 
```
sudo apt-get install ia32*
``` 
is there anymore i should have??

i am trying to add a google earth search box to my website but i need ge running first..

i wish i knew i was going to use ubuntu when i got this computer i think i may have gotten the most uncompatable computer for linux....lol...harddrive, wireless, apic errors, etc...etc...just buggy as hell....but i've learned so much by fixing these problems....so i guess theres a silver lining....

---

### Post by Simpele on 2007-02-23
This is my output:

willem@willem:/opt/google-earth$ linux32 sh googleearth-bin
googleearth-bin: 2: Syntax error: word unexpected (expecting ")")
willem@willem:/opt/google-earth$ sh googleearth-bin
googleearth-bin: 2: Syntax error: word unexpected (expecting ")")

---

