---
title: "Am I going to be doing a lot of this?"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by kob0724 on 2006-08-28
I say this being a new user of linux, it seems like almost everything is for 32-bit. Since I have an AMD-64 this is a problem. From what I can tell, one way to circumvent this is to download the source code for what ever program it is that you want and compile it yourself. Is this a correct conclusion? Also, am I going to have to be doing this a lot? This could become quite the hassle. Any one got a good way to getting around this? Thanks in andvanced.

---

### Post by Kilz on 2006-08-28
> **kob0724 said:**
> I say this being a new user of linux, it seems like almost everything is for 32-bit. Since I have an AMD-64 this is a problem. From what I can tell, one way to circumvent this is to download the source code for what ever program it is that you want and compile it yourself. Is this a correct conclusion? Also, am I going to have to be doing this a lot? This could become quite the hassle. Any one got a good way to getting around this? Thanks in andvanced.

No you wont. It would help if you could give an example of a program.

---

### Post by kob0724 on 2006-08-28
> **Kilz said:**
> No you wont. It would help if you could give an example of a program.

I had to download a 32-bit version of firefox to get flash and java to work (or so the little faq i read said i needed to do)

Recently i just tried to download some extensions for gaim and they only had a 32-bit version

---

### Post by Kilz on 2006-08-28
> **kob0724 said:**
> I had to download a 32-bit version of firefox to get flash and java to work (or so the little faq i read said i needed to do)

Recently i just tried to download some extensions for gaim and they only had a 32-bit version

There will be some things that need a 32bit version. Mainly those things that use proprietary codecs or proprietary plugins. But there is a lot in the repositories you will not have to compile. 
The firefox issue is easy to setup. My signature links to my automated setup script for 32bit firefox and plugins. Its all of 2 commands to set it up.
As for the gaim extensions, what extensions were they? I see that there are a lot of them in synaptic. But most of them are in the optional universe repository. Do you have [the universe and multiverse enabled? ]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") I find that people who are new to Ubuntu somethimes go looking for things because they have not enabled them.

---

### Post by kob0724 on 2006-08-28
I had universe enabled, but not multiverse. I already set up a 32-bit version of firefox (that was a doozy). So the multiverse has a lot of 64-bit packages then? I was searching in packages and I found the gaim extended preferecs (package I was looking for). Will the repos only show packages that will work on my architecture, or if i select this package might I be getting a 32-bit version? 

P.S.
I was also following your faq for setting up wine. It was very nice. Now I just have to figure out how to get steam running so I can play CS.

---

### Post by Kilz on 2006-08-28
> **kob0724 said:**
> I had universe enabled, but not multiverse. I already set up a 32-bit version of firefox (that was a doozy). So the multiverse has a lot of 64-bit packages then? I was searching in packages and I found the gaim extended preferecs (package I was looking for). Will the repos only show packages that will work on my architecture, or if i select this package might I be getting a 32-bit version? 

P.S.
I was also following your faq for setting up wine. It was very nice. Now I just have to figure out how to get steam running so I can play CS.

The multiverse has a ton of packages. The packages in the repos only show things that will work on your archetecure. But there may be a few 32bit packages in the repos. Packages in the repos will install and work without configuration regardless.

---

### Post by kob0724 on 2006-08-28
sweet! thanks a lot.

---

### Post by martinrandau on 2006-08-29
So a 'normal' (= web, mulitmedia, gaim, email, cedega, ooffice) ubuntu user will not see any difference between using 32 bit and 64 bit (except the different installation cd:s)?

---

### Post by John.Michael.Kane on 2006-08-29
martinrandau everything is the same with both versions. though as stated some codecs/plugins may need some coaching to get them installed,and there's scripts/guides to help the transfer from 32bit to 64bit as painless as possable.

---

### Post by Kilz on 2006-08-29
> **martinrandau said:**
> So a 'normal' (= web, mulitmedia, gaim, email, cedega, ooffice) ubuntu user will not see any difference between using 32 bit and 64 bit (except the different installation cd:s)?

They will get a slightly faster os. Some tasks will be a lot faster than the 32bit version. They may have to spend an extra hour following a cut/paste howto or run a automated setup script. But nothing to difficult.

---

