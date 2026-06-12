---
title: "[SOLVED] Command And Conquer .Red Alert 3 Licensing Server"
date: 2008-12-01
forum: Wine
---

### Post by iOverflow on 2008-12-01
Hello I have a huuuge problem with my RA3(Red Alert 3)
 
I have done all (if not all then most) instructions in this site
( [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14371](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14371) )
*I have done the Wine-Patch instructions as well as the Wine-Hacked Instructions with the same results from both...
*I am also using Ubuntu 8.10 (which is supposed to be network enhanced?)

And Continue to have a problem.
My problem is related to the licensing of Red Alert 3, Whereby the first time you install from the original disc Red Alert 3 it requires internet Acess.
Now I have done the winhttp dll override to buildin in winecfg.
And I have a problem as it continues to ask for a Internet connection.

From this I have further investigated and found out that under my process , and in the Red Alert 3 bar, it says  " inet_wait_for_connect " under waiting channel.

I have checked this " inet_wait_for_connect " and found a website related to it ( [http://www.erg.abdn.ac.uk/users/gerrit/dccp/notes/closing_states/short_lived_connections_bug.txt](http://www.erg.abdn.ac.uk/users/gerrit/dccp/notes/closing_states/short_lived_connections_bug.txt) ) and from what I can gather is that my DCCP connection is shortlived (as stated in the title of that site) .

The problem is I have no idea how I'm going to fix this... 
If anyone can give me any advice or point me in a direction to fixing this , I will welcome it full heartedly!

---

### Post by ryry46d9 on 2008-12-01
hmmm its bin along time since I played any of the red alerts 

I thought you only needed internet for updates and you could op out to not register on line

---

### Post by iOverflow on 2008-12-01
I think it's because EA is making the Command and Conquer series now that's why.
Also because RA3 has Online Coop Playing mode.

But You need to activate the internet licensing in order to go online otherwise your online function is ruined inside the game, and I really want to play online!
The Internet licensing is only needed the very first time you go onto red alert 3 after a clean install...

---

### Post by iOverflow on 2008-12-04
I used wine 1.1.8 and solved this issue by hooking up my pc with my friends internet connection.

I think it could've been my internet connection blocking ports or something. But it was definantly the networking.

---

### Post by Rob-e on 2008-12-07
"using your friends internet" isnt really solving the problem, i am seeing what i can find because Im having the same problem

---

### Post by iOverflow on 2008-12-13
Well I only had to get past the "licensing" stage of the game ,after that playing and stuff online was fine.

I can list the differences between my friends connection and my connection if you want?

Although I don't want to recreate the problem to investigate more specificly due to the new "DRM" idea, that is to say you only have 5 installs that are able to play online, and the rest offline.

---

