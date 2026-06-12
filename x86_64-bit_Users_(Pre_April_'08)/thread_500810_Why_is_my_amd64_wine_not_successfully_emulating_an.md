---
title: "Why is my amd64 wine not successfully emulating anything?"
date: 2007-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joe88 on 2007-07-14
I have an AMD64 processor, Ubuntu feisty 7.04 32 bit and Wine AMD64 0.9.40. 

When i try and emulate a program which the wine application list says should work fine; it doesn't. For example according to W3ird_N3rd, Microsoft office 2000 should install and run well on feisty 7.04 using wine 0.9.39.

[http://appdb.winehq.org/appview.php?iVersionId=5124](http://appdb.winehq.org/appview.php?iVersionId=5124)

But when i click the install button i get an endless list of errors in the terminal, mainly to do with things being unimplemented. When the install completes  the office 2000 install wizard says it was successful yet no shortcuts have been made to office 2000 so i don't think it was installed. 

Does anyone know why its not working?

---

### Post by Kilz on 2007-07-14
> **Joe88 said:**
> I have an AMD64 processor, Ubuntu feisty 7.04 32 bit and Wine AMD64 0.9.40. 

When i try and emulate a program which the wine application list says should work fine; it doesn't. For example according to W3ird_N3rd, Microsoft office 2000 should install and run well on feisty 7.04 using wine 0.9.39.

[http://appdb.winehq.org/appview.php?iVersionId=5124](http://appdb.winehq.org/appview.php?iVersionId=5124)

But when i click the install button i get an endless list of errors in the terminal, mainly to do with things being unimplemented. When the install completes  the office 2000 install wizard says it was successful yet no shortcuts have been made to office 2000 so i don't think it was installed. 

Does anyone know why its not working?

Wine installs programs to a hidden folder in your home folder . To see if , click edit, then preferences, then check the "Show hidden and backup files". Close nautilus and reopen. You should see a .wine folder, inside that is c_drive and Program Files. Look and see if it was installed and a shortcut wasnt made.

---

### Post by tjotser on 2007-07-14
" I have an AMD64 processor, Ubuntu feisty 7.04 32 bit and Wine AMD64 0.9.40. "

I could be wrong on this, but you have a 32 bit ubuntu, and are running a 64 bit versionof wine, is that even possible ? What i do is add their repository for ubuntu (9.41 IS OUT !!) and get it from there.

---

### Post by Joe88 on 2007-07-14
> **Kilz said:**
> Wine installs programs to a hidden folder in your home folder . To see if , click edit, then preferences, then check the "Show hidden and backup files". Close nautilus and reopen. You should see a .wine folder, inside that is c_drive and Program Files. Look and see if it was installed and a shortcut wasn't made.

**I have used the search tool and looked in my home directory and file system for .wine and it found nothing - i had enabled "Show hidden and backup files"**

[QUOTE=tjotser] I could be wrong on this, but you have a 32 bit ubuntu, and are running a 64 bit version of wine, is that even possible ? What i do is add their repository for ubuntu (9.41 IS OUT !!) and get it from there.[/QUOTE]

I had originally tried installing the non AMD 64 version of wine (which is 32bit) which came with Ubuntu and that said it couldn't work because it wasn't made for an AMD64. 
tjotser do you have an AMD64 processor? if so please give me the terminal commands you used to install wine 9.41 with.

---

### Post by Motoxrdude on 2007-07-14
I have an amd 64 bit capable processor but i am using the 32bit version of wine in ubuntu 32bit.
Try
```
sudo apt-get remove --purge wine
```
```
sudo apt-get install wine
```
```
winecfg
```
Now try running your programs and see if you get any better results.

PS- Are you sure you are running ubuntu 32bit? Post the output of
```
uname -r
```

---

### Post by Joe88 on 2007-07-16
My uname -r output is : 2.6.20-16-generic

i reinstalled wine and ran winecfg, the .wine directoy appeared in my home folder but office 2000 still doesn't work, along with all the other software I've tried.

---

### Post by Motoxrdude on 2007-07-16
> **Joe88 said:**
> My uname -r output is : 2.6.20-16-generic

i reinstalled wine and ran winecfg, the .wine directoy appeared in my home folder but office 2000 still doesn't work, along with all the other software I've tried.

Can you run it in the terminal and paste the output here?

---

### Post by Joe88 on 2007-07-18
Thanks for all your help, but i have set up windows xp to dual boot now so i can play games on that and don't need wine.

---

### Post by W3ird_N3rd on 2008-01-13
> **Joe88 said:**
> I have an AMD64 processor, Ubuntu feisty 7.04 32 bit and Wine AMD64 0.9.40. 

When i try and emulate a program which the wine application list says should work fine; it doesn't. For example according to W3ird_N3rd, Microsoft office 2000 should install and run well on feisty 7.04 using wine 0.9.39.

[http://appdb.winehq.org/appview.php?iVersionId=5124](http://appdb.winehq.org/appview.php?iVersionId=5124)

But when i click the install button i get an endless list of errors in the terminal, mainly to do with things being unimplemented. When the install completes  the office 2000 install wizard says it was successful yet no shortcuts have been made to office 2000 so i don't think it was installed. 

Does anyone know why its not working?
I know it's a big bump, but if you just mention me it takes a while before I read your message.

I made a mistake in that test. I installed Office 2000 with wine 0.9.33. That works fine. I ran it with 0.9.39. That works fine as well. *Installing* however is absolutely impossible with 0.9.39. But I believe that bug is fixed by now ;). I don't know which other applications you tried, but if you want to test wine you should first test winecfg and regedit. If they work you could try a simple application that is not fullscreen, does not need Direct3D or OpenGL, should work according to the appdb and has no installer. Something like notepad++ for example.

---

