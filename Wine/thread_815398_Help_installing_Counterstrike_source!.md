---
title: "Help installing Counterstrike source!"
date: 2008-06-01
forum: Wine
---

### Post by Kidfork on 2008-06-01
Ok i just purchased a copy of counterstrike source. Now It installs fine. BUT  when it says to insert another disc. The drive wont let me open. COunterstrike has about 4 discs and i cant get the drive to  open. When it says "Insert disc 2" i put the button manauly on the drive. And when i try to open it through Ubuntu it just says "Unable to Unount application is blocking"

IM USING UBUNTU 8.04 HARDY HERON

---

### Post by Kidfork on 2008-06-01
I havea purchased copy of croosover games if that helps.

---

### Post by seekers on 2008-06-01
If you install this at a windows machine.  It makes you create a account and then you can install your game.  The reason I said this is then you can go to linux and then download steam and just install steam and then your game.  It installs from the internet.  Which is pretty cool.  If you don't have a windows box you might need to umount the cd and put your next cd in the drive.  Hope this make sense.

---

### Post by Kidfork on 2008-06-01
It wont let me Unmount

---

### Post by seekers on 2008-06-01
First off I assume you this is your first steam game?  Also you don't have a windows machine to install on correct?

---

### Post by seekers on 2008-06-01
On your desktop you have a cdrom icon you can click on it and say eject  Does this work?

---

### Post by Kidfork on 2008-06-01
NO its says it the install app. is blocking it from unmounting

---

### Post by seekers on 2008-06-01
in a termial type 

sudo umount /media/cdrom

---

### Post by ukblacknight on 2008-06-02
in the terminal type:

wine eject d:

(where d: is your CD-ROM drive letter)

---

### Post by Brynster on 2008-06-02
you could make folders for each cd on your desktop and run the install from there. When it says insert disc 2 click browse and point it towards disc 2 folder.

Or download steaminstall.exe and create an account. When thats done on the my games tab at the bottom there is a link to activate a game. do that and it will then allow you to download and the game directly.

---

### Post by seekers on 2008-06-13
It good to know there is more then one mind out there with a solution.  I hope you get Counterstrike source up and running.  :popcorn:  The forum makes Ubuntu great because of the people who are on it.

---

