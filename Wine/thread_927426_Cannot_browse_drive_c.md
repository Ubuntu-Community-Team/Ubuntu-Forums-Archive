---
title: "Cannot browse drive_c"
date: 2008-09-23
forum: Wine
---

### Post by cf1709 on 2008-09-23
When I try to "Browse C: Drive", (Applications>Wine>Browse C: Drive) an error message tells me that

"Failed to open URL "~/.wine/drive_c".

The URL "~/.wine/drive_c" is not supported."

But I can access that drive_c via the terminal.

---

### Post by Qrikko on 2008-09-23
hmm.. strange.. do you have it "up to date"? I have 

wine --version
wine-1.1.5


also the command that is run from when I do what you say is this:
xdg-open ~/.wine/drive_c

this work for me, not sure what really could be wrong but maybe it give you a frame of reference if nothing else :) hope you find a solution.

---

### Post by cf1709 on 2008-09-23
Tried to update but updating doesn't help it. :(

---

### Post by Qrikko on 2008-09-24
ah, sorry to be slow.. but by the way.. did you try to run it in nautilus.. then maybe you could set your path to it.. if it is only to get it to work..

nautilus ~/.wine/drive_c

that is.. 

and what happen if you run the command in terminal? do you get the same error message.. I am thinking that maybe it will work if you run the nautilus command.. but it's just a hunch :)

---

### Post by david_kt on 2008-09-24
> **cf1709 said:**
> Tried to update but updating doesn't help it. :(

This error related to xdg-utils or default browser, not wine. Please try:

```
sudo dpkg-reconfigure -phigh xdg-utils nautilus
```

might help you to solve your problem.

That is assuming your default browser is nautilus. If it is something else, please change nautilus to your default browser.

DK

---

### Post by cf1709 on 2008-09-26
I think I'm using "Thunar" as the file browser, the one that comes with Xubuntu. I'll try to do it with Nautilus but:

*How do I install Nautilus/unintall Thunar?
*Any side effects by doing that?

I'll try browsing it with Nautilus.

---

### Post by david_kt on 2008-09-26
> **cf1709 said:**
> I think I'm using "Thunar" as the file browser, the one that comes with Xubuntu. I'll try to do it with Nautilus but:

*How do I install Nautilus/unintall Thunar?
*Any side effects by doing that?

I'll try browsing it with Nautilus.

No, do not install nautilus. Just stick to thunar then. Try:

```
sudo dpkg-reconfigure -phigh xdg-utils thunar
```

DK

---

### Post by cf1709 on 2008-09-26
Wait... I can access the drive_c via Terminal by...

thunar ~/.wine/drive_c

Thanks a lot guys.

---

