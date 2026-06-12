---
title: "Wine Windows Program Loader - is this what must be installed to use wine?"
date: 2012-08-10
forum: Wine
---

### Post by Alexander108 on 2012-08-10
I'm trying to install wine from the Software Centre. I search for 'wine' and get a list which has an option called Wine Windows Program Loader. 
 
1. Is this what I need to install to use wine? When I click install it takes a long while and then error implying internet connection.
 
2. Is there a way to install wine without accessing the internet?
 
3. How do I copy a file from Windows folder into ubuntu Documents folder?
 
Your help will be appreciated.

---

### Post by flurospar on 2012-08-11
> **Alexander108 said:**
> I'm trying to install wine from the Software Centre. I search for 'wine' and get a list which has an option called Wine Windows Program Loader.

All you need to do is type in the terminal:
```
sudo apt-get install wine
```
 
>  Is there a way to install wine without accessing the internet?
Yes, there is: downloading the wine package and all required dependencies, but that's a painful process:

[http://ubuntuforums.org/showthread.php?t=1762889](http://ubuntuforums.org/showthread.php?t=1762889)

You have to replace natty with precise or whatever you have.

---

