---
title: "World of Warcraft vs Warhammer online"
date: 2007-11-02
forum: Wine
---

### Post by Nooblit on 2007-11-02
My first post :)

Hi everyone I'm new too Linux and using wine so far i did not understand all the code and etc but i got my wine and updated it. I got World Of Warcraft  to work and diablo 2 and the  d2 expansion to work and they both work flawless for me.

The odd thing is i didn't understand the instructions on here to install them but i figured out my own way .. witch to me seemed allot easier than what iv seen posted on there. All i did was put my Cd wow or d2 in for example and the window came up and i opened the window to scroll down and fined the exe file or a file that says install  and i right clicked  on the file and select open with other application and then scroll down to open with wine windows emulator and they installed auto too wine C but it didn't say wine C so just let it choose the location. just C. So for me its been a matter of putting a CD in and right click on install and open with wine emulator. But I'm learning more and more as i read and play around.

I hope when Warhammer Online comes out ill be able to play it with wine it looks awesome and I think it will Beat wow and i know that is a far stretch for some to think but Look 

[http://interviews.slashdot.org/article.pl?sid=06/11/27/1752236](http://interviews.slashdot.org/article.pl?sid=06/11/27/1752236)

and

[http://www.warhammeronline.com/english/media/video/](http://www.warhammeronline.com/english/media/video/)
check on the forums on the site too if your interested.

I am still new too Ubuntu and i have a question although i feel it is most likely a dumb question please don't be too rude lol but I'm going to ask anyway.. Can i Install Xp on Wine like right click on the Xp open with wine and let wine install Xp too C wine and then install my games on Xp under wine c using Xp in wine?

---

### Post by Nooblit on 2007-11-02
My 2nd post

Hi everyone I'm new too Linux and using wine so far i did not understand all the code and etc but i got my wine and updated it. I got World Of Warcraft to work and diablo 2 and the d2 expansion to work and they both work flawless for me.

The odd thing is i didn't understand the instructions on here to install them but i figured out my own way .. witch to me seemed allot easier than what iv seen posted on there. All i did was put my Cd wow or d2 in for example and the window came up and i opened the window to scroll down and fined the exe file or a file that says install and i right clicked on the file and select open with other application and then scroll down to open with wine windows emulator and they installed auto too wine C but it didn't say wine C so just let it choose the location. just C. So for me its been a matter of putting a CD in and right click on install and open with wine emulator. But I'm learning more and more as i read and play around.

I hope when Warhammer Online comes out ill be able to play it with wine it looks awesome and I think it will Beat wow and i know that is a far stretch for some to think but Look

[http://interviews.slashdot.org/artic.../11/27/1752236](http://interviews.slashdot.org/artic.../11/27/1752236)

and

[http://www.warhammeronline.com/english/media/video/](http://www.warhammeronline.com/english/media/video/)
check on the forums on the site too if your interested.

I am still new too Ubuntu and i have a question although i feel it is most likely a dumb question please don't be too rude lol but I'm going to ask anyway.. Can i Install Xp on Wine like right click on the Xp open with wine and let wine install Xp too C wine and then install my games on Xp under wine c using Xp in wine?

---

### Post by Nooblit on 2007-11-02
Im Wow and use Wine... Hope i can make it work for Warhammer online when it comes out

---

### Post by Nooblit on 2007-11-02
I think warhammer online is going to blow wow out of the water.

this being why

[http://interviews.slashdot.org/article.pl?sid=06/11/27/1752236](http://interviews.slashdot.org/article.pl?sid=06/11/27/1752236)

and

[http://www.warhammeronline.com/english/media/video/](http://www.warhammeronline.com/english/media/video/)

Speculate, What do you think?

---

### Post by Ardrias on 2007-11-02
I have a hard time with the part about no Mac/Linux client, and it being an EA game.

---

### Post by hikaricore on 2007-11-02
Yoiu posted in 3 places about the same thing.  Please refrain from this in the future.

--Aaron

---

### Post by jaybombalous on 2007-11-02
I doubt wine will even support warhammer when it is released. Its a new game taking advantage of new technology, wine will not have this technological up-to-date code and so warhammer will fail.

WOW/wine was a side project for many linux users, thats half the reason why some people still use windows. Unless u get that kind of pushing force behind warhammer I doubt wine will emulate it until the game is long gone and boring.

---

### Post by pelle.k on 2007-11-02
> I am still new too Ubuntu and i have a question although i feel it is most likely a dumb question please don't be too rude lol but I'm going to ask anyway.. Can i Install Xp on Wine like right click on the Xp open with wine and let wine install Xp too C wine and then install my games on Xp under wine c using Xp in wine?
No. Wine already "is" XP (or win98, win95, 2000 or NT). Wine *is* the emulating layer, pretending to be windows. You can however add some .dll files, thus adding to a more complete environment for wine to use for it's "masquerade". that would be inside **/home/yourusername/.wine/drive_c/windows/system32/**
Note that .wine is a hidden folder because of the dot (.)

---

### Post by stuart.crouch on 2007-11-02
Unfortunately not.

Wine is an application layer (**W**ine **I**s **N**ot an **E**mulator).  It has a kernel and a set of dlls that catch any requests made by programs you run using WINE, and converts them into the equivalent linux based calls.

If you install XP (not even sure that would work as installations in windows reboot the computer, something not possible in wine) it would replace the dlls wine needs with windows ones, and it would all fall over in a big heap.

Hope that helps.

NB. For those that wonder - an application layer converts requests from one format to another in order to talk to the hardware (eg linux is controlling the hardware, wine is just telling linux what to do), and an emulator pretends to be the hardware.

---

### Post by hikaricore on 2007-11-02
Merged another one of your threads OP.

---

### Post by Dark Hornet on 2007-11-02
--along this same line of thought....would you be able to copy the .dll's from a copy of windows and replace the WINE versions of the dlls?

---

### Post by hikaricore on 2007-11-02
> **Dark Hornet said:**
> --along this same line of thought....would you be able to copy the .dll's from a copy of windows and replace the WINE versions of the dlls?

You can do this, but it is only useful/sane in certain situations.

These are few and far between, and it's usually recommended that you refrain from doing so as it will not benefit you outside of said situations.

---

