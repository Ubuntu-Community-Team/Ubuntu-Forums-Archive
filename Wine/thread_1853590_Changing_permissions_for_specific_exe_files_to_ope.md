---
title: "Changing permissions for specific exe files to open in Wine"
date: 2011-10-02
forum: Wine
---

### Post by gringo loco on 2011-10-02
I use Ubuntu 11.04 as my primary OS and the original windough$ is still an option (for the time being). What I would like to do is open a selected number of the exe files (currently in the Windough$ partition)  using wine in Ubuntu. When I try to do this, I get a permission error. I know that there must be a simple way to change these permissions [make them executable] but I'm going crosseyed reading the "how to" pages. Can someone give me the code I need to use in order to make either specific exe files or all exe files in specific folders executable in an Ubuntu/wine environment?

---

### Post by philinux on 2011-10-02
Moved to Wine forum.

---

### Post by ergo-proxy on 2011-10-03
What do you mean by open exe files? Do you mean execute them or open in a notepad etc?

---

### Post by gringo loco on 2011-10-07
execute them - I want to run a windows program in wine. When I try to do this it says I don't have permission.

---

### Post by Toz on 2011-10-07
The simplest way is to open a terminal window, type **wine ** (wine plus a space), then drag and drop the icon on the terminal window. Press enter to execute the program.

---

### Post by gringo loco on 2011-10-08
OK I tried that and got two results. The first result was a pop-up message telling me that the file was not marked as executable. I believed it and pressed OK. The message went away and I tried again. this time i got a message in the terminal
 "wine: Install the Windows version of Mono to run .NET executables"

still confused!!

---

### Post by Toz on 2011-10-08
What application are you trying to run? For most windows programs, you won't be able to run them directly from your windows partition - you will need to install them in a wine environment.

---

### Post by Suroh on 2011-10-09
Right click the .exe properties then go the permision tab then click is executable if it's not already! Just for the fun of it right click the .exe then click open it with wine like that or as stated above through the terminal for an output :) Hope that helps

---

### Post by gringo loco on 2011-10-22
OK I tried the terminal idea - same result
and the right click then open in wine - same result

then I right clicked the exe file and opened properties and noted that it was not marked as an executable file. I clicked on the little check box and the check mark appeared and then immediately disappeared. I could not get the box to stay checked.

The program that I am trying to run is a handy little free program that downloads youtubes and converts them to whatever format I choose. I have it installed in the windows partition of this computer and it is a hassle to shut down and open in windows just to download something my friend has put on youtube. I have searched all over for a linux based program that does this but no luck there either.

I suppose the next thing to try is downloading it again into the ubuntu section of the HD. If I'm lucky, one day I'll be able to eliminate the windough$ partition entirely. The only reason I left it was this program and my scanner which doesn't work in ubuntu.

---

### Post by scania_gti on 2011-10-22
Your'e right, windows programs from windows disk Wine not have permisions to launch. Copy instalation file to linux partition and install it with Wine.

---

