---
title: "DVDs refuse to play"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by Digikid on 2009-11-10
Greetings all.

I will get right to the point.

DVDs refuse to play.
DVDs are playable everywhere else
Tried VLC and other players
Restricted Extras are already installed.
Will play in Win7 ( So it is not the drive )

Pls advise.

---

### Post by blueridgedog on 2009-11-10
Did you install libdvdcss2?  The process I used was:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install libdvdcss2
```

You have to add the medibuntu sources.  If you run the commands one at a time, then omit the &&

---

### Post by Digikid on 2009-11-10
Sorry but I am a complete noob when it comes to Linux.....sources?

I need a step by step.  Sorry in advance........

---

### Post by mudguts on 2009-11-10
AWESOME!
I had the same problem.
Now I can watch movies with VLC
Looks like I'm keeping this laptop for awhile.

step by step..

open 'Terminal'
copy and paste each line: i.e. "sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list"

In terminal, paste = SHIFT+CTRL+V or click on 'edit' then paste.

it will ask you for the user password.

do that for each line, don't put in the "&&"  Should see LOTS of lines of code roll up.

after about 5 minutes, you'll be done.

Then start VLC and put in a DVD.

---

### Post by Digikid on 2009-11-10
I figured it out.


Thanks blueridgedog!!!!!!!!!!!!!!

You would think that this would have been a part of the restricted extras install......ah well.

Thanks mudguts!!!!

---

### Post by blueridgedog on 2009-11-10
> **Digikid said:**
> Sorry but I am a complete noob when it comes to Linux.....sources?

I need a step by step.  Sorry in advance........

Sorry, though I see you have it solved, you could just copy and paste the commands into a terminal (all at once the way they are written).

I apologize for not being clear.  The commands add the medibuntu sources to your repositories, then downloads the dvd library.  I too wish they would include it in the restricted bundle...

---

