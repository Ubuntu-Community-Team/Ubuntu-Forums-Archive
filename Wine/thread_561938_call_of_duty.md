---
title: "call of duty"
date: 2007-09-28
forum: Wine
---

### Post by Hightide on 2007-09-28
HI All

tried to intall COD1 via wine on 6.10. CD1 works fine but wont let me intall CD2.

any ideas

regards

---

### Post by Sockerdrickan on 2007-09-28
What does it say?

---

### Post by cogadh on 2007-09-28
Call of Duty can't be installed normally through Wine. You can get around the CD switch problem by entering "wine eject D:" in a terminal, but the install will fail completely when you have to switch back to the first CD. There is a Loki installer script that can install the game for you, you can get it here (right-click the link and "Save link as"):
[http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run](http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run)

---

### Post by Hightide on 2007-09-28
HI Guys

thanks for that 

regards

---

### Post by cogadh on 2007-09-28
Almost forgot, after the install completes, you will likely get a "wine is not in your PATH" error when you try to run the codsp or codmp launch scripts. You can get around it by running the script with bash instead os "sh" or "./".
```
bash codsp
```

---

### Post by Hightide on 2007-09-28
Thanks for that.

im new to Ubuntu. can you tell me next steps after downloading the loki installer?

much obliged

---

### Post by Sockerdrickan on 2007-09-28
You don't need loki installer, I didn't

---

### Post by cogadh on 2007-09-28
Okay, first you need to make the script executable. Open a terminal and run this:
```
chmod +x call.of.duty_1.5-english.run
```
The script requires the libgtk 1.2 package if you don't already have it installed, run this:
```
sudo apt-get install libgtk1.2
```
Then put in the first CoD cd, change directories to wherever you downloaded the script and run the installer like this:
```
./call.of.duty_1.5-english.run
```
You can accept the default install options. The installer will likely produce one warning (Gdk-WARNING **: locale not supported by C library) and one error (ERROR: No matching delta for /home/<username>/cod/Main/pak0.pk3), both can be ignored. Once the installer completes, change directories to the game's install directory (default is "/home/<username>/cod") and run the game like this:
```
bash codsp
```
For multiplayer, run this:
```
bash codmp
```
That should be it.

> **Tux0r said:**
> You don't need loki installer, I didn't
How did you get past the error after the second CD swap? That one still occurs for me and it prevents the single player game from running. I think multiplayer might work, but that doesn't really matter since PunkBuster can't work anyway. Whatever caused the error also prevents me from updating the game to 1.5 or installing the United Offensive expansion pack.

---

### Post by Hightide on 2007-09-28
Hi

superb advice. Game running well.

i am indebted to you.

regards

---

### Post by go_beep_yourself on 2007-11-24
> **cogadh said:**
> Call of Duty can't be installed normally through Wine. You can get around the CD switch problem by entering "wine eject D:" in a terminal, but the install will fail completely when you have to switch back to the first CD. There is a Loki installer script that can install the game for you, you can get it here (right-click the link and "Save link as"):
[http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run](http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run)

Which other Call of Duties can run native in Linux? That would be nice, but I don't think COD4 can.

---

### Post by Sockerdrickan on 2007-11-24
Who said COD4 can?

---

### Post by finito on 2007-11-24
> **Tux0r said:**
> Who said COD4 can?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699")

---

### Post by hikaricore on 2007-11-24
I may be mistaken.  But i dont believe any of them have native ports...

---

### Post by Sockerdrickan on 2007-11-24
Like hikaricore said that is nowhere near native :P

---

### Post by woody123 on 2008-12-12
i also had this problem - from what i have gathered you use the first cd, use the command 'wine eject' use the second cd eject then works, and then im stuck - this is as far as i can get- please help me (im new to ubuntu)

---

