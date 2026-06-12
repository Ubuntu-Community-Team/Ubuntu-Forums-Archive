---
title: "Flash based windows program linking to more flash files"
date: 2008-01-18
forum: Wine
---

### Post by Gabes Dad on 2008-01-18
This is my first post here in Ubuntu forums, so  . . .

I have setup a computer for my mother with ubuntu and all is working well, except some training / tutorial CDs from the company Curves International.  The cd's are intended for a windows based installation.

I got the the programs to install using the latest version of wine (as of about 2 months ago).  The programs are flash based.  When I click on the shortcuts created on the desktop, the program starts up fine in a window titled "Macromedia Flash Player 8".  However it seems that the program acts as an interface of shortcuts to additional flash files and web links.  I cannot get any of the links to work from within the program.

Do I need to install a win32 based browser (such as firefox or internet explorer) in wine with win32 based flash plugins?  If so could you please point me in a direction on how to do so.

I currently do not have access to this machine, but thought I might get the question out there so that if was an easy fix, some helpful person might have an easy answer.  If you need more specifics, please let me know and I can post them later.

I really would like to avoid reverting back to a windows install as that would be all too easy.  On all other fronts Ubuntu is working great!  Thanks in advance for any advice.

---

### Post by kostkon on 2008-01-19
You can install the built-in Wine web browser that mimicks *Internet Explorer* (but actually is *Gecko* based, like *Firefox*) and maybe your links will work. 

To install it, open a terminal and do
```
wine iexplore.exe
```

It will ask you (I think) if you want to install the browser; accept it and wait the install to finish.

---

