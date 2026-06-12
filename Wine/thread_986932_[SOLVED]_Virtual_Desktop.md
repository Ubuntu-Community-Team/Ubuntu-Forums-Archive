---
title: "[SOLVED] Virtual Desktop"
date: 2008-11-19
forum: Wine
---

### Post by finito on 2008-11-19
I like to game with wine, but I have utorrent, I can't find anything better, its just too good. 

Now I have a question is there a way to run utorrent without virtual desktop and the games can run in virtual desktop. I did before but I don't know how. It just happened by itself (I know that's not possible, but I think i was messing with something else and I inadvertently did it).

---

### Post by karth on 2008-11-19
There are several ways to do this.

One of them is to tell wine to run in a virtual desktop in the command line (leaving NO VIRTUAL DESKTOP as default)

```
wine explorer /desktop=name_of_desktop,1024x768 MyApp.exe
```

Another way is to tell wine to default to a virtual desktop by checking the appropriate box in the video tab of winecfg
```
$ winecfg
```
[IMG]http://img185.imageshack.us/img185/7754/image2fe1.png[/IMG]

winecfg can also be setup to put on a virtual desktop for a specific application. It's the same as the above method, except that you have to create a "profile" for your app first, and highlight it.

[IMG]http://img149.imageshack.us/img149/8308/image1ze2.png[/IMG]

---

### Post by finito on 2008-11-19
O I get it, silly me. 
I even tried doing that but it didnt work for me ok now I understand

thanks

---

