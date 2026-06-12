---
title: "Gnome/Nautilus Browsing for Other Programs Not Working - Help!"
date: 2009-04-13
forum: x86 64-bit Users
---

### Post by damian_dman on 2009-04-13
Just recently installed Intrepid Ibex 64-Bit onto a brand-new HP G60 Laptop. Everything has worked great so far with one exception.  If while using a program (F-Spot for example) or I am offered the opportunity to browse file system for default location to save or load from (like while using Firefox while trying to set up a Flickr upload or Nikon My Picturetown upload) I am unable to browse through the file system (actually, Firefox cannot execute an "Open File" command for this same reason).  The Nautilus browser window will pop up labeled "File Open" or "Import" or whatever the governing program is calling for.  I can see my /home directory and navigation panel to jump to any directory or drive I want to select.  However, I am unable to click on anything and have it respond.  I can point all I want, but the highlight will never move, window pane cannot scroll via mouse or the window scroll bar.  I feel that this may be a simple permission problem, but I can't seem to figure it out.  This new laptop is set up very similarly to my desktop running Hardy Heron 32-Bit and user permissions are identical.  What am I missing?

---

### Post by 3Miro on 2009-04-13
Just a guess, but you shouldn't put things in /home, but rather /home/your_username.

What happens if you start nautilus regularly from Places -> Home?

You can try running nautilus from the command line: Applications -> Accessories -> Terminal and then
```
nautilus
```

That may show you some more specific error messages.

---

### Post by damian_dman on 2009-04-13
Nautilus works just fine on its own.  The weirdness only happens when you try to access the file system through another program.  For example, crank up Firefox and then go to File-> Open File.  You get a standard Gnome/Nautilus file browser with the heading tag from the program that opened it.  It looks normal enough, but I can't highlight, scroll down, or open anything.  The only thing that responds is the Cancel button (no lag either).

---

### Post by damian_dman on 2009-04-13
I noticed the following error while running *sudo nautilus* from a terminal:  [I]net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share[/I].

I ran the following from a terminal: *sudo apt-get install samba smbfs*

No more error message in the terminal.  I can now browse to save email attachments where I want to and to upload photos from a directory to flickr.

No.  Now it stopped working.  Will try to see if another error exists.  This might just be a samba problem after all?

---

