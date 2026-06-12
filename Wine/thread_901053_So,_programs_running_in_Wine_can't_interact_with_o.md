---
title: "So, programs running in Wine can't interact with other programs?"
date: 2008-08-26
forum: Wine
---

### Post by shatteredmindofbob on 2008-08-26
Not so much looking for help, but I'm just curious as to whether this is correct and the technical reasons as to why. 

I've noticed that anything running in Wine can't really interact with other programs. For example, I can't drag an image on the desktop into Photoshop. 

..or am I doing something wrong?

---

### Post by YokoZar on 2008-08-26
> **shatteredmindofbob said:**
> Not so much looking for help, but I'm just curious as to whether this is correct and the technical reasons as to why. 

I've noticed that anything running in Wine can't really interact with other programs. For example, I can't drag an image on the desktop into Photoshop. 

..or am I doing something wrong?
Think about what happens for a program when you drag and drop something.  If everything is going well, when you drag that icon on your desktop onto a program, then your window manager has to send a message to that program ("hey, do something with this file").  Then the program has to respond in some way ("ok" or "whoa, I don't know what to do, make it look like the drag and drop failed").

Now, with most programs, those messages are fairly standard - every window manager sends the same message when you drag and drop something, so drag and drop should work on every desktop environment after programming it once in an application.  That is, every Linux application.


For Wine apps, though, some magic has to happen in between.  The window manager can't send that message to the Wine program directly, since it doesn't speak Linux.  So instead it has to send it to Wineserver, which then translates Linux into Windows, sends the Windows version of the message to the program, and then translates its response back to the window manager.  But Wineserver has to do more than that, since it's not just the message that needs to be translated - the pathname has to be converted from Linux to Windows (so something like /home/user/Desktop/Picture.jpg turns into Z:\Desktop\picture.jpg).


All of that requires special code inside Wine to handle that translation.  Code that's...not exactly done.  This page on the Wine wiki includes a bunch of "Desktop Integration" projects in various stages of completeness.  You can see Drag and Drop listed there.

Incidentally, some drag and drop functions do work, like dragging from one Wine program to another.

---

### Post by shatteredmindofbob on 2008-08-26
> **YokoZar said:**
> Think about what happens for a program when you drag and drop something.  If everything is going well, when you drag that icon on your desktop onto a program, then your window manager has to send a message to that program ("hey, do something with this file").  Then the program has to respond in some way ("ok" or "whoa, I don't know what to do, make it look like the drag and drop failed").

Now, with most programs, those messages are fairly standard - every window manager sends the same message when you drag and drop something, so drag and drop should work on every desktop environment after programming it once in an application.  That is, every Linux application.


For Wine apps, though, some magic has to happen in between.  The window manager can't send that message to the Wine program directly, since it doesn't speak Linux.  So instead it has to send it to Wineserver, which then translates Linux into Windows, sends the Windows version of the message to the program, and then translates its response back to the window manager.  But Wineserver has to do more than that, since it's not just the message that needs to be translated - the pathname has to be converted from Linux to Windows (so something like /home/user/Desktop/Picture.jpg turns into Z:\Desktop\picture.jpg).


All of that requires special code inside Wine to handle that translation.  Code that's...not exactly done.  This page on the Wine wiki includes a bunch of "Desktop Integration" projects in various stages of completeness.  You can see Drag and Drop listed there.

Incidentally, some drag and drop functions do work, like dragging from one Wine program to another.

Ah, so it's possible...just...complicated. The path conversion definitely sounds scary and I'm surprised I didn't think of that. I guess because of how well implemented some thing are i.e. Photoshop is fooled into thinking /home/myname/photos is c:\documents and setting\etc...

Thank you for the explanation.

---

