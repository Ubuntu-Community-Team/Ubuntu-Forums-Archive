---
title: "system totally buggered up - freezes, slow, high loads, etc"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by bluepowder7 on 2008-06-20
something is madly wrong with my current OS (7.10-64 with the 2.6.22-14 and 2.6.22-15 kernels, in both generic and rt versions)

**_symptoms:_**

1- opera 9.50 (full release, build 2042) constantly freezes on pages, window goes shaded gray - takes 10-15 seconds to free up, and after some time freezes again - repeat!

2 - system monitor shows idle load of at least 0.25, sometimes 0.50.  at idle.  doing nothing.  as an added bonus, i mistakely opened up a video file about 40 times (held down "Enter" key in nautilus, instead of "Shift" key).  understandably, load skyrocketed to over 70, but after i quickly closed all those VLC windows (took me less than 30 seconds), the load stayed WELL above 5 for the next 5-10 minutes.  should it not have recovered MUCH quicker?

3 - over the past 2-3 days, doing vobcopy has been REALLY slow, at least 5 times (and probably 10-20 times) slower than just 4-5 days ago.  unbelievably slow, on original or other material, on either the internal or USB-connected dvd drives.

4 - tops of window borders that show the _ and square and X and the name of the window are now half-size, meaning using smaller font than normally and just not right.  sometimes after a reboot, they use normal font size.  other times, tiny font size.

5 - occasionally, apps don't launch at all.  last case was system monitor - it would not launch yesterday so i couldn't figure out what my loads were and what processes were hogging the resources and kill them.

6 - last night, as i was doing some encoding, my network interface went bonkers so my desktop that was doing the encoding was no longer able to read the VOB file that is stored on my file server, and wasn't able to write the encoded MP4 file to the file server.  trying to ping the file server told me that my NIC wasn't doing anything useful.


is there any sort of "diagnostic" i can do that'll tell me "hey, you've got excess packages" or "some packages are busted" or "you have 7948 processes running in the background" or "there's 542 unused packages that need to be cleaned up" or anything like that?

ubuntu ain't what it used to be just a few days ago.  it's (GASP!) about as durable and steady as windows on a bad day with a virus.

---

### Post by ScaredNoob on 2008-06-20
Install Hardy 8.04 and you'll love new features to speed things up like graphically checking/unchecking which services startup when you boot.  If Ubuntu Hardy still seems sluggish, try Xubuntu Hardy, and if Xubuntu Hardy is slow for ya, maybe Xubuntu Dapper might be a better fit, as it has way lower spec's in mind and is still supported for awhile longer.  Sometimes a fresh install is just what the doctor ordered.

---

### Post by pixel :-) on 2008-06-20
**idle load of at least 0.25, sometimes 0.50**
In system monitor chek wich aplication eats up CPU, thers a zomby prosses that gets relanched at reboot.Try top in a terminal.

tell us it's name.

Are you sure you didn't do something special with your computer.

---

### Post by bluepowder7 on 2008-06-20
i'm hoping not to have to reinstall the OS (or even install a newer OS like 8.04) since this one was running just fine a week ago.

hmm, what did i do?  i installed ubuntustudio-... packages (audio, video, graphics), but that was 2-3 weeks ago and stuff was still working nicely after that.  i did have to un-/re-install some mplayer and mencoder apps since i was doing quite a bit of h264 encoding, which was more recent but stuff still worked fine after.

i DO recall having to pop into the terminal and do one of those "-autoremove" or something like that commands fairly recently since during some install it told me "hey, these packages are no longer used, type that command to clean it up".  i then had to reinstall certain things that actually WERE needed.

i removed firefox altogether around a week or two ago since i'm now using JUST opera, but opera wasn't going through those freeze cycles until recently.  now that i think about it, around half of the time it goes into freeze-unfreeze is when it's loading a forum page where someone embedded a youtube clip.  the other half of the time it freezes regardless of page content. ([color=red]edit: case in point - just after i posted this reply, it froze for a while.  and then killed / closed opera altogether[/color])

right now, my PC is still busy encoding the VOB's into h264 mp4's (script running through 8 flicks since late last night - looks to be about half way done after 11 hours).  i'll grab another "top" screen capture when i'm doing the vobcopy task which as i've said is for some reason 5-20 times slower than it was less than a week ago.

here's the "top" result while the PC is busy doing the h264 encode (from vob files stored on hard drive):

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/top-h264-encoding.jpg[/IMG]

---

### Post by pixel :-) on 2008-06-20
When you get thies slow down't quick have a look at top to see if you can spott it.Keep a terminal ready for this

open system monitor,and tell it to **show all prosses**.Once i had a wild gksudo that was eating up 50% of cpu,and it wasn't showing up in my own processes.It could be a prosses with root privileges.

Like you said it could be tens of small prosses.

what's that thing mencoder.It has 180% of CPU (dual core?) it's what encoding?You can copy paste from top,no need for a screenshot.When you finished encoding close a maximum of aplications and see if a prosses eats up cpu.

You have a wild prosses,that gets reactivated at each reboot,or one of the programms you usually use have a bug and stays as a zombie

Also be carefull,some prosses are stuborn,they recreat them selves if a single one remains,you have to kill them all
"killall -9 prossesname"

Try creation a new user and see if the new user has that problem.

Good luck Greg.

---

