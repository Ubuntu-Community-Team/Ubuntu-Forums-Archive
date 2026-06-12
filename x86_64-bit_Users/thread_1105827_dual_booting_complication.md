---
title: "dual booting complication"
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by kushy on 2009-03-25
I apologize if what I am asking has already been posted. I have a dual booting hard drive with Windows xp and Ubuntu(latest). As usual, my windows partition became unstable and I had to re-format it. All I did was delete the ntfs file partition, then re-install xp. All of my past reformats have been successful, with the choice screen appearing with the option to chose which format to launch. Instead it goes straight into xp. Running the live disk, I can see the old linux partition is still there, but I cant launch it. Do I need to create a new swap file? I am looking for the least time consuming method. I don't know if I am overlooking something or not. any advice?

---

### Post by dagoth_pie on 2009-03-25
I can help with this, boot up on the live cd, go to the terminal and type

```
sudo grub
```

it could take a few minutes, depending on the speed of your computer, but youll end up at a grub terminal (unless something goes wrong), type at the terminal 

```
find /boot/grub/stage1
```

then it will give you a responce, on my pc since my ubuntu partition is the second one I'll use (hd0,1) as an example but youll need to use what it comes up with
then type

```
root (hd0,1)
```
and then
```
install (hd0)
```

I'm pretty sure thats right, if you get an error with the last part, try using setup instead of install

Good luck

---

### Post by kushy on 2009-03-25
thank you very much! about to try now!

---

### Post by dagoth_pie on 2009-03-25
Happy to help, I need to know things like this to help friends who insist on having windows

---

### Post by kushy on 2009-03-25
worked perfectly with setup. thanks again!

---

