---
title: "Dual Monitor Scrolling Desktop"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by IlllmikeIlll on 2008-01-27
I have read the other posts regarding this and I have not found a similar issue.

That having been said,

Hello everone my name is mike, I just installed Ubuntu last night and this is the first time I have ever used Linux. Needless to say I need some HELP. I do not know the first thing about any other os than windows, I have several macs here at the house but I have never used them much. I have just built a new Quad core system with a TON of memory a decent graphics card and more hard drive space than I know what to do with. I am running a dual boot with xp on another drive.

Now on to my problem, I have a Nvida 7600GS with dual monitor output on 2 21" apple studio CRT Displays I can get dual monitor to work but when in dual monitor both screens scroll. I have adjusted the res both ways and it does not fix the problem. Ubuntu actually had the correct drivers for these monitors (Thank god because I have been looking for some for windows for 2 years now). If I put it back to single monitor mode this goes away. Whats up with this? and how do I fix it? I want to use both monitors like I do in windows and I know I can. How do I disable this scrolling and keep both monitors at my prefered 1024x768 85hz?

---

### Post by IlllmikeIlll on 2008-01-27
oh yea I need specific details, I do not yet know how to navigate/use this os. AT ALL

---

### Post by kyleabaker on 2008-01-27
If you're not already, try using nvidia-settings to set your resolution.
```
$ sudo nvidia-settings
```
Make sure you click the button that says "Save to X Configuration file". I had this problem several months ago.
You should always make a backup copy of your Xorg.conf file before saving changes to it.

---

### Post by IlllmikeIlll on 2008-01-28
How do I do that, I dont know anything about this. I would imagine I type that in somewhere, but where and how do I get there. Like I said I know NOTHING. I have managed to get here and set a couple of preferences. but other than that I am stupid to all this. Thank you for your help

Mike

---

### Post by matjaz on 2008-01-28
Go to Applications->Accessories->terminal 
And type that in the terminal that you have just opened.

It might be a good idea to read the linux basics section
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

It will help you getting started.

---

### Post by IlllmikeIlll on 2008-01-29
That took me into the settings but no matter what I do I cannot disable this irritating scrolling of the desktop, If I disable one of the monitors everything is fine but this os looses its damn mind when 2 monitors are enabled.....:confused::confused::confused::confused:

---

### Post by deadhike on 2008-02-23
Hi Mike,

I just had the same problem with 2x samsung sm226bw's.

Solution may be that you have both screens set to absolute positions.

1. Restart x server settings ($ sudo nvidia-settings) in terminal
2. Select 'X server display configuration'
3. Notice that in 'Layout' you can select both the left and right screen, selected one is highlighted. Notice that when the first (left hand) screen is selected, the 'X screen' position attribute is set to 'Absolute'. The +0+0 part simply means top-left.
4. Select the second (right hand) screen in the layout pane.
5. Change the 'position' attribute to  'right of', you should notice the gap between the screens in 'layout' disappear so they sit close together.
6. Restart x server by pressimg CTRL+ALT+BACKSPACE (NOTE: This will log you out of your current session!)

Hope that helps.

;)

D

---

### Post by Yellow Pasque on 2008-02-23
Mike, I don't understand your issue. First off, are you trying to use clone mode or Extended/Big Desktop? Second, are you saying that the actual desktop space is bigger than the combined monitor area?

Please post your /etc/X11/xorg.conf and your /var/log/Xorg.0.log

---

