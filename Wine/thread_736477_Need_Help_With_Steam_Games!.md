---
title: "Need Help With Steam Games!"
date: 2008-03-26
forum: Wine
---

### Post by volksgewer on 2008-03-26
](*,) I have gotten Steam to work. But every time I go to play a game it loads up fine. But, then it quits the program. Can anyone help? ](*,)

---

### Post by fela on 2008-03-27
are you running compiz/desktop effects? if so, turn them off and see if it works.

---

### Post by volksgewer on 2008-03-27
Yes, I am. I will try that. Thankyou.

---

### Post by eythian on 2008-03-28
> **volksgewer said:**
> ](*,) I have gotten Steam to work. But every time I go to play a game it loads up fine. But, then it quits the program. Can anyone help? ](*,)

If turning of compiz doesn't help, try running steam, and then from the terminal loading the game using pasuspender, e.g.:

 pasuspender ./hl2.exe -- -dxlevel 81 -window

makes HL2 work for me, where previously it'd quit after loading.

---

### Post by equity on 2008-03-28
Lol, I do not recommend you to use wine to play games on Linux.
Use cedega, it is developed to make DirectX and OpenGL games playable under Linux.
Unfortunately it is closed source and commercial software, but afaik there is no alternative available atm.

If somebody knows a cedega alternative PLEASE POST.

[http://www.cedega.com/](http://www.cedega.com/)

---

### Post by fela on 2008-03-28
> **equity said:**
> Lol, I do not recommend you to use wine to play games on Linux.
Use cedega, it is developed to make DirectX and OpenGL games playable under Linux.
Unfortunately it is closed source and commercial software, but afaik there is no alternative available atm.

If somebody knows a cedega alternative PLEASE POST.

[http://www.cedega.com/](http://www.cedega.com/)

Yes, the alternative is to not play windows games under Linux, or play them using WINE (which is perfectly good IMO)

I mean, who would damage his/her linux installation with software that you have to PAY FOR, let alone get the source code of? are you barking mad? lol

---

### Post by equity on 2008-03-29
Wine is good to emulate the Windows productive applications on Linux.
But Wine does not emulate all this Microsoft stuff like DirectX as good as Cedega does.
Compare for example emulating WarCraft III with Wine and with Cedega and you will find out that it runs better with Cedega.

---

### Post by Swarms on 2008-03-29
I have played the big Valve titels like HL2, CSS etc., which goes just as smooth on Wine than on Windows.

So please, only speak of Cedega when its relevant, like its not playable on Wine (which it is in this case) and is in Cedega.

---

### Post by Blackmag+c on 2008-03-29
wine-doors?

Theres a guy on youtube who runs linux mint. He says it works fine.

my two cents.

---

### Post by mattchew on 2008-04-03
> **equity said:**
> Lol, I do not recommend you to use wine to play games on Linux.
Use cedega, it is developed to make DirectX and OpenGL games playable under Linux.
Unfortunately it is closed source and commercial software, but afaik there is no alternative available atm.

If somebody knows a cedega alternative PLEASE POST.

[http://www.cedega.com/](http://www.cedega.com/)

Never use cedega.The "download and install version" is  worse maintained than their CVS. All you are paying for is the same thing they offer free, and faster forum replies because they're paid to do that. Please don't troll cedega in a Wine forum. Cedega != wine.

That's all. Use wine, many people do for gaming, you just gotta figure out some config.

---

### Post by equity on 2008-04-04
>  That's all. Use wine, many people do for gaming, you just gotta figure out some config. 

^^ Yes, and this is exactly the problem. Wine is particularly written to emulate applications that are not games. The biggest barrier is to find out a well working configuration, that is, in my opinion, quite complex. So the Cedega developers have tested thousands of configurations to find out the best working for every single Windows-like game, so you just have to tell Cedega what game you are playing and it automatically brings up the best working configs.

---

### Post by Brynster on 2008-04-04
instead of trying to start a my mum is better than you mum argument over which is better Wine or Cedega can we try assist  the original poster with his issue which  is that source based games are not working.

To the original poster.

Could you please post what hardware your running. please and especially which video card your using many thanks.

---

