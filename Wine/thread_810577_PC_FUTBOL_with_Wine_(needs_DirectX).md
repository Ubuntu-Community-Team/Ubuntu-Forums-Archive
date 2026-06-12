---
title: "PC FUTBOL with Wine (needs DirectX)"
date: 2008-05-28
forum: Wine
---

### Post by LitusMayol on 2008-05-28
Hi everyone!

I've a **Wine** doubt, maybe someone knows how to solve it!

Here it goes:

I wanna install a game called **PC Futbol 2000** by *Dinamic Multimedia*. I've **Wine** installed. Till here everything's fine. 

By the way, when I install the game (running "*wine setup.exe*" at the directory) it is installed perfectly. The problem comes when I try to run the game. It turns the screen black and nothing happens. I thinks it is because it needs **DirectX**, but not sure about it... This is the error the terminal gives me if I run "*wine pcf2000.exe*":

```
litus@mayolets-desktop:~$ cd /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ wine pcf2000.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f22dac0,0x00000000), stub!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$
```

I don't know what to do... 

These are the technical requirement of the game:
[LIST]
[*]graphics DirectX 7
[*]sound DirectX 7
[/LIST]

Of course, keyboard, mouse... But these ones are the only ones that I don't fulfil.


Thanks everyone!

---

### Post by soccermonster5 on 2008-05-30
I found this, it looks like it is what you need. I hope it helps!

[http://wiki.winehq.org/PreloaderPageZeroProblem]("http://wiki.winehq.org/PreloaderPageZeroProblem")

---

### Post by LitusMayol on 2008-05-30
> **soccermonster5 said:**
> I found this, it looks like it is what you need. I hope it helps!

[http://wiki.winehq.org/PreloaderPageZeroProblem]("http://wiki.winehq.org/PreloaderPageZeroProblem")

Thanks **soccermonster5**! ;) 


It have changed a little bit my situation. Right now what happens is this:
```

litus@mayolets-desktop:~$ wine /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/pcf2000.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33dac0,0x00000000), stub!
```

Does anyone know how to solve it? 


Thanks! ;)

---

### Post by ajackson on 2008-05-30
> **LitusMayol said:**
> Thanks **soccermonster5**! ;) 


It have changed a little bit my situation. Right now what happens is this:
```

litus@mayolets-desktop:~$ wine /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/pcf2000.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33dac0,0x00000000), stub!
```

Does anyone know how to solve it?
Solve what? a fixme isn't an error.

It might be best if you run pcf2000.exe from the directory it is installed in (i.e. cd to that directory first).

If you are still having problems, saying what happens would help because the terminal output shows no real problems.

---

### Post by LitusMayol on 2008-05-30
> **ajackson said:**
> Solve what? a fixme isn't an error.

It might be best if you run pcf2000.exe from the directory it is installed in (i.e. cd to that directory first).

If you are still having problems, saying what happens would help because the terminal output shows no real problems.

What is a fixme? (I don't know, thought it was an error...) Can I change it?


Running this:

```
litus@mayolets-desktop:~$ cd /home/litus/.wine/drive_c/Program\ Files/DINAMIC\ MULTIMEDIA/PC\ FÚTBOL\ 2000/
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ wine pcf2000.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33dac0,0x00000000), stub!
litus@mayolets-desktop:~/.wine/drive_c/Program Files/DINAMIC MULTIMEDIA/PC FÚTBOL 2000$ 

```

The wine-desktop turns black, and an error windows appear called "***manager***". Inside it there's a message in spanish that says "*The program can't be started*" and only one option "*Accept*". If I click on it, nothing happens, the wine-desktop remains black till I close it. So... that's what happens. Any idea?


Thanks **ajackson**! ;)

---

