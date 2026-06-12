---
title: "elisa and ardour not working in Hardy Heron 8.04"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by scarrabri on 2008-05-10
Hi i use elisa media centre and ardour which is for multitracking,both work brilliant in ubuntu 64 7.10 ,but as soon as i upgrade to Hardy Heron both develop problems,and are impossible to use,the elisa media centre wont even begin to open,and the ardour opens but is no good for any thing,is there some thing i should be doing,because,i cant for the life of me get them working ,very best wishes Scarrabri

   8 gb mem
  ip35 pro abit motherboard
conro cpu
running on ubuntu 7.10

---

### Post by Kilz on 2008-05-10
> **scarrabri said:**
> Hi i use elisa media centre and ardour which is for multitracking,both work brilliant in ubuntu 64 7.10 ,but as soon as i upgrade to Hardy Heron both develop problems,and are impossible to use,the elisa media centre wont even begin to open,and the ardour opens but is no good for any thing,is there some thing i should be doing,because,i cant for the life of me get them working ,very best wishes Scarrabri

   8 gb mem
  ip35 pro abit motherboard
conro cpu
running on ubuntu 7.10

What problems are you experiencing? What errors if any do you get?

---

### Post by scarrabri on 2008-05-10
> **Kilz said:**
> What problems are you experiencing? What errors if any do you get?
Hi thankyou for your reply,the elisa media centre does not start it trys then just stops,,no error is given ,the ardour starts but weeps,or spills in to the next track,and shows a input reading all the time ,even when nothing is connected,it does the same every time i upgrade to hardy heron,yet it is perfect in ubuntu 7.10 64,which is why i keep going back to it,i only go to hard heron,because,the updates,where as the 7.10 will be ending,best wishes Scarrabri

---

### Post by cariboo on 2008-05-10
Start Elisa in a terminal and post the output here.

Jim

---

### Post by Ekeluo on 2008-05-12
You should delete the elisa.conf file from ~/.elisa. That should do it (just move it away if you don't want to lose it, it will create a new one).

---

### Post by KryoFrk on 2008-06-14
For the Elisa problem:

Guess no one else but me tried this, otherwise they would have come back and told the community it WORKED. Thanks! 

One thing though, I can't get the settings in the program to open up (the icon shaped like a cog/sprocket. I'm going to search and fiddle with it, but in the mean time, any ideas?

---

### Post by drjonze on 2008-06-20
> **Ekeluo said:**
> You should delete the elisa.conf file from ~/.elisa. That should do it (just move it away if you don't want to lose it, it will create a new one).

I was having a similar issue, although the app would load but I just couldn't do anything. Your fix worked for me too.

Thanks!

---

### Post by scarrabri on 2008-07-11
Hi where about do i find the .conf file from ~/.elisa. so has to deleat it,because i have no clue ,best wishes scarrabri:lolflag:

---

