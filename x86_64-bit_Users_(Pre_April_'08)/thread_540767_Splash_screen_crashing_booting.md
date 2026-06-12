---
title: "Splash screen crashing booting"
date: 2007-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by hadeshorn on 2007-09-01
Hello,

I am finally getting it to slowly work. But I have one annoying bug.

Specs of my machine is AMD x64 3000, ati X700 Pro.

Anyway when Ubuntu gets to grub, when it tries to load ubuntu. It starts for a second then screen goes black and caps lock key flashes.

Now to fix this I have to edit the command line that runs ubuntu to remove the splash command.

So now Ubuntu boots up ok. Like when it boots it goes thru all the text information.

But its kinda annoying to have to always have to edit the boot command to remove splash. Plus be nice to have a splash screen happening.

Any suggestions??

---

### Post by Rui Pais on 2007-09-02
try to reinstall usplash and a usplash theme:
```
sudo aptitude reinstall usplash usplash-theme-ubuntu
```
or replace usplash-theme-ubuntu by other theme you prefer (like kubuntu-artwork-usplash or xubuntu-artwork-usplash)

Alternatively, to make the edit persistent you need to edit the file /boot/grub/menu.lst

---

### Post by crjackson on 2007-09-02
> **hadeshorn said:**
> Hello,

I am finally getting it to slowly work. But I have one annoying bug.

Specs of my machine is AMD x64 3000, ati X700 Pro.

Anyway when Ubuntu gets to grub, when it tries to load ubuntu. It starts for a second then screen goes black and caps lock key flashes.

Now to fix this I have to edit the command line that runs ubuntu to remove the splash command.

So now Ubuntu boots up ok. Like when it boots it goes thru all the text information.

But its kinda annoying to have to always have to edit the boot command to remove splash. Plus be nice to have a splash screen happening.

Any suggestions??

Hey, let me know if that worked.

---

### Post by crjackson on 2007-09-02
Just tried it.  Didn't work for me.

---

### Post by hadeshorn on 2007-09-02
Hey CRjackson,

I notice we have similar specs, maybe thats the problem

As I am also running an AMD64 with an ATI x700

---

### Post by crjackson on 2007-09-02
> **hadeshorn said:**
> Hey CRjackson,

I notice we have similar specs, maybe thats the problem

As I am also running an AMD64 with an ATI x700

Oh, I thought you knew.  Yes, it's the ATI video card / splash screen combination.

---

### Post by hadeshorn on 2007-09-02
Well im going to try installing the kubuntu theme and see if that fixes it.

---

### Post by Rui Pais on 2007-09-02
you may try to add to kernel boot line:
```
vga=791
```
or even 
```
video=vesafb vga=791
```
to use "vesafb" framebuffer rather than "vga16fb".

Or try different vga definitions. Sometimes helps.
[Here]("http://ubuntuforums.org/showpost.php?p=2719341&postcount=2") a list of vga codes. 
[here ]("http://ubuntuforums.org/showthread.php?t=258484")a more complete howto.

good luck

---

### Post by hadeshorn on 2007-09-02
YAY IT WORKS!

in the /boot/grub/menu.lst 
Find where it says splash and then put in vga=0x317 which makes it load the splash in 1024x768

Thanks for all the assistance. CJ! This should work for you as well man!

---

### Post by crjackson on 2007-09-02
> **Rui Pais said:**
> you may try to add to kernel boot line:
```
vga=791
```
or even 
```
video=vesafb vga=791
```
to use "vesafb" framebuffer rather than "vga16fb".

Or try different vga definitions. Sometimes helps.
[Here]("http://ubuntuforums.org/showpost.php?p=2719341&postcount=2") a list of vga codes. 
[here ]("http://ubuntuforums.org/showthread.php?t=258484")a more complete howto.

good luck

I used the 1st one and it worked out good for me.  Very nice, thank you.

what would be the advantage of using vesafb over just vga=###

---

### Post by nicktheawesome on 2007-09-02
Is there a way to remove the splash screen so when I hit Ubuntu in grub it boots like it does in recovery mode, but then goes directly to the login screen? I'd prefer it if I could do this from within Ubuntu, instead of the Grub menu...

---

### Post by Rui Pais on 2007-09-02
> **crjackson said:**
> I used the 1st one and it worked out good for me.  Very nice, thank you.

what would be the advantage of using vesafb over just vga=###

no prob :)
About vesafb, thats an alternative to the framebufer console used by Ubuntu. 
The only reason to use it, it's that it seems to work better with some cards with proprietary drivers. 
If a simple change of vga definition solves the issue, there is no need (and no advantage, as far as i know) for change it.

> **nicktheawesome said:**
> Is there a way to remove the splash screen so when I hit Ubuntu in grub it boots like it does in recovery mode, but then goes directly to the login screen? I'd prefer it if I could do this from within Ubuntu, instead of the Grub menu...

hi,
in the file /boot/grub/menu.lst each kernel entry has a kernel line with a quiet option, and a 'quiet' line. Those are the ones you can tune for that.
I'm not sure whats the actual behavior of each, but it used to be:
- remove quiet splash from kernel line gives an usplash but with blue lines of the main things happen on boot process (dapper style)
- remove the 'quiet' gives a recovery kind of boot, with all info of what it's happening (debian style)... don't remember exactly if it needs the quiet splash removed too or not.
Just try all combinations to see what you like more :)

---

### Post by crjackson on 2007-09-02
> **nicktheawesome said:**
> Is there a way to remove the splash screen so when I hit Ubuntu in grub it boots like it does in recovery mode, but then goes directly to the login screen? I'd prefer it if I could do this from within Ubuntu, instead of the Grub menu...

It's very easy:
```
sudo nano /boot/grub/menu.lst
```

search for every instance of "splash" and change it to "nosplash"

There should only be 2 instances.

Save the changes and reboot.  That should do it.

---

