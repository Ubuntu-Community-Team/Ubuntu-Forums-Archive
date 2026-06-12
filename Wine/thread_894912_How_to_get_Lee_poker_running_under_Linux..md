---
title: "How to get Lee poker running under Linux."
date: 2008-08-19
forum: Wine
---

### Post by j0mpa on 2008-08-19
Hello every one. 
Iam gonna write a guide on how to get Lee Poker working under linux.
Before we begin i just want to appologize for my bad english and i hope you can stand it :) 

First of this guide is based that you have 3D support and wine installed on you machine. If not search the forum on how to install video drivers.

First step is to find out if you got 3D support on you linux machine.
Open a terminal and enter this command:
glxinfo | grep direct rendering
If you get 
direct rendering: Yes

Then you can go to step 2.
Download Lee poker client from here to your desktop.
[https://www.leepoker.com/client/leepoker_en.exe](https://www.leepoker.com/client/leepoker_en.exe)
Then open a terminal enter command:
wine /home/"user"/Desktop/leepoker_en.exe
Follow the instruktions.

Step 3.
After installation Lee poker will run automatic otherwise
go to a terminal and enter
wine /home/(user)/.wine/drive_c/Program Files/Lee Poker/LeePoker.exe
Now the client will start to update. It will try to run a couple of times then it will fail so just click ok and then go to /home/(user)/.wine/drive_c/Program Files/Lee Poker/Download/update/ copy all files and overwrite to /home/(user)/.wine/drive_c/Program Files/Lee Poker/
Now when you start the client i had some problems whit the graphics but i've found a way to make it stable so go to step 4.

Step 4. 
Go back to the terminal enter:
regedit
Browse to: 
HKEY_CURRENT_USER/Software/Wine
Right click the wine folder and add "new key" rename it to:
OpenGL <--- Name must be exactly like that.
Doubble click the OpenGL folder go to the right screen.
Right click any where i the screen add "new string" rename it to:
DisabledExtensions
Double click it and add folowing under value data:
GL_ARB_vertex_buffer_object 
Quit regedit start Lee Poker again and now enjoy.

Hope this guide helped you and see you at the poker tables :)
Good luck

---

