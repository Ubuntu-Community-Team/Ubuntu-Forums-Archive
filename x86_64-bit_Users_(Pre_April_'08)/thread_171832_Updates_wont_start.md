---
title: "Updates wont start?"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by BGOAT PiNkY on 2006-05-07
Ok my friend just recently switch to Ubuntu Linux...  but when he goes to install the 125 updates he has to install he go's in and types his pw.. and after that nothin happens? so is ther a way that he can get his updates in.. thanx.

---

### Post by oscar on 2006-05-07
He could try upgrading from the command line.
Open a terminal and:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by BGOAT PiNkY on 2006-05-08
ok dood... the update manager... wont even budge...... everytime when clicked on da updates wont start after puting in password.... and when i did the sudo command in the terminal nothing aswell....

---

### Post by Harold P on 2006-05-08
[QUOTE=BGOAT PiNkY]ok dood... the update manager... wont even budge...... everytime when clicked on da updates wont start after puting in password.... and when i did the sudo command in the terminal nothing aswell....[/QUOTE]

Make sure you did

```
sudo apt-get dist-upgrade
```

---

### Post by aimislame15 on 2006-05-08
Are you connected to the internet?

---

### Post by Churusaa on 2006-05-09
[quote=aimislame15]Are you connected to the internet?[/quote]

...

I imagine he would have to be for his computer to be reporting available updates.](*,)

In any case, [COLOR=Red]Ctrl + Alt + F1[/COLOR], enter his [COLOR=Red]username[/COLOR] (hit enter), his [COLOR=Red]password[/COLOR] (hit enter), then enter this line at the prompt:
[COLOR=Red]sudo apt-get update && apt-get upgrade && apt-get dist-upgrade && exit

[/COLOR]After this completes, [COLOR=Red]Ctrl + Alt + F7[/COLOR] and you're done.

---Churusaa

---

