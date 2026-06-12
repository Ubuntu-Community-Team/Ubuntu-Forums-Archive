---
title: "32-bit software stopped working"
date: 2006-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by kaffelars on 2006-08-30
I run the 64-bit Ubuntu version with the Xeon-optimized kernel, and recently both Skype and Picasa have stopped working. Picasa starts in the tray, but the application itself won't start. I have the ia32-packages installed, and also tried the linux32-wrapper but this had the same results.

Skype won't do anything other than complain about some floating number-error (don't have the computer here, can't remember exactly).

I really can't think of anything I've done recently that can have caused this. Both Picasa and Skype used to run fine. 

Anyone has any suggestions at all? (If not, I think it's gonna be 32-bit this time ;))

---

### Post by John.Michael.Kane on 2006-08-30
kaffelars have you tried to reinstall both programs?

---

### Post by kaffelars on 2006-08-30
Yes, and i deleted the .picasa folder in my home directory, but this didn't change anything. 

I also reinstall ia32 and linux32 but no luck :(

My impression now is that 64 bit is FAST, but best if you don't need all the multimedia stuff that's 32 bit only. Which is what I read before I installed, but I'm glad I gave it a try :)

---

### Post by kuja on 2006-08-30
Assuming you installed them from debs, try running something to the extent of "sudo dpkg-reconfigure skype picasa"

---

### Post by Kilz on 2006-08-30
> **kaffelars said:**
> Yes, and i deleted the .picasa folder in my home directory, but this didn't change anything. 

I also reinstall ia32 and linux32 but no luck :(

My impression now is that 64 bit is FAST, but best if you don't need all the multimedia stuff that's 32 bit only. Which is what I read before I installed, but I'm glad I gave it a try :)

The multimedia stuff thats 32bit only isnt a lot. Its mostly the propretary stuff that gives you fits no matter what version you run. When you try to start the applications in a terminal do you get any errors?

---

### Post by kaffelars on 2006-08-31
With Skype I got an error, but not with Picasa. 
However, I decided to try the 32-bit version, and it really wasn't much slower. Now I have OpenGL, Picasa, Skype and Flash working, so I'm happy :D

Guess I'll give 64 bit Edgy a try in October, though ;)

---

