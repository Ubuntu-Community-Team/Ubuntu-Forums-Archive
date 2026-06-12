---
title: "Does this page make firefox crash?"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoyOfDestiny on 2005-11-16
Anyway, I ran firefox (64-bit) through console and went to [http://www.vgmaps.com/index.htm](http://www.vgmaps.com/index.htm)

Click on a link and boom, crashes/closes.

NP_Initialize
New
SetWindow
SetWindow
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 35 error_code 167 request_code 144 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I'm not at my 32-bit firefox at the moment, but I'm pretty sure I could reach this page on my laptop. 
Is this a bug? I don't think the page has anything bizzare...

---

### Post by ofek on 2005-11-16
Well im using firefox 1.5 rc2 and it works fine...

---

### Post by ubernoob on 2005-11-16
it works fine with me.

---

### Post by grsing on 2005-11-16
Works fine for me (Firefox 1.0.7)

---

### Post by bonzodog on 2005-11-17
The page will load fine as long as you don't have flash installed in anyway on your machine. It's using the most recent version of the flash player.

---

### Post by etitor on 2005-11-17
No problem with The Game Atlas site here (Breezy AMD64, pure 64-bit Firefox 1.0.7).

---

### Post by auburn on 2005-11-17
fine here with breezy (32bit) kernel-2.6.12-8 (not 9), ubuntu's firefox 1.07, and flash installed. Are you working with a profile *without* extensions installed?

---

### Post by BoyOfDestiny on 2005-11-17
[QUOTE=bonzodog]The page will load fine as long as you don't have flash installed in anyway on your machine. It's using the most recent version of the flash player.[/QUOTE]

You nailed it, it was having libflash.

Thanks!

---

