---
title: "Google Picassa for 64bit Unbuntu"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by pschuyler on 2006-09-14
Has anyone gotten Picassa Google image viewer/organizer to work on the 64bit ubuntu?

](*,)

---

### Post by kuja on 2006-09-17
I just tried it and it seems to work flawlessly. Download their linux deb. Install it with this:

```
sudo dpkg --install --force-architecture picasa_2.2.2820-5_i386.deb
``` The version may of course change.

One thing that won't change though is the uglyness (IMO) of the interface. I think that picasa may require that you have wine installed. If you don't have wine installed, check the sticky in this subforum for information on how to install it.

---

### Post by fakie_flip on 2007-06-26
sudo apt-get install ia32-libs*

---

### Post by derrekito on 2007-06-26
Unfotunatly picasa is a bit limited right now for Linux.  there is no online album support, etc.  WHich is the only reason why I use it. :p

---

### Post by Mr. Swiveller on 2007-07-02
Hmmm... This is quite interesting. I had to copy the Picasa folder to my regular .Wine folder (version 0.9.40) in order to get the programme to function normally. Before, it would crash as soon as I tried to import pictures which were on external hard drives. But perhaps I simply have an older version...

Swiveller

---

### Post by derrekito on 2007-07-02
> **Mr. Swiveller said:**
> Hmmm... This is quite interesting. I had to copy the Picasa folder to my regular .Wine folder (version 0.9.40) in order to get the programme to function normally. Before, it would crash as soon as I tried to import pictures which were on external hard drives. But perhaps I simply have an older version...

Swiveller

Google encapsulated Picasa in their own version of wine.  It is possible that if you move it to the wine folder it may become unstable?  regardless there is NO need to put it in the wine folder.  Also if you are having installation issues, try using automatix2 to auto install, worked fine for me.

---

### Post by Mr. Swiveller on 2007-07-02
> **derrekito said:**
> Google encapsulated Picasa in their own version of wine.  It is possible that if you move it to the wine folder it may become unstable?  regardless there is NO need to put it in the wine folder.  Also if you are having installation issues, try using automatix2 to auto install, worked fine for me.

Well, this may be true for most people - but in my case moving Picasa from its own Wine folder (labelled '.Picasa') to the folder created by 'regular Wine' made the programme more useable. 

Needless to say, I had to create a new link in the K menu, since the old one pointed to the .Picasa folder.

Cheers,

Swiveller

---

### Post by fakie_flip on 2007-07-02
pkill -9 exe

then I started it up again and its fine

---

