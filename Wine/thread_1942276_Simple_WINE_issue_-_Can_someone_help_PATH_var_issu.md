---
title: "Simple WINE issue - Can someone help? PATH var issues?"
date: 2012-03-17
forum: Wine
---

### Post by SweetBearCub on 2012-03-17
I'm using WINE to play World of Warcraft on a private server. Because of the way that Blizzard designed their software, an executable loader must be used to actually load the game.

The game is installed to in ".wine/drive_c/"Program Files"/"World of Warcraft". The game was copied from my Windows partition, not officially installed, so there is no shortcut in my menus.

If I open the folder and run the loader (which is in the main WoW folder), everything works fine. If I make a link to the loader and copy that link to my desktop - Which is the way I'd prefer to launch it - I get .NET framework errors about not being able to find the main WoW executable that the loader is looking for.

Perhaps if I could find a way to change the "working directory" of the link?

In WINE's registry, I have the PATH string set as "c:\windows\system32;c:\windows;c:\Program Files\World of Warcraft", which seems to be correct per WINE's documentation. But it still does not work.

Help!

---

### Post by Nytram on 2012-03-17
One way to do it is to create a script which, like you mention, will change directory and then execute the loader.

Create a file in a text editor, call it wow.sh or whatever, and include this:

> 
cd "/home/username**/.wine/drive_c/Program Files/World of Warcraft"
wine loader*


*Use the filename of the loader program.
**Replace with your own username.

After creating your script, you need to give it executable permission, which can be done by right clicking the file and accessing its properties.

Let me know if you need more detailed instructions.

---

### Post by Elfy on 2012-03-17
*Thread moved to **Wine**.*

---

### Post by SweetBearCub on 2012-03-17
> **Nytram said:**
> One way to do it is to create a script which, like you mention, will change directory and then execute the loader.

Create a file in a text editor, call it wow.sh or whatever, and include this:



*Use the filename of the loader program.

After creating your script, you need to give it executable permission, which can be done by right clicking the file and accessing its properties.

Let me know if you need more detailed instructions.


That's an excellent idea.

I tried a script as you suggest, but got the same .NET framework error about not being able to find the main WoW executable. However, if I open a terminal window and type out both lines exactly as they appear in the script - It works!

I'm confused.

---

### Post by SweetBearCub on 2012-03-17
> **forestpiskie said:**
> *Thread moved to **Wine**.*

Thanks.

---

### Post by Karlchen on 2012-03-17
Hello, SweetBearCub.
> I tried a script as you suggest, Could you be bothered to post the exact content of _your_ script, please.

>  but got the same .NET framework error about not being able to find the main WoW executable. Could you be bothere to post the exact error message which is displayed, please.

>  However, if I open a terminal window and type out both lines exactly as they appear in the script - It works! This suggests that you have not granted execute permissions to your script?!
Cf. Nytram's advice given before > After creating your script, you need to give it executable permission,  which can be done by right clicking the file and accessing its  properties.Kind regards,
Karl

---

### Post by Nytram on 2012-03-17
Doh my mistake, it's necessary to give the absolute path for the **cd** command.

> 
cd "/home/username**/.wine/drive_c/Program Files/World of Warcraft"
wine loader* 


*Use the filename of the loader program.
**Replace with your own username.

---

### Post by SweetBearCub on 2012-03-17
> **Nytram said:**
> Doh my mistake, it's necessary to give the absolute path for the **cd** command.



*Use the filename of the loader program.
**Replace with your own username.

Yes!

Adding the absolute path made it work! Thank you!

But why would that be so, when the previous commands worked fine when typed into the terminal in my home folder? That makes no sense to me.

Also, is it possible to suppress the 'Run in Terminal', 'Display', 'Cancel, and 'Run' options (while defaulting to run), and to give it the link the icon out of the World of Warcraft executable?

---

### Post by dino99 on 2012-03-18
note that wine path are written with some custom rules: to get the good writing, use the Tab key to complete the path to be sure about slash, double slash, space, %, \, ....

---

### Post by Karlchen on 2012-03-18
Hello, SweetBearCub.

[quote=Nytram]cd "/home/username**/.wine/drive_c/Program Files/World of Warcraft"
wine loader*                       [/quote]
[quote=SweetBearCub]Adding the absolute path made it work! [...]
But why would that be so, when the previous commands worked fine when  typed into the terminal in my home folder? That makes no sense to me.[/quote]
Pretty simple:

You launch the gnome-terminal. By default, it will open and your current path will be your home folder. Let us assume the home folder is /home/SweetBearCub.
Now you use the command ```
cd ".wine/.wine/drive_c/Program Files/World of Warcraft"
``` et voilà, you are in the right folder.

Yet, when you launch the script from some random folder the only way of making sure that you go to the right folder is by using the absolute pathname.

Current path: /home/SweatBearClub
Command: cd ".wine/drive_c/Program Files/World of Warcraft"
Result: works

Current path: /tmp
Command: cd ".wine/drive_c/Program Files/World of Warcraft"
Result: does not work
Reason: The target does not exist inside /tmp.

Current path: /tmp
Command: cd "/home/SweatBearClub/.wine/drive_c/Program Files/World of Warcraft"
 Result: works
 
Kind regards,
Karl

---

### Post by Nytram on 2012-03-18
> **SweetBearCub said:**
> 

Also, is it possible to suppress the 'Run in Terminal', 'Display', 'Cancel, and 'Run' options (while defaulting to run), and to give it the link the icon out of the World of Warcraft executable?

No problem glad it worked for you.

To supress that dialog box and default to Run, you need to go into Nautilus preferences (Edit/Preferences) select the Behaviour tab and choose "Run executable text files when they are opened."

To change a program's icon, right click on the file and select Properties, then click on the current image (it's within the Basic tab in the top-left corner.)

HTH.

---

