---
title: "Issue with Steam Chat"
date: 2007-12-05
forum: Wine
---

### Post by IOA on 2007-12-05
Well, I'm running the Steam fine in Linux and all, I can play games and all that jazz, it's just that when I go to talk to someone (NOT INGAME, not using the overlay) it doesn't show my nor my friend's messages in the chat. I installed fonts, the Mozilla Gecko thing, all my fonts and Mozilla controls are installed correctly. I've had this issue ever since I was able to emulate Steam on Linux, and it's been a real gear-grinder for me, so I decided to post here, I guess.


Thanks in Advance.


-IOA

---

### Post by Rafadagaffer on 2007-12-05
I have this problem too, never could find a solution for it unfortunatley

---

### Post by IOA on 2007-12-05
Ah, sorry, I JUST found a solution after about 15 pages of google.

You need to disable your notification options in the Steam Friends by going to view -> Friends -> then Disable all notifications and sounds.

Phew, it worked ^_^

---

### Post by Ralphie on 2007-12-19
what version of wine are you using?
i have tried this with no success. 

is there some trick to it other than simply disabling the notifications?

thanks for any tips!

---

### Post by jupiter12 on 2007-12-29
I have the same problem... i tried what you did but it didnt help... can anyone pllz help me to?:confused:

---

### Post by TheOneGuy on 2008-01-02
> **jupiter12 said:**
> I have the same problem... i tried what you did but it didnt help... can anyone pllz help me to?:confused:
I'm also havin' the same problem. It's mildly annoying, eh wot.

I tried disabling all the notifications, but it still doesn't work. I can send messages so that they show up in my friends' chat windows, but they don't show up in mine (and obviously their messages don't show up in my window either). It kinda kills Steam for me, as 90% of my Steam gaming is multiplayer.

Anyway, bump, I guess!

EDIT: For the record, I just put a fresh install of Ubuntu on my laptop today. Updated the video card drivers using Envy (it's an nVidia GeForce Go 7600), and then installed Wine and Steam.

---

### Post by blackboxwlan on 2008-01-11
no need to start a new thread on this issue so i thought i would bump this one.

i have the same problem also using wine-0.9.46 (ubuntu7.10) i have attempted using different fixes and nothing has worked so far

but i have noticed if you keep the friends users list open and just start resizing it continually (keep making the window smaller and larger) it can force any steam chat windows to finally update and then you will see any messages sent or received.

its very odd but works to get it to update.

its very annoying and makes steam friends a bit useless.

---

### Post by SoberWarlock on 2008-01-11
> **Ralphie said:**
> what version of wine are you using?
i have tried this with no success. 

is there some trick to it other than simply disabling the notifications?

thanks for any tips!

Oh that sucks, because I chat with my friends through steam a lot. Does Sound really need to be disabled?

---

### Post by Z4ndX on 2008-01-26
I have the same problem .. !

---

### Post by Ralphie on 2008-01-26
Well I have found, though other peoples suggestions that the only way to send and receive messages through steam is to periodically adjust the size of the friends box. this refreshes everything, and new messages will show up.

it works. but sadly, you have to adjust the size at random to see if someone decided to message you.

---

### Post by Krypttt on 2008-03-16
Has this been fixed?

---

### Post by fatbuttlarry on 2008-03-19
Unfortunately no. :(

If someone can suggest how to reverse engineer, I'd be happy w/ an opensource alternative. :beer:

-Tres

---

### Post by historisis on 2008-03-20
:lolflag: You just have to reset the system os on Wine.

The problem isn't sending messages its getting them. Me and my friend tested it out and he can see the messages from me but i can't see the messages from him. He is using windows xp and i am using a wine program on linux set to the os emulation of windows 2000.

I am using Ubuntu debain (or something like that) and it workes for me. :)

First, start a terminal 
type winecfg
go to the applications tab (if not already there)
at the bottem click _Add Application..._(it will open a file open box)
Dubble click Program files
then steam
and open steam.exe
it will show up in the list
select steam
at the bottem there will be a box that shows the windows version
click the arrow and scroll to Windows xp.
now restart steam.

it will take a little longer than just normal messaging on the real system but you won't be burdened with the chat message box after you resize the friends list the first time. Plus don't close it cause it will make the delay between messages last longer. And you must move your mouse insted of the friends list (Ex: Playing a game) 1/2 the time it won't work unless it shows activity for some reason.

Now lets all :guitar:

---

### Post by skreech on 2008-03-24
did what historisis posted and switched the WINE operating system for Steam.exe to Windows XP and chat works as expected now.

It takes a long time for the window to come up but it seems to perform alright.

It's currently using about 90 megs of memory (but it works!)

---

### Post by ELD on 2008-04-22
I have tried the method that "historisis" posted with no luck :'(

Resizing the windows do nothing, i could see my status changes for a minute, now i can't again.

Nothing seems to get it to fricken work :(

---

### Post by Sl4sh3r on 2008-05-24
I did what historisis said but instead of selecting Windows XP I just kept it on "Use Global Settings". That seems to work fine, and it doesn't seem to lag much.

---

### Post by ELD on 2008-05-25
I am hoping with the RC's that it will be fixed, it is a pretty big thing for most steam users!

---

### Post by Sleaka J on 2008-05-25
> **ELD said:**
> I am hoping with the RC's that it will be fixed, it is a pretty big thing for most steam users!

Agreed, but even with 1.0 RC2, the problem still exists. In another 2 weeks 1.0 final will be out and hopefully it will be fixed (They had it on the schedule for a 1.0.0 release).

---

### Post by HaXiT on 2008-06-17
Something you can try:
Try calling someone, then ending the voice call and see if you can talk with them with the chat.

---

### Post by rbolio on 2008-06-27
wait how about getting the in-game thing to work? anyway to do that?

---

### Post by ELD on 2008-06-30
Has anyone tested with the new 1.1.0 release?

---

### Post by Lathilde on 2008-09-20
It certainly does work in 1.1.0, although if someone sends more than 1 message, it might lag a little, that is, by sending all messages at once after several seconds of actually being posted. But perhaps this is just my issue. 

As long as the tahoma.tff font (find this on Google) is in ~.wine/drive_c/Program Files/windows/fonts , and you keep the Steam Client main window OPEN at all times, it will work without that unnecessary need to resize the Steam window that others have mentioned. And it will work well.

---

### Post by Lathilde on 2008-09-20
Hmm, it seems as if Steam will 'reveal' these logged messages by typing something into the text box. You don't have to send the message. If you do not type anything in, then nothing will be revealed. How strange.

---

### Post by Hobo Joe on 2008-09-28
I've had a degree of success with the resizing thing, but it's really a hassle, and makes it not very worth it.

Hopefully a fix will be found someday... :(

---

### Post by Deadmode on 2009-10-14
I know this may be a strange way to do it, but just run a windows virtual machine on your linux box.  I have a virtual windows running just for programs that I absolutely need windows for.

---

