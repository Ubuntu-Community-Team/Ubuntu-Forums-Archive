---
title: "Installing from cd"
date: 2007-12-02
forum: Wine
---

### Post by badger127 on 2007-12-02
Hi I'm a complete beginner. I want to know how to install a game from a cd using wine. I have wine, I have the cd-rom drive listed in drives. The cd is in the drive. I checked on the wine database and it says it is compatible. So any ideas on what I do?

---

### Post by cogadh on 2007-12-02
Run this in the terminal:
```
wine /media/cdrom/setup.exe
```
Change the path and such to match your actual drive and the executable name, if necessary. 

You might also want to check the "Stuff I've learned about Wine" link in my sig. It will give you some pointers on the basic usage of Wine.

---

### Post by badger127 on 2007-12-02
Ok I'm an absolute beginner. What's the "home directory" referred to in the "stuff I've learned about wine" article?

---

### Post by cogadh on 2007-12-02
Your home directory is where your login profile is stored. It's like the "Documents and Settings" directory in Windows. In the file system it is found in /home/<username>. When you open a terminal, it opens in your home directory by default.

Just a little unsolicited advice; if you are that new to Linux, you should probably spend more time learning about the ins and outs of it before you try tackling running Windows apps through Wine. While Wine is not the most advanced thing you can do with Linux, it is generally not for fresh beginners.

---

### Post by badger127 on 2007-12-03
Ok thanks. My tech support guy who teaches me stuff is sick at the moment. Thanks for your help.

---

### Post by ubuntienewb on 2011-05-19
just wanted to say thanks as your post helped me out aswell as i was installing from a cd and had no idea what i was looking for.

---

### Post by chromatica86 on 2011-05-20
An even easier way is to just open the cd, right click setup.exe and choose "open with wine windows program loader"

---

