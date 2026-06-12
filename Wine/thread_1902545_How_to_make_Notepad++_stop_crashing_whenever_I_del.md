---
title: "How to make Notepad++ stop crashing whenever I delete or rename a file that is opened"
date: 2011-12-31
forum: Wine
---

### Post by venom104 on 2011-12-31
Okay, I'm running ubuntu 10.04 LTS and wine 1.3.35. Notepad++ works wonderfully in WINE (I even use it as my primary text editor!), but if I have a file opened in Notepad++ and rename or delete the file outside of notepad++, notepad++ crashes and takes the wine process down with it.

I think what's going on here has something to do with a file exist flag, notepad++ checks constantly to see if a file was altered outside of its program, if it is, it throws up an error message. I'm not really sure if the problem is with the signal that ubuntu is sending the the kernel (changing the file name) or if it has to deal with wine dealing with that signal. Either way, I need help.

What can I do to solve this problem? And yes, it is a big deal, I constantly rename my files all the time (as I am an amateur programmer, and I don't use a CVS).

---

### Post by BC59 on 2011-12-31
No I don't have this problem. I tried it and it's not crashing. Maybe is the Ubuntu 11.10 I'm using. You should consider upgrading.

---

### Post by venom104 on 2011-12-31
> **BC59 said:**
> No I don't have this problem. I tried it and it's not crashing. Maybe is the Ubuntu 11.10 I'm using. You should consider upgrading.

If you don't mind me asking, what version of wine are you using? Are you using gnome as a desktop manager, kde, xcfe, or something else? Please give me as many details as you can.

As for upgrading, I did, and I hated it. I could not get used to the unity interface, and the classic gnome desktop just wasn't for me. I tried using KDE but I had too many issues with my nivida diver (causing segmentation faults). I'm sticking with 10.04 until the new LTS comes out.

---

### Post by 73ckn797 on 2011-12-31
Can't you do a "save as" in Notepad when you want to rename the file? Maybe you could copy and paste the file outside of Notepad, then paste as a copy then rename the copied file? 
I do not use Notepad but it seems a logical way to do it.

---

### Post by syerges on 2011-12-31
You can't delete or rename open files in windows so why would you be able to in wine? you have to close out of the files first!

---

### Post by venom104 on 2012-01-01
> **syerges said:**
> You can't delete or rename open files in windows so why would you be able to in wine? you have to close out of the files first!

Your argument is unsound. In windows if I rename or delete a file that is in use (opened in notepad++) an error message pops up asking wither or not I would like to continue having the file displayed in notepad++. It DOES work correctly in windows, this is what I am asking for.

---

### Post by venom104 on 2012-01-01
> **venom104 said:**
> Okay, I'm running ubuntu 10.04 LTS and wine 1.3.35. Notepad++ works wonderfully in WINE (I even use it as my primary text editor!), but if I have a file opened in Notepad++ and rename or delete the file outside of notepad++, notepad++ crashes and takes the wine process down with it.

I think what's going on here has something to do with a file exist flag, notepad++ checks constantly to see if a file was altered outside of its program, if it is, it throws up an error message. I'm not really sure if the problem is with the signal that ubuntu is sending the the kernel (changing the file name) or if it has to deal with wine dealing with that signal. Either way, I need help.

What can I do to solve this problem? And yes, it is a big deal, I constantly rename my files all the time (as I am an amateur programmer, and I don't use a CVS).

I wont mark this problem as solved (because it's not), but there is a workaround listed here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=13036](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13036) (under the comments section).

---

### Post by syerges on 2012-01-01
an error message does not mean it's working... error means doesn't work. Windows gave you a cop out that isn't transferring through wine. If you are trying to change the file in Ubuntu, Ubuntu doesn't give you that option. What you may be able to do is change the file through another windows file management program but what you most likely will have to do is install Windows within Ubuntu if you wish to take advantage of Windows errors.

> **venom104 said:**
> Your argument is unsound. In windows if I rename or delete a file that is in use (opened in notepad++) an error message pops up asking wither or not I would like to continue having the file displayed in notepad++. It DOES work correctly in windows, this is what I am asking for.

---

### Post by syerges on 2012-01-01
An easier possible solution if this is what you are doing: Modding code, testing to see if it works, then either returning to the old code if it didn't or moving forward if it did... Open multiple files in notepad++ and utilize the ctrl + A, C, V to move your code among the files so your test code can be moved to the appropriate file, saved, tested and then continue... If that is not what you are trying to accomplish, perhaps letting us know why you need to change filenames or what you are trying to accomplish may help as I doubt Ubuntu is going to create an error option such as this and then have wine transfer it through.

---

### Post by whatthefunk on 2012-01-01
Just out of curiosity, why use Notepad when there are several other text editors out there made specifically for Linux?

---

### Post by syerges on 2012-01-01
Notepad++ is far beyond Notepad...
I haven't found something close enough myself yet to be satisfied...

---

### Post by venom104 on 2012-01-01
> **whatthefunk said:**
> Just out of curiosity, why use Notepad when there are several other text editors out there made specifically for Linux?

I'd rather this conversation stopped here (it has nothing to do with the forum topic), but to answer your question, it's the best program I've seen so far for writing code. It has the functionality of vi(m) with the ease of use of notepad. I would use vi, but it has a learning curve that I am not willing to go though, just to write code that will solve problems in my textbooks.

I may end up switching to vi, if I ever get a job as a real coder, but for now I will stick with notepad++.

PS gedit doesn't compare to notepad++ (in my opinion).

---

### Post by venom104 on 2012-01-01
> **syerges said:**
> an error message does not mean it's working... error means doesn't work. Windows gave you a cop out that isn't transferring through wine. If you are trying to change the file in Ubuntu, Ubuntu doesn't give you that option. What you may be able to do is change the file through another windows file management program but what you most likely will have to do is install Windows within Ubuntu if you wish to take advantage of Windows errors.

Windows didn't give me the cop out, notepad++ did. The pop up starts to appear under ubuntu, but it freezes the application. It's something that WINE doesn't do that works under windows, but it has to deal with the notepad++ program, not windows.

---

### Post by whatthefunk on 2012-01-01
> **venom104 said:**
> I'd rather this conversation stopped here (it has nothing to do with the forum topic), but to answer your question, it's the best program I've seen so far for writing code. It has the functionality of vi(m) with the ease of use of notepad. I would use vi, but it has a learning curve that I am not willing to go though, just to write code that will solve problems in my textbooks.

I may end up switching to vi, if I ever get a job as a real coder, but for now I will stick with notepad++.

PS gedit doesn't compare to notepad++ (in my opinion).

Thanks for answering the question.  Didnt mean to drag your thread off-topic.

Anyway, resume talking about solutions to your problem.:P

---

### Post by syerges on 2012-01-01
Your best bet is installing VirtualBox and Installing Windows in that so you can manage your files in Windows without having to deal with the confusion between notepad++, Wine, and Ubuntu. I would not suggest anything else in your situation as that will do exactly what you are comfortable with. Good Luck.

---

### Post by syerges on 2012-01-01
Geany is exactly like notepad++ with a couple extra benefits to boot. It will match what you are used to and allows you to rename files without any errors! I didn't try deleting them however...

---

