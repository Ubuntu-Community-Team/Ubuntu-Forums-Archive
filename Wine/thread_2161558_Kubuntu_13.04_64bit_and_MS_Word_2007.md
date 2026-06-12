---
title: "Kubuntu 13.04 64bit and MS Word 2007"
date: 2013-07-11
forum: Wine
---

### Post by mastablasta on 2013-07-11
I've installed MS office 2007 in wine. it works except word is giving out errors. according to it something is missing on install as well as some main templates are missing. the funny thing is it actually sort of works but is giving out annoying erros (about nromal.dot and few other templates missing and such). i am not sure but i think it could be because i installed it on 64 bit OS. Previously i installed it to 32bit Kubuntu 12.04 an dit works without any errors there. i used Playon linux to install but i installed manually without using prescripted option. anyway i've read wine database and saw this:

> If using 64 bit Wine, you must create a pure 32 bit wineprefix with WINEARCH=win32


i am thinking perhaps this is the reason why the errors are popping out. so how do i see this up? there is nothing in wineconfig it seems. at leats i can't find it. where do i create this wineprefix? playonlinux didn't ask me this.


this is the last thing i need to install and then i need to give some quick tour for the new Linux convert.:guitar: i really wish they made MS Office for Linux.

---

### Post by mastablasta on 2013-07-16
Bump!

---

### Post by BreezyBrooke on 2013-07-16
Why are you bothering with MS Office? Calligra is more than enough, and is MS Office compatible.

---

### Post by robert shearer on 2013-07-16
Something close to MSoffice and rather more up to date than '07 
[http://www.omgubuntu.co.uk/2013/07/wps-office-hits-alpha-11](http://www.omgubuntu.co.uk/2013/07/wps-office-hits-alpha-11)
[http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt](http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt)

Distrowatch currently have a review of it.....
[http://distrowatch.com/weekly.php?issue=20130715#qa](http://distrowatch.com/weekly.php?issue=20130715#qa)

and there is a community site here...
[http://www.wps-community.org/](http://www.wps-community.org/)

---

### Post by Elfy on 2013-07-16
> **BreezyBrooke said:**
> Why are you bothering with MS Office? Calligra is more than enough, and is MS Office compatible.

For you maybe - this is a support thread - either help with the support request or don't post in it.

---

### Post by BreezyBrooke on 2013-07-16
Elfy, I am helping. I was just asking him why it was cructial to use MS Office programs. Wasn't really telling him to not use them or anything, but rather giving a good alternative. Just want to know what are his specific needs and can they be met elsewhere. If not, then we look to fixing the problem at hand.

"Why fight on the beaten path, when there is a less treturous one that leads to the same place?"

---

### Post by mastablasta on 2013-07-18
i saw the WS review already and intend to try it out.

however that is still not MS office.

i have MS office running on Kubutnu 12.04 32 bit with no issues. However the 13.04 64 bit is giving error (but only in word). and it seems the error has something to do with using 64 bit OS.

So where do actually i put this line (that could solve the issue):

> If using 64 bit Wine, you must create a pure 32 bit wineprefix with WINEARCH=win32

i've found this tip on wine appdb but it doesn't say where to put it. i suspect the erro is cause because word is searhcing for file sin wineprefix while in reality the all the files are in wineprefix(x86).

also i have a further question regardign wine and MS office  - does Word, Excel and Powerpoint 2010 work well in Wine (on 13.04 64 bit)? has anyone tried them here?

there is a reason why i need to install MS office that might need to be used within next 2 or 3 years. i've told the user about libre office and will have them give WPS a try, but they still might need MS Office to propperly edit documents from work. for all their other programmes we found Open source alternatives, while for some they've already used open source on windows (TB, FF, GIMP) so we only needed to migrate the user data. i will post about experience of switching windows XP user to linux later in "review section" once we get it all up and running. it might help some users pondering wheather to make/stick with the move or not.

---

