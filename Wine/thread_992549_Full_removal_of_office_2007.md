---
title: "Full removal of office 2007"
date: 2008-11-24
forum: Wine
---

### Post by b3n0 on 2008-11-24
Hey all,
I've been following this tut [http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/) to install Office 2007 under wine. I made a few mistakes, and would like to start over. I thought I had removed it properly. but when I try to re-install it comes up with an error. I don't want to start from step 1 again. I just want to completely remove the office suite and start that step again.
Thanks

Edit:
Big thanks to cogadh. After fully removing office 2007, I was able to successfully install office 2007. Hats of to cogadh and the fore-mentioned tut! :KS

I had actually bothered to read the comments, and it came as no surprise when I found the programs wouldn't launch. One of the comments said that installing NET 2.0 would fix this. It told me to take some code put it into text editor. I saved it as 'fixit.bn' (I didn't know what tag to put on the end).
As I've never ran a script before I did a quick google ad got this (adapted for my scenario)
```
cd /home/concorde/Documents
sudo chmod 755 fixit.bn
./fixit.bn
``` 

I get to step two and get a 'chmod: cannot access `fixit': No such file or directory' error.

Where am I going wrong?
Thanks guys

---

### Post by cogadh on 2008-11-25
I'm assuming that you already tried using Wine's uninstaller app and that was unsuccessful... Well, you can always just delete the .wine directory from your home directory, that will restore Wine to its initially installed state. Of course, that will also delete any other applications you may have installed with Wine.
```
rm -rf ~/.wine
```

---

### Post by b3n0 on 2008-11-25
Thanks heaps :D Problem solved!

---

### Post by b3n0 on 2008-11-29
Has anyone installed office 2007 and got it running?

---

### Post by killer_d76 on 2008-11-30
look here bro... ;) [http://ubuntuforums.org/showthread.php?t=922963]("http://ubuntuforums.org/showthread.php?t=922963")

---

### Post by b3n0 on 2008-11-30
Thanks, thats really good

---

