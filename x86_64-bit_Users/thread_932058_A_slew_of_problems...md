---
title: "A slew of problems.."
date: 2008-09-28
forum: x86 64-bit Users
---

### Post by skunkrecords on 2008-09-28
Ok, I want to start off by acknowledging the fact that I am unlucky. Lets start from the top :)

* I installed 8.04 the other day. It freezes all the time. I installed NVIDIAs drivers, install went smoothly... It still freezes all the time. (I use XP, so it isn't a hardware defect problem). I even bought a new SATA hard drive. No cigar. 

I read in various places the new kernel was messing things up. So I downloaded 7.04. 

During 7.04 install, after I initially choose the Install option, my monitor turns off! AHHH

I waited it out, and after about 5 minutes, the monitor comes back to life. So after I go through the install... IT FREEZES AGAIN

I have a 9800gtx, Intel core 2 quad, 2 gig of gskill ddr2 800.. This is really frustrating me. 

I used Ubuntu before, and it worked fine. The only thing different is my graphics card, so somewhere around there lies the problem.

---

### Post by Sef on 2008-09-28
> * I installed 8.04 the other day. It freezes all the time. I installed NVIDIAs drivers, install went smoothly... It still freezes all the time. (I use XP, so it isn't a hardware defect problem).

How did you install the drivers?

---

### Post by Kilz on 2008-09-28
> **skunkrecords said:**
> 
I read in various places the new kernel was messing things up. So I downloaded 7.04. 


In October Feisty Fawn (Ubuntu 7.04), one of the best versions imho to date, will reach end of life and will get no more updates. You may want to try and fix the issues with Hardy (2.5 years left) or install Gutsy (6 months left).

---

### Post by bford16 on 2008-09-28
> **skunkrecords said:**
> Ok, I want to start off by acknowledging the fact that I am unlucky. Lets start from the top :)

* I installed 8.04 the other day. It freezes all the time. I installed NVIDIAs drivers, install went smoothly... It still freezes all the time. (I use XP, so it isn't a hardware defect problem). I even bought a new SATA hard drive. No cigar. 

I read in various places the new kernel was messing things up. So I downloaded 7.04. 

During 7.04 install, after I initially choose the Install option, my monitor turns off! AHHH

I waited it out, and after about 5 minutes, the monitor comes back to life. So after I go through the install... IT FREEZES AGAIN

I have a 9800gtx, Intel core 2 quad, 2 gig of gskill ddr2 800.. This is really frustrating me. 

I used Ubuntu before, and it worked fine. The only thing different is my graphics card, so somewhere around there lies the problem.
According to this post <http://ubuntuforums.org/showthread.php?t=762064>, it is possible to make your video card work. You'll probably want to do a clean install (I'd use Hardy, but if you have an SATA drive, you'll need to boot with the pci=nomsi option).

---

### Post by skunkrecords on 2008-09-28
> **Sef said:**
> How did you install the drivers?

I just followed the directions on their website. 
- Stop X
- Run the script as root
- Whala, it works
The drivers actually worked nice. I even got my duel screens to work flawlessly. 

* My sata drives worked fine too. I installed 8.04 on the new sata drive btw. 

* My bad, I did download 7.10. 

Again, my graphics card works fine, I'm just suspecting it's the culprit in the freeze ups. I imagine maybe it's a kernel issue or something.. :(

---

### Post by skunkrecords on 2008-09-28
bump

---

### Post by Sef on 2008-09-28
Please wait 24 hours before bumping your thread.   Thank you.

---

### Post by skunkrecords on 2008-09-29
bump :)

---

### Post by Jouke74 on 2008-09-30
> Are the freezes occuring at random? You might want to run a memtest at least a couple of hours before installing your Ubuntu. It's on the CD under options as well (Just to make sure). 

> Is ubuntu running fine from the live cd, and I don;t mean just starting and checking it for 5 minutes? 

> Install Ubuntu in safe graphics mode, then install your video drivers afterwards. Another option is the alternate cd.

---

### Post by skunkrecords on 2008-09-30
> **Jouke74 said:**
> > Are the freezes occuring at random? You might want to run a memtest at least a couple of hours before installing your Ubuntu. It's on the CD under options as well (Just to make sure). 

> Is ubuntu running fine from the live cd, and I don;t mean just starting and checking it for 5 minutes? 

> Install Ubuntu in safe graphics mode, then install your video drivers afterwards. Another option is the alternate cd.

They appear to be random. Sometimes I'll be browsing, or sometimes I'll just be editing a text file. 

I havent checked the live cd, that will probably be my next move. It did freeze once during the install process though. 

I would like to use 8.04, and I have no problem viewing the installer with that version. Should I still go ahead and try to install it in safe graphics mode? Thanks for the reply!

---

### Post by Sef on 2008-09-30
> They appear to be random. Sometimes I'll be browsing, or sometimes I'll just be editing a text file. 

Bad ram can cause that.  Check out the [memtest86]("http://memtest86.com") site for more information.

---

### Post by skunkrecords on 2008-09-30
I'm running Debian right now without any problems.. And I tried running Ubuntu live, and it froze after about 10 minutes (I was running Firefox). The thing is, it doesn't happen just when I'm running firefox, but that just happens to be what I'm using. 

BTW, I miss ubuntu. This Debian world is a cold harsh one :(

---

### Post by skunkrecords on 2008-10-01
bump

should I just give up?

---

### Post by Jouke74 on 2008-10-02
Did you run the Memtest as suggested and have you found any errors? If you have found errors, it does not matter if you run Debian  / Ubuntu / Vista / Xp or even MS-DOS. At certain point something will be written to your bad memory module and that will cause your computer to hang.

Again, to run the memtest : put the Ubuntu live CD in the CD drive, let it start, when there comes the menu  select "memtest" instead of install Ubuntu. (I don't know whether Debian has this under the normal start-up menu as well). If your computer hangs during the memtest then there is bad memory. If there are any errors during the test then there is bad memory as well. This means you need to replace your memory modules (=hardware issue, not software).

---

