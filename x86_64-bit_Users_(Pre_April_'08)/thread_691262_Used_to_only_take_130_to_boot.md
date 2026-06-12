---
title: "Used to only take 1:30 to boot"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by redrovo on 2008-02-08
I run a 64 bit turion laptop with 1 gig of ram. It is a dual boot with XP. My XP takes 45 seconds to boot. My ubuntu used to take 1:30 minutes to boot, until recent software updates were downloaded. Since then ubuntu now takes well over 3 minutes to boot. 

All my past experiences with linux installations, always gave me a desktop that was way more responsive and snappier than XP. This 7.10 ubuntu has been anythin but. I've spent a lot of time reading all the forums, and making all the changes to help correct this. 

I'm not bashing ubuntu. I love what you have done, but unfortunately I think it is time we go our seperate ways. I'll never forget you ubuntu. Thankyou for everything. 

Goodbye. Au Revoir. Despedida. &#1087;&#1088;&#1086;&#1097;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;. Abschied. &#21578;&#21035;.

---

### Post by JoshuaRL on 2008-02-08
So, you say you've investigated a lot of ways to fix this.  So is it the usplash?

---

### Post by kbless7 on 2008-02-09
> **redrovo said:**
> My XP takes 45 seconds to boot.

maybe to get to the desktop but not to the point where you can start running programs

---

### Post by Yellow Pasque on 2008-02-09
Don't let the door hit ya where the good lord split ya.

---

### Post by Cappy on 2008-02-09
Turn off the splash screen (delete "splash" on the kernel lines of /boot/grub/menu.lst ) . Look to see where it is taking a long time. Then downgrade the package and file a bug on launchpad.

You may also want to look to see if your previous kernel (on the GRUB boot menu) still boots fast. This will let you know if it is a kernel problem.

---

### Post by crjackson on 2008-02-09
Bueno Bye

---

### Post by redrovo on 2008-02-09
Yup, land on my desktop in 45 seconds ready to go. Hard drive happy and quiet. I got this program that was originally created by a team at microsoft to insure the quickest boot of xp.

---

### Post by redrovo on 2008-02-09
I've removed the usplash from the menu.lst

---

### Post by redrovo on 2008-02-09
JoshuaRL   , i love your avatar.

---

### Post by JoshuaRL on 2008-02-09
> **redrovo said:**
> JoshuaRL   , i love your avatar.

Thanks man.  I dug around for a while to find it.  I wasn't looking for that exactly, but when I saw it I knew it had to be mine.

As far as usplash, I just want to make sure you did the fix right.
```

gksu gedit /etc/usplash.conf

```
And make sure your xres and yres settings are correct.  Then run the following command to make sure it stays updated:
```

sudo update-usplash-theme usplash-theme-ubuntu

```
Hope that helps.

And rock on Honda racing.

---

### Post by SIXAXIS on 2008-02-09
Mine was like that too, but I install a program called "Startup-Manager" if I remember correctly. I enabled the settings that said colors, the text of what it was doing, and the splash. It now boots in like 30-45 seconds from 3 minutes.

---

### Post by redrovo on 2008-02-15
I really appreciate all the feedback you guys have provided. I've tried all the above mentioned fixes, but nothing resolves it. I guess sometimes it just isn't a happy hardware/software match. I went ahead an installed the latest 64bit openSUSE. Happy to say I haven't had a problem yet. Haven't had to mess with the uspalsh. Starts up good, shuts down quick, hibernates too. Easy install script for ATI cards. I guess some distros are just better suited for some hardware setups (64bit turion 200m Radeon128mb, 1gig ram)

Thank you again. Wish you all the best.

---

### Post by redrovo on 2008-02-17
> **steveneddy said:**
> So instead of posting to help you fix the problem, possible helping someone else with the same problem, you gave up and abandoned your thread.

Why did you post in the first place?

To whine to everyone and try to get more attention?

Some people were actually trying to help you, and I actually had a repair that some are missing but is a suspect in some cases, so I read through the entire thread only to see that you jump ship and abandon the cause that you posted for in the first place, only to see that you were only a lonely whiner that was only looking for some more attention.

Go whine in the SUSE forums.

Don't forget to take your Windows with you, fan boy.

You sound as frustrated as I've been. My original post to this thread was a week ago. Of course I don't expect things to be resolved any quicker than that, but I've been reading other threads of similiar issues on here for over three weeks now. So in all I've been tinkering with these issues for about a month now. 

 I am in no way bad mouthing Ubuntu. I think it is a great distro. As ignorant of all this as I am, it seems to be some distros are more geared toward certain hardware setups than others. Am I saying openSUSE is better than Ubuntu, not at all. For whatever reason it just fit my laptop better. 


My point about windows, was that in all my past installs of linux I've always found it to be snappier and quicker than my win xp installs. So with this install of 7.10 being so much slower I figured something must be wrong. For the record, I cannot stand windows. I only maintain an install of it for adobe premiere.

Just figured I should share my findings with you.

---

### Post by JoshuaRL on 2008-02-17
> **redrovo said:**
> You sound as frustrated as I've been. My original post to this thread was a week ago. Of course I don't expect things to be resolved any quicker than that, but I've been reading other threads of similiar issues on here for over three weeks now. So in all I've been tinkering with these issues for about a month now. 

 I am in no way bad mouthing Ubuntu. I think it is a great distro. As ignorant of all this as I am, it seems to be some distros are more geared toward certain hardware setups than others. Am I saying openSUSE is better than Ubuntu, not at all. For whatever reason it just fit my laptop better. 


My point about windows, was that in all my past installs of linux I've always found it to be snappier and quicker than my win xp installs. So with this install of 7.10 being so much slower I figured something must be wrong. For the record, I cannot stand windows. I only maintain an install of it for adobe premiere.

Just figured I should share my findings with you.

You're right.  If Linux boots and runs slower than XP, something's up.  That is, unless you have **seriously** cranked over Windows.  And your other point is correct too.  Sometimes other distros just work better on some hardware, especially laptops.  Glad you found a solution that works for you.

---

### Post by Jouke74 on 2008-02-17
Ahem, on my machine there is not much difference between Xp and Xubuntu boot either (without too much of tweaking). I don't really care much about it as well, on both it's about a minute.

Once it's runing is where things start to matter, and here my Xubuntu is as snappy as XP. I assume because both my XP as well as Xubuntu are performing (close to) optimal. Therefore I can't get much more snappiness out of either OS. I mean 2 to 3 seconds to start up Firefox under both OSes?

Ubuntu mileage may vary a bit.... that's why there are more distro's as well. 
(If you want quicker boots, you can profile your boot under Ubuntu).

---

### Post by An_Dynas on 2008-02-17
I don't know if it's insightful, but I have three machines running Ubuntu (or a derivative).  Two are notably quicker to a functional point from the cold boot.  My Xubuntu machine, however, takes significantly longer to get running than it does under Win.  I have noodled and struggled with it to no avail.:confused:  I have taken it apart, reconnected everything, formatted everything, tried a clean boot repeatedly from numerous distros -- same result.

I know I'm no help, just to explain that some machines may be quirky and/or inexplicably moody.

---

### Post by JoshuaRL on 2008-02-17
> **An_Dynas said:**
> I don't know if it's insightful, but I have three machines running Ubuntu (or a derivative).  Two are notably quicker to a functional point from the cold boot.  My Xubuntu machine, however, takes significantly longer to get running than it does under Win.  I have noodled and struggled with it to no avail.:confused:  I have taken it apart, reconnected everything, formatted everything, tried a clean boot repeatedly from numerous distros -- same result.

I know I'm no help, just to explain that some machines may be quirky and/or inexplicably moody.

Yeah, I've had a few [magic-feelings boxes](http://www.qwantz.com/archive/001163.html) in my time.

---

