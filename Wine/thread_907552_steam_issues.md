---
title: "steam issues"
date: 2008-09-01
forum: Wine
---

### Post by mckinnley on 2008-09-01
so i installed wine, everything seems to be working. so i install steam and it works fine too.
but when i try to load a game the screen just gets all screwed up. it doesn't work right at all and i have no idea why. i've gone to so many sites trying to find people with the same problem but i haven't found anybody.
i've attached a picture of what it looks like when i try to load up the game. i'm not sure if this is in the wrong section or not but i need help with this. thanks in advance for any help.

oh yeah, it does the same when i run portal and counterstrike aswell.

---

### Post by aoanla on 2008-09-01
That is rather weird.

We're going to need actual information, though.

What version of Wine? What graphics card, what drivers for graphics card? (Do you know you have 3d acceleration? - what is the result of 
glxinfo | grep -i render
typed in a terminal?)

If you run Steam in wine in a terminal, what does the output look like?

---

### Post by mckinnley on 2008-09-01
the output from that is

direct rendering: Yes
OpenGL renderer string: ATI Radeon X1200 Series


i'm pretty sure i have the restricted driver thing going right now. i'm going to get the actual linux driver for it right now but i'm not sure if it'll make a difference.
and i don't know how to run it through the terminal so i think you'll have to explain that one a little bit. i'm completely new to linux so i don't really know much about this stuff.
thanks.

looks like this is the only driver for it so it should work fine. i also tried to install adobe photoshop cs4 but it wouldn't let me. it would open the wine window but close almost instantaneously, so there's really nothing i can do with that. i haven't tried anything else in wine but i don't think it's very good that it won't work with two of the programs that i have.

---

### Post by aoanla on 2008-09-02
Actually, Wine *does* work with Steam - and, indeed, I regularly play Team Fortress 2 (and have played through Portal) in Wine.
If you'd checked the Wine AppDB - which *is* linked to near the top of these forums, as I recall, you'd have noticed that there's no entry for Photoshop CS4, and CS3 is listed as not working. Always check!

To launch Steam in Wine from a terminal:

cd .wine/drive_c/Program\ Files/Steam
wine Steam.exe

Please tell us any output from it - especially things starting with err:

Additionally, I have no idea how old the repository drivers for ATI cards are, but I suspect they're a bit old. You can use Envy to upgrade to newer drivers - but I know that some of the new releases have issues with Wine (ATI's fault, not Wine's).

Sam

---

### Post by mckinnley on 2008-09-02
thanks i didn't know about that, that explains a bit. but i'm still having a problem. i ran envy but it said that something was wrong and in order to fix it i needed to run this command

sudo synaptic

which i do, and then it opens another error window that says that i have to manually install something that says i need to run this command

dpkg --configure -a

so i do that. and what do you know? yet another issue. it says that i need superuser privileges to run that command and i have no idea what it means. so yeah... i need to know how to become a super-user so that i can start opening files and i guess, saving the world or something.

---

### Post by JPtux on 2008-09-03
> **mckinnley said:**
> thanks i didn't know about that, that explains a bit. but i'm still having a problem. i ran envy but it said that something was wrong and in order to fix it i needed to run this command

sudo synaptic

which i do, and then it opens another error window that says that i have to manually install something that says i need to run this command

dpkg --configure -a

so i do that. and what do you know? yet another issue. it says that i need superuser privileges to run that command and i have no idea what it means. so yeah... i need to know how to become a super-user so that i can start opening files and i guess, saving the world or something.
```
sudo dpkg --configure -a
```

---

