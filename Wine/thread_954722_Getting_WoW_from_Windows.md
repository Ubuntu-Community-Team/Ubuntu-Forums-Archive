---
title: "Getting WoW from Windows?"
date: 2008-10-21
forum: Wine
---

### Post by wownerd87 on 2008-10-21
Hi guys, 
I'm currently Dual booting with Windows Vista and 8.04 Hardy Heron and I am interested in installing WoW on Ubuntu. I already have Wine and I was copying data from the discs when I realized I could view my windows partition from Ubuntu, so I navigated over to where my WoW folder was and was wondering "**Is there someway you can copy the WoW folder from your Windows partition over you linux to avoid patching and installing crap?**Just a thought, just wondering if any of you have tried it. Thanks

---

### Post by Thelasko on 2008-10-21
No

---

### Post by aoanla on 2008-10-21
I'm not sure it wouldn't work. 
I know people who've copied their WoW folder to random places in their harddisk and it still works.

It's worth a try in Wine - the important thing to remember is that you probably won't be able to run it direct from the Windows partition, as Wine doesn't like running stuff from NTFS filesystems, like modern Windows OSs use.

---

### Post by hikaricore on 2008-10-21
> **Thelasko said:**
> No

Don't listen to this one...

YES you can copy your WoW installation over from a ***dows partition to your Linux/Ubuntu partition just fine.
You may need to make a few adjustments to your config.wtf file but normally assuming you have the proper video drivers installed it will run out of the box once you install WINE.

---

### Post by ooobuntooo on 2008-10-21
It does work, I did exactly the same thing.

---

### Post by liquidfunk on 2008-10-21
I did it. So yes.

---

### Post by toasty_ghosty on 2008-10-21
I'm interested in this. Is there any howto's or anything that do it this way? If I were to get Wine working with WoW I could waste even more of my life!

---

### Post by Mahinva on 2008-10-21
If I am not mistaken, what you would do is, while logged into Ubuntu (and presuming you already have Wine installed):

Browse through your Windows partition, locating the entire WoW folder. Copy this folder into the Program Files subfolder that Wine has. The path should be: USER -> .wine -> drive_c -> Program Files. .Wine is a hidden folder (as denoted by being prefixed with a period) so you may have to check off "show hidden files" under the View option for your USER folder. Alternatively, Ctrl+H works for the same effect.

If I'm incorrect, I hope I'll be corrected in a timely fashion.

As others have stated, you may have to alter your config.wtf file - also keep in mind that Blizzard has made changes that many, many users are seeing as a performance drop, regardless of OS.

---

### Post by Eviljim on 2008-10-22
> **Thelasko said:**
> No

Wrong...

 	
> Re: Getting WoW from Windows?
If I am not mistaken, what you would do is, while logged into Ubuntu (and presuming you already have Wine installed):

Browse through your Windows partition, locating the entire WoW folder. Copy this folder into the Program Files subfolder that Wine has. The path should be: USER -> .wine -> drive_c -> Program Files. .Wine is a hidden folder (as denoted by being prefixed with a period) so you may have to check off "show hidden files" under the View option for your USER folder. Alternatively, Ctrl+H works for the same effect.

If I'm incorrect, I hope I'll be corrected in a timely fashion.

As others have stated, you may have to alter your config.wtf file - also keep in mind that Blizzard has made changes that many, many users are seeing as a performance drop, regardless of OS. 

Correct.

---

### Post by wownerd87 on 2008-10-22
> **hikaricore said:**
> Don't listen to this one...

YES you can copy your WoW installation over from a ***dows partition to your Linux/Ubuntu partition just fine.
You may need to make a few adjustments to your config.wtf file but normally assuming you have the proper video drivers installed it will run out of the box once you install WINE.

hahaha i **LOVED** how you censored windows. And thanks for the advice. this will save me time.

---

### Post by hikaricore on 2008-10-24
> **wownerd87 said:**
> hahaha i **LOVED** how you censored windows. And thanks for the advice. this will save me time.

;)

---

