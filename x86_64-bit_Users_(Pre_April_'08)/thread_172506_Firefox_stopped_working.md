---
title: "Firefox stopped working"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjthfx on 2006-05-08
Hi folks,

I am very new to Linux so please bare with me. Also new to the forums. I see a lot of discussion regarding FF 1.5 and Flash but my problem is unrelated (I think)

Installed Ubuntu 64 over the weekend on my AMD 64 system.

Had some issues with my ATI vid but some solid How to's from the community helped me through it. I used Firefox, no problem when I first installed... but now I go to run it and all the happens is the "Starting Firefox" appears on the panel bar... then it goes away and I don't get anything. No error, no firefox.

I do recall an upate happening, but I tried to go into the app loader and re-install mozilla firefox, but no luck.

Should I mv my profile or what? I don't want to totally remove it as its tied in with gnome desktop and yelp and other apps.

What do you suggest?

Thanks in advanced,

Mark

---

### Post by kaffeine on 2006-05-08
what output does running firefox from a command prompt give?

---

### Post by mjthfx on 2006-05-09
:-k  Hmmm how do i do that?

start firefox? at the terminal?

Sorry, I am such a newb.

---

### Post by kaffeine on 2006-05-09
we are all newbies at some point :) open up a terminal, and just type ```
firefox
```

if there is some error with firefox, then it will spit out on the terminal. you can copy paste that error here.

or if you like a nifty shell trick, do ```
firefox >& foo.txt
``` and that will redirect(write) the error to the text file foo.txt in your working dir.

---

### Post by mjthfx on 2006-05-12
Nothing happens, no error message, no nothing

---

### Post by henriquemaia on 2006-05-12
On a terminal, type:

```
killall firefox-bin
```

Then, restart firefox. I had that previously. Firefox hang for some reason and wouldn't start. I killed its process and restared it after a while and everything was ok.

---

### Post by mjthfx on 2006-05-12
Sorry double posted

---

### Post by mjthfx on 2006-05-12
Message says:

> firefox-bin: no process killed](*,) 
and still nothing... managed to get Ephiany browser working... the Mozilla Browser didn't work either. Same thing... Starting Firefox Browser would show in panel then go away.

---

### Post by henriquemaia on 2006-05-12
Try deleting (backup) your firefox directory, where it keeps your firefox's configurations. On a terminal type:

```
cd ~
```
then
```
mv .mozilla/ .mozilla-backup
```

After this, restart firefox.

Maybe this will help.

ps: this will backup the directory of firefox's configuration files. If you have bookmarks you like to recover, then import them throught firefox, looking for them on that directory (~/.mozilla-backup)

---

### Post by mjthfx on 2006-05-12
Henrique,

YOU DA MAN! Thank you very much, that was it!!!!\\:D/ \\:D/

---

### Post by henriquemaia on 2006-05-12
[QUOTE=mjthfx]Henrique,

YOU DA MAN! Thank you very much, that was it!!!!\\:D/ \\:D/[/QUOTE]

lol, I had that issue a couple of times also, :)

---

### Post by henriquemaia on 2006-05-12
If everything is ok now, you can delete that backup directory.

Just rm it.

---

