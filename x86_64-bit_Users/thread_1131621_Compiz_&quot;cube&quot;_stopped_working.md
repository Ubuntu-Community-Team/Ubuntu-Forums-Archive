---
title: "Compiz &quot;cube&quot; stopped working"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by slayr007 on 2009-04-21
I have only used a few versions of ubuntu, 8.04 being my first, and Jaunty so far has had the least problems of all. However, I just started having problems with the Compizconfig cube.  I asked my "computer geek" friend for help and everything he tried didn't work.  I use comp geek as a complement, by the way, just in case anyone is offended.  Can anyone help me?

---

### Post by grege on 2009-04-21
First guess, compiz is turned off.

Check System -> Preferences -> Appearance -> Visual Effects

Second Guess, compiz defaults to "wall" rather than "cube", so each time you change compiz in any way it reverts to wall.

I assume you have CompizConfig Settings Manager installed.

System -> Preferences -> CompizConfig Settings Manager -> Desktop

And set cube, when it says it must unset "wall" say yes.

cheers

---

### Post by nwadams on 2009-04-21
your intel card has been blacklisted by compiz for the time being due to a critial bug. This is for stability and is being fixed asap. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

see that bug for more information.

EDIT: this is not a 64 bit problem this is a general ubuntu problem.

---

### Post by slayr007 on 2009-04-21
Dang I hate it when that happens](*,) One of the reasons i left ubuntu was the instability of the drivers.  Thank you for all the help.

---

### Post by Vrekk on 2009-04-21
> **slayr007 said:**
> I have only used a few versions of ubuntu, 8.04 being my first, and Jaunty so far has had the least problems of all. However, I just started having problems with the Compizconfig cube.  I asked my "computer geek" friend for help and everything he tried didn't work.  I use comp geek as a complement, by the way, just in case anyone is offended.  Can anyone help me?
Ya for being that computer geek \\:D/

Do we have a ETA on when this will be fixed? Or is more of a it will be fixed when it is kinda thing?

---

### Post by nwadams on 2009-04-21
an eta. no. not yet. but its being actively worked on. It will hopefully get fixed in a few days. 

@slayr007: may I ask what distro you've moved to from ubuntu.

---

### Post by slayr007 on 2009-04-22
i have been ubu loyal since my first 8.04 experience.  When I took my brake i went back to the OEM OS on my laptop-Windows Vista.

---

### Post by FredB on 2009-04-22
Cube worked for me since beryl time...

---

### Post by Found on 2009-04-22
Recently i turned the cube of, and set number of desctops to 2. I don't think everyone actualy using 4 desktops...
Now i'm quiet happy with Wall feature and Expo :)

---

### Post by empty_spaces on 2009-04-22
Hopefully, this might help with the desktop effects issue.
I have a Toshiba laptop with GMA 965 / X3100 graphics.
I just did a fresh install of Jaunty 64bit yesterday, and was immediately presented with the "Desktop effects could not be enabled" message when I tried to enable it.
I went ahead and installed "fusion-icon" from the repository and added it to the startup programs.
When I right-clicked on fusion-icon and the "Select Window Manager" option was showing as compiz.
Then I clicked on "Reload Window Manager" and immediately had wobbly windows working, which told me that desktop effects was now working.
Then I went to CompizConfig-Settings-Manager and enable the cube.

---

### Post by Thelasko on 2009-04-22
> **empty_spaces said:**
> Then I clicked on "Reload Window Manager" and immediately had wobbly windows working, which told me that desktop effects was now working.

That wasn't the problem.  Desktop effects have always worked with Intel cards.  The problem is that you can't watch decent video with it enabled.

---

### Post by empty_spaces on 2009-04-22
Well, the thread title does talk about the cube not working and the OP has intel graphics, so I assumed we were talking about Desktop effects.
I agree that Desktop effects have usually worked with Intel cards, but occasionally you get the "Desktop effects could not be enabled" error, hence my post.

---

### Post by nwadams on 2009-04-22
yes. desktop effects are currently blacklisted on intel cards until a bug causing lockups and crashes gets fixed.

---

### Post by Thelasko on 2009-04-22
> **empty_spaces said:**
> I agree that Desktop effects have usually worked with Intel cards, but occasionally you get the "Desktop effects could not be enabled" error, hence my post.

If I am correct, that message is a "bug fix" for the video issue.  The effects can be enabled, but aren't because the video issue.

In other words, the message, "Desktop effects could not be enabled," isn't a bug.  It's a feature that prevents a different bug.

---

### Post by nwadams on 2009-04-22
> **Thelasko said:**
> If I am correct, that message is a "bug fix" for the video issue.  The effects can be enabled, but aren't because the video issue.

In other words, the message, "Desktop effects could not be enabled," isn't a bug.  It's a feature that prevents a different bug.

yes that is correct. 
please see this bug for more information: [https://bugs.launchpad.net/bugs/359392](https://bugs.launchpad.net/bugs/359392)

there is a way to force them to enable which involves skipping the blacklist check which can be used if you don't care about occasional crashing or if you are testing a possible fix.

---

### Post by slayr007 on 2009-05-07
I got it working by installing the Compiz fusion icon:guitar:

---

