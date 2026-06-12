---
title: "Warcraft III troubles. Files transfered from a Windows machine"
date: 2008-07-17
forum: Wine
---

### Post by Horomancer on 2008-07-17
Hello there. I'm wanting to know if there is any hope for me getting my Warcraft III files working again now that i have switched to linux.

I orginaly had my Warcraft III and Frozen Throne installed on a windows vista machine with frozen throne cracked to run from PIGON_LOADER.exe.

When i made the jump to Ubuntu I backed up the entire contents of my Warcraft III folder (minus most of the movies to save space) on a vista laptop. I could load up and play Dota on the laptop just by running PIGON_LOADER without a hitch.

I've now moved all those files onto my ubuntu desktop and here is whre the trouble starts.
I can run Warcraft III with the Frozen throne cd in my drive. I cannot run the actual Frozen Thrown expansion (it cannot locate the cd for some reason while WC3 can). PIGON_LOADER.EXE does nothing in wine but open a small black window for half a second and close it. If i try to re-install Frozen throne, it says i must install Warcraft 3 first.

I have read the threads listing patches to use and changes to wine needed, but I'm not certain I can perform these becuase i do NOT have my orignial warcraft III cd. It is lost to time and a couple of moves. All i have is the Frozen throne expansion cd and all the old patches that I had originally installed some years back on my comp.

Is there any chance of me being able to host Dota games again? Since i can run Warcraft III reliable can i join a Dota game created by someone else?

thanks for your support.

---

### Post by SBFC on 2008-07-17
Not sure what to tell you, other than as far as I know Pigon Loader and Wine don't get along (at least from my experience).

I just have a regular nocd crack (from megagames.com) which is basically just a replacement war3.exe, and everything runs peachy.

---

### Post by Horomancer on 2008-07-18
The No cd patches that are out now, are they for warcraft III or the Frozen throne executable? I'm thinking if i can patch my .exe files on a vista machine then move the files over to my ubuntu machine i can get around the fact that pigon loader doesn't work.

EDIT: Update

ok i did some snooping and found that i could use the new 1.22 patch by altering wine's system.reg file to include

[Software\\Blizzard Entertainment\\Warcraft III]
"InstallPath"="C:\\Program Files\\Warcraft III"

That got me past the error i had before, but now i have a new one.

Error: Unable to patch file Abilities\Spells\Items\AIsp\SpeedTarget.mdx

Any ideas?

UPDATE 2: Success!!
I used the wrong patch >_< (War3ROC_122a instead of War3TFT_122a)

Game is patched and I am in!
Now to fix the networking bugs so i can have a LAN game between myself and someone on my laptop.

---

