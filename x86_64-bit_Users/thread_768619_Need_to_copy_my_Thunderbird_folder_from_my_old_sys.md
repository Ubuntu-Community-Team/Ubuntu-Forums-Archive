---
title: "Need to copy my Thunderbird folder from my old system, will it work"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by philinux on 2008-04-26
Old system being 32bit. Can I just lift the .mozilla-thunderbird folder and copy it to my 64 bit system?

---

### Post by hariprs on 2008-04-26
You may face issues with some plugins. other than that everything should work fine. I did copying like this several times, it worked for me without any issues.

---

### Post by philinux on 2008-04-26
Ok cheers, the only thing I had setup is webmail/hotmail addons.

---

### Post by thekat on 2008-04-26
I have done this several times and from Windows and Linux.

- Make a back up copy of your working thunderbird directory
- Make a back up or delete the contents of the mozilla-thunderbird directory
- copy xxx.default and profiles.ini to the new location

(Note) I don't use plugins so the previous poster was probably correct :)

I do the same thing for firefox (on 32 bit Gutsy).. (did get a complaint about a plugin)

It worked fine for me in both cases.. on my 64-bit Hardy box now..

tk

---

### Post by philinux on 2008-04-26
Thanks guys, I'd mark this solved if the feature was working. :)

---

### Post by GeekGirl1 on 2008-04-26
I'm sharing my Thunderbird and Firefox profiles with my Win XP partition (dual-boot). You may need to configure Thunderbird for the new folder location:

From a terminal:

thunderbird -ProfileManager
firefox -ProfileManager

Create a new profile and just point the folder location to the new area. Works fine.

---

### Post by philinux on 2008-04-26
Ah sorry should have explained. Old profiles are on old pc pentium 3.

Destination of this pc unknown at this point.
New box only has ubuntu on it.

---

