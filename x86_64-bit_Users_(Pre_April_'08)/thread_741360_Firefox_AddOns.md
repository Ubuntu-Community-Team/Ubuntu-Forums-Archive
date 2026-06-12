---
title: "Firefox AddOns"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by frogotronic on 2008-03-31
Is there a way to install/run Firefox addons for 32 bit in x64?

---

### Post by scragar on 2008-03-31
all firefox addons are in xpi format(just another archive like tar or zip) and contain plain text documents, nothing strange would happen or change between 32 and 64 it systems.

---

### Post by DJ_Peng on 2008-03-31
Unless I've completely missed something Firefox (and all Mozilla) addons don't know about 32 bit or 64 bit. At least I've never heard of an extension being for one system or another.

---

### Post by frogotronic on 2008-03-31
> **DJ_Peng said:**
> Unless I've completely missed something Firefox (and all Mozilla) addons don't know about 32 bit or 64 bit. At least I've never heard of an extension being for one system or another.

okay, so when I go to install on Hardy x64 I get an Error 203 and the xpi doesn't install.

  Am I missing something?

- CH

---

### Post by DJ_Peng on 2008-03-31
Could be any number of things, but I doubt it's due to a 32/64 bit argument. It could be easier to diagnose with the extension you're trying to install and the build ID of the version of Firefox you're running. The Nightly Tester Tools extension will let you paste the build ID to the forum.

---

### Post by frogotronic on 2008-03-31
its was a corrupted extensions files.  I deleted them and now its all good.

- CH

---

### Post by DJ_Peng on 2008-03-31
Coolness. I'm glad you were able to get things fixed.

---

### Post by frogotronic on 2008-04-01
The only wierdness I've encountered with x64 has been realplayer and the i32 libraries, but I this that's because Hardy is a Beta; because supposedly Gutsy Beta didn't have this problem.

I'm a little suspicious of the ne Xorg (but that's not an x64 issue).

- CH

---

### Post by DJ_Peng on 2008-04-01
Actually the realplayer issue may eb a combination Hardy Geta/Firefox Beta isue. I've been seeing a lot of people having issues with it. I'm about to the point of having to decide to try the "official" RealPlayer install just to get some videos from the BBC to play (and hopefully not crash Firefox 2 since I'm turning my back on Firefox 3 -- again) or decide I simply won't enjoy the teaser video for season 4 of Doctor Who.

Hardy Xorg is being pretty good to me, although if I load the Windows  INF file for my Envision LCD so I can use my monitor's settings rather than the Plug and Pray monitor I get the failsafe display, unlike what I had in Gutsy before I had to wipe and reinstall to deal with some then-current kernel issues.

---

### Post by frogotronic on 2008-04-01
> **DJ_Peng said:**
> Actually the realplayer issue may eb a combination Hardy Geta/Firefox Beta isue. I've been seeing a lot of people having issues with it. I'm about to the point of having to decide to try the "official" RealPlayer install just to get some videos from the BBC to play (and hopefully not crash Firefox 2 since I'm turning my back on Firefox 3 -- again) or decide I simply won't enjoy the teaser video for season 4 of Doctor Who.

Hardy Xorg is being pretty good to me, although if I load the Windows  INF file for my Envision LCD so I can use my monitor's settings rather than the Plug and Pray monitor I get the failsafe display, unlike what I had in Gutsy before I had to wipe and reinstall to deal with some then-current kernel issues.

Hmm.  Well my Realplayer issues are with the icons not being found (GDK) issue because the IA32 libraries aren't linked properly.  (that's what googling around the web gave me)  This *should* be fixed for the final release, but it is a tad annoying.

I have to test drive the new HARDY XORG against projectors and for presentations, as I use my laptop for several presentations/Impress shows per week.

- CH

---

### Post by DJ_Peng on 2008-04-01
Ah, ok. Test that baby until it cries for it's momma. You need Xorg for a hell of a lot more than I do, but I just have my little homebuilt desktop. :)

---

