---
title: "TvAnts"
date: 2008-05-03
forum: Wine
---

### Post by mcgooie on 2008-05-03
Hey, i have read on a few sites that it is possible to get tvants working with WINE. I have both installed but when i select a channel to view, i get the message:

```

Failed to open channel http://localhost:16900/4.asf
Do you agree to open it by windows default player?
If the external player encounters error, please try again later
```

I have read that i should be able to get it working using mplayer and the terminal, but i cant get that to work. 

Is it possible to use VLC - Open network stream and type in an address to view the channel? If so, what should i type in?

Thanks

---

### Post by hkduddu on 2008-05-15
> **mcgooie said:**
> Hey, i have read on a few sites that it is possible to get tvants working with WINE. I have both installed but when i select a channel to view, i get the message:

```

Failed to open channel http://localhost:16900/4.asf
Do you agree to open it by windows default player?
If the external player encounters error, please try again later
```

I have read that i should be able to get it working using mplayer and the terminal, but i cant get that to work. 

Is it possible to use VLC - Open network stream and type in an address to view the channel? If so, what should i type in?

Thanks
In Terminal;

$vlc mms://localhost:16900/1

I got mine working using the above command.

Read more here:- [http://linuxclues.blogspot.com/2007/09/tvants-on-ubuntu.html](http://linuxclues.blogspot.com/2007/09/tvants-on-ubuntu.html)

---

### Post by orduek on 2008-06-13
for some reason i get an error message saying unable to open localhost...
any ideas of why?

---

### Post by jjgomera on 2008-06-20
the error have the answer:

[http://localhost:16900/4.asf](http://localhost:16900/4.asf)

so you can use the player you prefer:

mplayer [http://localhost:16900/4.asf](http://localhost:16900/4.asf)
vlc [http://localhost:16900/4.asf](http://localhost:16900/4.asf)

---

### Post by stevenyu on 2008-09-23
Hi guys

Did any of you manage to get the Chinese and Japanese font to display properly under WINE?

And is there a way of automatic lunching linux based player to view the mms streaming?

---

