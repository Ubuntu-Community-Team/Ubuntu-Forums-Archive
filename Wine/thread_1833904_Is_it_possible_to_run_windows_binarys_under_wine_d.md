---
title: "Is it possible to run windows binarys under wine directly off a windows partition?"
date: 2011-08-26
forum: Wine
---

### Post by ninjaaron on 2011-08-26
I just set a friend of mine up with Ubuntu on a partition alongside Vista.  She, like all rational human-beings, cannot stand using Vista because it is enormous and horrible, and she's got it on a low-end laptop.

She wants to cut it loose, but she also wants Word, at least until she figures out if she can use LibreOffice or not.  Anyway, I set the windows partition to mount in a folder inside of her home folder and made links to all the folders that have her personal data.

Then she asked me if she could also use the programs on the windows partition in Ubuntu.  I just said no and didn't really think about it.  Then I started thinking about Wine, and now I'm wondering if this is possible.

Also, Ubuntu is 32-bit (cause it still has better application support), and all the Vista bins will be 64-bit. I don't know if this makes a difference.

---

### Post by Gunman1982 on 2011-08-26
Can you run windows programs straight from the windows partition with wine: yes
Can you run 64bit windows binarys in wine: not yet, wine64 is still mainly for devs and supports only a handfull of programs
Are those programs on windows vista64bit all 64bit programs: they don't have to be since you can run 32bit windows executables in 64bit windows ... so you could give it a try

Oh and btw:
I'm running Debian 64bit and have no problems regarding application support. So I would suggest to run 64bit if you have the hardware for it. But thats just my personal opinion.

---

### Post by ninjaaron on 2011-08-27
> **Gunman1982 said:**
> Can you run windows programs straight from the windows partition with wine: yes
Can you run 64bit windows binarys in wine: not yet, wine64 is still mainly for devs and supports only a handfull of programs
Are those programs on windows vista64bit all 64bit programs: they don't have to be since you can run 32bit windows executables in 64bit windows ... so you could give it a try

Oh and btw:
I'm running Debian 64bit and have no problems regarding application support. So I would suggest to run 64bit if you have the hardware for it. But thats just my personal opinion.

Thanks for the answer.  I'll let her know.  It's mostly Flash and Skype that I'm thinking of, which she uses all the time, and in all my experience, do not offer the same performance on a 64bit system.

---

### Post by cwwilson721 on 2011-08-27
[COLOR="Red"]WARNING: 

Saying a blanket "Yes" to your question is WRONG.[/COLOR]

SOME programs you CAN run, but quite a few will NOT.

The biggest question is:

*Should* you run them?

And that answer is a **HUGE NO**.

Why? Because you are messing with two TOTALLY different registries, and if you run binaries from the Win partition directly, you run a huge risk of either screwing your entire Windows install, or to a lesser extant, your Ubuntu install (A Windows virus running wild on your Ubuntu partition is NOT something I would want to see)

So, in conclusion:

*Can* you do it? Maybe so, maybe not (think of how much stuff gets installed from a normal program installing in Windows. DLL's, registry settings, 'special' exe and com files in System , etc., that WON'T be there in your wine install. So, maybe, maybe not.

*Should* you do it? **[COLOR="Red"][SIZE="3"]NO WAY!!![/SIZE][/COLOR]**

---

### Post by lordjj on 2011-09-02
> **cwwilson721 said:**
> 
you run a huge risk of either screwing your entire Windows install


How can running applications on Wine affect in any way the Windows install?

> **cwwilson721 said:**
> 
or to a lesser extant, your Ubuntu install (A Windows virus running wild on your Ubuntu partition is NOT something I would want to see)
 

A Windows virus on Ubuntu? How is that even possible?

---

### Post by cwwilson721 on 2011-09-02
> **lordjj said:**
> How can running applications on Wine affect in any way the Windows install?

 

A Windows virus on Ubuntu? How is that even possible?
Go ahead. Do as you wish.
wineHQ even says "DON'T", but you obviously know better (think first. How many registries does it take to screw up Windows? 1. wine has it's own, too. That's 2. Do the math.)

wine CAN run viruses. The possibility is there. And, since you think that wine cannot, you probably have one of the wine drives as "/". OR "/home/<USER>". How long do you think it would take a Windows nasty to erase everything in your home folder?

Read the wineHQ site. Read about Windows viruses in wine. Read.
The possibilities are there, no matter how small you think they are. Even a small one is too much, IMO.

I never run from the Windows partition. (Also, speed is horrible, in some cases). I also only allow wine to have "drives" in it's own folder, never in my "/" or "home/<USER>". It's easy to fix.

I guess in yours the risk isn't too great. 

But, as I said, do as you wish.

So don't cry that "wine erased my Ubuntu!", or "wine destroyed my Windows install!". It IS possible. Is it probable? Maybe not. But I don't like losing data when it is SO easy not to, especially when you allowed it.

---

### Post by Gunman1982 on 2011-09-02
> **cwwilson721 said:**
> [COLOR="Red"]WARNING: 

Saying a blanket "Yes" to your question is WRONG.[/COLOR]

SOME programs you CAN run, but quite a few will NOT.

The biggest question is:

*Should* you run them?

And that answer is a **HUGE NO**.

Why? Because you are messing with two TOTALLY different registries, and if you run binaries from the Win partition directly, you run a huge risk of either screwing your entire Windows install, or to a lesser extant, your Ubuntu install (A Windows virus running wild on your Ubuntu partition is NOT something I would want to see)

So, in conclusion:

*Can* you do it? Maybe so, maybe not (think of how much stuff gets installed from a normal program installing in Windows. DLL's, registry settings, 'special' exe and com files in System , etc., that WON'T be there in your wine install. So, maybe, maybe not.

*Should* you do it? **[COLOR="Red"][SIZE="3"]NO WAY!!![/SIZE][/COLOR]**
There is no difference if you run the windows program straight of the windows partition or copy it somewhere else and run it from there. Yes it is true that you have a dedicated registry with wine but I'm really curious how you can muck around with the windows registry of the program by starting it via wine/ubuntu or even screw up your whole windows install. Apart from the "Setting your wine installation to include your windows-installation c:\" which is in my opinion on the same scale as trying to order your filesystem by the alphabet.

If it is malicious software/virus then it doesn't matter much where you run it from and that risk is always there. You might be lucky that the virus relies on functionality which is not implemented in wine yet and thus fails simply. And its not really related to the question asked.

This "maybe runs"/"maybe runs not" counts for every windows executable you run through wine. I answered the simple question if you can run windows programs straight of the windows partition, and that's a YES. If you should or if it will actually work for a specific program is another question.

---

