---
title: "[SOLVED] Wine 1.4 Help Needed"
date: 2013-03-02
forum: Wine
---

### Post by speartip on 2013-03-02
I have just done a clean install of Ubuntu 12.04.2, but when I went to install wine it wants to remove about 30 packages,
mainly mesa & xorg. Is this safe?

---

### Post by Karlchen on 2013-03-02
Hello, speartip.

This does not sound correct. A Wine installation should not suggest to remove mesa and xorg packages.
I installed Wine 1.4 on Ubuntu 12.04.2. Wine did not suggest to uninstall anything.
Which Wine package did you select to install exactly?

Oh, by the way. I use Synaptic Package Manager in order to (un)install/update software on Ubuntu, because I have got used to it since Karmic Koala times and because it gives me more precise control over what I am doing. (Software Centre looks too much like an iPhone/Google appstore to me. - My perspective.)

I selected to install "wine1.4", and the installed package is displayed as "wine1.4" - version string "1.4-0ubuntu4.1". - Works fine here.

Kind regards,
Karl

---

### Post by speartip on 2013-03-03
Hi Karl. Thanks for your reply.
This is a stock 12.04.2 Desktop install, hours old, that has all the Quantal extras included.
What Wine1.4 seems to want to do is remove all the "lts-quantal" stuff, & replace it with the original packages.
But even if I click ok to this it will not install, as it says I hold "broken packages" which I don't.
So it seems i'm screwed either way.
I've attached  screenshots.

---

### Post by Karlchen on 2013-03-03
Hello, speartip.

I assume that the Wine1.4 package which you are trying to install holds a list of dependent and conflicting items which simply does not match the software list of Ubuntu 12.04.2. This is why it 
I cannot, however, easily reproduce your situation. Reason: My Ubuntu 12.04.2 started as 12.04 (no service pack). At that time Wine1.4 was installed without any hassle. In the course of time, keeping Ubuntu up-to-date turnt Ubuntu 12.04 into Ubuntu 12.04.2. Wine 1.4 still works fine and does not complain about any other software packages.
I am a bit reluctant to uninstall Wine1.4 and re-install it again just to find out whether I will run into the same problem as you.

What I would like to suggest instead is this:

[LIST]
[*]Open a terminal window. 
[*]Execute the commands ```
sudo apt-get update
sudo apt-get install wine1.4
``` 
[*]Post the screen output of the two commands here, please. 
[/LIST]

The screen output of the two commands should hold - among a lot of other things - error messages which may enlighten us as to what goes wrong and why.

Kind regards,
Karl

---

### Post by speartip on 2013-03-03
Thanks Karl.
I think it is something to do with the 12.04.2 iso.
My original 12.04 install had no problems with Wine at all. But after a lot of messing I decided to do a fresh install.
Like I mentioned this is a fully updated fresh install, so I cannot understand the issue.
I will keep googling.

---

### Post by speartip on 2013-03-03
I have just solved the problem from this thread.
[http://ubuntuforums.org/showthread.php?t=2117758](http://ubuntuforums.org/showthread.php?t=2117758)
```
sudo apt-get install libgl1-mesa-glx-lts-quantal:i386
```
Then install wine1.4.

---

### Post by Karlchen on 2013-03-03
Hello, speartip.

Great. Congratulation that you have found that thread which explains the root cause is a known bug. =D>
And thanks a ton for caring to pass on this important piece of information.
And of course have fun using Wine finally!

Cheers,
Karl

---

