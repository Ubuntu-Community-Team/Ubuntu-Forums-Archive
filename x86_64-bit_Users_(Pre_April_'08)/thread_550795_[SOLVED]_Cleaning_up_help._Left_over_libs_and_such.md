---
title: "[SOLVED] Cleaning up help. Left over libs and such..."
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-14
Here's the deal.  I have a light gray desktop background and white fonts.  Yuk, it's hard to see.  I wanted to change the fonts on the desktop to black and leave everything else alone.  I searched the forums...  Couldn't find it...  I googled and found; [Desktop Configurator]("http://www.krakoa.dk/linux-software.html#COG") 

So I downloaded the source, and looked at the dependencies.  I did a synaptic search and installed the missing parts (I think).  I did the ./configure  nor errors, I did the make - no errors, I did the sudo make install (wouldn't work without sudo) and no errors.

The problem is it seems not to have installed.  I can't find it anywhere including the terminal.

Now once again, I have tried and failed to actually compile something and have it work.  I'm and cli loser.  

I just want to clean up all the JUNK I've installed over the past month trying to compile things on my own.

Is there a way to clean up orphan libs and junk I don't actually need with out a manual seek and destroy that could go bad?

Any help would be appreciated.

Thanks.

---

### Post by John.Michael.Kane on 2007-09-14
> **crjackson said:**
> Here's the deal.  I have a light gray desktop background and white fonts.  Yuk, it's hard to see.  I wanted to change the fonts on the desktop to black and leave everything else alone.  I searched the forums...  Couldn't find it...  I googled and found; [Desktop Configurator]("http://www.krakoa.dk/linux-software.html#COG") 

So I downloaded the source, and looked at the dependencies.  I did a synaptic search and installed the missing parts (I think).  I did the ./configure  nor errors, I did the make - no errors, I did the sudo make install (wouldn't work without sudo) and no errors.

The problem is it seems not to have installed.  I can't find it anywhere including the terminal.

Now once again, I have tried and failed to actually compile something and have it work.  I'm and cli loser.  

I just want to clean up all the JUNK I've installed over the past month trying to compile things on my own.

Is there a way to clean up orphan libs and junk I don't actually need with out a manual seek and destroy that could go bad?

Any help would be appreciated.

Thanks.

To remove the files type the commands below.
```
make clean
```

If the above command does not get all the files. Try running the command below.
```
make distclean
```

Also if you want to check further for other orphan files. You can use the guide below.
[HOWTO: Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan")

---

### Post by crjackson on 2007-09-14
> **SD-Plissken said:**
> To remove the files type the commands below.
```
make clean
```

If the above command does not get all the files. Try running the command below.
```
make distclean
```

Also if you want to check further for other orphan files. You can use the guide below.
[HOWTO: Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan")

Excellent.  I'll do this when I get home from work.

---

### Post by crjackson on 2007-09-15
Wow, it actually did install the program.  It just didn't give me a launcher right away.  Now I have to start a thread to figure out why I still can't change my desktop icon text to black or any color other than white.

---

