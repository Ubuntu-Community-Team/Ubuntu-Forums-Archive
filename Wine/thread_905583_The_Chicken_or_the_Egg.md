---
title: "The Chicken or the Egg"
date: 2008-08-30
forum: Wine
---

### Post by lakersforce on 2008-08-30
I'm trying to install EMI (Escape from Monkey Island) and I'm doing it from iso's rather then cd's (I let a friend borrow the game from me, but he returned it scratched. So now I have downloaded it from a torrent). I mount the first cd and runs the setup (wine /path/to/mounted/iso/setup.exe). Halfway through I have to switch to disc two. But I can't unmount it, since it in use.

Any advice?

(I don't want to burn it to cd's)

---

### Post by scragar on 2008-08-30
I think you should be able to temp freeze the state of the wine ap:
```
kill -STOP **pid**
```
do what your doing with the disks, then resume the process:```
kill -CONT **pid**
```
This doesn't work with xkill though, so no GUI(the gnome system monitor has the option built in BTW).

I can't be 100% sure this will work though.

---

### Post by gmxgeek on 2008-08-30
you should be able to mount the 2nd iso to a different drive, then specify an alternate location for CD2. Most installers have this for support for multiple cd drives.

eg: E:/setup.exe vs D:/setup2.exe

---

### Post by lakersforce on 2008-08-30
Stopping the process does not work. I am still told that the device is busy. 

And the installer does not allow you to specify a location.

---

### Post by scragar on 2008-08-30
can you move/rename the iso file? You might be able to take advantage of the remount option...

---

### Post by lakersforce on 2008-08-30
Yes, I can rename the file. But I am not sure I understand what you mean. Could you spell it out for me?

---

### Post by scragar on 2008-08-30
well the command to remount something is```

mount -o remount **normal stuff here**

```

if your file for example is called CD1.iso you should be able to change that to CD1_read.iso, and them rename/link to the second CD under the old name of CD1.iso run the remount(which should work, I've never had any problems remounting in use devices before) command to switch the CD.


I know this is far from a perfect solution, but in future might I recomend setting your CD drive in wineconfig to be a symlink from your desktop, then change where the link points as needed...

---

### Post by lakersforce on 2008-08-30
I cannot get it to work which is probably because I am using the command wrong, so I'll write what I wrote in the console here.

First I mounted the first iso with: mount -o cd1.iso /path/to/mount/point/

Then I did as you suggested, renamed the first cd and then renamed the second cd to cd1.iso. Then I used the following command: mount -o remount cd1.iso /path/to/mount/point/

I am not receiving any error messages (or any messages at all). When I check the mountpoint, the first cd is still mounted.

(Just for clarification, I of course used sudo with the mount commands)

---

### Post by nickgaydos on 2008-08-30
:( you got me all excited...
The Chicken or the Egg is a VERY popular restaurant in Long Beach Island, New Jersey. I went there 4 times this year it's so good!

---

### Post by lakersforce on 2008-08-30
I am still stuck....

---

### Post by scragar on 2008-08-30
I've got 1 last idea, don't mount the iso's, extract them in the folder, wine see's the folder as the CD, so the fact that somethings mounted there or not doesn't matter to wine, since your putting files into it you can delete the files later and extract the next iso to it.

Sorry if you don't want to try it, but that's my last idea, after that I've nothing.

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Schitso on 2008-08-30
```
wine eject
```

---

### Post by lakersforce on 2008-08-30
```
wine eject
```

...does not work. Not even if configured in winecfg

---

### Post by lovinglinux on 2008-08-30
You could try mounting the CD using CDAnywhere under Wine. I didn't tested, because I was too lazy to download the CDAnywhere program, but this method works on Windows. I just unmounted the first CD in the CDAnywhere interface, mounted the second CD in the same drive and hit OK in the installation.

Anyways, what I did under Ubuntu was extracting both CD's to the same directory and the installation went all the way without asking for the second CD. Obviously that you need to check if both CD's have conflicting file names.

---

### Post by lakersforce on 2008-08-31
I solved the problem by copying the iso's into each-other, as suggested.

But we can also conclude that it is impossible to eject mounted iso's under wine. This means that you can not install anything that's on more than one disc.

---

### Post by lovinglinux on 2008-08-31
> **lakersforce said:**
> I solved the problem by copying the iso's into each-other, as suggested.

But we can also conclude that it is impossible to eject mounted iso's under wine. This means that you can not install anything that's on more than one disc.

w00t

Don't forget to mark the thread as solved

---

### Post by lakersforce on 2008-08-31
> **lovinglinux said:**
> w00t

Don't forget to mark the thread as solved

But it's not solved :-k

Yes, I managed to install EMI, but I still did not find a way to "change cd's" when installing from an mounted iso under wine, which is what is the entire cause of the problem.

I can not unmount while installing, and I can not install without unmounting. Hence the title "The Chicken or the Egg".

---

### Post by lovinglinux on 2008-08-31
> **lakersforce said:**
> But it's not solved :-k

Yes, I managed to install EMI, but I still did not find a way to "change cd's" when installing from an mounted iso under wine, which is what is the entire cause of the problem.

I can not unmount while installing, and I can not install without unmounting. Hence the title "The Chicken or the Egg".

Sorry, I saw the sentence "I solved the problem" so i figured....

---

