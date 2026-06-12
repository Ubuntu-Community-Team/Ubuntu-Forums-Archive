---
title: "The Fn keys on my laptop don't work in OS 11. Is it possible a KDE update will fix?"
date: 2008-07-15
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Redrazor39 on 2008-07-15
KDE just got 4.1RC1 and I was thinking of hopping on back to OS11 from ubuntu if my Fn Keys work. Also, Suspend doesn't work. That just stinks.

Is it possible that a KDE update could fix these things? The Fn keys work fine in ubuntu and suspend never worked in either :(

---

### Post by Growbag on 2008-07-16
NO, no, and no!

Here's the reply from the dev responsible:

"hotkey-setup is no longer supported by opensuse, why can't you understand that?".

Sick eh?

Apparently you are supposed to know how to use HAL or something to get your keys working!

I too was extremely angry about my laptop keys not working, and after many days of trying I simply switched back to KDE3, they work perfectly now!

KDE4 is a big pile of dog droppings, it is PRE BETA and NOT ready for general release at the moment.  If you read all the stuff flying between users and devs, you get the impression that it was pushed out and hyped up in order to generate interest and get the devs working!

All very nice in the scheme of "advancing software", but bad for the everyday user and the reputation of Linux in general.

SUSE seems to have adopted the attitude: "we need to change to make things better, so who cares if it doesn't work right now, eventually it will".

Again, great for the long term, but damaging in the short term, which means that everyday users will simply jump ship! 

Although when I last tried KDE 4.1 beta2, they actually got kmix to remember the keys I assigned it, a big leap forward.

I use a tool called DCOP under KDE3, it is quite cool, you can assign keys to functions in apps, but I still have a few (laptop) keys that aren't recognised.

As for suspend, I actually had it working once under 10.3, or was that just a dream?

But it took so long that it was completely pointless, it was faster to simply shutdown/restart each time, so I never use it.

The problem with "suspend to disk" is that the more memory you have in your system, the longer it takes, as it has to write it all out to disk.  Oh, and I believe that your swap partition MUST be greater than your memory size for suspend to work as well.  Although I'm not 100% sure, and am usually wrong!

When I was playing with DCOP trying to assign some of my more obscure laptop keys, it kept going into "suspend" mode, which is a pseudonym for "Screw Up Something Purposely End 'n' Die" mode!

My advice, just forget about "suspend" and all that stuff, it never worked, and never will!

Good luck :).

---

### Post by Barrucadu on 2008-07-16
I just use xbindkeys to get my media keys working.

---

### Post by Redrazor39 on 2008-07-16
Is that in the repos?

---

### Post by anshuljain on 2008-07-16
The hotkey-setup is in the Packman repos...and it works just fine on my Thinkpad R61 (KDE3 install-Opensuse 11.0). The only key that dosen't work is the brightness control through Kmilo. Suspend to Ram/Disk have always worked great with Suse...what one needs to get Suspend to Ram/Disk working is to tweak the fdi files in /usr/share/hal/information/10freedesktop. More details at :- [http://people.freedesktop.org/~hughsient/quirk/](http://people.freedesktop.org/~hughsient/quirk/).

In my experience, the procedure works great on GNOME (I've tried it on Mandriva and Suse), but for some reason dosen't work all that well with KDE. I would suggest that you try the KDE3 variant of 11.0 and see how it works for you. KDE4 is still major work in progress...

-Anshul

---

### Post by Redrazor39 on 2008-07-16
I keep hearing so many bad things about KDE4, but I really like it. What's so bad about it?

---

