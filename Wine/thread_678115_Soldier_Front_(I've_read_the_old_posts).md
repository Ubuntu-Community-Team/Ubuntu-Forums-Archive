---
title: "Soldier Front (I've read the old posts)"
date: 2008-01-25
forum: Wine
---

### Post by Shmargin on 2008-01-25
I was wondering if anyone can give me any advice on running Soldier
Front? I googled around, but all the posts were old, and they said it
was pretty much impossible, but I have a feeling that now it should be
possible. Maybe. I'm till a Linux noob, coming from 18 years of DOS
and Windows use.

Reason being, IJJI (the guys behind SF) has a system where in order to
play, you log in on their website [http://www.ijji.com](http://www.ijji.com) and click a
"PLAY NOW" button to start the game. Before, they only let you use IE,
pretty much screwing you over if you were on Linux and wanted to try.

But now, they let you use Firefox. So far, what I have been able to
do, is install the Windows version of Firefox on Wine, and log into
the website, I can download the IJJI Launcher (required to play) and
the games files, and the games updates. I can click the PLAY NOW
button, and the launcher pops up, and loads things up, patches if
necessary. GameGuard then pops up, and this is where the problem seems
to lie. GameGuard loads up, and updates, but then gives me:

 "GameGuard Error : 114 GameGuard Initialization Error. Try rebooting
and executing the game or close the program considered to cause a
collision."

On my terminal, Wine scrolls the following:

fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:LsaOpenPolicy ((null),0x7d5f3b1c,0x00000001,0x7d5f3b38)
stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wininet:INET_QueryOptionHelper Stub! 75
fixme:wininet:INET_QueryOptionHelper Stub! 40
fixme:reg:GetNativeSystemInfo (0x757ecb) using GetSystemInfo()
err:seh:setup_exception stack overflow 116 bytes in thread 0026 eip
7bc6f462 esp 00240f8c stack 0x241000-0x350000

Now, while I was looking around, I saw some old posts saying that
GameGuard wont work in Wine "Period" according to at least one person.
But I find that at least a little hard to believe because I can run
Silkroad Online (a mmorpg) and that game uses GameGuard also, but
GameGuard loads up, patches, and initializes just fine for that game,
and the game plays fine also.

One thing that might be of interest to anyone who might want to help
me, is that in order for Silkroad to work in Wine, you have to run
Wine set to Windows 98 compatibility. But in Soldier Front, to get it
as far as I did with the loading things up, I had to have Wine set for
Windows XP compatibility.

I'm also running Wine using DLLs taken from one of my computers actual
Windows/System32 folder, on an XP machine, if that helps.

Sorry if I left anything out that might help someone fix this problem,
like I said, I'm still a Linux noob, and programming and codes are
even more above my head.

But some feedback would be great, this is one of the only games I was
playing on Windows, that I cant get to load up on Wine.

Thanks in advance. 

(I also understand Wine is extremely unstable, and how its insane  that it works period, but I've had so much luck with everything else I've tried, I'm just determined to get this game going, thanks for understanding)

---

