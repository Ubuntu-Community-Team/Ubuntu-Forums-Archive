---
title: "sound blaster live USB audio problem"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by Onythias on 2008-08-09
I've been trying to transition to Ubuntu in a more complete capacity for about two years, but every time I try, there's something that I just can't seem to fix.  This time (and about the last 3) it's been my sound card.  For the life of me, I can't get it to make noise, except when I'm testing it in the sound preferences.  

When I hit the test button (after selecting USB audio, since nothing else makes noise) it gives off the test beep.  But when I got to listen to any audio anywhere else, it does nothing.  I've looked around, and the only place that I've found that has anything resembling useful information is this site. [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

The problem with that is that when they describe how to install anything, I have no idea what it's talking about.  Everything is way more technical than I understand.  I am still quite a fledgling with linux in general.  Does anyone else have a card like mine, that they know how to get working (and can walk me through it in the simplest way possible)?  If you need any more information, I would be happy to give it, since I really like how far ubuntu has come in usability, but if I can't get audio working it'll all be useless.

---

### Post by jocko on 2008-08-09
It may be that you only have to tell your computer which soundcard to use.

Type this in a terminal:
```
asoundconf list
```That should give you the name of the card (or a list of cards if you have more than one) as asoundconf sees it.
Now type:
```
asoundconf set-default-card [COLOR=Blue]name_of_your_card[/COLOR]
```where you should replace [COLOR=Blue]name_of_your_card[/COLOR] with the output from the first command.
What this does is that it generates a default sound configuration and sets alsa to use the correct sound card. 
Log out and log in again, and if you are lucky you will have sound..

---

