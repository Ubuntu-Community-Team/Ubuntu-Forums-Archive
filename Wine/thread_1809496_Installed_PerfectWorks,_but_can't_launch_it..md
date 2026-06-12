---
title: "Installed PerfectWorks, but can't launch it."
date: 2011-07-21
forum: Wine
---

### Post by grey1beard on 2011-07-21
After some trial and error, and by changing my configuration of Wine 1.2.2 to windows 98, I seem to have installed from my original disc, an old word processing program called PerfectWorks 2.1.

I used the method described on the Ubuntu/Documentation/Wine page, and needed to choose a "minimal" installation for laptops for my Toshiba Satellite running 10.04.

As may be seen in one of the screenshots, there are two .exe files, one of which should launch the program, probably the wpworks.exe, if I remember correctly from running it in win 98.

However, if I click on either of them, I get the window opening that is shown in the other screenshot, titled "winevdm.exe".
Can anyone advise on how I can move forward, as after about 3 secs, the window closes, with nothing else happening.

John

---

### Post by JustinR on 2011-07-22
Hi,

If you open a terminal, navigate to the directory of the WpWorks.exe, then type "wine wpworks.exe", does it give any error messages?

---

### Post by grey1beard on 2011-07-22
Problem for me - the location is in the .wine/drive_c/Program Files
How do I write the **cd** command in Terminal to the *Program Files*, as it doesn't accept "Program Files" as a valid location ?

John

---

### Post by grey1beard on 2011-07-23
Just read in my copy of Keir Thomas, use " " marks round the folder name if it has spaces in it.

---

### Post by grey1beard on 2011-07-23
Result -

> john@frizzy:~/.wine/drive_c/Program Files/WPWW21$ wine wpworks.exe
fixme:toolhelp:NotifyRegister16 (0,12570000,0), semi-stub.
fixme:hook:SetWindowsHookEx16 hook type 6 broken in Win16
fixme:toolhelp:NotifyUnregister16 (0), semi-stub.
[email]john@frizzy:~/.wine[/email]/drive_c/Program Files/WPWW21$

Could you now translate this for me please ?

Many thanks
John

---

### Post by JustinR on 2011-07-23
Hi,

I'm not sure how to fix the error.

If you look up the line that says:
> 
fixme:hook:SetWindowsHookEx16 hook type 6 broken in Win16

in Google, there could be some solutions.

---

### Post by grey1beard on 2011-07-24
Thanks Justin, I'll give that a go.
John

---

### Post by grey1beard on 2011-07-24
I've just wasted 30 minutes trying to get to the advanced reply window from the quick reply window and in the process losing my carefully thought out response to earlier help.
I have attached the screen shot of the message, just so everyone knows what I am talking about, and I would like to know

              [SIZE="4"]WHAT IS THE POINT[/SIZE]

of not giving me the opportunity to save what I have written, before deleting it, and sending me back to where I started.

When I've calmed down, I'll try again.
John

---

### Post by grey1beard on 2011-07-24
Now I've recovered, I'll try and gather my thoughts.

I followed the idea of googling the error message, and while there are many examples of the same, there doesn't seem to be any explanation of what it means. Thus it's impossible to make any logical guess at a way forward.
One contributor's helpful advice was "Ignore it" - good grief - ](*,)

My own idea is that the problem may be a combination of not having the software installed in the correct place and not making correct use of the Wine configuration window.
Either, neither, or both.

I must confess that I find the wine config somewhat lacking in not having a *Help* tab.

It's all very well being given information like
> This tab is linked to the Libraries and Graphics tabs to allow you to change systemwide or per application settings in those tabs as well.

But no help in how to bring each about, and this* may* be crucial to my present dilemma.

John

EDIT  I've now found the Ubuntu Wine documentation which is helpful.
Why not a link on the wine window to it ?

---

