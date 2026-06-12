---
title: "How to start an .exe application with additional commands?"
date: 2016-05-06
forum: Wine
---

### Post by TechGhost on 2016-05-06
It has been quite a while since I used Windows, but I remember I could edit shortcuts, and add things like "name.exe" -power (just as a quick example). 

I remember this made it possible to load additional settings for applications etc. But how can I do something like this with Wine in Ubuntu? I need to load an .exe file, with a .dll file attached to it. The only information I have is that I need to run the following: 

Run the .exe file with [FONT=Verdana, Arial][SIZE=2]"/p:name.dll"[/SIZE][/FONT]

How do I do this?

---

### Post by TechGhost on 2016-05-08
So I tried to run cmd.exe from Wine and run it through there, but it wont open the original .exe file because it does not know that it needs to use Wine for it. This leaves me baffled, as I cant find any method to open an exe file with additional arguments, in a Wine env. 

Anyone has any clue?

---

### Post by David_Farkas on 2016-05-09
It was a while I used Wine but I remember that I solved something similar with wineconfig. With wineconfig you can define different environments for different applications and it should be installed if you have wine installed. So just open it, browse the *.exe file and set the command line arguments. Or if you prefer doing it through the command line check this:
[https://wiki.winehq.org/FAQ#How_do_I_pass_command_line_arguments_to_a_program.3F](https://wiki.winehq.org/FAQ#How_do_I_pass_command_line_arguments_to_a_program.3F)

---

