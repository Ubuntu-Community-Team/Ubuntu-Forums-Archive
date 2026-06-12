---
title: "Rosetta Stone problem with Wine"
date: 2013-12-02
forum: Wine
---

### Post by micah-gray on 2013-12-02
I installed Wine through Ubuntu Software Center, put in my Rosetta Stone CD, right-clicked on "setup.exe" and a window popped up with the Rosetta Stone icon, saying: "1158:"

How can I install Rosetta Stone?

---

### Post by Mark Phelps on 2013-12-02
Suggest you look through the details on the linked page for the version you're trying to run:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1867")

---

### Post by micah-gray on 2013-12-04
My wine version should accept Rosetta Stone just fine. I tried going another route with this and it got all the way up until it needed to find where to install the program. Its only option was to install it in "C:/" which is only in Windows and isn't the letter of my hard drive.

---

### Post by inthefold on 2013-12-27
I don't think you'll be able to get it to work with Ubuntu. I installed Rosetta Stone and was able to open it, but none of it's fuctionality ever worked. I tried all sorts of things to make it happen but was never able to. If you do, post what you did to get it to work. I just keep a small windows partition for RS.

---

### Post by Profetak on 2013-12-27
SOLUTION! This worked for me:
[http://rosettastone-challenge.blogspot.com.br/2013/12/rosetta-stone-linux.html](http://rosettastone-challenge.blogspot.com.br/2013/12/rosetta-stone-linux.html)

1 &#8211; Install Wine 1.5.14    

  Open the terminal and paste these commands:
sudo add-apt-repository ppa:ubuntu-wine/ppa 
sudo apt-get update 
sudo apt-get install wine1.5  

  
2 - Go to Configure Wine, in the tab 'libraries', enter 'winepulse.drv' in the box and click on add, click yes on the warning. Select winepulse.drv and change load order to 'disabled'.  

3 - Try running Rosetta Stone and see if the problem was solved.  For me, two options of microphone appeared, any will do.

More details on the blog.

---

