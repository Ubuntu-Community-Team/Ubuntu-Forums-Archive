---
title: "Can't install Dragon Naturallyspeaking 12.5 in Xubuntu 14.04 64-bit"
date: 2014-05-03
forum: Wine
---

### Post by Bill Tetzeli on 2014-05-03
I think I may know the answer to this but I'm not sure.  I was at a friend's house today to install Xubuntu on her Windows 8 computer (HP 2000 Notebook, 64-bit).  I installed the 64 bit version of Xubuntu 14.04 LTS, showed a few of the basics of Linux, then we installed Winetricks and proceeded with installing Naturallyspeaking 12.5.  Unfortunately the installation crashed before completing, yielding this message.

[IMG]http://i138.photobucket.com/albums/q275/laptap3r/Screenshot-05032014-050435PM.png[/IMG]

Now, here's what I read on WineHQ's Apps Database page for Naturallyspeaking 12.5:

*[COLOR=#000000][/COLOR]*> [COLOR=#000000]The download program comes in a single EXE that is, I believe, supposed to distinguish between 32-bit systems and 64-bit systems. Right now it installs in a 32-bit version.
[/COLOR][I][COLOR=#000000]
[/COLOR][/I][COLOR=#000000]Also this comment from Susan Cragin on the same page:[/COLOR][I][COLOR=#000000]

[/COLOR][/I][FONT=verdana]> [COLOR=#000000]NaturallySpeaking is currently a native 32-bit application with 64-bit support. [/COLOR]

[COLOR=#000000]See: [/COLOR][www.nuance.com/naturallyspeaking/support/vista_64bit.asp]("http://www.nuance.com/naturallyspeaking/support/vista_64bit.asp")

[COLOR=#000000]When installing on 64-bit wineprefixes, this may produce errors and failure to install. If it installs, not all features may work on 64-bit that work on 32-bit systems. [/COLOR]

[COLOR=#000000]Suggestion: Install into a 32-bit wineprefix. [/COLOR]
[COLOR=#000000]Here's how. [/COLOR]

[COLOR=#000000]delete or move your current wine prefix and create a clean 32-bit one. [/COLOR]
[COLOR=#000000]WINEARCH=win32 WINEPREFIX=~/.wine winecfg [/COLOR]
[COLOR=#000000]set Windows version to Vista and close [/COLOR]
[COLOR=#000000]winetricks fontfix vcrun2010 [/COLOR]
[COLOR=#000000]Then install Naturally Speaking normally. [/COLOR]

[COLOR=#000000]For now, it runs better and is happier.

Now I get that "WINEARCH=win32 WINEPREFIX=~/.wine" is meant to be run as a typed command in terminal.
Configuring Wine to run in Vista mode is also clear.
What about the next line - is that also supposed to be a typed command, run in terminal?

I'd like to try this method out.  Otherwise I'm thinking I might have to install the 32-bit version of Xubuntu - not sure if that would work or is even advisable.

Anyway, any help would be very much appreciated.  Thanks![/COLOR][/FONT]

---

