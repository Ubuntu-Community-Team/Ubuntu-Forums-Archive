---
title: "Age of Empires 2 Resolution, Sound and Multiplayer / Online"
date: 2008-09-08
forum: Wine
---

### Post by frankstrudel on 2008-09-08
Hi

Running Conquerors. I've got all the DLL's, no probs.

Started fine with the disk, and works with NoCD. 

Few problems; Option for highest res greyed out (unselectable)...?
              Sound very intermittent, stops for no reason then starts again, playing the backed up sounds.
              

               Most importantly, the online (not LAN) multiplayer seems rather broke. Tried hosting on a windows machine, another ubuntu machine and this hardy machine. Tried forwarding all the ports microsoft requires on my network and the windows one. Tried DMZ'ing this machine.

[-o<Can anyone help with anything? I only post together cos i thought they may be connected, if you think otherwise I will bow to command ;)

---

### Post by frankstrudel on 2008-09-10
Anyone? I wonder whether anyone with experience of other wine multiplayer games could help, or experience with other wine apps in general?
Thanks!

---

### Post by frankstrudel on 2008-09-12
I have multiplayer working ubuntu-ubuntu, yet to try ubuntu-windows.

Forwarded all ports on mine, along with a DMZ on mine that I will try without. I believe the clincher was using ufw to allow ports 2300-2400 and 47624. All were done on both ubuntu machines. For the range i used Brazen's method for ufw ranges;

"for i in `seq 2300 2400`; do
  sudo ufw allow $i
done"

Hope this helps someone else... i'll try taking out the DMZ and see if it was really necessary.

Still problems with sound and res

---

### Post by pytheas22 on 2008-09-20
Could you please describe in more detail what you did with ufw to get things to work?  I'm trying to run AOE2 in a virtual machine (which solves the sound and resolution problems: the application itself works flawlessly inside VirtualBox) but I can't get multiplayer games to work, and one possible problem is that Ubuntu is blocking the necessary ports (they're open on my router).  Please let me know.

---

### Post by frankstrudel on 2008-11-26
for i in `seq 2300 2400`; do
sudo ufw allow $i
done

replacing 2300-2400 with the required ports for AOE2

---

### Post by Wally_dog on 2008-11-26
You should no that the intermittent sound problem is a problem within the game, not Ubuntu. I used to play AoE on Windows 2000 and Windows XP, and they both had that problem, different machines, too. So don't worry there, I don't think there is a fix for it.

---

### Post by talking Llama on 2009-04-19
> **Wally_dog said:**
> You should no that the intermittent sound problem is a problem within the game, not Ubuntu. I used to play AoE on Windows 2000 and Windows XP, and they both had that problem, different machines, too. So don't worry there, I don't think there is a fix for it.

My copy of the game does this on Ubuntu. Thought it was Wine or Ubuntu! Thanks for the info. :D

---

