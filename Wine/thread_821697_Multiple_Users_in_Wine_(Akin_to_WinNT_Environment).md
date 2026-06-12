---
title: "Multiple Users in Wine (Akin to WinNT Environment)"
date: 2008-06-07
forum: Wine
---

### Post by mini_g on 2008-06-07
Hi all,

I got to thinking how I could enable multiple users to use the same WINE directory on a computer, and I got to the point where I could allow all of the selected ones to use the same .wine DIR.

If I were to create '/home/.wine' and link the users that are needed to use the same .wine DIR to that directory via a link (ln -s /home/<user>/.wine /home/.wine ).

Now, my only issue would how would one have WINE view each user, as a seperate user that's accessing the same "setup"? (Akin to the way that Windows WinNT (NT, 2000, XP, & Vista) works each user)

Thank you!

---

### Post by doorknob60 on 2008-06-07
I've always wanted to know that, I'll keep an eye on this thread *bookmarks*

---

### Post by doorknob60 on 2008-06-16
Bump! No, I didn't forget about this :P

---

### Post by cogadh on 2008-06-16
Okay, this is just a theory, and I've never tried to do it myself, but you could try this:[LIST=1]
[*]Create a .wine directory in its own partition, separate from the /home directory
[*]Change the permissions on the .wine directory from a specific user to everyone
[*]In each user's home directory, create a ".wine" symlink that connects to that separate .wine directory
[*]Create a profile directory for each user in .wine/drive_c/windows/Profiles/<Linux username>[/LIST]
In theory, each user should be able to access that Wine directory as if it were their own. The only problem might be is if Wine changes the directory permissions each time a user tries to access it.

EDIT - I've though about this a little more and there would still be problems with Wine accessing certain things like its link to "My Documents", which usually defaults to the user's home directory. To get around some of it, you could probably do this instead:[LIST=1]
[*]Create a real .wine directory for each user in their home directory
[*]replace the ~/.wine/drive_c, ~/.wine/dosdevices directories and ~/.wine/system.reg file with symlinks to the same directories and file in the separate .wine directory you created earlier
[/LIST]
If it works, each user would have their own user.reg and userdef.reg, which would give them the proper access to Wine's "My Documents" and such, but all users would use common system files and program directories. However, you would have to manually create menu shortcuts on each user's menu for any applications you install. 

EDIT 2 - Almost forgot, if you try my second idea, you do still need to create those profile directories for each user in the separate .wine directory.

---

### Post by mini_g on 2008-06-17
Sorry for being quiet on this quest, RL got to the forefront of my time & thought. (Doesn't help that my brain has been fried as of late due to the lack of sleep)

I have a separate copy of this question posted on **comp.emulators.ms-windows.wine**, so if you wish to check out the thread, feel free. (The first post was posted on 6/7/08)

In shorthand (for those who don't have Usenet access), I got two response,

> **Bob Bob]
Jon
 
Sorry I dont really have an answer for you. I am more trying to clarify.
I guess you mean multiple users using (say) the same Program/System
stuff but having a user profile that you would normally store in
"C:\Documents and Settings?"
 
I would guess that for that to happen you dont link the entire .wine
directory for each user but only those common "read only" sections like
"C:\WINNT" "C:\Program Files" and so on. I cant imagine this not working.
 
Cheers Bob
[/quote]
[quote=My reply to Bob Bob]
> Jon
 
> Sorry I dont really have an answer for you. I am more trying to clarify.
I guess you mean multiple users using (say) the same Program/System
stuff but having a user profile that you would normally store in
"C:\Documents and Settings?"

 
Yep.
 
 
> I would guess that for that to happen you dont link the entire .wine
directory for each user but only those common "read only" sections like
"C:\WINNT" "C:\Program Files" and so on. I cant imagine this not working.
 
> Cheers Bob

 
I thought about that, however the programs that I was thinking about using under this configuration need to have a common registry.
 
~Jon
[/quote]
[quote=And Bob Bob's reply]
Hi Jon
 
My wine version is a litle old so I dont know if the registry file
location has changed. If it hasnt though there is no problem using
symlinks for those files as well...
 
(ie ./wine/user.reg, ./wine/system.reg)
 
 
Cheers Bob
[/quote]
[quote=ljkramer]
I have done this slightly differently.  I gave (as root) each user
their own ~/.wine and a symlink to /home/.wine-doors  so they can each
have their own settings and I started each user with their own copy of
user.reg and userdef.reg with rw access.  Then, in the user's  ~, ln -
s /home/.wine-doors and in each user's ~/.wine ln -s /home/wine-doors
wine-doors said:**
> 
[quote=And my reply to both]
I have to apologize if I wasn't being clear enough...
 
My basic plan of action already has the universal portion of the registry and the filesystem symlinked within /home/.wine/ along with the WINE filesystem.
 
Also, my understanding of how the WinNT registry works is somewhat so-so, so please bear with me if I'm making mistakes here.
 
My thought (this is with some pondering + some investigation) was to possibly have the [HKEY_CURRENT_USER] tree and the [HKEY_USERS][USER ID] branch be symlinked/unique for each user that used /home/.wine/ as it is in WinNT.
 
I don't believe that were to happen if I were to leave each user their ~/.wine/user.reg physically intact, and symlink everything else to the common /home/.wine/
 
As a side note, how does one create a new user registry profile within WINE? I noted that each user's personal registry assigns them to be [S-1-5-4].
 
Also, with some investigation I figured out that each user would need to have a unique /home/.wine/drive_c/windows/profiles/<USER>/
 
I need to do some serious thinking if this idea of making WINE act like there are more than one user using it in one area is feasible...
 
MSDN here I come!
 
>_<
 
~Jon
 
Note: I'm currently running 1.0 rc4.
Also: The way that the common .wine directory & registry would be used, there should be no possiblity of collisions.

I got WINE-Doors installed that day, and have been kinda idling on this since, as some chickens needed to be kicked out of the house ASAP *(Don't ask)*, and I've been getting the 2.6.25 kernel going on my lappy, as I'm tired of not being able to fully use it.

I'm thinking trying ljkramer's suggestion about creating "bottles", as it may be easier.

cogadh, I'm sorry about not being able to parse your question right now, as my brain isn't able to easily process your idea.  I hope that my Usenet rephrasing may have answered your thoughts.

So far, all I've done is installed WINE-Doors and found two MSDN pages on the Registry: [Page 1]("http://msdn.microsoft.com/en-us/library/ms725488(VS.85).aspx"), [Page 2]("http://technet2.microsoft.com/windowsserver/en/library/a1377b7d-277f-47ba-adde-96ee781be5b31033.mspx?mfr=true"), [and a search page that may contain leads to more information]("http://clusty.com/search?input-form=clusty-simple&v%3Asources=webplus&query=msdn+registry+windows").

---

### Post by cogadh on 2008-06-17
Actually, I didn't have a question, I had a suggestion to to answer yours. Basically, my answer was virtually the same as what you have attempted to do already, but without the addition of wine-doors. I honestly don't understand the need for wine-doors in this situation. 

On a side note, MSDN information about the Windows registry really won't help you much. The Wine registry is not the same as the Windows registry, with the exception of a few things in system.reg that pertain to application installs.

---

### Post by manishanchan on 2008-06-17
I didn't ever tried it before but i would like to tell that through windowsNT it might work

---

