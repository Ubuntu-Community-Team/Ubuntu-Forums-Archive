---
title: "Caret stickiness ..."
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2006-01-15
I've asked this before but haven't really gotten an answer. 

Does anyone else have the problem that the blinking caret which denotes your text position on the screen, sticks to the screen when you move it. So that you end up with a long line of like this '|s|a|m|p|l||e |t|e|x|t|', which makes everything impossible to read ?

I'm using ubuntu64 with nVIDIA 6series, I can't find lilo.conf or grub.conf on my system so I'm unsure whether it's framebuffered or not.

---

### Post by thojoh on 2006-10-14
SOLUTION FOUND!

at least for my computer. I had the same problem: which was that I had those 'ghosts' of the cursor (caret, whatever it is called - the vertical line that shows you where the letters you type will appear). Many of these lines where just staying on the screen when I was moving through text in OpenOffice or Firefox.

I had to change my NVIDIA driver that was installed. If you have a certain graphic card version, you might need a different (older) driver to get rid of this ghosting thing. At least, that was it with me.

Changing it was easy using Synaptic:


1. Search for "Nvidia" in Synaptic

2. Look which NVIDIA driver is installed.

On my computer, "NVIDIA binary XFree86 4.x/X.Org driver" was installed (which probably is the default for computers using NVIDIA)
I had to change it to the "legacy" version:
"NVIDIA binary XFree86 4.x/X.Org 'legacy' driver"

3. Install the "legacy" version of the NVIDIA driver
(uninstalling the current driver will automatically be done by Synaptic)

4. In the terminal, run "sudo nvidia-glx-config enable" to enable the driver. 

5. Restart you computer.

Done!

(of course this solution only applies if you have one of these graphic cards that need the older 'legacy' version. I didn't know for sure about my graphic card, but I just tried it and it seems that that was the case. Now, the problem is solved.) 
The computer makes a backup of the changes to the xorg.conf file and tells you in the terminal which command to use to bring back the old settings. So if you note down that command before restarting you computer, you can always revert your changes if it doesn't solve your problem.

I hope this helps some of you!  (I have seen the problem posted several times, but never seriously addressed with a soution.)

all the best!   :-D 

thomas

---

