---
title: "Super meat boy crash on start up!"
date: 2012-06-16
forum: Wine
---

### Post by meathdeath on 2012-06-16
Everytime i try to start up the steam version of Super Meat Boy the game crashes and i get an error saying "fatal error: cold not create XAudio 2 Device."  I am using Wine for anybody who is curious and i got this game from the humble bundle sale that the ubuntu software center had for sale. Any ideas on how to fix this?

---

### Post by Cheesemill on 2012-06-16
The Steam version doesn't work with Wine.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12449](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12449)

---

### Post by meathdeath on 2012-06-16
Thats a load of bull because ive been using it to run Limbo and super brother sword and sworcery. besides the humble bundle gave me steam keys and not linux ones... is there any way to correct that or i am stuck as is?

---

### Post by Cheesemill on 2012-06-16
> **meathdeath said:**
> Thats a load of bull because ive been using it to run Limbo and super brother sword and sworcery. besides the humble bundle gave me steam keys and not linux ones... is there any way to correct that or i am stuck as is?

Sorry, I should rephrase that.

The Steam version **of Super Meat Boy** doesn't work with Wine.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12449](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12449)

This is according to the Wine website.

For any support issues try asking at:
[http://support.humblebundle.com/](http://support.humblebundle.com/)

---

### Post by meathdeath on 2012-06-16
is there a way to unsteam it? if that question makes sense.. thanks for clarifying.

---

### Post by Cheesemill on 2012-06-16
I don't have the Humble Bundle #5 but I have a couple of the previous releases.

Purchasing them has always provided me a page of download links for the native Linux versions (I've always purchased from the website, never from the Software Centre), if #5 is the same then there should be no reason to use Steam or Wine, just download and install the Linux version.

---

### Post by uRock on 2012-06-16
Moved to *Wine*.

---

### Post by Dlambert on 2012-06-16
The humble bundle is LINUX NATIVE, so just download the Linux version and run it. There is no steam version for linux because Steam for linux doesn't exist outside or testing.

---

### Post by meathdeath on 2012-06-16
Well i guess its okay because most of my machines run windows and steam is easy to work with... whatever case closed. Thanks all for responding.

---

### Post by Dlambert on 2012-06-17
> **meathdeath said:**
> Well i guess its okay because most of my machines run windows and steam is easy to work with... whatever case closed. Thanks all for responding.

Please mark thread as solved

---

### Post by meathdeath on 2012-06-17
cant mark it as solved for two reasons...

1 i dont know how

2 installed the linux version and its still crashing:lolflag:

---

### Post by Dlambert on 2012-06-19
Can you elaborate on your errors?

---

### Post by Kymus on 2012-06-29
Bump.

It doesn't work for me either.

There are two ways given to install the game (for Linux) via Humble Bundle:

[LIST=1]
[*]Install the bin file
[*]Install it through the software center (which I think uses Crossover to make it playable in Ubuntu)
[/LIST]

When the game loads, it crashes on startup. No error message is given. I have tried the software center version as well as trying it after an install through the bin file and both times it does the same thing.

---

### Post by Dlambert on 2012-06-29
It doesn't use WINE.

---

### Post by Kymus on 2012-06-29
> **Dlambert said:**
> It doesn't use WINE.

My apologies; I'm not sure what WINE has to do with this. Could you elaborate, please?

---

### Post by Ecchlesius on 2012-07-29
Hi,

Even though the thread has been dead for about one month I hope somebody might be able to help me. I lately installed super meat boy from humble bundle  V, but when I start it (both the USC version and if installed via the .bin file) a small black window shows up and then it exits. I get the following Error if started via the Terminal:

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xaf
  Serial number of failed request:  141
  Current serial number in output stream:  143
```Has anbody a clue how to solve this?

Thanks!
Ecchlesius

---

### Post by Kymus on 2012-07-30
I'll have to run it in the terminal on my end and see if it gives the same error.

---

### Post by Kymus on 2012-09-06
I did some searching and found that Super Meat Boy needs to run in windowed-mode ([https://bugzilla.icculus.org/show_bug.cgi?id=5624](https://bugzilla.icculus.org/show_bug.cgi?id=5624)). When you run it in the terminal, use the extension *-windowed*; that did it for me. 

When I ran it though, the screen was chopped off some at the bottom, so skip through the intro and then press enter and you'll be able to access the options and change the window size.

---

