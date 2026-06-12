---
title: "Can you run a 64-bit compiled program on a 64-bit machine running 32-bit ubuntu?"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cheese Sandwich on 2007-06-14
I'm curious as to this, if someone''s having 64-bit OS issues, and wants to switch to the 32-bit OS on their 64-bit hardware, but wants to compile their own programs for for the 64-bit architecture (gcc -m64, for example), could they take advantage of the 64-bit performance in those limited cases.

-Thx

---

### Post by Ayuthia on 2007-06-14
I could be wrong but I don't think that it would work because the OS is running in 32-bit mode so it will not be able to translate the 64-bit addressing properly.  The only way that I know is that you can make some 32-bit work on 64-bit OS because you can make the 32-bit address fit in a 64-bit processor.

---

### Post by Cheese Sandwich on 2007-06-14
> **Ayuthia said:**
> I could be wrong but I don't think that it would work because the OS is running in 32-bit mode so it will not be able to translate the 64-bit addressing properly.  The only way that I know is that you can make some 32-bit work on 64-bit OS because you can make the 32-bit address fit in a 64-bit processor.

Ah, thanks. That's too bad, it would be a nice compromise to go with the problem-free 32 bit setup but use high-performance apps compiled for 64.

---

### Post by Kilz on 2007-06-14
> **Cheese Sandwich said:**
> Ah, thanks. That's too bad, it would be a nice compromise to go with the problem-free 32 bit setup but use high-performance apps compiled for 64.

What is this fud day? The 64bit version is as problem free as the 32bit version. Perhaps the HUGE amounts of posts from people that have problems with the 32bit version has some how been missed by you. If you need a clue where they are, look in every other section of this forum.

---

### Post by Cheese Sandwich on 2007-06-14
> **Kilz said:**
> What is this fud day? The 64bit version is as problem free as the 32bit version. Perhaps the HUGE amounts of posts from people that have problems with the 32bit version has some how been missed by you. If you need a clue where they are, look in every other section of this forum.

OUCH!! :lol:

Just trying to see what options are out there.  :) Hey, this would be a good thing (if it were possible), it would be a good anti-FUD-of-64bit as it would allow incremental adoption on a user's system.

---

### Post by Kilz on 2007-06-14
> **Cheese Sandwich said:**
> OUCH!! :lol:

Just trying to see what options are out there.  :) Hey, this would be a good thing (if it were possible), it would be a good anti-FUD-of-64bit as it would allow incremental adoption on a user's system.

Thats just it, it works the other way around. You can run 32bit applications on a 64bit os.

---

### Post by Cheese Sandwich on 2007-06-14
> **Kilz said:**
> Thats just it, it works the other way around. You can run 32bit applications on a 64bit os.

Yes, and that's definitely the better way to go, I'm just throwing around ideas here.

Eventual full adoption of 64 bit is inevitable, and we'll be having this same conversation about 64 bit vs. 128 bit.

---

### Post by tgm4883 on 2007-06-14
> **Cheese Sandwich said:**
> Yes, and that's definitely the better way to go, I'm just throwing around ideas here.

Eventual full adoption of 64 bit is inevitable, and we'll be having this same conversation about 64 bit vs. 128 bit.

Thats just it though, your throwing around ideas that A:  Aren't possible, and (get ready for this) B:  Already exist (although the other way around)

The real question is why doesn't Feisty 64-bit work as good as Feisty 32-bit.  Oh yea, thats right.  It does.

---

### Post by capecove on 2007-06-14
What is amazing is this line in the sand about 32 bit vs. 64 bit. The fact of the matter is that it is very unlikely that we need a discussion like this when we should all be focusing on how excellent Ubuntu can be. So, when we have an Ubuntu conference, will we have to split it up into two different camps, 64 bit and 32 bit? Who needs BATTLE OF THE SEXES when you could have BATTLE OF THE BITS!

---

### Post by Kilz on 2007-06-14
> **capecove said:**
> What is amazing is this line in the sand about 32 bit vs. 64 bit. The fact of the matter is that it is very unlikely that we need a discussion like this when we should all be focusing on how excellent Ubuntu can be. So, when we have an Ubuntu conference, will we have to split it up into two different camps, 64 bit and 32 bit? Who needs BATTLE OF THE SEXES when you could have BATTLE OF THE BITS!

I will admit , sometimes it just gets to be to much. The constant FUD over and over , and over. That and the inability to see sticky posts or use the search function. This thread wasnt that bad. Maybe it was just me having a bad day.
Its also that I have been using the 64bit version a long time. I have done what I can to make it better. I tend to defend it now. I know its the future, heck anyone who was around during the 16 to 32bit knows it will happen.

---

### Post by Cheese Sandwich on 2007-06-14
> **capecove said:**
> Who needs BATTLE OF THE SEXES when you could have BATTLE OF THE BITS!

Battle of the Widths

---

### Post by incubus on 2007-06-14
I know the OP didn't mean any harm, but please do think how you will scare people away from even trying 64bit with that kind of comment.  This contributes to the endless cycle of 64bit having less support because... it has less support.  I'm on 64bit on both desktop and laptop and I have no problems.

Now, by the way, I had a crazy idea, but then I would answer Yes to your question.  You could emulate a 64bit processor in a 32bit install using, say QEMU or Bochs.  I know, it would probably be terribly slow, but the question was general, right?  : )

incubus

---

