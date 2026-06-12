---
title: "Office 2007..playonlinux...open office direct from files possible?"
date: 2014-05-12
forum: Wine
---

### Post by boyofford on 2014-05-12
Hi all,

Got office 2007 running on Ubuntu 14.04 fine using playonliux.
Doing this as a test really, to see if would be worth installing Ubuntu on my Mrs's netbook, Office is a must have for her.

One sticking point that she is not so keen on is you can't just click on a word doc etc and automatically have it open in word.
Is there a easy fix for this? am I being dumb?

cheers
Rich

---

### Post by scouser73 on 2014-05-12
All you need to do is associate the OpenOffice files with MS Word.

Right click on an OpenOffice file

Click Properties

Select Open With

Now choose the program that you want to have open that file.

---

### Post by boyofford on 2014-05-12
> **scouser73 said:**
> All you need to do is associate the OpenOffice files with MS Word.

Right click on an OpenOffice file

Click Properties

Select Open With

Now choose the program that you want to have open that file.

Sorry, don't think I've been clear.

I mean all files...for example .docx... I want to open with corrosponding office 2007 program....i.e. word 2007 in this case.
None of the programs in the M$ office suite show up when I try the 'open with' dialogue, I expected to find them there but they are not showing up.

Cheers
Rich

---

### Post by boyofford on 2014-05-12
Sussed it after many tutorial fails.

Followed this [http://www.tuxtrix.com/2012/06/set-file-associations-for-ms-office.html]("http://www.tuxtrix.com/2012/06/set-file-associations-for-ms-office.html")

Basically all you need to do is copy the shortcuts playonlinux creates on desktop to /usr/share/applications.... then when you right click and go to open with other application the office suite shows up!
Also works if you change default by selecting properties then open with and lets you select default.
Thought I'd post a pointer as did need to do some searching!
Cheers

Rich

---

### Post by oldrocker99 on 2014-05-13
I personally have no interest in MS Office (been using Open/Libre Office for a decade), but this is some very useful information, and you are to be thanked. It is, I might add, considered proper forum etiquette to edit your header to include **SOLVED** to make it easier for people looking to find a solution.

---

### Post by boyofford on 2014-05-14
> **oldrocker99 said:**
> I personally have no interest in MS Office (been using Open/Libre Office for a decade), but this is some very useful information, and you are to be thanked. It is, I might add, considered proper forum etiquette to edit your header to include **SOLVED** to make it easier for people looking to find a solution.

Thought it was marked as solved? is it not showing up?

I've been using libre office personally and is fine until you need to open files in M$, formatting goes off.
Not been problem for me as mostly just use spread sheets but useless for mrs.

---

