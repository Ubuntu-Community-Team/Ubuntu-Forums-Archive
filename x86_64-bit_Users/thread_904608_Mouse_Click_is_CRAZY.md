---
title: "Mouse Click is CRAZY"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by causeitsme on 2008-08-29
Hi, running amd64 on 2.1.24-19-generic with compizfusion on an ACER 5100 notebook. (No extras: Default Theme - Nautilus for windows, etc.) 

Memory runs around 50% of 1.5G, processors runs at 4% to 10%. 

I don't think it applies but, I recently installed the latest Flash 10. (the problem was already starting to appear before that)



For the past week or so my mouse clicks are totally screwing up.

Seems like it's worse in Firefox but, it happens system wide.

For example: In Firefox - click a link it'll sometimes open email, sometimes page source, sometimes a totally different link. Earlier I right-clicked and copied a url, then when I right-clicked in pidgin to paste it, it pasted it but also opened a firefox tab and the page it opened was a windstream (my ISP) page. The link I pasted into pidgin was for an article in YahooNews. I have no idea where the windstream page could've come from (I haven't visited my ISP's pages in ages)

In FreeCell the left click and drag make the game almost unplayable. When I try to pick up a card and drag it over to another pile, it'll do all sorts of things, sometimes it'll send two or three cards to empty reserves, sometimes it'll just drop what I tried to pick up, other times it'll just send one card to reserve.

In Suduko, click to enter a note and it'll open the spot for entering a number instead, sometimes I have to click three or more times to get the field I want.

If I click and drag to highlight a section of text it mostly doesn't work well. Sometimes it works, sometimes it'll highlight just one word and then start dragging that word along with my pointer. Sometimes it'll highlight a whole section before I've even moused over that area and will be dragging it around, sometimes I'll click in a spot of text to correct spelling or enter extra text and it'll highlight some word or group of words and just delete them, sometimes it'll move those words to other places in the text(usually to the end but, not always). Sometimes I'll successfully highlight some text and when I let go of the click, parts of the text become 'unhighlighted'.

Sometimes when I click a slider adjustment (for volume, or adjustments in certain Ubuntu dialogs) it just does whatever, i.e.; moves the slider independent of actual mouse movement, doesn't 'let go', closes the entire dialog by itself.


Things I've tried:

Touchpad is disabled

Adjusted mouse settings, slow down, speed up pointer speed, drag and drop and double-click timeout.

Tried to manually go really slow with mouse movements. - This one only helps in Freecell and only sporadically.

I've googled this and haven't been able to locate anything like it. (Maybe I'm wording my search wrong?)

Any ideas?:confused:

---

### Post by Sef on 2008-08-30
Maybe your mouse is bad.  I had problems with a mouse until I replaced it.  Find another mouse and see if the problems still occur with the newer mouse or not.

---

### Post by mister.teapots on 2008-08-30
Yes! Yes! Someone with the same symptoms of mouse craziness! I thought I fixed this by increasing the mouse drag-drop threshold to very large. You can do it in System>Preferences>Mouse and just adjust the slider. It seems to adjust the length of movement before Gnome realises you're trying to drag-drop something. I think in Firefox, it guesses that you are always trying to drag-drop because the slider is too low.

---

### Post by Milleman on 2008-08-30
My mouse works fine, but I have noticed irregularities when using the mouse in Firefox sometimes. Just when I click on a link, the whole page scrolls up slightly and I miss the link I were clicking on. Sometimes this can cause wrong link to be clicked, if they appears in row.

A bit annoying...

---

### Post by causeitsme on 2008-08-30
> **Sef said:**
> Maybe your mouse is bad.  I had problems with a mouse until I replaced it.  Find another mouse and see if the problems still occur with the newer mouse or not.

It's funny you say that as I have two identical Logitech wireles usb mice and one quit working about 3 weeks ago. I went and dug the other one out and I couldn't get it working for about 5 minutes and then all of a sudden it started working. Then kinda gradually these symptoms have arisen. I'll try a different mouse later today when my daughter gets off of her computer I'll grab hers and try it.

> **mister.teapots said:**
> Yes! Yes! Someone with the same symptoms of mouse craziness! I thought I fixed this by increasing the mouse drag-drop threshold to very large. You can do it in System>Preferences>Mouse and just adjust the slider. It seems to adjust the length of movement before Gnome realises you're trying to drag-drop something. I think in Firefox, it guesses that you are always trying to drag-drop because the slider is too low.


I've adjusted those settings with no luck, however, I realized upon reading your post that I'd never maxed out the drag and drop threshold. I just did that and it's working properly for the moment. However, I just started up and it always seems to be fine right after being started up. 

I'll update this later today and let ya'll know what I find out.:)

---

### Post by causeitsme on 2008-08-31
I tried a different mouse and same result. I maxed out the drag and drop threshold and that has helped. I still get intermittent problems but, not as bad. Firefox and Free Cell are by far the worst culprits. Half the problems with FF though is right click stuff whereas with freecell that's drag and drop problems.

At least it's better :)

---

### Post by causeitsme on 2008-09-05
Mouse has still been acting up. I did get a little more relief by adjusting the sensitivity down to 0.

Also, there is a bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/37929](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/37929)

---

### Post by Crafty Kisses on 2008-09-05
Post the results of ```
lsusb
```

---

### Post by causeitsme on 2008-09-05
> **Codename said:**
> Post the results of ```
lsusb
```

bobby@bobby-laptop:~$ lsusb
Bus 003 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000

---

### Post by philinux on 2008-09-05
> **Milleman said:**
> My mouse works fine, but I have noticed irregularities when using the mouse in Firefox sometimes. Just when I click on a link, the whole page scrolls up slightly and I miss the link I were clicking on. Sometimes this can cause wrong link to be clicked, if they appears in row.

A bit annoying...


This happens to a lot of people, me too. It happened in windows so god knows what causes it.

---

### Post by jay3712 on 2008-09-08
My mouse clicks are driving me insane!! I was messing around in xorg.conf to get compiz to work, but I didn't touch the mouse or keyboard part. 
IBM Thinkpad T40:
Same behavior on laptop as well as usb mouse.
Single clicks register as double clicks in everything.
Right clicks do not do anything in Firefox, but works elsewhere (folders, desktop).
Everything else works great, but the computer is almost unusable like this. 

Thanks for any suggestions!
Jason

---

### Post by causeitsme on 2008-09-10
Well, I've finally figured out a workaround for this. 

WORKAROUND:   Never open Firefox!! I have done this for two days. I simply started using Epiphany (customized it to my liking).
Reboot your system, don't open firefox at all, use Epiphany for browsing. My mouse has given me no troubles since then.

Another plus is that Epiphany seems to be even faster than firefox.

---

