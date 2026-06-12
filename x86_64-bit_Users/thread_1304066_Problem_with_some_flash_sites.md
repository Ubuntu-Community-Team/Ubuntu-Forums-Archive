---
title: "Problem with some flash sites"
date: 2009-10-28
forum: x86 64-bit Users
---

### Post by tom17 on 2009-10-28
Hi,

I am running into a problem with some flash sites. I did not consider asking in here before as I figure that it is a badly coded applet, but recently, comments in a slashdot article saying how friendly the feedback is on here have prompted me to ask anyway. What the hell.

So, i'm running Jaunty 64 bit, with Firefox 3.0 on my Dell Inspiron 640m laptop. It was an fresh install and not an upgrade. I get the same behaviour on my Desktop which is also Jaunty 64 with the same Firefox, but it was an upgrade from Intrepid. I also get the same behaviour on a 32 bit Jaunty at work so not sure if the 64 bit forum may be the wrong place for this.

The problem site is here:

[http://www.kneebouncers.com/](http://www.kneebouncers.com/) (yes, it's just a silly thing for my kid)

Go to the 'peekaboo' game. Now, normal behaviour on FF & IE on Windows (and also on Opera on Linux, I might add) is that if you hold down a key, the 'curtains open' and the character makes a noise. If you keep it down, they stay open.

The behaviour I am seeing here is as if Linux/Ubuntu/Gnome/Firefox or something is sending the a key-repeat sequence to the flash applet. As a result it judders and stutters as it receives the multiple key strokes. This makes it pretty useless.

I tried installing the Windows version of firefox & flash under Wine and got the same behaviour which makes me think the problem could be in the way the OS or window manager is passing the keystrokes through to the app. The only fix so far is Opera.

I tried the wine fix as I saw some "Farmville" users had problems in Ubuntu and running FF under wine helped. Unfortunately the Farmville problems (general slowness and jittery rendering) still exist for my wife under wine too. Interestingly, Opera fixes the peekaboo problem, but Farmville does not work properly.

Should I just forget about this problem cos it's a broken app (or try to get the developer to look into it which I don't think will be fruitful) or does anyone think there could be a problem with how the keystrokes are getting passed down through the layers in Ubuntu?

I have not tried 9.10 yet, will do so tomorrow (32 bit) for sure :)

Mods, if you think this would be better off in a non-64 bit section, then please move this thread.

Thanks,

Tom...

---

### Post by bashphoenux on 2009-10-29
its works for me perfectly when you press ctrl,alt ...the rest of the keys, Yes it acts as if it has received multiple strokes :P
probably becos  a proper flash plugin has not yet arrived :(

---

### Post by tom17 on 2009-10-29
I would have thought that if it was a linux flash issue, then I wouldn't have still seen the problem with the windows versions FF& Flash under wine...

Tom...

---

### Post by tom17 on 2009-10-29
I just tried it in a fresh install of Karmic Koala, x86.

I installed flash from the flash website

About:plugins shows:
  File name: libflashplayer.so
  Shockwave Flash 10.0 r32

It behaves the same :(

---

### Post by pietro_spina on 2009-10-29
capslock
shift
ctrl
alt
num lock
and Left Mouse click 
all work, the rest send the repeat key to the game...

you could disable the repeat key temporarily or make a user with that config to switch to when you and your kid play on the computer...

System-->Preferences-->Keyboard  (first tab....) for the repeat key setting

And on another note, not being a parent yet... do kids actually like that kind of stuff? I mean is it any different to actual peek a boo or rolling a ball on the floor? Our cats like to watch us type or read blogs (lots of scrolling) but neither was interested in Peek a boo. The leaves outside are just too interesting.

cheers,
P

---

### Post by tom17 on 2009-10-29
Interesting that the problem is only with the alphanumeric keys.

I have to say, he is enamoured by it, but it's not something I plan to use to keep him occupied. Real life is far more fun, but there are times when I am on the computer with him on my knee and it's fun to just fire up something like this every now and then as he is constantly trying to use the keyboard. This way he can "join in with Daddy" kinda thing.

But really, i'm more concerned that there may be some compatibility problem with the way linux is passing keystrokes and with flash. My wife is desperately trying to get me to revert to Windows and it's the little things like this, and Farmville not working properly for her, that hinder my efforts to stay with Linux :)

Tom...

---

### Post by pietro_spina on 2009-10-29
> **tom17 said:**
> 

But really, i'm more concerned that there may be some compatibility problem with the way linux is passing keystrokes and with flash. My wife is desperately trying to get me to revert to Windows and it's the little things like this, and Farmville not working properly for her, that hinder my efforts to stay with Linux :)

Tom...

I've noticed that sometimes when a tab has a flash video in it I can't close the tab with ctrl-w until I click on some white space on the page... It's always felt like a focus issue. I was about to tell you to just disable the repeat key setting again (because it stops the behavior we are seeing and, really, who uses it?) but I typed this response with it off and am moderately frustrated. HAHA

On the bright side it will teach him to be more accurate with his typing and that different keys do different things...(great for cognitive development)
-p

---

### Post by bobince on 2009-10-30
> The behaviour I am seeing here is as if Linux/Ubuntu/Gnome/Firefox or something is sending the a key-repeat sequence to the flash applet. As a result it judders and stutters as it receives the multiple key strokes. This makes it pretty useless.

Yes. I believe the problem to be GTK+. Firefox-on-GTK and Chromium (which is always GTK) exhibit the problem; Opera, Konqi and Firefox-on-KDE do not.

It affects JavaScript key events as well as Flash, which sucks for me as I'm writing some JS games. I have to sniff for Firefox/Chrome+Linux and change the keys to only the shifting keys (which don't repeat so don't exhibit the problem, as noted).

It isn't fixed in Karmic and I don't know when it started happening. See the bug filed at [URL="https://bugs.launchpad.net/ubuntu/+bug/369880"]https://bugs.launchpad.net/ubuntu/+bug/369880
[/URL]

---

