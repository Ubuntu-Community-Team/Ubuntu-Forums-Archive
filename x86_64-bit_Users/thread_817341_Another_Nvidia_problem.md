---
title: "Another Nvidia problem"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by mad_max0204 on 2008-06-03
I installed 8.04 some time ago and with it came 169.12 driver. Everything works fine but there are some glitches. There are dots on screen like monitor is having bad pixels and when I drag window around dot draws like a pencil, when I play video there are some weird looking glitches in video. This is not my hardware problem because everything was fine in gutsy. I even tried some live cd's and other distros. Any help would be appreciated.

Thanks

PS I forgot, I'm not using compiz or any other desktop effects and GPU is Nvidia 7900GTX.

---

### Post by EXCiD3 on 2008-06-03
Thats an odd issue...Havent had any problems like that before. You might want to try installing the new 173 nvidia driver which was just released a couple of days ago. Heres a quick tutorial on everything you need to do: [http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by mad_max0204 on 2008-06-03
I followed your guide and it did install nvidia drivers properly. I thank you for that.
But it still didnt solve my problem with graphical glitches. I'll try to figure out what is the problem.

---

### Post by EXCiD3 on 2008-06-03
Well that rules out that it was a driver issue. And since you arent running compiz it cant be that either. Can you take a screenshot so i can see what it looks like?

---

### Post by JEvsn on 2008-06-03
Something like this happened to me a couple of days ago. It turns out my gfx-card was way too hot. Placing a big fan next to it helped.

---

### Post by mad_max0204 on 2008-06-03
Yeah I'll try to take a screenshot of that. Btw my GPU is at 50*C and I dont think its hot. I was hotter before. I just connected my monitor to laptop and didnt have any problems so I ruled it out.

---

### Post by EXCiD3 on 2008-06-03
Yeah im fairly sure its not your video card getting too hot. Mine averages at 67C and gets up into the 80s when im gaming. A screenshot should help explain ur problem better than words ;)

---

### Post by David E. Fox on 2008-06-03
[QUOTE=mad_max0204;5107311]I installed 8.04 some time ago and with it came 169.12 driver. Everything works fine but there are some glitches. There are dots on screen like monitor is having bad pixels and when I drag window around dot draws like a pencil, when I play video there are some weird looking glitches in video. This is not my hardware problem 



I wonder if you might be seeing what I'm seeing (I put this under a different thread on the forum -- look for my name on the post.) So far I have only gotten one response and it was not helpful.


What I'm getting are black blotches in text - firefox and other programs, terminal sessions, and so forth, after running most any 3D app that I have (stellarium, google earth). Sometimes I see momentary freezups and other times I get hard lockups (such as compiz). Compiz is really not running very well, if at all. I've gotten it to work somewhat, but I see green screens when trying to play video. Other times if I play a video it works just fine - and the -vo gl2 switch on mplayer makes for extremely stunning views, by the way.

Aptitude grabbed a new upgrade for nvidia-glx-new (which is what I use) but it doesn't solve the problem; it makes it worse in some situations, such as starting compiz.

I'm about to give up on 3d on Ubuntu.

My board is an ECS motherboard with embedded 6100 nforce 430 graphics controller.

---

### Post by Sef on 2008-06-03
> Sometimes I see momentary freezups and other times I get hard lockups (such as compiz).

I wonder if it might besides a graphics card issue, a ram or motherboard problem.   For the ram, boot into grub and do a [memtest86+]("http://www.memtest86.com/").  It will check your ram.

---

### Post by David E. Fox on 2008-06-03
> **JEvsn said:**
> Something like this happened to me a couple of days ago. It turns out my gfx-card was way too hot. Placing a big fan next to it helped.

How do you tell the temperature of a graphics card anyway? Mine's embedded anyway. I can tell the overall system temperature (or is it cpu temp?) using $ acpi -V

My problems tend to happen extremely soon after launching a 3d app. So I don't think the temperature is an issue here. 

According to acpi -V, my system temp is 39 deg C.

It might go up to 51 if I do a heavy compile or video encode (avi-mpeg2).

---

### Post by David E. Fox on 2008-06-03
> **mad_max0204 said:**
> Yeah I'll try to take a screenshot of that. Btw my GPU is at 50*C and I dont think its hot. I was hotter before. I just connected my monitor to laptop and didnt have any problems so I ruled it out.


Here's a screenshot of what I see here:

[[IMG]http://img522.imageshack.us/img522/5548/screen2mi6.th.png[/IMG]](http://img522.imageshack.us/my.php?image=screen2mi6.png)

---

### Post by mac143_01 on 2008-06-04
Try the steps that others tell you maybe one of them will work for you...

---

### Post by EXCiD3 on 2008-06-04
> **David E. Fox said:**
> Here's a screenshot of what I see here:

[[IMG]http://img522.imageshack.us/img522/5548/screen2mi6.th.png[/IMG]]("http://img522.imageshack.us/my.php?image=screen2mi6.png")

Now thats just weird...I've never seen problems with the black boxes like that before...It looks to be a problem with your fonts.

---

