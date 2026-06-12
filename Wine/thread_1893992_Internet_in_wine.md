---
title: "Internet in wine?"
date: 2011-12-11
forum: Wine
---

### Post by jtmcc on 2011-12-11
Hello. I have tried to use 3 programs in wine:  Google scetch-up, Windows media player, and Nitto 1320 Legends. None of them were able to connect to the internet. How do I connect?

Thanks in advance,
     Jtmcc

---

### Post by bluexrider on 2011-12-11
you may need to install Internet Explorer to have WINE gain Internet access.

  [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

WineHQ

---

### Post by ergo-proxy on 2011-12-12
It should be working out of the box, check on winehq for applicationts compatibility.

---

### Post by thatguruguy on 2011-12-13
> **bluexrider said:**
> you may need to install Internet Explorer to have WINE gain Internet access.

  [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

WineHQ

That's not even close to being correct.

---

### Post by jtmcc on 2011-12-13
> **thatguruguy said:**
> That's not even close to being correct.
 Well before you said that, i tried with IE and it didn't work. Can anyone give me an answer?

---

### Post by Claus7 on 2011-12-13
Hello,

I have internet explorer in wine and it works!
You can try crossover as well...

Regards!

---

### Post by jtmcc on 2011-12-13
No, I think there is a misunderstanding. IE works, but nothing else does. Also, crossover is not free or open sourse, and i am kinda looking for something free or open sourse. I also wouldn't mind it if it were in BETA stage...

---

### Post by matt_symes on 2011-12-16
Hi

@jtmcc

Are you using NAT or bridged mode in Virtual Box ?

Kind regards

---

### Post by haqking on 2011-12-16
> **matt_symes said:**
> Hi

@jtmcc

Are you using NAT or bridged mode in Virtual Box ?

Kind regards

where does the OP mention virtual box ?

are they not referring to WINE ?

or am i missing something ?

cheers

---

### Post by matt_symes on 2011-12-16
Hi

> **haqking said:**
> where does the OP mention virtual box ?

are they not referring to WINE ?

or am i missing something ?

cheers

I just had a senior moment, i think.

If you were posting where i currently am, you would understand ;)

Kind regards

---

### Post by jtmcc on 2011-12-16
I am not using virtualbox. I am using wine.

---

### Post by haqking on 2011-12-16
> **matt_symes said:**
> Hi



I just had a senior moment, i think.

If you were posting where i currently am, you would understand ;)

Kind regards

ha no worries.

You may want to go back and edit your post, it may confuse the OP.

senior moments, i have had them since i was 16 ;-)

cheers

---

### Post by haqking on 2011-12-16
> **jtmcc said:**
> I am not using virtualbox. I am using wine.

you need to give more information.

I probably cannot answer your questions as i am not a wine user, however you need to say what version of WMP etc you are using.

have you checked the wineHQ appdb to see if issues ? some versions of WMP are rated as garbage so it depends i guess.

cheers

---

### Post by jtmcc on 2011-12-16
I have isited Wine HQ, and searched some of my apps. I am not on my computer, but as soon as i get home I can provide more information.

---

### Post by matt_symes on 2011-12-16
Hi

If you run those programs that have no Internet access, using wine, through the terminal, do you see any error messages?

If you do then post them back here.

Kind regards

---

### Post by jtmcc on 2011-12-16
> **matt_symes said:**
> Hi
 
If you run those programs that have no Internet access, using wine, through the terminal, do you see any error messages?
 
If you do then post them back here.
 
Kind regards
 
How to you open wine in the terminal?

---

### Post by haqking on 2011-12-16
> **jtmcc said:**
> How to you open wine in the terminal?

edit: bad command path

---

### Post by matt_symes on 2011-12-16
Hi

> **jtmcc said:**
> How to you open wine in the terminal?

Read this.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

```
wine "C:\PATHTOPROGRAM\Program.exe" 
```

Kind regards

---

