---
title: "Firefox Crash and Open Terminal"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by icarusfall on 2005-10-13
Congrats to everyone involved in the latest Ubuntu release. I have two really simple questions that I hope people can help me with. I have the AMD64 version of Ubuntu, by the way.

Firefox: Firefox often shuts down without prompting. The only time I can get it to repeatedly do this is when I log in to [www.lovefilm.com](www.lovefilm.com). Presumably other people don't have this as I haven't seen a post about it, but can anyone tell me which log files I should be looking in to try to diagnose what's causing Firefox to crash?

Also, I used to open a terminal by minimising all windows, then right clicking on the desktop and clicking "open terminal", I don't have that option on 5.10. How do I get the option back?

---

### Post by Wille on 2005-10-13
[QUOTE=icarusfall]
Firefox: Firefox often shuts down without prompting. The only time I can get it to repeatedly do this is when I log in to [www.lovefilm.com](www.lovefilm.com). Presumably other people don't have this as I haven't seen a post about it[/quote]
Nope, firefox keeps crashing on my amd64 all the time as well.

---

### Post by Ptero-4 on 2005-10-13
check that site from other computer or browser and post the sites source code. Maybe someone here can see if it have any strange tag put there to crash or otherwise screw non-M$ browsers.

---

### Post by icarusfall on 2005-10-13
Well it works on my Windows version of Firefox, either way, they've taken the site down for maintenance, so I can't view the page source, so I'll have to post tomorrow. Can anyone else find any examples of pages that make firefox crash?

---

### Post by Alex1 on 2005-10-14
it happen also to me, i don't have an amd64 so i think it is a bug into the last firefox ubuntu package (the old one was ok).

---

### Post by wmcbrine on 2005-10-17
[QUOTE=icarusfall]Also, I used to open a terminal by minimising all windows, then right clicking on the desktop and clicking "open terminal", I don't have that option on 5.10. How do I get the option back?[/QUOTE]I can't answer that, but it sounds a bit cumbersome to have to minimize all windows first. What I did was to add a Terminal icon to the bar, right next to Firefox.

---

### Post by Pablo_Escobar on 2005-10-17
Terminal right click thingy can be back by installing "nautilus-terminal" (something like that) package. I'm not on my ubuntu box so I can't tell. Then logout or reboot and You have right click terminal :)

---

### Post by byronsalty on 2005-10-17
Pablo, thanks for the lead. 

The package is called "nautilus-open-terminal". I also had to restart gdm (sudo /etc/init.d/gdm restart) to get it to show up. 

At least I did that before I noticed that the "open terminal" addition to the right click menu is now in the middle instead of at the top.

---

### Post by clarke.rainey on 2005-10-23
Well I am using Ubuntu 32 and it also crashes in firefox and epiphany... examples of sites are torrentspy.com, vwvortex.com... I hope I can fix this... I don't want to have to go back to windows...

---

### Post by RAOF on 2005-10-23
My firefox works fine browsing torrentspy.com, and I'm using the standard, amd64 firefox package.  Chances are, with these sort of problems, is that it's actually a plugin that's killing firefox.  Try running firefox from a terminal, and see if it gives error messages before dying.

I've had these sort of problems with the gplflash plugin - some sites with flash it would kill firefox without warning, some sites it just wouldn't work, and for a very few sites it would actually work :)

---

### Post by Wille on 2005-10-23
[QUOTE=RAOF]My firefox works fine browsing torrentspy.com, and I'm using the standard, amd64 firefox package.  Chances are, with these sort of problems, is that it's actually a plugin that's killing firefox.  Try running firefox from a terminal, and see if it gives error messages before dying.[/QUOTE]
I did just that - went to torrentspy.com, found a search box somewhere, typed something ("history" I think, it probably won't matter) pressed enter, firefox died and here's what I got in the console:

(tons of Write/WriteReady)

> 
WriteReady
Write
WriteReady
Write
DestroyStream
Destroy
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 113 error_code 168 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

