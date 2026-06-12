---
title: "[SOLVED] Ubuntu 64 HELP please"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by roycerm2 on 2008-09-29
Hi, I have just switched from Windowsxp to Ubuntu 64. My system is as fallows:

Asus M2n-sli mobo
Asus Silent Magic ATI Radeon HD 3600
AMD 64 5000+
2 gigs ram
Ubuntu Hardy

The problem im having is that after I install my restricted drivers through Envy, there is no longer any sounds/music from games. I hear the login sounds, can hear mp3's play but nothing is games. I cant remember the command i used but when i checked to see if ubuntu could see my sound card on the mother board it came up with 2 cards. the first :0, said that i had a radeon sound card or something. i want the sound card on my mother board to be the default. 

i dont know if i have given enough or the right information, but if i could get a little help i would really appreciate it thanks.:)

---

### Post by cariboo on 2008-09-30
In a terminal type:

```
asoundconf list
```

This will list the sound caeds in your system, in the same terminal type:

```
asoundconf set-default-card PARAMETER
```

where PARMAETER is the sound card listed in the previous command.

Jim

---

### Post by roycerm2 on 2008-09-30
Thank you so much!!!!! it worked perfectly. the support from the forums kicks butt!!!

Royce

---

