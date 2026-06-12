---
title: "Rosetta Stone won't execute 2011"
date: 2011-07-13
forum: Wine
---

### Post by griffermans on 2011-07-13
Hi all,
 
Complete newby here and first time poster.
 
The missus has forced me into buying her Rosetta Stone Total(e). I installed it onto her PC but getting it onto my laptop is driving me mad!
 
I run Ubuntu 11.04. When I right click on the .exe file is says it can't be executed. Then when I go into properties I get a very similar message when I try to check the allow executable box.
 
Any help would be great as me and the missus are now in a race to master Mandarin!
 
Cheers,
 
:P:P:P

---

### Post by Azdour on 2011-07-13
Hi,

Since its an .exe file I am assuming you have installed Wine?

---

### Post by dcsoldschool53 on 2011-07-13
I did a bit of searching for Rosetta Stone. It can be run with wine. Do you have the latest installment for wine. If you don't, I would say try the one that you can get from repositories first, before you try to use the one that you can download from the Internet.```
[http://www.winehq.org/download/](http://www.winehq.org/download/)
```This is another web page I had found with information on wine and Rosetta Stone```
[http://ubuntuforums.org/showthread.php?p=10563240#post10563240](http://ubuntuforums.org/showthread.php?p=10563240#post10563240)
```I hope these help you.

---

### Post by 3rdalbum on 2011-07-13
This is such a commonly-asked problem, but people still don't really know the answer to it. Threads about "How do I actually run stuff in Wine, it says I don't have execute permission" tend to drag on for pages.

It's actually really easy to run programs in Wine. Type 'wine ' in the terminal - yes, with a space character at the end. Now drag the program yo uwant to run into the terminal. Run the resulting terminal command. Done, easy. Just make sure that you really do want to run that program and that you trust its origins.

---

### Post by Mark Phelps on 2011-07-13
Speaking from personal experience, Wine is a very hit-or-miss proposition, meaning, there is no guarantee that ANYTHING will work with Wine -- as the results vary not only by Wine version, but also by the specific app and the version of the app.

The page below is the WineHQ page for Rostetta Stone:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867")

As you can see, the ratings vary from Garbage to Gold.  So, your results will vary as well.

---

### Post by griffermans on 2011-07-15
> **3rdalbum said:**
> This is such a commonly-asked problem, but people still don't really know the answer to it. Threads about "How do I actually run stuff in Wine, it says I don't have execute permission" tend to drag on for pages.

It's actually really easy to run programs in Wine. Type 'wine ' in the terminal - yes, with a space character at the end. Now drag the program yo uwant to run into the terminal. Run the resulting terminal command. Done, easy. Just make sure that you really do want to run that program and that you trust its origins.

Thanks for the tip. I did that and got this

The file '/media/RS_TOTALe/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Any more ideas would be really appreciated. Thanks all.

:):):):)

---

### Post by Mark Phelps on 2011-07-15
> **griffermans said:**
> Any more ideas would be really appreciated. Thanks all.

:):):):)

Yeah ... go to the link I posted for you and read through the testing results by clicking on the right side of the page.  You may find something that fixes it.

---

### Post by griffermans on 2011-07-16
> **Mark Phelps said:**
> Yeah ... go to the link I posted for you and read through the testing results by clicking on the right side of the page.  You may find something that fixes it.

Thanks Mark. Well I looked at that and there are no results for my version of Rosetta with Ubuntu 11.04. I'm guessing that means greater minds than mine haven't tried this yet. Is this case closed?

Please help!!! I'm losing the great Mandarin race! Against Windows 7!!!

:(:(

---

### Post by kittkatt on 2011-07-16
> Thanks Mark. Well I looked at that and there are no results for my version of Rosetta with Ubuntu 11.04. I'm guessing that means greater minds than mine haven't tried this yet. Is this case closed?

Please help!!! I'm losing the great Mandarin race! Against Windows 7!!!


You can definitely get in the trenches (testing, finding hacks/workarounds) if you want.  But if it hasn't been done already and you don't really know your way around Linux that well, its just way less headache to use Windows.

---

### Post by Mark Phelps on 2011-07-16
> **griffermans said:**
> Thanks Mark. Well I looked at that and there are no results for my version of Rosetta with Ubuntu 11.04. I'm guessing that means greater minds than mine haven't tried this yet. 
No, it means that no one who has tested the latest version of Rosetta Stone has bothered to add their results and rating to the list.  This is an opportunity for YOU to do that.
> Is this case closed?:(:(
If none of the other results work, and you can't find something that will -- yes.

As I've tried to tell folks, Wine is NOT a miracle cure, it's a works-some-of-the-time cure, only.

---

