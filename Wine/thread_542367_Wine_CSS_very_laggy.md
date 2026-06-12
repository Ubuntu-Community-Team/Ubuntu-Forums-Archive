---
title: "Wine CS:S very laggy"
date: 2007-09-03
forum: Wine
---

### Post by shrumhead on 2007-09-03
I really have no idea what is slowing down CS:S and it seems like I have tried every configuration I can find in both wine and cs:s to fix the problem.  I'm simply not getting the sort of FPS I should be.  In windows xp with the same hardware (see below) I was getting about 80+fps all the time with medium settings.  Now, with the lowest settings and directx7 I'm getting a good 15fps with more than 10 people on the screen .  

I was thinking it had to be a problem with the sound seeing as how when I ran the video stress test I was pulling an easy 180fps score at the end.  I tried using oss, emulated oss (with and without emulated driver turned on), and when nothing changed I used the ALSA sound drive method (listed [here]("http://appdb.winehq.org/appview.php?iVersionId=3731&iTestingId=13907") ) but still  nothing is changed.  

Then I went into winecfg and unchecked both oss and alsa (I assume that should disable both drivers) and the game still ran like trash which, if my assumption is correct, means it isn't the sound afterall.  

I used the Envy script to update my Nvidia drivers and it worked just fine.  I have another game on the computer, Jedi Knight Jedi Academy, and it is an older game but works flawlessly with alsa sitting pretty with the highest graphic settings at about 100+fps.  

I've tried switching the DirectX between 7, 8.1, and 9, but that doesn't change anything.  I've tried "renice" all the way through '-19' but still no dice.  I've tried running CS:S in its own X server with and without gdm running.  I've changed the heapsize to a much larger number than it needs to be (768, I have 2gig physical).  I've run it with and without WINEDEBUG=-all.  I've switched the operating system the application thinks its running on in winecfg and they all yield nearly the same results.  The last thing I did was, in winecfg, turned off 'Allow Pixelshader' which seemed to increase performance by a couple FPS here and there but nothing close to solving my dilemma.   

I am using an AMD64 3200+, Integrated mobo sound, Nvidia 7800GTX (256mb), and Fiesty 7.04. 

Does anyone have any suggestions as to what I might do in order to get my CS:S performance back to where it should/used to be?

Thanks

...Shrum

---

### Post by ubu-for on 2007-09-04
It's probably a sound problem. Do you get any error messages, if you run winecfg?

Which Wine version do you use?

Do you use Beryl or Compiz as window manager?

---

### Post by Fir3chi3f on 2007-09-04
try launching the program from the terminal and add '-opengl' to the end

Also, could you post the output of your terminal?

---

