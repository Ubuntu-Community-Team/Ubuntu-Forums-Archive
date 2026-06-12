---
title: "Wine and 64 is it running 32 or 64?"
date: 2008-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-15
Ok, I use wine a lot for my Bible program (Linux just does not have comparable Bible software, it doesn't exist).  So I got to thinking, when I run a program in wine, is my wine actually running at 64 bits, or 32?  And if it does run at 64 bits, does it really matter because more than likely the windows program I'm running is only a 32 bit program.  **IF** there were a 64 bit version available, would it be worth my time to run it?  I know this is a technical question, but just wondered if it had been talked about before. 

Shane

---

### Post by prince_niceguy on 2008-02-16
It runs 32 bit only. There are some compilation issues for making it 64 bit.

---

### Post by kolbycrouch on 2008-02-16
well performance will be slightly noticeable. because 64-bit ubuntu emulates wine under a 32-bit environment. obviously running in native 32-bit would work better.

I used Ubuntu gutsy x86_64 for month until i had problems with frets on fire so i decided to run 
ubuntu i386 and test wine, WoW and FoF. WoW actually ran about x2 as fast in wine on i386 then on cedega and wine on 64-bit. FoF runs perfect and runs faster. so even though 64-bit OS's run faster, the majority of the programs are 32-bit native so they actually run slower. unless your doing floating point math(i believe thats what its called) or mass encoding, you should probably run a 32-bit ubuntu until the majority of software is compiled and fixed for 64-bit versions.

---

### Post by gsmanners on 2008-02-16
A 64-bit version of Wine would be very much worth it. Not only would the performance of certain CPU-intensive tasks increase, but it would then be possible to use 64-bit Windows software (which will become more and more prevalent soon).

---

### Post by Kilz on 2008-02-16
> **kolbycrouch said:**
> well performance will be slightly noticeable. because 64-bit ubuntu emulates wine under a 32-bit environment. obviously running in native 32-bit would work better.

I used Ubuntu gutsy x86_64 for month until i had problems with frets on fire so i decided to run 
ubuntu i386 and test wine, WoW and FoF. WoW actually ran about x2 as fast in wine on i386 then on cedega and wine on 64-bit. FoF runs perfect and runs faster. so even though 64-bit OS's run faster, the majority of the programs are 32-bit native so they actually run slower. unless your doing floating point math(i believe thats what its called) or mass encoding, you should probably run a 32-bit ubuntu until the majority of software is compiled and fixed for 64-bit versions.

That is only true is if you are running a lot of **Windows** software that is 32bit. But why on earth would you be running that much windows software?

---

### Post by shane2peru on 2008-02-16
Wow, info!  Thanks for the info everyone.  I really run very few programs in wine about 3 and only one of those do I run on a daily basis.  I enjoy 64bit over all, and think there is an advantage to running it for me.  The only thing I have noticed about wine is that it is slower to opening the application, it is not a process intensive app, it is only a Bible program, which is based on sqlite3 so it is always accessing the database, however it runs overall very well on wine.  I just couldn't help but wonder the status of wine and 64bit platform.  Thanks all for the input!

Shane

---

### Post by Kilz on 2008-02-16
> **shane2peru said:**
> Wow, info!  Thanks for the info everyone.  I really run very few programs in wine about 3 and only one of those do I run on a daily basis.  I enjoy 64bit over all, and think there is an advantage to running it for me.  The only thing I have noticed about wine is that it is slower to opening the application, it is not a process intensive app, it is only a Bible program, which is based on sqlite3 so it is always accessing the database, however it runs overall very well on wine.  I just couldn't help but wonder the status of wine and 64bit platform.  Thanks all for the input!

Shane

Sometimes there is a need to run the one or 2 windows applications that you cant find a linux equivalent of. Libronix is one of these. I have yet to find a linux application that can access the files it uses.  But I have found I like gnomesword a lot as a bible, there are a lot of modules for it. including a kjv and scofield commentary.

---

### Post by shane2peru on 2008-02-16
> **Kilz said:**
> Sometimes there is a need to run the one or 2 windows applications that you cant find a linux equivalent of. Libronix is one of these. I have yet to find a linux application that can access the files it uses.  But I have found I like gnomesword a lot as a bible, there are a lot of modules for it. including a kjv and scofield commentary.

I have been running [The Word]("http://www.theword.gr") for me it is great.  I have a hard time using the Gnomesword or Bibletime after using the nicer Windows programs.  I also have a lot of material in Spanish since I'm working in Peru, it is very helpfull to me, something that Gnomesword and Bibletime are lacking.  Seeing that is the only windows program I need, I can live without windows and have become very proficient in running wine.  And troubleshooting some of the problems or library dll's that it needs.  

Shane

---

### Post by Kilz on 2008-02-16
> **shane2peru said:**
> I have been running [The Word]("http://www.theword.gr") for me it is great.  I have a hard time using the Gnomesword or Bibletime after using the nicer Windows programs.  I also have a lot of material in Spanish since I'm working in Peru, it is very helpfull to me, something that Gnomesword and Bibletime are lacking.  Seeing that is the only windows program I need, I can live without windows and have become very proficient in running wine.  And troubleshooting some of the problems or library dll's that it needs.  

Shane

There are not a lot of modules in the Ubuntu Repository for gnomesword . [But the sword project has more.]("http://www.crosswire.org/sword/modules/") Thanks for the link to theword.

---

### Post by shane2peru on 2008-02-16
> **Kilz said:**
> There are not a lot of modules in the Ubuntu Repository for gnomesword . [But the sword project has more.]("http://www.crosswire.org/sword/modules/") Thanks for the link to theword.

Yes I have been on the Sword Project site many times.  I need to visit it again and see if there is anything new.  Also on TheWord, Version 3 beta is the best, it allows study material.  Version 2 is not my favorite.

Shane

---

