---
title: "chroot to 32bit and run X server...."
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by ZeroHimself on 2008-05-05
ok, i successfully installed a 32-bit hardy, and booted it with dchroot....
when i start x(startx -- :1) it runs for about 10 seconds, and displays an error message saying that something might be wrong, and locks my keyboard/console....

I can ssh in from another computer, but i can't recover the system short of a sudo shutdown -r now

I am trying to get a 32 bit server running so i can use wine, and all of my other noncompatable 32-bit programs....

any ideas?

---

### Post by Kilz on 2008-05-06
Wine has a package in the repositories for the 64bit version. Are you doing 32bit development work? If not you are going to find few if any applications that do not have a 64bit version and none to my knowlage that cant run as 32bit. chroots are not needed for the most part. Please list all 32bit applications you need to run.

---

### Post by ZeroHimself on 2008-05-28
Well, yes, I do 32-bit development....
The major thing I was trying to run was Floola..., a 32-bit(doesn't work on 64-bit) Ipod manager...

Plus I'm just exploring, learning how things work, and what they can and can't do....

I did success fully run a chrooted X-server(32 bit) ....(too buggy)....

then I opened access to my X-server, so that I could try to run my 32-bit app...

I suceeded... but no Cross-X drag and drop support!!!!(floola needs drag and drop)....

Ultimate solution..... RUN A VIRTUAL MACHINE!!!!!

I started a second X-server on the 64bit ....
then I run VBox on it in full screen....

With both X-servers accepting tcp connections, I can run X programs on either 32 or 64 bit(just switch VT's ), or I can specify which X server to connect to!!!

It works... Oh yeah, and with VBox you can set shared folders, so that you can access your data in both OS'es...

---

