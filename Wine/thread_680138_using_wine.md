---
title: "using wine"
date: 2008-01-27
forum: Wine
---

### Post by omi291 on 2008-01-27
I am able to run programs in wine from the virtual c drive it creates, but i dual boot with windows xp, and i was wondering if there was any way i could run programs by using the executables in the windows partition. Much thanks in advance.

---

### Post by emarkd on 2008-01-27
You can boot your entire Windows partition in VMWare and run them that way, but otherwise I don't think that's going to work.

---

### Post by omi291 on 2008-01-27
> **emarkd said:**
> You can boot your entire Windows partition in VMWare and run them that way, but otherwise I don't think that's going to work.

It turns out that vmware can't be installed on my computer :(...but it's no big deal. There's probably a lot of linux equivalents anyway. Thanks for your help though :D

---

### Post by GavinZac on 2008-01-27
It depends on the program.

If its something large that uses various DLLs and registry keys, you might have some problems. However, I'd encourage you to give it a go :)

Heres how, for an imaginary "My Application" program :) :
If your "Windows" drive already shows up in ubuntu, you can open a terminal window and "change directory" so you're in the folder with your application.
command (where XX is the id of the drive you're change into):

cd "/media/sdXX/Program Files/MyApplication"

then we want to run it with wine... which is very simple :)
command: (quotes are needed if there are spaces in the name)

wine "My Application.exe"

With luck, your program will start :) if not, the terminal will show some helpful, if ugly ;) , error messages explaining what went wrong, to help you trouble shoot.

---

### Post by omi291 on 2008-01-27
> **GavinZac said:**
> It depends on the program.

If its something large that uses various DLLs and registry keys, you might have some problems. However, I'd encourage you to give it a go :)

Heres how, for an imaginary "My Application" program :) :
If your "Windows" drive already shows up in ubuntu, you can open a terminal window and "change directory" so you're in the folder with your application.
command (where XX is the id of the drive you're change into):

cd "/media/sdXX/Program Files/MyApplication"

then we want to run it with wine... which is very simple :)
command: (quotes are needed if there are spaces in the name)

wine "My Application.exe"

With luck, your program will start :) if not, the terminal will show some helpful, if ugly ;) , error messages explaining what went wrong, to help you trouble shoot.

I tried changing the directory using the terminal, but this is what i get when i try to run something like internet explorer:

dominator@Javaid:~$ cd /media/SQ004224P01/Program Files/Internet Explorer/
bash: cd: /media/SQ004224P01/Program: No such file or directory

I don't understand why the termal doesn't recognize this as a valid directory...

---

### Post by GavinZac on 2008-01-28
> **omi291 said:**
> I tried changing the directory using the terminal, but this is what i get when i try to run something like internet explorer:

dominator@Javaid:~$ cd /media/SQ004224P01/Program Files/Internet Explorer/
bash: cd: /media/SQ004224P01/Program: No such file or directory

I don't understand why the termal doesn't recognize this as a valid directory...

Remember your quotation marks! :) it sees the space and assumes anything afterwards is extra info. try:
cd "/media/SQ004224P01/Program Files/Internet Explorer/"

Although I doubt Internet Explorer will work :( Not that I would want to use it, but it would be helpful for website debugging. The IEs4Linux project might get somewhere though :)

---

### Post by p_quarles on 2008-01-28
> **GavinZac said:**
> Remember your quotation marks! 
+1. Linux doesn't understand spaces the same way that Windows does.

I've moved this to the Wine forum, as this is where the Wine-os tend to hang out. ;)

---

### Post by Joeb454 on 2008-01-28
Thanks p_quarles, bet you feel all powerful now ;)

---

### Post by omi291 on 2008-01-28
ok. It's working. Thanks for the help everybody, I really appreaciate it. :D

---

### Post by GavinZac on 2008-01-28
> **omi291 said:**
> ok. It's working. Thanks for the help everybody, I really appreaciate it. :D

Wow, Internet Explorer is working? :) Tell me how! I keep making perfect websites in Firefox 3 then people IM me and tell me how awful it looks in IE7.

---

### Post by p_quarles on 2008-01-28
> **GavinZac said:**
> Wow, Internet Explorer is working? :) Tell me how! I keep making perfect websites in Firefox 3 then people IM me and tell me how awful it looks in IE7.
A little trick I found, thanks to another forum member, that makes it really easy to test web sites:
[http://browsershots.org/](http://browsershots.org/)

---

