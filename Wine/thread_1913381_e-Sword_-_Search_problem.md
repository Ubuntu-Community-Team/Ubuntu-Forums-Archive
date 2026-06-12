---
title: "e-Sword - Search problem"
date: 2012-01-22
forum: Wine
---

### Post by partos on 2012-01-22
My operating system is Lucid 64 bits. I installed WINE 1.2 and it was upgraded to 1.3. I'm working with e-Sword 10.0.5 and WINE. The software has aproblem with the following search options:

1) Search for all the words
2) Search for any of the words
3) Search for any exact phrase
And it works very well with the search option:
Regular Expression (REGEX)

Anybody knows whats the problem? I'm considering problems with VISUAL BASIC or something similar. How can I correct this problem?

---

### Post by oxman on 2012-01-22
I had a similar problem when I transitioned to 11.10. The latest sword requires that you index your modules after they are installed. Look in your modules manager for the option. This solved my problem.

---

### Post by sgage on 2012-01-22
> **partos said:**
> My operating system is Lucid 64 bits. I installed WINE 1.2 and it was upgraded to 1.3. I'm working with e-Sword 10.0.5 and WINE. The software has aproblem with the following search options:

1) Search for all the words
2) Search for any of the words
3) Search for any exact phrase
And it works very well with the search option:
Regular Expression (REGEX)

Anybody knows whats the problem? I'm considering problems with VISUAL BASIC or something similar. How can I correct this problem?

Have you tried Xiphos? It is a native Linux program based on Sword, and uses all the same modules. No messing around with Wine. It's in the repos and works very well here... also available in Windows version now.

---

### Post by oldos2er on 2012-01-22
Thread moved to Wine.

---

### Post by Double.J on 2012-01-22
> **sgage said:**
> Have you tried Xiphos? It is a native Linux program based on Sword, and uses all the same modules. No messing around with Wine. It's in the repos and works very well here... also available in Windows version now.

Plus 1 to xiphos - it's brilliant and runs all the translations and commentaries of Esword :) you can get it from the repo's (software centre)

---

### Post by forrestcupp on 2012-02-02
> **gnu/mirow said:**
> Plus 1 to xiphos - it's brilliant and runs all the translations and commentaries of Esword :) you can get it from the repo's (software centre)

Can it run the Greek and Hebrew Word Study module that I paid $40 for?

---

### Post by sgage on 2012-02-02
> **forrestcupp said:**
> Can it run the Greek and Hebrew Word Study module that I paid $40 for?

I would bet that you can. Why not try it - it's free!

---

### Post by forrestcupp on 2012-02-02
> **sgage said:**
> I would bet that you can. Why not try it - it's free!

I was kind of making a point. Sword can't run e-Sword modules, and there is no way to convert them. I have a few modules that aren't available for Sword that I spent a lot of money on, and they are important to me. So for me, Sword is not an option.

And I have used Sword a lot in the past. If it could run my modules, I would definitely rather use a native app than running e-Sword through Wine.

The reason I was making this point is because the OP was asking for help with e-Sword, which is a different program than what everyone else was talking about.

---

### Post by sgage on 2012-02-02
> **forrestcupp said:**
> I was kind of making a point. Sword can't run e-Sword modules, and there is no way to convert them. I have a few modules that aren't available for Sword that I spent a lot of money on, and they are important to me. So for me, Sword is not an option.

And I have used Sword a lot in the past. If it could run my modules, I would definitely rather use a native app than running e-Sword through Wine.

The reason I was making this point is because the OP was asking for help with e-Sword, which is a different program than what everyone else was talking about.

You know more about it than I do. Xiphos (what you are referring to here as plain old "Sword" I'm guessing) uses the Sword Project modules. I assumed e-Sword did the same - I didn't realize it used its own format.

Sorry for any confusion.

---

### Post by forrestcupp on 2012-02-02
> **sgage said:**
> You know more about it than I do. Xiphos (what you are referring to here as plain old "Sword" I'm guessing) uses the Sword Project modules. I assumed e-Sword did the same - I didn't realize it used its own format.

Sorry for any confusion.

Yeah, I think it used to just be called The Sword Project in Windows. Seems like it used to be called GnomeSword in Linux. It uses an open format for it's modules, but e-Sword uses its own proprietary format that won't work with anything else. That's too bad, because on Windows, it's about the best free of charge Bible software. It has more options for modules than the Sword Project.

The search bug that comes from running e-Sword in Wine is making it unusable for me.

---

### Post by sgage on 2012-02-02
> **forrestcupp said:**
> Yeah, I think it used to just be called The Sword Project in Windows. Seems like it used to be called GnomeSword in Linux. It uses an open format for it's modules, but e-Sword uses its own proprietary format that won't work with anything else. That's too bad, because on Windows, it's about the best free of charge Bible software. It has more options for modules than the Sword Project.

The search bug that comes from running e-Sword in Wine is making it unusable for me.

Yes, GnomeSword was renamed to Xyphos. I've been testing Precise (12.04), and as of now, Xiphos doesn't even work - simply segfaults at launch. Oh well. It works great in Oneiric.

I prefer Xiphos to e-Sword, but then, my needs are rather simple. Sorry e-Sword won't work for you in wine...

---

### Post by forrestcupp on 2012-02-08
In case anyone ends up here looking for a fix to e-Sword's search problems, I put a [fix right here](http://ubuntuforums.org/showthread.php?p=11673552#post11673552). I does involve reinstalling e-Sword, though.

---

