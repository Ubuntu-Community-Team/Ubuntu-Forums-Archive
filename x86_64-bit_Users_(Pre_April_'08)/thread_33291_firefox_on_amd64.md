---
title: "firefox on amd64"
date: 2005-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by AmJosh on 2005-05-10
I am not being able to run firefox and thunderbird on 64 bit kubuntu 5.04. When i start them, they just try to start .. but eventually die down. Is there a solution to this? I dont know why others are not having this problem.

---

### Post by mthaddon on 2005-05-10
try running it from the console - what output do you get?

---

### Post by medication on 2005-05-13
[QUOTE=AmJosh]I am not being able to run firefox and thunderbird on 64 bit kubuntu 5.04. When i start them, they just try to start .. but eventually die down. Is there a solution to this? I dont know why others are not having this problem.[/QUOTE]

I realize that this isn't very helpful... but I have firefox up and running on AMD Athlon 3200+ and ubuntu 5.0.4.  I think that you should try what mthaddon suggested and then post what you find here.  Then perhaps we can help you a bit more.

---

### Post by Bitchcassidy on 2005-05-13
[QUOTE=mthaddon]try running it from the console - what output do you get?[/QUOTE]

Hi all !

I have a crash too with my firefox under AMD 64
here is my output :

:~/prog/Skale076wFixed$ firefox
NP_Initialize
New
SetWindow
[3]+  Done                    firefox
Erreur de segmentation
:~/prog/Skale076wFixed$

I have to notice that it crashes down only when I run a flash web 
like skale.org for example

I think the bug is simple to resolve; THERE IS NO FLASHPLAYER plugin for AMD64 based ubuntu !!
ARGH !!

I am so desappointed with that !!

Have you any other information ?
Thx in advance

AMD64
HOARY and fan

---

### Post by Crad on 2005-05-13
[QUOTE=Bitchcassidy]Hi all !

I have a crash too with my firefox under AMD 64
here is my output :

:~/prog/Skale076wFixed$ firefox
NP_Initialize
New
SetWindow
[3]+  Done                    firefox
Erreur de segmentation
:~/prog/Skale076wFixed$

I have to notice that it crashes down only when I run a flash web 
like skale.org for example

I think the bug is simple to resolve; THERE IS NO FLASHPLAYER plugin for AMD64 based ubuntu !!
ARGH !!

I am so desappointed with that !!

Have you any other information ?
Thx in advance[/QUOTE]
 Setup a chroot ubuntu env, then you can run firefox with flash, java, etc without issue.

---

### Post by Bitchcassidy on 2005-05-13
Hi, 

thx for immediate answer !

i was just reading this solution on your post [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) 

but i have to resolve all pb which occure on my amd64, it's my deal  :grin: 

The flash player bug is the lastest bug left, so i want to find a more suitable solution than chroot (even if it works !) because I ever know that it runs on 32B ...  ](*,) 

no more idea ?

---

### Post by harryc on 2005-05-13
Install 32bit Firefox.

---

