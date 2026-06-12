---
title: "World Of Warcraft Help"
date: 2008-03-19
forum: Wine
---

### Post by MrShurr on 2008-03-19
Hey all,

I'm new here but I've read through some old posts and I don't think this has been covered yet.

I've got the WoW Battlechest. It comes with a WoW DVD and a Burning Crusade DVD. I'm really struggling to install the game on my ubuntu OS. I'm running Feisty, by the way. When the DVD goes in, only the mac files come up.

I guess my question is, how do I install World of Warcraft from the DVDs that come in the Battle Chest? :) Thanks!

David

P.S. I know about WINE and all of that. The only thing I need to know is how to get the game installed. I can get the rest from [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by donnyblaze1 on 2008-03-19
IIRC, you will need to mount the DVD "nohide", as installer.exe is a hidden/protected file.  See [http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab]("http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab").  man mount will probably give you some insight as well.

Good luck!

---

### Post by miller64917 on 2008-03-19
I had the same problem with a different game, ill try what you said, THANKS!

---

### Post by MrShurr on 2008-03-20
> **donnyblaze1 said:**
> IIRC, you will need to mount the DVD "nohide", as installer.exe is a hidden/protected file.  See [http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab]("http://wiki.jswindle.com/index.php/Winetools#NoHide_with_fstab").  man mount will probably give you some insight as well.

Good luck!

Thanks, dude. I'll try it out.

---

### Post by pedro_orange on 2008-03-20
If you install WINE:

```
sudo apt-get install wine
```

When you put in the DVD, you will get the splash screen you get with Windows. Then it's a case of clicking next, and sticking in the DVDs at the right time. It's not rocket science :)

Oh, but WINE holds onto the DVD during installation, so you'll need to do a

```
wine eject d:
```

everytime it asks you to enter disk n.

[Where d is the drive name according to wine (I only have 1 CD/DVD drive so it was d)]

---

### Post by MrShurr on 2008-03-20
Thank you to everybody! I've got WoW running beautifully now. It's awesome!!!

---

### Post by Dlambert on 2011-02-23
> **MrShurr said:**
> Thank you to everybody! I've got WoW running beautifully now. It's awesome!!!

How? If i may ask.

---

