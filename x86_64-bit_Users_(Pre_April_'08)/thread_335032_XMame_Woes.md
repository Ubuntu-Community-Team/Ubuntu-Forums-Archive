---
title: "XMame Woes"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlacroix on 2007-01-09
Hello, I installed xmame and Kxmame today and am having some problems with it.

1.) No matter what I do, I can't set up the controller. In KXMame I went into the settings and enabled it, it's a no go.

2.) If I change directory to the directory where my roms are stored (/home/jeremy/Documents/Roms/Arcade) and run a command like "xmame mk2.zip" it cannot find the files. If I load the same rom in Kxmame, it loads flawlessly. I have Kxmame set up to look in the /home/jeremy/Documents/Roms/Arcade directory also.

Also if I do a direct path command like this: "xmame /home/jeremy/Documents/Roms/Arcade/mk2.zip" it still can't find the files.

3.) Kxmame does not have an option to load Ultimate Mortal Kombat 3. I'm okay with just doing this from the command line if necessary. I was thinking I could make a shell script, something simialir to:

[/code]
cd /home/jeremy/Documents/Roms/Arcade
xmame mk2.zip
[/code]

And then I could set up icons on my desktop for each game. However, that won't work as of now because the xmame command won't notice the roms in the directory I run it from.

Any ideas?

---

