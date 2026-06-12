---
title: "DDO patchclient.dll"
date: 2008-02-12
forum: Wine
---

### Post by banished_one on 2008-02-12
I have DDO verion 5 installed im trying to update it via the lotro launcher but i get a 

Error launching patch process, incorrect version of patchclient.dll.

I read in a lotro topic that i need to do following to fix this

wine rundll32.exe SelfPatch,SelfPatch

but when i do i get a

fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!

or 

fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to write pipe!
err:rundll32:main Unable to load L"SelfPatch"

What should i do ?

---

### Post by banished_one on 2008-02-13
does this mean DDO cant update itself ? If thats the case i can load & update it on a windows pc and transfer here but idont want to do that unless i got no choice

---

### Post by Ferrat on 2008-02-13
> **banished_one said:**
> does this mean DDO cant update itself ? If thats the case i can load & update it on a windows pc and transfer here but idont want to do that unless i got no choice

DDO is behind on the patchclient.dll and uses a locked version I've been told but LOTRO book 11 and later uses a new unlocked version that the launcher can use, according to people this new patchclient.dll should work with DDO aswell only getting hold of it is a bit of a pain, there is nowhere that I could find where the dll is availible for download unless you download and install the 8GB+ LOTRO trial >_<

Unless you ask someone to send it to you. 

Also I've been told that LOTRO releases a patch soon and that maybe contain a even better patchclient.dll cause the current won't let the linux launcher update high res grafics so fingers crossed :) 

I updated my game on windows (virtual PC) and just copied the whole folder, a hassle but I got the high res grafics and at least I didn't have to download 8GB+ and install it

---

